---
title: "Howto: Ubuntu Intrepid in VMware Fusion"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hajk on 2008-10-26
**Ubuntu Intrepid in VMware Fusion**
This Howto works as described on my MacBook Pro 4,1 and should also work on other Apple MacIntel computers with minimal changes.

**VM setup**
Virtual HDs are best specified as "split and sparse" (the default), with which they start small and are expendable to their maximum size as the
need arises, all of which in chunks of at most 2GB in size. This will make HD maintenance easier as well, since compaction (or disk shrinkage)
then requires only 2GB additional disk space. But do specify a maximum size sufficient for future needs, even if not used at first, as changing
this later is complicated.

VMware Fusion allows the virtual processor to shadow the real one, or 64-bit dual core in case of the MBP C2D processor. Using all cores in the
VM is not recommended, however, since the virtual cores must synchronize with the real ones under Mac OS X control, leading to a performance hit
of some 30%. So, leave at least one of the cores entirely for Mac OS X tasks, meaning that on an MBP the VM should only use a single-core
virtual 64-bit processor.

The amount of RAM allocated to a VM depends on how many VMs will run simultaneously; if just one, then half of available RAM could be a good
choice. My current choice is 1.5GB (1536MB) out of a total of 4GB. Video RAM is already by default the maximum of 128MB (this can be specified in
bytes in the ".vmx" file for the VM). Video performance in the VM is limited, e.g. no OpenGL acceleration...

A shared internet connection (via NAT) is the default, which sets up a 172.16.191.0/8 sub-network with Mac OS X 172.16.191.2 acting as gateway.
This works fine as long as the VM doesn't have to be accessible from outside (with SSH or FTP, say). VMware Fusion allows some sort of printer
sharing, but I don't enable this, since I prefer to let CUPS (in System - Administration - Printing) find my network printer.

It is worthwhile prior to installing Ubuntu to change the boot order in the BIOS of the freshly-created VM: CD-ROM before virtual HD. Enter the
BIOS by hitting fn-F2 after starting it. Doing this later, when the OS has been installed, will be much more difficult. Booting from a CD-ROM
will have its uses when things go wrong...

**Installing Ubuntu**
Installing with the Ubuntu AMD64 8.10 (Intrepid) desktop CD (I used the Release Candidate) was just standard and uneventful, except that upon
rebooting the VM hung for several minutes with a black screen. Just wait, then the message "acpid: exiting" appears, after which shutdown is
immediate and the reboot starts as per usual. This behaviour also occurs with the kernel installed in the VM. Using the "acpi=off" boot option 
does not change this, so a solution is not yet available. So, be prepared for now to wait it out for a few minutes when shutting down or rebooting.

**Video**
The Xorg vmware video driver is installed by default, but does not automatically identify the correct virtual screen resolution. This 
requires editing /etc/X11/xorg.conf. First, add to the Monitor Section```

        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 75.0
```
Next, change the Screen Section to```

        Device             "Configured Video Device"
        DefaultDepth       24
        SubSection         "Display"
                Depth      24
                Modes      "1440x900"
        EndSubSection
```
After logging out or rebooting Xorg will come up, and stay up, in the correct 1440x900 screen resolution at 60Hz for my MBP.

**Keyboard**
Keycodes for the MBP keyboard have changed once again in the latest Xorg included in Ubuntu Intrepid, so make sure to select the Apple 
MacBook/MacBook Pro keyboard in System - Keyboard - Layout. Most keys now work as expected on my US English keyboard, including the right mouse
click by holding down Ctrl while clicking.

Yet, the BackQuote/Tilde key (next to the Z-key) is not yet right. I also need the Euro sign, various accented characters, and a one-finger right
mouse click. I fix this with the script /usr/local/bin/keyboard```

#!/bin/sh



## Keyboard modifications at startup to MacBook/MacBook Pro
## Make left Apple key the third-level chooser
xmodmap -e "keycode 133 = ISO_Level3_Shift"
# Make right Apple key the compose key
xmodmap -e "keycode 134 = Multi_key"
# BackQuote and Tilde as printed
xmodmap -e "keycode 94 = grave asciitilde"
# Make right Alt-Option key the right mouse click...
xmodmap -e "keycode 108 = Pointer_Button3"
xkbset m
# ...requires xkbset package
```
The *xev* command (and package) can be used to check for the actual keycodes on other MacIntel machines. The script must be made executable
by all with```

sudo chmod a+x /usr/local/bin/keyboard
```
and the */usr/local/bin/keyboard* command must be added in System - Preferences - Sessions to the start-up programmes. Next, open the System
- Preferences - Keyboard menu, and in Layouts add the EuroSign to the E-key; and in Mouse Keys enable using keys to move the mouse pointer. The
*keyboard* command (as user) will now enable all of this without first having to log out.

**VMware Tools**
I like to use the open VMware Tools packages, *open-vm-source*,  *-tools* and *-toolbox* that have made it into the Intrepid repositories. Compile and install the modules with```

sudo aptitude install module-assistant debhelper dpatch
sudo m-a prepare
sudo m-a a-i open-vm
```
That last step has created and installed a modules package (in /usr/src), which put a set of
kernel modules in the /lib/modules/2.6.27-7-generic/misc/ directory.  The modules package is listed in the package manager under Obsolete and Locally Created Packages. Note that the modules must be recompiled (just the two *sudo m-a* command lines) when a new kernel version is 
installed; this is not needed when the new kernel is just an update of the existing 2.6.27-7-generic version.

The modules are loaded through the *open-vm-tools* package. Check with command *lsmod |grep vm* that five open-vm modules are now present and loaded. This will happen
automatically from now on through the */etc/init.d/open-vm-tools* script.

Finally, *open-vm-toolbox* provides the "vmware-toolbox" command with which to shrink the virtual HD, see later.

**Shrinking a virtual disk**
Virtual HD usage in a VM differs considerably from that of the physical HD, as files deleted on the virtual HD may still occupy space on the
physical HD. The latter space must be reclaimed by means of a shrinking process. Luckily, *open-vm-tools* can initiate this from within a
running VM.

In a terminal run the command```

sudo vmware-toolbox
```
choose the Shrink tab, select the partition(s) to shrink and hit the Shrink button. Choosing the root partition ("/") will also shrink any
other partitions mounted under root. User approval will be asked before the final shrink process is started.

Note that shrinking is a two-stage process. First those parts of the virtual HD that are to be retained are marked, filling the virtual HD 
completely in the process (there is a harmless message to that effect). Then the underlying VMware Fusion, running in Mac OS~X, takes over to 
effect the actual shrinking.

Have fun!

---

