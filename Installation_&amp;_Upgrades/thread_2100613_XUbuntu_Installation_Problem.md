---
title: "XUbuntu Installation Problem"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by wobbledog on 2013-01-02
Hi all.
I'm relatively new to the Ubuntu forums here, so please excuse my inexperience in this area.

I've been trying to install XUbuntu onto an older Pentium 4 era machine in order to create a home server.
While presented with the XUbuntu installation menu, I am told I cannot install XUbuntu as I do not have the required disk space for the installation. I know this to be untrue as I've just formatted both IDE drives I am using beforehand. 

I was wondering if anyone could give me some help/advice?
Thanks in advance,

wobbledog

---

### Post by ibjsb4 on 2013-01-02
First thing that comes to mind is do you have four primary partitions?  If so, 4 is the limit.

---

### Post by ajgreeny on 2013-01-02
Give us a detailed list of what you are doing and what stage you get this error message.

What do you mean by "While presented with the XUbuntu installation menu";  what menu is this?

Are you using a live CD (or USB) to install?

---

### Post by wobbledog on 2013-01-02
> **ibjsb4 said:**
> First thing that comes to mind is do you have four primary partitions?  If so, 4 is the limit.

In response to this, all I've done is formatted my two IDE drives using my Windows machine, I've formatted to the NTFS file system and I don't believe any partitions exist on the disk at the moment.

Thanks :)

---

### Post by wobbledog on 2013-01-02
> **ajgreeny said:**
> Give us a detailed list of what you are doing and what stage you get this error message.

What do you mean by "While presented with the XUbuntu installation menu";  what menu is this?

Are you using a live CD (or USB) to install?

Will do.

Firstly, I created a XUbuntu boot disc buy burning the .iso file onto a CD. Then using an older machine, I booted the CD onto it. While presented with XUbuntu's OS installation interface, I was unable to continue with the installation as I apparently do not have the required space for the OS (4.7GB). This is weird as I know, having formatted both drives beforehand and them both being free.

Hope this helps.

---

### Post by steeldriver on 2013-01-02
You can't directly install Linux on an NTFS formatted disk (it doesn't count as 'free space' just because you don't have data on it) 

You will need to reformat first from the live session I think, or choose 'Something else' when you get to the partition stage of the install and manually delete the NTFS partition(s) from there

---

### Post by wobbledog on 2013-01-02
> **steeldriver said:**
> You can't directly install Linux on an NTFS formatted disk (it doesn't count as 'free space' just because you don't have data on it) 

You will need to reformat first from the live session I think, or choose 'Something else' when you get to the partition stage of the install and manually delete the NTFS partition(s) from there

So are you saying I should format to a different file system (i.e. FAT32)? Also I don't recall there being a partition stage of the installation process, in order to format and manage partitions of these drives I use an adapter to plug the drives into my Windows machine and use the disk management program there.

Thanks.

---

### Post by Bashing-om on 2013-01-02
wobbledog; Hi !

If I am not to far off-base here.... NTFS is the windows file system; You want the EXT4 file system on your disk to install 'buntu.
Quickest way I know is from GParted in the live environment -> choose "new device" ->format and choose "msdos"// this is not MicroSoft Disk Operating System !// This will format the selected device in ext4, setting it up to boot bios mode using MBR (you are not booting UEFI are you ???)

As an aside: If windows was partitioned GUID -dynamic partitioning- I do not know that GParted can cope with (re)partitioning the drives.


exit out of GParted
click on the desktop "install" icon and let the install wizard do it's thing, 'less you have need of customized partitions.
[INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by wobbledog on 2013-01-02
> **Bashing-om said:**
> wobbledog; Hi !

If I am not to far off-base here.... NTFS is the windows file system; You want the EXT4 file system on your disk to install 'buntu.
Quickest way I know is from GParted in the live environment -> choose "new device" ->format and choose "msdos"// this is not MicroSoft Disk Operating System !// This will format the selected device in ext4, setting it up to boot bios mode using MBR (you are not booting UEFI are you ???)

As an aside: If windows was partitioned GUID -dynamic partitioning- I do not know that GParted can cope with (re)partitioning the drives.


exit out of GParted
click on the desktop "install" icon and let the install wizard do it's thing, 'less you have need of customized partitions.
[INDENT][INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

okay, this might be a bad time to mention, but I'm completely new to Linux and all its formats, so I might need a step-by-step drive on how to perform this operation and acquire the XUbuntu file system.

Thanks in advance :)

---

### Post by steeldriver on 2013-01-02
or if they really are 'new' disks (you don't have any Windows stuff you need to save) you could just use the Windows Disk Management tool again if you are comfortable with that, but this time delete the NTFS volume / partition so it really is raw free space (the Windows tool refers to it as 'Unallocated')

after that the Xubuntu installer should default to using the whole free space I think

---

### Post by ibjsb4 on 2013-01-02
This may help you out.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bashing-om on 2013-01-02
wobbledog;

Step by step. not a problem.
1. Boot up the install CD -> "try" Xubuntu mode:
2. Look around the various menus -ie "system" and find the utility "GParted" that is 'buntu's partition editor.
3. Open Gparted ->insure that "sda" is highlighted in the upper right gparted screen, in the menu bar choose devices -> new -> msdos. [INDENT]choose "sdb" upper right and repeat for the second drive.
[/INDENT]At this time, what does GParted see for partitioning scheme ? I hope "unallocated" space. good !

Nothing else at this point is required of GParted if you will accept the default partitioning of the installer.

Done with Gparted, close it out - back to desktop.

4. Choose the "install" icon on the desk top and answer the few simple questions, remember your user name and REMEMBER your password. Vital to remember your pass word. Pay attention to the screens during install for where the installer is going to install "grub" -GRand Unified Bootloader - default should be "sda" location// "sda" is where you want grub installed to in this present installation.

5. Remember your password.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-01-02
Just a point: If you are looking to create a server why are you not using Ubuntu 12.04 LTS Server Edition? This has everything you need for a server and you can simply install the desktop environment you want to use (Xubuntu uses xfce4). Simple.

Installing Xubuntu *then* the server packages will leave you with a bunch of Xubuntu default apps you don't need ... Installing the server edition then xfce4 will leave you with only the packages you need for a server, same desktop environment as Xubuntu, and then you can install anything else that you find is required down the track ...

---

