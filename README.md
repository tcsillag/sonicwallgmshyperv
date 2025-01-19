This project is to create a kernel for the Sonicwall GMS appliance with HyperV compatibility.

Problem:

The kernel shipping with the GMS appliance 9.3 has not drivers for HyperV network interfaces.

Solution:

The original config used to build the kernel was extracted with this tool:
https://stuff.mit.edu/afs/sipb/contrib/linux/scripts/extract-ikconfig

Added HyperV NIC support (both normal and legacy) to the config, also enabled additional HyperV features.
Just for reference: the legacy network interface needs the tulip kernel module, as it is a 21140 chip based NIC (not e100 as I initially expected).
The resulting .config is available here if needed.

Install:

The compiled kernel can be copied to the /dev/sda1 partition of the appliance as /00/vmlinux (make sure to backup the original).

Note:

If you need to increase the size of the data disk like me, it's a simple LVM extension to a new disk and it is officially supported:
https://www.sonicwall.com/support/knowledge-base/how-to-expand-the-hdd-of-a-gms-virtual-appliance/170502427615315
