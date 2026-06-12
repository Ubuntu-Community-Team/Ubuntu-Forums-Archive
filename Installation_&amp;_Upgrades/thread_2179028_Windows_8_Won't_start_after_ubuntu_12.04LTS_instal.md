---
title: "Windows 8 Won't start after ubuntu 12.04LTS install"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by Strikeiron on 2013-10-06
Hi everyone,
I hope somebody could help me.
I bought a Lenovo S400 ideapad with Windows 8 pre-installed.
With G-parted I assessed that there are 8 partition, between them windows 8 was in a 250 Gb partition.
So from windows I reduced that partition to 125 Gb and I obtained a 125Gb partition of free space.
Then I booted with a live iso usb of 12.04LTS and I tried to install ubuntu on the free space alongside with windows.
All seemed well but when I rebooted and selected in the grub menu windows the result is:

```
errore: unknown command 'drivemap'
errore: invalid EFI file path
```

Then I decided to try according to this blog:

[http://whoochee.blogspot.it/2012/12/uefi-ubuntu-boot-along-with-win8.html](http://whoochee.blogspot.it/2012/12/uefi-ubuntu-boot-along-with-win8.html)

Before repairing the result was this one:

[http://paste.ubuntu.com/6200203/](http://paste.ubuntu.com/6200203/)

Then I ran boot repair but It gave me an error:

[http://paste.ubuntu.com/6200230/](http://paste.ubuntu.com/6200230/)

What could I do? I disabled secure boot in advance, but windows refuses to boot now.... the difference is that in the grub menu there are new voices related to back up boot for EFI mode.

Thanks in advance.

---

### Post by adamitj on 2013-10-06
Dude... I bought a Dell notebook and had the same problem.

Altough there are many options to make a dual boot work with a pre-installed Windows 8 OEM, I couldn't make it. You can try a lot of things installing a signed boot manager inside GRUB (or whatever you call it) but, really, it's kind of complicated and doesn't bring expected results since GRUB menu will be filled up with a lot of options and one or another may try to boot Windows without success.

Part of the problem (I think) it's because OEM installs for Windows 8 came with EFI/UEFI and secure boot in a GPT layout partition (instead of MS-DOS layout as before). I didn't see any GRUB working perfectly with this setup. I did these steps to make Windows 8 works along Linux with Secure Boot and UEFI disabled (you must disable them at BIOS setup before proceed with the steps below):
- Backed up all disk partitions with third-party software ACRONIS 2013 live CD;
- Used Ubuntu 13.04 live CD to boot and access GParted, then I created a new partition table type MS-DOS "ERASING EVERYTHING IN DISK", so be careful of what you doing;
- Installed Windows 8 with an full licensed DVD-ROM from a friend, just to create boot sectors and a new "C:" partition;
- Used ACRONIS 2013 to restore ONLY "C:" partition from backup;

At this point, I could boot Windows 8 OEM like a boss, just as if it came from factory;

From now on its kind easy to resize and install my beloved Xubuntu 13.04 like old times, when there was no UEFI and Secure Boot.

Notice you'll need a great knowledge of partition tables and BIOS to execute the steps above, and by doing it will break your product warranty. Do it by yourself, I'll not be responsible for any data loss or for any kind of mess you can make on your notebook :)

---

### Post by oldfred on 2013-10-06
Many do get UEFI to dual boot, but a few systems have issues. Most issues are related to how the vendor has configured UEFI. Boot-Repair, Grub and Ubuntu have created work arounds for many of the common issues but some just do not work. It also may be in some cases that they have made the install process with secure boot & UEFI so complicated that many just give up.

It looks like you have an Ultrabook which usually has issues with the Intel SRT that uses RAID and dual video that needs some extra effort to get working.

If you go directly into UEFI menu (not grub) can you boot Windows. With secure boot off, or with secure boot on?
Grub2 & Ubuntu are installed with secure boot grub & kernel. But Windows should boot with secure boot off. 

Grub menu may get busy as grub2's os-prober has a bug and still creates BIOS boot entries that will not work with UEFI. Boot-Repair should add correct entries, but it looks like it added entries from your recovery efi partition not the efi partition that is labeled efi. You may have to create correct entry manually. examples in bug report.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

    
More info in links in link in my signature.

Some other threads with similar models.
 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by Strikeiron on 2013-10-06
Ok, thankyou very much for your answers... I won't judge you responsible for any damages, don't worry. Now I've got something to study!
I'll have a try with ubuntu 13, I've seen there's a version dedicated for problems in dual booting and then we'll see...

---

### Post by Strikeiron on 2013-10-07
Here I am.
Today...
I managed to do something but I don't know what I did.
So here is a resume:

First I reduced the partition of windows 8 from windows 8. Il let me reduce it from 250 Gb to about 125. Eventually there was a part not allocated.
Then I reboot, from bios I disabled secure boot, then inside windows 8 I disabled fast Boot.
I made a live usb pen with ubuntu 13.04 and then I booted the computer from the USB pen.
From the live version I manually partitioned the not allocated part of 124 GB. I created 512 b with the root /boot, then two partition: one for swap (4 Gb, equal to ram) and the other with the root /.
I installed the ubuntu Os on /boot, then I restarted and Windows started.
I installed easyBCD and then I gave priority to ubuntu.
I rebooted.
And here are the problems: if I start the computer from the normal button It gives me the boot menu, but if I select ubuntu It saus me that windows can't start, instead windows 8 starts without problem.
But if I start the computer with the button of the "rescue" system (It is a button on the left side of the computer) It gives me another menu and in this ubuntu starts without problem.
The result is: I managed to do It.
But the problems is: what have I done? :D

I think I would use boot repair....

---

### Post by Strikeiron on 2013-10-07
Post Scriptum

I ran boot repair and the result is IT WORKS! YEAH!
Now I have the boot menu, from the first voice ubuntu I open the menu for ubuntu system, from another voice I run windows 8.
Great!

---

### Post by oldfred on 2013-10-07
I think the first time you installed in BIOS boot mode and needed UEFI. But Boot-Repair if booted in UEFI mode can convert a BIOS install to UEFI.
You do not need EasyBCD with UEFI as either UEFI or grub can easily handle dual booting.

---

### Post by Strikeiron on 2013-10-08
Thank you very much. I appreciated your help. This one is the unique forum where somebody gave me some help relating to this problem.

---

### Post by oldfred on 2013-10-08
Glad you got it working. :)

---

