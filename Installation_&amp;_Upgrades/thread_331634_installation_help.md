---
title: "installation help"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by cyberkitty on 2007-01-04
i installed ubuntu 6.10 using vmware workstation but i'm having problems installing vmware tools that are necessary for graphics quality. basically my need is this: how do u install  tarballs tar.gz? the help files are not that helpful.


kitty

---

### Post by Sqwishy on 2007-01-04
> **cyberkitty said:**
> how do u install  tarballs tar.gz? the help files are not that helpful. I don't suggesnt you do that, usually the source code is in the tarballs and installing from the source is somewhat risk. But if you want to install it from the source you need to run these commands in the folder of the extracted tarball
```

./configure (should tell you what dependacies you need, look for then in synaptic and try to get the 'thingy**-dev**' package)
make
make install-schemas
sudo checkinstall

```
i think thats right?

---

### Post by zencoder on 2007-01-15
Cyberkitty would be right in some of the more basic situations, but this is a specialized script written for a very specific situation.  A little RTFM goes a long way.

Per the VMWare doco:
> **Installing VMware Tools from the Command Line with the Tar Installer**
The first steps are performed on the host, within Workstation menus: 
1. Power on the virtual machine.

2. After the guest operating system has started, prepare your virtual machine to install VMware Tools. 
Choose **VM > Install VMware Tools**. 
The remaining steps take place inside the virtual machine. 

3. As root (su -), mount the VMware Tools virtual CD-ROM image, change to a working directory (for example, /tmp), uncompress the installer, then unmount the CD-ROM image.
Note: Some Linux distributions automatically mount CD-ROMs. If your distribution uses automounting, do not use the mount and umount commands below. You still must untar the VMware Tools installer to /tmp. 
Some Linux distributions use different device names or organize the /dev directory differently. If your CD-ROM drive is not /dev/cdrom or if the mount point for a CD-ROM is not /mnt/cdrom, you must modify the following commands to reflect the conventions used by your distribution. 
[FONT="Courier New"]mount /dev/cdrom /mnt/cdrom 
cd /tmp [/FONT]
Note: If you have a previous installation, delete the previous vmware-distrib directory before installing. The default location of this directory is 
[FONT="Courier New"]/tmp/vmware-tools-distrib[/FONT]. 

4. Untar the VMware Tools tar file:
[FONT="Courier New"]tar zxpf /mnt/cdrom/VMwareTools-5.0.0-<xxxx>.tar.gz
umount /dev/cdrom [/FONT]
Where <xxxx> is the build/revision number of the VMware Workstation release. 
Note: If you attempt to install a tar installation over an rpm installation - or the reverse - the installer detects the previous installation and must convert the installer database format before continuing. 

5. Run the VMware Tools tar installer:
[FONT="Courier New"]cd vmware-tools-distrib 
./vmware-install.pl [/FONT]
Respond to the configuration questions on the screen. Press Enter to accept the default value. 

6. Log off of the root account.
[FONT="Courier New"]exit [/FONT]

7. Start X and your graphical environment.

8. In an X terminal, launch the VMware Tools background application.
[FONT="Courier New"]vmware-toolbox & [/FONT]
Note: You may run VMware Tools as root or as a normal user. To shrink virtual disks, you must run VMware Tools as root (su -).  


Confirmed to work for me out of the box on guest OS Kubuntu-6.10

---

