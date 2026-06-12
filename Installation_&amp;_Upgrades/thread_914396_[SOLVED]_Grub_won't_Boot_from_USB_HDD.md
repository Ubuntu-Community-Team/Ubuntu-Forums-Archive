---
title: "[SOLVED] Grub won't Boot from USB HDD"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by yogikeshava on 2008-09-08
I have an HP Media Centre PC m7170n, Dual-core Pentium D, 250GB SATA primary HDD, and 500GB USB HP Personal media Drive. Windows XP Media Centre is installed on my Primary HDD[(hd0,1)]. I seemed to successfully install Ubuntu 8.10 Alpha 5 on my USB HDD [(hd1,0)]using the 64bit Alternate CD.

When I boot I see the GRUB menu and various selections for my ubuntu OS and two selections for my Windows XP OS.

When I select the Linux entry Grub returns an "ERROR 15, File Not Found" message. However, I checked the /boot/grub directory and both the initrd... and vmlinuz... files are there. 

When I try to select one of the Windows partitions I get an "Unrecognizable Format" message.

Any thoughts on what Linux file Grub is not able to find? 

Any suggestions on how I can debug this problem?

What I am trying to do is have a complete ubuntu install on my USB HDD. This way I can just plug in my HP Personal Media drive when I want to run Linux without touching the MBR on my primary HDD.

Thanks in advance,

Chris

---

### Post by Pumalite on 2008-09-08
After booting your USB, and getting error 15, hit 'space' then 'e', 'e' again. Try (hd0,0); 'b' to boot.
If met with success, edit your USB menu.lst

---

### Post by yogikeshava on 2008-09-08
I found another ubuntu post that had some good suggestions:
[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

One of the suggestions was to enter the grub command line from the grub menu and enter this command at the grub prompt:
find /boot/grub/stage1  <== boot installed at root

The output should point to the correct device like, (hd1,0). Assuming what is displayed is different from what is defined in grub, you can edit it there and then boot after making the change. After a successful boot you can make the permanent change to your menu.lst file.  

When I tried this command my system hung. I had to do a hard boot to get out of it. 

I went in again and tried to use another grub command, like "cat" to display the contents of a file. I was able to display the contents of my menu.lst file as well as stage1 and stage2. All files were where they are supposed to be.

I have a feeling that maybe my HP Personal Media Drive requires a firmware update or is just not capable of doing what I am trying to use it for.

Anybody familiar with hardware that might know what is causing this? Why would the grub "find" command just hang? Or was I just impatient and should have waited 5,10,30,...minutes?

Thanks for your reply Pumalite. I did try this before. This is the first Windows entry in my grub menu. it's supposed to be my XP recovery partition. However, even when I select this entry I get an unrecognized format error. However, I will try it in the ubuntu linux entry just to see what happens and report back Thanks :)

---

### Post by yogikeshava on 2008-09-08
WhoooHaaaaa!!! Pumalite, U must B some kind of Freaky Linux Wizard.

I don't know why, but I followed your instructions and I was able to boot into Ubuntu.

Is there any logical explanation for this...Or maybe, an illogical one? One of my biggest faults is the desire to understand ;-)

Thanks!

---

### Post by Pumalite on 2008-09-08
When you boot your USB, that drive becomes (hd0,0)
Edit your menu.lst and change 'groot' and 'boot' to (hd0,0)
Good luck!

---

