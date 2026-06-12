---
title: "Installed Ubuntu on external harddrive and got GRUB error21"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by linux4m3 on 2007-09-15
Today I installed Ubuntu 7.04 on my comstar 250gb external hardrive. I Made a partion on it ext3 40gb. To install ubuntu on it. I ran the liveCD and installed it just like i was installing it on my main internal hardrive but instead i put it on my external hardrive. So then i restarted the computer and got

loading GRUB
 error21 ..

something like that not sure why.

I have windows XP proffesionall on my internal hardrive that has 160gb. And now on my external hardrive I have 40gb partition for my linux OS. I cannot boot into XP or Ubuntu because of this error. Can someone please help me. Thanks.

---

### Post by eionmac on 2007-09-15
First, you need to reset Windows. Use Windows disc and  load windows as follows.
Put windows disc in CD drive.
Stop computer
Reboot.
windows will try to load , use 'repair' it will find existing windows system and reset your MBR  (first  part of C drive.)
Reboot into Windows.
Windows should now work.

Start up from your external hard drive.  If this is a USB drive you need to set the BIOS  start order to:
Floppy (First)  
CD ROM (second)
USB device (Third
Hard Drive (fourth)
       
Then computer will start from one of these devices in order shown, so Windows CD would start before Hard Drive if in CD  drive is a Windows or Ubuntu or Live Linux CD .

Ubunto would overwrite the windows MBR with GRUB.

However if you use an external CD now either LIVE Ubuntu or Knoppix you can edit Grub   and IF USB drive is before CD then computer will start at GRUB on External menu.lst and offer choice of Ubuntu or windows (Edit GRUB to longer than default time, I use 20 seconds to allow time to chose  Windows or Ubuntu)

---

### Post by logos34 on 2007-09-15
After you do the fixmbr command from the XP CD recovery console, you need to run the ubuntu live cd and write grub to the external drive so you boot into ubuntu.

Follow this [howto]("http://ubuntuforums.org/showthread.php?t=224351"), except you will enter 'setup (hd**1**)' so Grub is written to the usb drive mbr.

---

