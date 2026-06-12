---
title: "dual installation / reinstallation"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Tatrman on 2011-01-31
Hi everyone,

I'd like to ask for a bit of advice here regarding dual boot and GRUB. 
Here is my situation:

Year ago I bought computer i7-920 6G one HDD, I installed windows 7 on it. than I bought second HDD, placed it into master 2 position and installed ubuntu on it. after installation of ubuntu I got GRUB loader as first thing when I start computer (I don't remember the particular settings during installation) So far so good now is the question - is GRUB on the first or on the second HDD?  can I swap both harddrives so the ubuntu one will be in master 1 position?
I'm asking because my windows 7 is now wrecked (can't even get it to safe mode) and I need to clean the first HDD and reinstall windows.

Thanks

T.

---

### Post by ronparent on 2011-01-31
Your grub boot loader is most likely installed on the drive identified as 'sda'. You didn't say which distro you are using, but, for 10.04 or 10.10 grub is easily reinstalled per the following: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Do what you have to do to get windows working again then use an Ubuntu live cd to reinstall grub. Good luck.

---

### Post by oldfred on 2011-01-31
Just to be save you can easily reinstall grub to the Ubuntu drive from your working Ubuntu. You only need liveCD when you cannot boot a Linux on the Hard drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If you want to know what is installed where with lots of detail:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

