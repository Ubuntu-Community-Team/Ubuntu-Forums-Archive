---
title: "GRUB will not load Ubuntu"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2012-07-16
The upgrade from 10.10 LTS to 11.04 went well with the new Boot_Repair application I found on the Forum loaded from a CD. I then went on to Upgrade to 11.10, but ran into a problem after I ran the Boot_Repair application from the Ubuntu CD. Windows 7 will load correctly from the GRUB Menu, but Ubuntu comes up to the Ubuntu screen with the 5 dots and stalls. I ran a bootinfoscript and the results are at [http://paste.ubuntu.com/1094848/](http://paste.ubuntu.com/1094848/). Ubuntu loads and runs normally from the bootable CD, but not from the GRUB Menu.

Michael
[email]spikels6@comcast.net[/email]

---

### Post by drs305 on 2012-07-16
If it boots to the 'dots' then Grub is doing its job and it is an issue with the OS. That's not to say that Grub can't help by adding kernel options in the boot command.

Your issue may be related to video drivers. You can try booting with the 'nomodeset' kernel option. At the Grub menu, press 'e' to edit the menu. 

Cursor to the end of the 'linux' line, remove 'quiet splash vt....' and add *nomodeset*

F10 or ctrl-x to boot. If it boots to the normal GUI desktop, try to install the correct video driver for your system.

You can also try adding nomodeset via Boot Repair, Advanced, Grub Options, Add a kernel module.

---

### Post by sudodus on 2012-07-16
If you backed up your 10.04 LTS system before starting to upgrade, I suggest that you recover it from the backup and wait until an LTS upgrade 10.04 to 12.04 will be offered (I think it will arrive within a few weeks).

---

### Post by SpikeLS6 on 2012-07-16
Thank you. I will try drs305's suggestions. For the desktop I still have to upgrade I will wait for the 12.10 LTS upgrade coming. I got fooled when I saw notices that my 10.10 LTS lost it's support many days ago. 

Spike

---

### Post by YannBuntu on 2012-07-16
Hello
In answer to your PM... I can't say better than the 2 answers above.

First try Drs305 suggestions (change kernel options).

Have you been able to use 12.04 before having this problem? if yes, have you installed some non-free drivers?

- if yes, the "nomodeset" option should allow you to boot 12.04. Then deactivate the non-free driver.
- if not, as you can boot on 12.04 live-session without any kernel option, I'm not sure if changing kernel option for the installed system will help or not.

---

### Post by SpikeLS6 on 2012-07-16
I went through drs305's procedure and ended up with the following screen (attached).

All are [OK] except the Starting Load Fallback Graphic Devices which [FAILED].

I have no files or software that did not come from the _U_buntu Software or Synaptic. Would I be better off discontinuing this install and just jumping up to the 12.04?

Spike

---

### Post by YannBuntu on 2012-07-16
Upgrades (major system updates, for example 11.10->12.04) often fail, and the risk was even bigger in your case because you have done several successive upgrades (10.10->11.04->11.10->12.04).

Now that your 11.04->11.10 has failed, I guess that some important system files are broken or missing, so I highly recommend you:
1) boot on your Ubuntu (or Ubuntu-Secure-Remix) 12.04 disk
2) choose "Try Ubuntu"
3) Install 12.04 above the broken 11.10 this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)


Next time, instead of doing successive upgrades, I recommend to upgrade via a live-CD (burn the CD of the last Ubuntu version, then reinstall it [this way]("https://help.ubuntu.com/community/UbuntuReinstallation"))

---

### Post by dino99 on 2012-07-16
note : 12.04 is LTS (precise), 12.10 is not.

Sadly dist-upgraded lot of releases does not give an installation as  clean as a fresh one. 

But you can still clean it as much as you can: 
-use: clean/autoclean/autoremove
- and/or : bleachbit as "root" but check carefully the optin boxes
- and finally rename or erase: .gconf, .config, .local, .gnome2 (they will be cleanly recreated on next login, but without your custom settings indeed as its a reset to default values)

---

### Post by SpikeLS6 on 2012-07-16
Went with Yannbuntu's suggestion to install 12.04 from the boot CD. The GRUB loader comes up, but takes me to the same screen as before that is purple and says 11.10 with the four dots below it. The hard drive goes quite and the cooling fan stops shortly thereafter. I installed 12.04 "beside" what was there, because I do not know which HD it is going to install itself on. Should I have selected the one that says override everything? Would another bootinfoscript help?

Spike

By the way, the 12.04 install had me set up the time zone and enter all my names and passwords. It seemed to partition the HD into two, 250 Gb partitions, but only one Ubuntu and it's restore shows up on the GRUB loader.

---

### Post by YannBuntu on 2012-07-16
> **SpikeLS6 said:**
> Would another bootinfoscript help?
Yes

---

### Post by SpikeLS6 on 2012-07-16
This is the latest bootinfoscript from the 12.04 CD load that still comes up as 11.10. It is at link [http://paste.ubuntu.com/1095457](http://paste.ubuntu.com/1095457).

If you need more information, please ask; I just can't think of what you might need at this point.

Spike

---

### Post by YannBuntu on 2012-07-16
[QUOTE=Boot-Repair]The boot files of [Ubuntu 12.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair].
[/QUOTE]

Here is the detailed tutorial: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by SpikeLS6 on 2012-07-18
Sorry for the delay. It has been 25 years since DOS 5.22 days and I have forgotten what I used to know about partitions. I have read through the entire GParted Help File. One place mentions that the good thing about using the boot-able Live CD is that I cn edit all the partitions because they are unmounted. Not so. My /dev/sdb2 will not let me unmount it via the Menu Partition/Unmount command (grayed out in the menu). That stumps the program.

I am wondering how to unmount it. (Attachment with GParted Graphic & Device Information panes.)

I wonder if once unmounted I should reformat the entire sdb2 drive to eliminate all the partitions then re-install 12.04 from the Live CD again.

I am not sure what to do because the GParted menu is not allowing me to do the functions the Help File says are available.

The most current bootinfoscript is still at: [http://paste.ubuntu.com/1095457](http://paste.ubuntu.com/1095457).

Spike

---

### Post by drs305 on 2012-07-18
You can't unmount /dev/sdb2 because the swap partition within it is still mounted. Try unmounting sdb by highlighting the sdb5 swap partition, then Partition, Swapoff. Then try unmounting sdb2 again.

---

### Post by drs305 on 2012-07-18
You can't unmount /dev/sdb2 because the swap partition within it is still mounted. Try unmounting sdb by highlighting the sdb5 swap partition, then Partition, Swapoff. Then try unmounting sdb2 again.

If you get it umounted, next select sdb6 and Partition, Check to try to run a check on sdb6, which may be able to repair whatever problem gparted is seeing.

---

### Post by SpikeLS6 on 2012-07-18
I highlighted the sdb5, clicked on Partition/Swapoff. The small key symbols and the circled red exclamation point disappered. (What are the meaning of these two symbols; I could not find them in the GParted Help File). I went back and highlighted sdb2, but again the Device Unmount was greyed out in the menu.

Attached is the new GParted screen.

Spike

---

### Post by SpikeLS6 on 2012-08-10
After three weeks without progress I finally took it to the PC repair shop and had the second hard drive reformatted and installed 12.04. Thank you for the help. I wish I had more in depth understanding of Linux and Ubuntu.

Spike

---

