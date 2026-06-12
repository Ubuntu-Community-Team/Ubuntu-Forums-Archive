---
title: "dual boot"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by linuxnoob40 on 2006-08-24
ok heres the deal i have linux on a 200 gigabyte serial ata drive and i have win xp on a 30 gigabyte IDE drive how do i set this up so i can dual boot from the bios?

i currently have to go into setup and disable the IDE drive in order to boot to linux otherwise microsoft will boot

---

### Post by noelneuw on 2006-08-24
As far as I know, you have 2 options here, 
Both use grub.
First enable both drives.

1. Use XP ntldr to boot windows or linux by chainloading "grub for win32".
2. Use Linux Grub to boot linux or XP.


If you want to boot from XP you need to dowload grub for DOS/Win32

See the Install ubunto from windows section
at [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

Follow there instructions but dont do the menu.lst there way rather 
point it to your kernel 

my menu.lst looks like this.
title		Ubuntu, kernel 2.6.15-26-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
boot

my first sata drive is /dev/sd1
Im not quite sure what your root parameter would be.
possibly root (sd0,1)



The other option would be to use "sudo grub-install" in a linux
terminal.

You might have to install to /dev/hda ( Your windows partition ).
They both can co-exist, I currenlty run that way.

If you have your windows install cd you will be able to restore the 
MBA by using FIXMBA and "FIX something else"
From the command prompt on the XP Installation 
type help and check out the FIX* cmds.

Hope this helps
Noel

---

### Post by ivandeterrible on 2006-08-24
well i dont know abt you windows xp usrs out there, but i dont like windows xp <verrrryy unstable>

if you are going to dual boot, you have to install windows XP first

1. pop in win xp cd
2.follow directions until they ask you for partitions--then delete all the present partitions visible and make two new partitions. one should be formatted with NTFS or fat32 depending upon size of partition (hint: fat32 for less than 20 gig, NTFS for 25 gig or above)after that is done, you should have two partitions one should be in <Raw> format, and the other in fat32 or ntfs
3.then install xp on ntfs or fat partition
4.follow directions throgh xp install <blah blah blah, yada yada yada>
5.after win xp install is done, you pop in ubuntu cd and boot into the live desktop
6. click 2x on file Install on desktop
7. it will show you some simple steps on installing (should be abt 6 )
8. when it comes to partitioning, in your empty <raw partion> create two new partitions. the first one----make it anywhere from 256 megs to 512(depends on ram norm=1/2 ram size) under partition type or format, select swap
9.then make another one with leftover space and use that as main linux partition (use EXT3 very fast)
10. if that goes okay, then it should be good

hope this helps
this video should help too
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu&hl=en)

---

