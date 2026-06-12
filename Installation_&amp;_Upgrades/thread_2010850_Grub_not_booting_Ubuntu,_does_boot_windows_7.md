---
title: "Grub not booting Ubuntu, does boot windows 7"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by Avinaash on 2012-06-26
I'm using Windows7 and Ubuntu 12.04 LTS. When I choose Windows from boot loader menu, its booting and launching windows7 but when I choose Ubuntu, GNU GRUB command prompt is launched instead of GUI. I tried some of the commands from the forum posts. The results are like...

**ls**
*(memdesk) (loop0) (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)*

all X & Y in **ls (hdX,Y)** resulted in *error: unknown file system* except **ls (hd0,msdos1)**.
but **ls (hd0,msdos1)/boot** is resulting in *error: file not found* so, I don't know about vmlinuz or initrd

I then tried code from this post and the results are like...

**insmod ntfs**
-> nothing happend

**set root (hd0,msdos1)**
-> nothing happend

**loopback loop0 /ubuntu/disks/root.disk**
-> error: file not found

But I have the *folder **ubuntu*** and *file **root.disk*** on my C drive.

Please help me out!
This is the first time I'm posting in ubuntu forums. Thanks!

---

### Post by nothingspecial on 2012-06-26
Question moved to it's own thread.

---

### Post by darkod on 2012-06-26
Are you sure msdos1 is your C: partition? Win7 often has a System Reserved partition not showing in Computer which would be msdos1. In that case C: would be msdos2.

---

### Post by YannBuntu on 2012-06-26
> **Avinaash said:**
> But I have the *folder **ubuntu*** and *file **root.disk*** on my C drive.

That means you have installed Ubuntu **inside** Windows (via the Wubi installer).
You can try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), it should (mount&)open the Wubi folder in a file browser so that you can backup your documents which are in the Wubi filesystem.
Then (if nobody has better idea) I recommend you install Ubuntu the standard way (**outside** Windows, see [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) )

---

### Post by prcdslnc13 on 2012-06-26
The same thing is happening to me. At first I wasn't getting grub at all so I installed easyBCD. Now I can at least get to select my OS but when I try to boot into Ubuntu I get this issue. 

I don't know about the OP but I didn't use wubi to install. I did the normal way and selected "something else" from the menu and created my own root, swap, and home partitions. 

One thing that comes to my mind is at the bottom when it asks for the device I selected the hard drive itself and not a partition. 

Any ideas?

---

### Post by martinr on 2012-06-26
> **prcdslnc13 said:**
> One thing that comes to my mind is at the bottom when it asks for the device I selected the hard drive itself and not a partition. 

Any ideas?
Sounds exactly like the problems I had. Have a look at this [UEFI boot issue]("http://ubuntuforums.org/showthread.php?t=2003442") and its [solution]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957")

---

### Post by Avinaash on 2012-06-27
Thanks people for your replies!

> **darkod said:**
> Are you sure msdos1 is your C: partition? Win7 often has a System Reserved partition not showing in Computer which would be msdos1. In that case C: would be msdos2.

Yes it is msdos1.

With **ls (hd0,msdosX)** all other resulted in *error: unknown file system*

> **YannBuntu said:**
> That means you have installed Ubuntu **inside** Windows (via the Wubi installer).
You can try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), it should (mount&)open the Wubi folder in a file browser so that you can backup your documents which are in the Wubi filesystem.
Then (if nobody has better idea) I recommend you install Ubuntu the standard way (**outside** Windows, see [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) )

I can't boot Ubuntu to run Boot-Repair :confused:

I installed the automatic updates from update manager ubuntu. And when I restart the computer to complete the installations it was redirected to GRUB. Grub boot loader is not compatible with my recent updates. This is my actual problem.

---

### Post by YannBuntu on 2012-06-27
> **Avinaash said:**
> I can't boot Ubuntu to run Boot-Repair :confused:

Boot-Repair can be run from a live-CD (or live-USB) ;)

---

### Post by Avinaash on 2012-06-28
> **YannBuntu said:**
> Boot-Repair can be run from a live-CD (or live-USB) ;)

:) Yeah, I'm preparing a LiveCD now! Once it is done I'll run Boot-Repair.

Thanks!

---

### Post by Avinaash on 2012-06-29
Hello,

I ran Boot-Repair from LiveCD. My problem is still unsolved.

Boot-repair URL:
paste.ubuntu.com/1066034/

Latest version of GRUB is installed on my system.

**[SIZE="2"]GNU GRUB   version  1.99-21ubuntu3[/SIZE]** This is there at the top of GRUB menu.

Thanks!

---

### Post by darkod on 2012-06-29
It looks like wubi wasn't installed correctly. There is no root.disk, only /ubuntu/disks/swap.disk.

---

### Post by YannBuntu on 2012-06-29
@Darkod: I think that is a bug of bootinfoscript, i will report it to Gert. Boot-Repair detected a /ubuntu/disks/root.disk file on sda2 (via [[ -f sda2mntpoint/ubuntu/disks/root.disk ]] ). It also [performed a fsck on it]("https://wiki.ubuntu.com/WubiGuide/#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F"), but this gave a "mount: /dev/loop1: can't read superblock" error, which I can't interpret.

@Avinaash: if i were you, i would reinstall Ubuntu the standard way (OUTSIDE Windows, see [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) )

---

### Post by prcdslnc13 on 2012-06-29
That's pretty much what I had to do. I used easyBCD to erase my current bootloader ( I don't recommend this unless your prepared to completely redo your PC), and used a windows restore disk to rebuild it. 

Then I reinstalled 12.04 using the "install side by side" option. Defining my own partitions always resulted in the above issue.

---

