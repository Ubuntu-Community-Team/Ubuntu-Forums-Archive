---
title: "Grub half installed to mbr - can't reinstall, can't find stage1"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by Curtisc on 2006-05-17
My computer (at work) is finicky, to say the least.  The ubuntu install disks do not work.  I used the same one (dapper flight 6) that worked perfectly on my home computer, and when that didn't work I burned dapper beta 2 and tried that.

Anyway, I kept on trying to install, and it seemed like it was sort of working (it would error, I'd continue, it would try again and seem to work).  Grub was installed to the MBR, and I got the "installation complete" message.  Grub correctly displayed all the options (linux, linux recovery mode, memtest, and windows XP), but when I chose linux (and recovery mode), I got a CRC error and then something about kernel panic and VFS error.  Hmm...

I had a knoppix CD around, so I booted into that, reformatted my attempted linux partitions, and followed the instructions for [Installing from Knoppix]("https://wiki.ubuntu.com/Installation/FromKnoppix?highlight=%28installation%29").  All went well until I rebooted the computer and grub failed with error 17.  So, I went back to knoppix and tried to reinstall grub, but nothing seems to work.  Not "grub-install sda", not grub -> root (sda), not anything I tried.  grub:  root (tab) gives me fd0 and nothing else.  Doesn't seem to recognize the partitions (which are all mounted).  "find /boot/grub/stage1" returns nothing.

Any suggestions?  I've obviously buggered the thing, but I really don't want to let windows have its way with the mbr with fixmbr...

---

### Post by chettyk on 2006-05-17
Take a look at this Ubuntu Wiki page:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

I found it very useful.

---

### Post by Curtisc on 2006-05-18
Thanks, that helped a bit... Grub is more or less working now, but I had to manually create a menu.lst file.

Now it says stuff about booting the kernel, detecting stuff, and then I get:
```

RAMDISK: Compressed image found at block 0
crc error
VFS: Cannot open root device "sda4" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

This seems very odd.  Windows boots just fine.  This is my menu.lst:
```

timeout 5 
default 0
fallback 1

title  Ubuntu
root   (hd0,3)
kernel /vmlinuz root=/dev/sda4
initrd /initrd.img

title  Windows XP Professional
root   (hd0,0)
makeactive
chainloader +1

```

So it appears something is wrong with where my root file system is located.  But it really is at /dev/sda4!  Any help is appreciated, thanks.

---

### Post by chettyk on 2006-05-18
The entry for Ubuntu in your **menu.lst** looks odd to me. Here's the Ubuntu entry in my menu.lst:

```
title		Ubuntu, kernel 2.6.12-10-386 (sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

```

Maybe you could try adding a boot-up option in your **menu.lst** with the above as a template. You'll, of course, have to make appropriate changes. Check your /boot directory and see what vmlinuz-* and initrd.img-* files are present there.

Good luck!

---

### Post by Curtisc on 2006-05-18
You're right, my menu.lst was wrong.  However, when I fix it (manually or with update-grub), I still get the error "unable to mount root fs on unknown-block(0,0).  Why does it not recognize my root file system?  I'm pretty sure my fstab is correct.  Is it because my swap partition is sda3 and my root is sda4, but they're in the opposite order on the hard drive?  Can I change that somehow?  Nothing similar I find seems to help!

---

### Post by chettyk on 2006-05-18
Could you post the output of the following:

```
sudo fdisk -l
```

```
sudo grub
find /boot/grub/stage1
```

```
ls -lh /boot/
```

```
ls -lh /boot/grub/
```

Also could you post your **fstab** file?

I'll compare those to what I have on my system and see if I can spot any obvious problems. By the way, which Ubuntu version is now installed on your computer -- Dapper or Breezy?

---

### Post by Curtisc on 2006-05-18
Hmm, I guess I wasn't quite clear... I don't really have a ubuntu version installed, just the kernel (that was as far as I could get through Knoppix).  I'm trying to install dapper.  I'm not going to be touching that computer until Tuesday, but today I tried reformatting and reinstalling the kernel (so that my root partition is now at sda3 and swap at sda4 rather than reversed).  Now, fdisk has something like (from memory):

sda1 ---- ntfs
sda2 ---- vfat
sda3 ---- ext3
sda4 ---- swap

grub find /boot/grub/stage1 gives (hd0,2)

ls -lh I haven't done

my fstab is something like:
```

proc  /proc   proc defaults 0 0
/dev/sda1  /media/windows ntfs defaults 0 0
/dev/sda2  /media/share vfat defaults 0 0
/dev/sda3  /  ext3 defaults 0 1
/dev/sda4  none   swap  defaults 0 0
+ cdrom/floppy etc

```

I realize it would be much better if I had the exact code, but that's the general gist of it.  I've read a lot of people with similar problems that seem to be able to fix it by doing things that I have done.

I just remembered, before I reinstalled I noticed that my mtab didn't have any mention of sda - could that affect it?  I meant to check it out but I forgot.  Oh, and Windows still boots just fine, so grub seems to be finding menu.lst no problem.

Thanks for all your help, I really appreciate it, sorry to be so obtuse.

---

### Post by chettyk on 2006-05-19
If you haven't been able to complete the installation, it is quite likely many key system files may be missing from your system.  My understanding is that you need the kernel as well as several other system files to run Linux.

My advice therefore is that you should try to get a minimal installation in place. Try doing a completely fresh server install (which will lack a desktop) with either the Breezy or Dapper install CD. A server install would be bare-bones installation without any desktop and programs like Open Office, Firefox and so on.

If even a server installation is not possible, then I wonder if you can get Ubuntu working on your computer.

---

### Post by Curtisc on 2006-05-19
I was afraid of that... yes, I tried a server install, and it failed.  That's why I was trying the install from Knoppix.  I don't quite understand what's going wrong - if it were the CD drive, then why was I able to burn and use Knoppix no problem?  I think the computer's just allergic to ubuntu.  Unfortunately... :(  Thanks for all your help.

---

### Post by Curtisc on 2006-05-19
I was afraid of that... yes, I tried a server install, and it failed.  That's why I was trying the install from Knoppix.  I don't quite understand what's going wrong - if it were the CD drive, then why was I able to burn and use Knoppix no problem?  I think the computer's just allergic to ubuntu.  Unfortunately... :(  Thanks for all your help.

---

### Post by chettyk on 2006-05-19
Instead of Knoppix, can you boot and run the computer with the Live CD of Breezy? If so, perhaps you could see if a server install is possible with Breezy, instead of attempting that with Dapper Flight 6.

If you don't have the Breezy Live and Install CDs, you can still download them from:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by Curtisc on 2006-05-23
Semi resolved!

I say only "semi", because nothing worked.  Absolutely nothing.  The CD installation still refused to behave properly, Knoppix still failed to help with installation... so in exasperation I just wiped out the hard drive entirely - and the installation went through without a hitch.  I was using the same CD!  I guess windows was the one screwing everything up... big surprise!

Thanks for all your help.

---

### Post by chettyk on 2006-05-24
Great! It is difficult, though to understand why having Windows on one partition should affect installation of Linux on the rest of the disk.

---

