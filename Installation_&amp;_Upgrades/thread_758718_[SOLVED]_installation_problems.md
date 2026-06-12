---
title: "[SOLVED] installation problems"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by stokerw on 2008-04-18
Having tremendous problems installing Ubuntu as dual boot onto machine with windows xp. (Packard Bell, intel pentium 4. 2.8 )
RAM 512, Space available for Lunux 20GB.
Already created a linux partition with Paragon Partition Manager.( four partitions on hard drive. Windows backup capsule. Windows system partition. Linux extf3. linux swap.)
Live desktop runs slowly & with difficulty. Prone to freeze. Clicking install icon causes lots of disk activity but nothing happen.
Tried SystemRescue CD. Gparted won't recognize existing partitions - looks at whole disk as empty.
Tried Alternative installation CD. As before partition routine won't recognize existing partitions.
Help! What do I do now?
Thanks.

---

### Post by dstew on 2008-04-18
> Live desktop runs slowly & with difficulty. Prone to freeze.You can try kernel parameters (use F6 at the opening menu) to try to get the Live CD to run better. Try **acpi=off** or **noapic nolapic** or both together.

If you can get a working desktop, open a terminal window (Applications --> Accessories --> Terminal) and enter the command```
fdisk -l
```Post the result to the forum. It is possible that there are errors on the disk. If you can get the Live CD working, we can use programs from there to examine the disk and correct errors, maybe.

---

### Post by stokerw on 2008-04-18
Hi, thank you for your advice.

made great progress! I removed the linux partitions that I had created with Partition manager. This allowed gparted to create new linux partitions.
I started installation with the alternative CD and all went well until installation of grub.
Following advice on various sites I would not allow grub to go onto MBR. But all the options I tried for grub would not work, and eventually I finished the installation without grub.
Now of course I can't start the installation. The installation said to boot manually using /vmlinz kernal on partition /dev/sda5 & root=/dev/sda5 passed as kernal agent.

Can you please expalin how to do this?

Also any tips on setting up grub after installation complete would be a help.
Stoker

---

### Post by dstew on 2008-04-18
> Following advice on various sites I would not allow grub to go onto MBR.If you want to dual boot, you should let grub into the MBR of the first disk. If you don't like it, you can remove it with the fixmbr command from the Windows recovery console, or the supergrub disk. If you don't let grub into the MBR of the boot disk, you have to install grub into the MBR of the Ubuntu disk, and then pick that disk to boot using the BIOS setup screen. Some computers make this easy, but others are more difficult.

Anyway, if you want to boot your installed system without grub installed, you will need to get a grub command line. You can get a grub command line by booting a [grub floppy]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html"), or booting a Live CD and opening a terminal, and entering```
sudo grub
```If you can get a command line on the Alternate Install CD, you can also try to start grub.

Once you have a grub command line, with the grub> prompt, you can boot your Ubuntu OS by entering four commands. They are root, kernel, initrd and boot. The problem is you have to know the correct arguments for the commands. You can figure out the arguments using grub's tab-complete function (like most shells in Linux). You enter a few characters on the grub command line, hit the tab key, and it completes the line. If there are a number of options, it will show you the choices you have. So, to boot your OS, you can start with:```
grub> root (hd
```then hit Tab. It will tell you the disk options you have, probably (hd0) and (hd1). Probably Ubuntu is on your second disk, which is (hd1). Now you have to get the partition. So you make the line```
grub> root (hd1,
```and hit Tab. It will tell you the available partitions, including the formats. When you figure out which one is the root partition, complete the line and hit enter.

Next, you have to get the kernel. To do that, start with the root partition:```
grub> root (hd1,0)/
```then Tab. It will give you a listing of the files and directories in the root directory of that partition. If you see a kernel image, which is usually "vmlinuz" something, you can complete the line with that. If you have a boot directory, then go to (I am leaving out the grub> prompt from now on)```
kernel (hd1,0)/boot/
```and hit tab to see your kernel images. Pick the generic kernel, and add root=/dev/sdb1 ro quiet splash to it, and hit return (if that is the correct root partition). Same procedure for the initrd. Pick the initrd image that matches the kernel version. Then enter ```
boot
```

Another thing to try instead of all that, is at the grub command line to look for the grub menu, if it was created. You use the same tab-completion with the grub command```
configfile (hd
```then hit tab. Eventually, you should be able to find the menu.lst file. The completed line will look something like this:```
configfile (hd1,0)/boot/grub/menu.lst
```Hit return and you get a grub menu.

---

### Post by stokerw on 2008-04-18
The desktop is now working fine from the Live desktop. Though it seems to be pulling a lot of stuff from the CD.

Tried your suggestions. I have 5 partitions. 0 & 1 are used by windows
The linux home and swap partitions are part of an extended partition to get them in. I think no 4 is the home on - it is listed as ext2fs, type0x83, though I'm sure I set it up as ext3.
When I try the root listing I get a message "Bad file or directory type"

If I select the install option from the desktop will it repair the installation or force a new installation?

Thanks again for your help. Stoker.

---

### Post by dstew on 2008-04-18
> If I select the install option from the desktop will it repair the installation or force a new installation?It will do a new installation.

If you want to install grub onto the MBR, you can do that. Isn't your problem that you can't boot your installed system, because you didn't install grub?

It might be easier to try the [Supergrub disk]("http://www.supergrubdisk.org/"). It is a CD that will let you set up grub fairly easily, or perhaps boot your installed system.

---

### Post by stokerw on 2008-04-20
Hi,

just to say that I seem to have a working installation running alongside windows XP. I could not get superGRUB to set up a booting routine for me, and after deciding to rearrange my partitions so that Ubuntu was in a primary partition, rather than an extended one, did a new install.

Many thanks for your helpful advice. All being well I hope this is the close of this thread. Cheers. Stoker. 
:)

---

### Post by the8thstar on 2008-04-20
Don't forget to mark your topic as [SOLVED]. :)

---

