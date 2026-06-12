---
title: "URGENT Installing Windows XP over Ubuntu 10.10"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by DavidOfLondon on 2011-09-10
Hi guys,

I desperately need your help.

I'm a doctor working on an aid mission in Kenya for the British Red  Cross and I have a ton of stuff I need windows for and it's now  affecting my work that I can't wipe Ubuntu and do a XP reinstall followed by Ubuntu dual boot install.

I desperately need someone to just tell me what to do and not ask a million questions - I can't access patient's files because the software the fiiles are stored in will not work with Wine at all. It's serious stuff.

I have Ubuntu 10.10 installed, I love it, it's great, I've used it for 18 months now.

I made the fatal error of totally wiping Windows XP from my laptop and then installing Ubuntu when I actually need Windows to run lots of other software (Wine is not a perfect fix).

I created an ISO of Windows XP Service Pack 3 and created a bootable USB using Unetbootin. But it's as useless as the CD was. When I plug the thing in and reboot all I get is an option to choose "Default" followed by a 10 second timer which just resets.

I've spent days scrambling around the internet on this and I'm amazed at how difficult it is to find an answer. I just want to wipe the machine and re-install Windows, it really is that simple a request.

 I have an install CD and (seemingly) now a dodgy XP USB bootable, yet STILL I can't get either to do anything. I'm usually quite proficient at this stuff but I just don't have a clue where to start. I basically want to have a dual boot on my machine - XP and Ubuntu 10.10. Obviously I have to get Windows on first.

PLEASE, someone tell me what the hell is going wrong. The USB just won't boot and the disk, obviously, is an exe operable so that just gets a "this archive" blah blah message.

I'm a doctor working on an aid mission in Kenya for the British Red Cross and I have a ton of stuff I need windows for and it's now affecting my work.

Please help me.

David.

---

### Post by YesWeCan on 2011-09-10
Hi there. What hardware are you using? Have you considered VirtualBox? I use this all the time to host Windows XP and Windows 7 on my Ubuntu 10.10 system. Its really very good and it allows you to run both at the same time and copy files between them. VBox will install XP straight from your iso file.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by DavidOfLondon on 2011-09-10
Hi,

Thanks for the response. The software I use to store patients' details is government property, very dense, and doesn't like virtual environments for some reason. Will Virtualbox give me complete functionality? 

I've somehow got the USB's setup.exe to behave normally with Wine but naturally it's saying "No valid partitions" and I don't know whether (and how) to credit the correct partition in the correct way. Seems to be a GRUB / MRB issue but it's driving me crazy. I just need to wipe the machine.

PS its a HP 6730s, nothing special but highly efficient for my purposes. BIOS is always very good on HP comps but I haven't a clue how to essentially undo Linux GRUB / Kernel issues. I think that's a serious weakness in the OS, if it's this damned difficult to uninstall.

D.

---

### Post by YesWeCan on 2011-09-10
> **DavidOfLondon said:**
> Hi,

Thanks for the response. The software I use to store patients' details is government property, very dense, and doesn't like virtual environments for some reason. Will Virtualbox give me complete functionality? 
VirtualBox is the real deal. It is a proper virtual environment originally developed by Sun Microsystems and now by Oracle. Your system has 2GB of RAM which is enough.

What other Virtual environments have you tried? Wine is not comparable.

It's pretty simply to try it. Just download the installer for your Ubuntu version and also the Extensions Pack. Fire it up. Create a new VM tell it where to find your XP iso file and voila. After you've booted XP it will invite you to install "VBox Guest Additions" which allows you to resize the display and have seamless mouse transitions between XP and Windows and allows you to share files between them.

> I've somehow got the USB's setup.exe to behave normally with Wine but naturally it's saying "No valid partitions" and I don't know whether (and how) to credit the correct partition in the correct way. Seems to be a GRUB / MRB issue but it's driving me crazy. I just need to wipe the machine.
I don't think you want to be using Wine for anything.
You are trying to burn the XP ISO image to a USB stick? Why not a CD? I'll try to find a USB method for you.

> PS its a HP 6730s, nothing special but highly efficient for my purposes. BIOS is always very good on HP comps but I haven't a clue how to essentially undo Linux GRUB / Kernel issues. I think that's a serious weakness in the OS, if it's this damned difficult to uninstall.
Once you have a Windows install CD or USB it is easy. You boot Windows and then erase the hard drive and install.
You can also erase it by booting a Ubuntu live CD/USB and reformatting the disk.

---

### Post by DavidOfLondon on 2011-09-10
> **YesWeCan said:**
>  You are trying to burn the XP ISO image to a USB stick? Why not a CD? I'll try to find a USB method for you.


Once you have a Windows install CD or USB it is easy. You boot Windows and then erase the hard drive and install.
You can also erase it by booting a Ubuntu live CD/USB and reformatting the disk.

Ah but that's the curious part - I've tried the disk on another windows machine and its fine. The USB bootable I'm not so sure about - I have a perfect Ubuntu USB bootable but the XP version I just made (as the CD is not being permitted to do its job) just pops me into this 10 second countdown at startup and then the bootloader just does nothing - resets the 10 second countdown.

I've seen this exact same problem all over the net on the 6,000 pages I've read: Linux just will not let me use my xp ISO.

Thanks for your help. I'm literally on the edge of just zeroing my machine over this.:(

---

### Post by Pumalite on 2011-09-10
Get a Gparted Live CD. Boot from it. Erase everything in your drive after you have saved what you need. Then format your entire drive NTFS or use your Windows Installation Disk. Install Windows.

---

### Post by YesWeCan on 2011-09-10
> **DavidOfLondon said:**
> Ah but that's the curious part - I've tried the disk on another windows machine and its fine. The USB bootable I'm not so sure about - I have a perfect Ubuntu USB bootable but the XP version I just made (as the CD is not being permitted to do its job) just pops me into this 10 second countdown at startup and then the bootloader just does nothing - resets the 10 second countdown.

I've seen this exact same problem all over the net on the 6,000 pages I've read: Linux just will not let me use my xp ISO.

Thanks for your help. I'm literally on the edge of just zeroing my machine over this.:(
Your Windows CD will boot ok on a different machine? If so, check your bios settings. A countdown often is there to give the user time to do something. Have you pressed a key or anything? Sometimes it waits for you to indicate you want to boot off a CD. This is your BIOS doing this - nothing to do with Ubuntu.

If you have a working Ubuntu live USB it is simple to erase your disk. Just boot live Ubuntu and run System/Admin/Disk Utility and select the disk and click "Format Drive" and select MBR. But this won't get you far if you don't have a Windows CD to boot from.

Are you sure you want to wipe your disk? It will originally have had a recovery partition for restoring WIndows. Have you already wiped that off when you put 10.10 on? To check, please post the output of [COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]

---

### Post by DavidOfLondon on 2011-09-10
The Countdown isn't from the BIOS, it's something from Unetbootin; my BIOS countdown is a totally different menu. And I've seen someone else having this problem.

Here's the read-out from -lu :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b1f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306440191   153219072   83  Linux
/dev/sda2       306442238   312580095     3068929    5  Extended
/dev/sda5       306442240   312580095     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 1028 MB, 1028653056 bytes
32 heads, 62 sectors/track, 1012 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 8127 MB, 8127512576 bytes
5 heads, 32 sectors/track, 99212 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15874047     7932992    c  W95 FAT32 (LBA)
me@me:~$

---

### Post by YesWeCan on 2011-09-10
Oh Unetbootin. I thought you were talking about the Windows CD.

What happens when you try to boot the Windows XP CD? You can boot it ok on your other PC, right?

I don't think you can make a bootable XP USB using Unetbootin. I think its just for linux.
I found this which may work if you do it from Windows (I don't know): [http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/](http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/)


fdisk -lu shows only linux on your 160GB disk.

---

### Post by DavidOfLondon on 2011-09-10
> **Pumalite said:**
> Get a Gparted Live CD. Boot from it. Erase everything in your drive after you have saved what you need. Then format your entire drive NTFS or use your Windows Installation Disk. Install Windows.

My luck is awful - sourceforge's site has slowed to a grind so I can't get hold of gparted or Parted Magic. What an awful day....5 hours trying to fix this already when I should be giving vaccinations. This is why technology is a disaster.

---

### Post by YesWeCan on 2011-09-10
What do you want to download GParted live CD for? You Ubuntu live USB has it. And you don't need it anyway. Just use Disk Utility to erase your drive.

---

### Post by Pumalite on 2011-09-10
Live cd ia up to date and allows to work with unmounted Drives. The best way to form partitions.

---

### Post by mue.de on 2011-09-11
> **DavidOfLondon said:**
> My luck is awful - [...
...]. This is why technology is a disaster.
I've made about the same experience; could you change the boot-sequence in HP's BIOS?, First CD, then USB, then HD ?
Don't try to boot a newer Ubuntu on an elder machine; my Kubuntu 11.04 Stick won't boot on a machine where Hardy Heron (8.04) was booting fine.
Did you let the stick time to settle? (pressing 'pause'-Button and <Return> a few times?)
Some machines won't boot at all when a usb-stick is plugged in, so remove it, when trying the CD.
(excuse my english, it's about 40 years old)
good luck

mue.de

---

