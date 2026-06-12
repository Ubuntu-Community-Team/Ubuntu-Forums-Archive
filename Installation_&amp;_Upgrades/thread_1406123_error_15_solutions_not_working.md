---
title: "error 15 solutions not working"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Suann on 2010-02-13
Hi there!
Please can someone help me?! I did a stupid thing a few days ago when I was trying to get my Garmin to work in Ubuntu 9.10 and installed something called QT and *un*installed libusb-0.1-4 and installed a newer version, I thought. After that, the PC wouldn't shut down using the menu, so I used the power button which then gave me the choice of Restart or Shut Down so I shut down that way. Then in the morning, I got error 15 file not found on boot up - I do get the Grub menu - and I have tried everything suggested on ubuntu forums and elsewhere and nothing works! Oh, after uninstalling and installing the libusb, half the System Administration menu items disappeared I noticed, before shutting down. I have a dual boot system with Windows Vista and Ubuntu is installed on an external USB drive so I have a feeling the error is with the uninstalling of the libusb package. I have tried installing again but with no results. The root is (hd1,5). I have done the process to get the results.txt file so I have that.
Please help, this is my work computer and thank goodness I can still boot into Windows using the Grub menu so I can still work but clearly a) I hate Windows and b) I didn't back up my Evolution mail before the crash so I can't function as well.
Thank you in advance to whoever can help!

---

### Post by tom4everitt on 2010-02-13
Without knowing exactly what went wrong I would suggest the following. 

1. Boot from a live cd and backup your home folder somewhere (this shouldn't be necessary, but backups are always good). 
2. Install ubuntu on the same hard drive as your old system WITHOUT reformatting the hard drive (this should make ubuntu keep your home folder). 

Although you will loose all your programs its a quick way to get a working system back, and your mails and settings should be safe as long as you keep a backup of your home folder.

---

### Post by Suann on 2010-02-13
Hi
Thanks for replying. The first problem is that when I click on my home/suann folder it says that i do not have permissions necessary to view the files.....? So I can't back everything up, although luckily I did do a partial backup before the error 15 happened so I have most of my files on an external hard drive but the mail files would be nice to have.
The second thing is that I did try to install ubuntu on the same hard drive but it still didn't work. ????
I've looked at the partitions in the editor and it says that sda1 and sdb6 are both boot partitions if that makes any sense? I've followed the solution of fdisk -l and then mounting the drives etc. but not sure if i'm getting the /mnt/boot thing right.

---

### Post by tom4everitt on 2010-02-13
To back up your home folder, do:

sudo cp -pR /home/suann /place/to/back/up/to

I'm not sure why your reinstallation doesn't work. Why are you mounting? I meant a completely regular install from live cd. Choose manual installation, and set your old ubuntu partitions mount point to '/'. Do not mark "format partition". In the last step click advanced and make sure boot loader is being installed to (hd0) or /dev/sda (same thing, different names) assuming thats the drive BIOS boot from.

I'm off to bed now, hope you fix it.

---

### Post by oldfred on 2010-02-14
You did not post results.txt so we can see your boot configuration.

Often error 15 with grub2 is a install of grub legacy and grub gets confused. The script may let us sort it out.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

