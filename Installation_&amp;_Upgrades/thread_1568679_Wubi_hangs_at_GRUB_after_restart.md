---
title: "Wubi hangs at GRUB after restart"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by NakurTheOdd on 2010-09-05
I have three hard drives, one of which was newly formatted for a Wubi installation.  I installed it on the blank drive, restarted when I was prompted to do so, but when booting up instead of giving me the choice of which OS to boot it shows only the word GRUB and hangs there.  It seems completely unresponsive to any keyboard commands.

From what I've read, this might be because I installed Wubi on a drive that doesn't have Windows on it (I'm using Windows 7 on a different drive).  The problem is, I'm not even able to boot into Windows, so I have been unable to fix the issue.  I've tried disconnecting the Wubi hard drive via BIOS setup, but that only cause it to come up with a GRUB Hard Disk Error message instead of the GRUB message.  Also, my Windows 7 dvd is scratched and no longer works, so trying to recover with that isn't an option.

Any advice on how to restore my system to it's status pre-Wubi installation, or how to bypass GRUB so I can boot straight to Windows, would be very much appreciated.  Thanks in advance.

---

### Post by NakurTheOdd on 2010-09-05
Addition - I'm about to try installing Ubuntu on the Wubi drive, see if that solves my problem (I'm hopeful it will).

---

### Post by NakurTheOdd on 2010-09-05
Well, installed Ubuntu on the Wubi drive, getting the same error as before... GRUB in the top left, just hangs there.  I'm at a loss of where to go from here.  Any help would be very much appreciated.

---

### Post by garvinrick4 on 2010-09-05
> **NakurTheOdd said:**
> I have three hard drives, one of which was newly formatted for a Wubi installation.  I installed it on the blank drive, restarted when I was prompted to do so, but when booting up instead of giving me the choice of which OS to boot it shows only the word GRUB and hangs there.  It seems completely unresponsive to any keyboard commands.

From what I've read, this might be because I installed Wubi on a drive that doesn't have Windows on it (I'm using Windows 7 on a different drive).  The problem is, I'm not even able to boot into Windows, so I have been unable to fix the issue.  I've tried disconnecting the Wubi hard drive via BIOS setup, but that only cause it to come up with a GRUB Hard Disk Error message instead of the GRUB message.  Also, my Windows 7 dvd is scratched and no longer works, so trying to recover with that isn't an option.

Any advice on how to restore my system to it's status pre-Wubi installation, or how to bypass GRUB so I can boot straight to Windows, would be very much appreciated.  Thanks in advance. Wubi is a folder inside of Windows not a partition install.
Put in your Ubuntu CD and boot off of it and choose try ubuntu. Then open a terminal
and copy and paste these to pieces of code one at a time. Should make Windows boot.

```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show an error just ignore we only want the mbr.

Now this is if your internal drive is your Windows drive and you cannot boot off of it and
do not have your install or recovery disk.

---

### Post by NakurTheOdd on 2010-09-05
I did what you said.  After typing in the two commands, I restarted the computer, but now instead of it saying GRUB and hanging, it's displaying a blinking underscore in the top left.  Again, it's completely unresponsive to any keyboard commands at that point.

I should note that this is the same thing that happens when I disconnect my Windows 7 hard drive so that the only thing it could boot from was the Ubuntu drive.  I don't know if this is related or not, but I thought it might be helpful.

---

### Post by garvinrick4 on 2010-09-05
> **NakurTheOdd said:**
> I did what you said.  After typing in the two commands, I restarted the computer, but now instead of it saying GRUB and hanging, it's displaying a blinking underscore in the top left.  Again, it's completely unresponsive to any keyboard commands at that point.

I should note that this is the same thing that happens when I disconnect my Windows 7 hard drive so that the only thing it could boot from was the Ubuntu drive.  I don't know if this is related or not, but I thought it might be helpful. The code I gave you was
for a Windows OS to fix boot when user does not have their Windows disks. Start over and explain what you are trying to do. What you have on drives and which ones you are trying to boot.

---

### Post by NakurTheOdd on 2010-09-05
I have 3 hard drives - a 2tb drive that I use for storage, a 650gb drive with Windows 7, and a 250gb drive with Ubuntu (I had installed Wubi to this drive, installed Ubuntu to it earlier as I said in a previous post).  I'd like to be able to dual boot both Windows 7 and Ubuntu.  As it stands now, neither will boot.  When it gets to the point where it would start booting an OS (or I suppose, where it would ask you which OS you want to boot), it instead displays a blinking underscore in the top left of the screen and becomes unresponsive to any keyboard input.

---

### Post by garvinrick4 on 2010-09-05
Ok lets get the 7 going first;
unplug the usb drives so just to have the internal with windows 7 on it.
Put in Ubuntu CD since that is all we have and boot, open terminal and put in code
I gave you before. Same thing with lilo.

Now plug in Usb for Ubuntu and it will come up in gparted as sdb click on right hand corner
of gparted and you will have sda and sdb : sda is windows sdb is ubuntu.

Right click on sdb on graph on face of gparted and choose NEW and format it ext4 and then
hit apply arrow. You just made one big new partition on sdb. Focus and make sure you are in sdb not sda. 

Now go out of gparted and choose install Ubuntu. Answer all the questions when you get to
install choose sdb now focus sdb not sda and choose whole drive then go through next few pages answering questions about name and password and such. When you get to page 8 hit advanced button in lower right and choose sdb to install your grub (boot) not sdb1 but sdb. continue and read it will tell you what you just did and then hit install.
When you boot into Ubuntu give it one of these code open a terminal:
sudo update-grub

your data drive you can plug in anytime and will be sdc when it is third in line.

You can set your Bios to boot anyway you want CD first, USB then HDD or you can select which one every time you boot. 
Let me know how you did.

---

### Post by NakurTheOdd on 2010-09-05
Sorry for the slow reply; I've been playing around with Ubuntu ^_^

Major thanks goes out to you; I now have Ubuntu + Windows 7 working great =)  

I don't know if this was the cause or not, but I know when I installed Ubuntu the first time I accidentally installed the boot loader to it's default location of my 2tb storage drive and not to the 250gb Ubuntu drive.  Maybe that's what ended up giving me issues?  I don't really know.  Oh well, it works now, so I'm not going to complain.

---

### Post by garvinrick4 on 2010-09-05
Mark as solved please.

Yes if you get off to wrong start and do not put grub in right place can be a mess.
Enjoy your Ubuntu. Start off with this so you get all your flash, java and codecs and things. Enjoy.

```
Sudo apt-get install ubuntu-restricted-extras
```

---

