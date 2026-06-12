---
title: "TAKE NOTE: Grub writting incorrect drive into menu.lst"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-09-28
[SIZE=3]I have been noticing a problem with the way that my hard drive (HD) configuration is being read in Ubuntu.

My physical, actual BIOS order HD connections are:
hd0 = 250Gib PATA on IDE connection
hd1 = 160Gib SATA on SATA1 connection
hd2 = 40Gib IDE on SATA2 with IDE to SATA adapter connection

Drives have been usually read with hd0 as hd2, hd1 as hd0 and hd2 as hd1.

Ubuntu will not read drives in this physical order at all times. This has been mostly when using the LiveCD. During installation the hd0 is read as hd2 and the grub/menu.lst is written accordingly. The hd1 has no OS installled. When rebooting, error 17 occurs. I have to  press the escape key to enter grub and manually edit hd2 to hd0 to boot system. Once into Ubuntu I edit menu.lst from hd2 to hd0 and system boots properly thereafter. This is accomplished via Applications/terminal.

Once in terminal type "**_gksudo gedit /boot/grub/menu.lst_**"

If anyone else is having this issue, you may need to try this fix.

I have submitted a bug report on Launchpad.

Hope this can be of assistance with anyone else installing Ubuntu and then not being able to boot up.
[/SIZE]

---

### Post by caljohnsmith on 2008-09-28
When you are in Ubuntu, Ubuntu usually orders the HDDs in /dev according to drive type, such as IDE, SATA, USB, etc, and IDE usually comes first if I remember correctly. Also, for any Grub commands you run in the Grub CLI from your Ubuntu install or from the bash shell, Grub at that point orders its drives according to the order in the /dev directory (unless you tell it otherwise):
```
/dev/sda = (hd0)
/dev/sdb = (hd1)
/dev/sdc = (hd2)
...etc
```
BUT, here is the point that I think might be confusing you: on start up, *Grub sees the order of HDDs as the same as the BIOS boot order*. That means that if you boot off your 160 GB SATA drive for example, that drive is then (hd0). And whichever HDD is second in the BIOS boot order will be (hd1), and the third drive in boot order will be (hd2). So the HDD order that Grub sees on start up has nothing to do with how the HDDs are ordered in the /dev directory in Ubuntu (although they could be the same).

Therefore, when you say that you have to modify your Ubuntu Grub menu entries to use (hd0) instead of (hd1) to make them work, that means you must be booting from whichever HDD has Ubuntu on it. Does this make sense? I don't think what you are reporting is necessarily a bug, it is just a difference in how Grub sees the order of devices on start up vs. when you use Grub commands within Ubuntu.

---

### Post by 73ckn797 on 2008-09-28
Ubuntu is on hd0 and it is and always has been the boot disk. I have not used hd1 as a boot drive at all. That is why I felt there may be a bug. I have actually thought about moving the IDE to SATA1 and the other drives to SATA2 & 3. I would leave the DVD/CD as IDE Master drive. I could eliminate the 40Gib IDE adapted to SATA2 drive and install another 160GiB SATA to SATA3 connection. Would the DVD on the IDE cause any issues? It has not been an issue so far.

Again, the order Ubuntu reads has not remained consistent at all. I have installed Ubuntu several times as a result of tinkering and fouling something up or, in this last case, Windows deleted the partition.

The bug report was suggested to me in an earlier thread.

---

### Post by 73ckn797 on 2008-09-28
*BUT, here is the point that I think might be confusing you: on start up, *[I]Grub sees the order of HDDs as the same as the BIOS boot order. That means that if you boot off your 160 GB SATA drive for example, that drive is then (hd0). And whichever HDD is second in the BIOS boot order will be (hd1), and the third drive in boot order will be (hd2). So the HDD order that Grub sees on start up has nothing to do with how the HDDs are ordered in the /dev directory in Ubuntu (although they could be the same).

Therefore, when you say that you have to modify your Ubuntu Grub menu entries to use (hd0) instead of (hd1) to make them work, that means you must be booting from whichever HDD has Ubuntu on it. Does this make sense? I don't think what you are reporting is necessarily a bug, it is just a difference in how Grub sees the order of devices on start up vs. when you use Grub commands within Ubuntu.[/I] 

BTW: I do not have this issue when using another linux distro (PCLinux, Gentoo) from a Live CD

---

### Post by louieb on 2008-09-28
IDE + SATA drives on the same computer = GRUB install confusion. Seems caljohnsmith is right in that the grub installer makes a guess that the ide drive will boot first when it builds the menu.lst file during the install. 

Anyway its just a guess on the installers part. Sometimes it gets it wrong. Maybe GRUB 2 will have a fix for the problem.

Just as a note starting with Edgy (v6.10) the Ubuntu installer switched to using a partitions UUID  in /etc/fstab instead of using the /dev/@@@@ notation for much the same reason. A partitions UUID doesn't change when adding a new drive. but its /dev/@@@@  could change depending on where the new drive is plugged in.

---

### Post by 73ckn797 on 2008-09-29
> **louieb said:**
> IDE + SATA drives on the same computer = GRUB install confusion. Seems caljohnsmith is right in that the grub installer makes a guess that the ide drive will boot first when it builds the menu.lst file during the install. 

Anyway its just a guess on the installers part. Sometimes it gets it wrong. Maybe GRUB 2 will have a fix for the problem.

Just as a note starting with Edgy (v6.10) the Ubuntu installer switched to using a partitions UUID  in /etc/fstab instead of using the /dev/@@@@ notation for much the same reason. A partitions UUID doesn't change when adding a new drive. but its /dev/@@@@  could change depending on where the new drive is plugged in.


It seems to be getting it wrong in most cases because the IDE is the boot drive and where I have Ubuntu installed.

---

### Post by 73ckn797 on 2008-09-29
> **louieb said:**
> IDE + SATA drives on the same computer = GRUB install confusion. Seems caljohnsmith is right in that the grub installer makes a guess that the ide drive will boot first when it builds the menu.lst file during the install. 

Anyway its just a guess on the installers part. Sometimes it gets it wrong. Maybe GRUB 2 will have a fix for the problem.

Just as a note starting with Edgy (v6.10) the Ubuntu installer switched to using a partitions UUID  in /etc/fstab instead of using the /dev/@@@@ notation for much the same reason. A partitions UUID doesn't change when adding a new drive. but its /dev/@@@@  could change depending on where the new drive is plugged in.


This all makes sense. I had an earlier problem with booting and found the UUID to be incorrect.

If I move Hd0 from the IDE to SATA1 connection and restart system I figure that, at the worst, I will have to edit grub? Posted similar, new thread, in installation and upgrade forum.

---

