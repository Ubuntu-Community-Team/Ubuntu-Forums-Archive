---
title: "Graphics screw up when attempting to install 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Old Marcus on 2011-10-17
I've been trying to upgrade my laptop to 11.10, but no matter how I go about it, about 2 or 3 minutes in the graphics screw up and I end up either looking at an interesting variety of messed up colours or a blank white screen. I've tried the live cd version on dvd and usb, and I tried the text based installer.

It would look like the problem is my graphics card, except for the fact it runs fine on 11.04 and Windows 7 and my laptop came back from the menders after being fixed for a dead graphics chip. My laptop is [URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02237229&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=4217498"]this one.
[/URL]
I'm reluctant to 'upgrade' rather than install over, since I don't trust it not to mess up. Is there any other way I might be able to install 11.10 without this problem?

---

### Post by collisionystm on 2011-10-17
> **Old Marcus said:**
> I've been trying to upgrade my laptop to 11.10, but no matter how I go about it, about 2 or 3 minutes in the graphics screw up and I end up either looking at an interesting variety of messed up colours or a blank white screen. I've tried the live cd version on dvd and usb, and I tried the text based installer.

It would look like the problem is my graphics card, except for the fact it runs fine on 11.04 and Windows 7 and my laptop came back from the menders after being fixed for a dead graphics chip. My laptop is [URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02237229&tmp_task=prodinfoCategory&cc=uk&dlc=en&lc=en&product=4217498"]this one.
[/URL]
I'm reluctant to 'upgrade' rather than install over, since I don't trust it not to mess up. Is there any other way I might be able to install 11.10 without this problem?


There is not a problem with your computer. It is a problem with Ubuntu being incompatible with your graphics card. At the moment there are a lot of issues with display drivers. I suggest you stay on 11.04 for a while longer until they get straightened out.

I see you have a ATI Mobility Radeon HD 5470 Graphics

If you decided to install, use the alternative installer.
[http://www.ubuntu.com/download/ubuntu/alternative-download]("http://www.ubuntu.com/download/ubuntu/alternative-download")

It is text based. Once installed, reboot your computer. Immediately after the BIOS screen that shows the HP logo, hold the SHIFT key down. You will be at a grub menu.
Choose system rescue
At this menu, click on resume normal boot and hold the SHIFT key down until you reach the text login.

Put in your login information

You need to edit your /apt/sources.list to include ubuntu partner repo's so you can install fglrx.

```
sudo nano /etc/apt/sources.list
```

remove the # from the ubuntu partner repo's

CTRL + X then Y to save.

```
sudo apt-get update
```

```
sudo apt-get install fglrx
```

Reboot normal...

Hopefully it works

---

### Post by Old Marcus on 2011-10-18
Thanks, but even on the text based installer it screws up, otherwise I would have done it. Any solutions for this? I doubt the iso will be updated at all between now and 12.04.

---

### Post by Quackers on 2011-10-18
Have you tried booting with the nomodeset boot option?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Old Marcus on 2011-10-18
Tried that, no luck. If there are any other options, I'd like to hear them, else I'll have to hold out until 12.04.

---

### Post by dotnick on 2011-10-18
I am having similar issues.  I've tried many of the different options with the livecd with no luck getting graphics up.  I would have thought the LiveCd would have defaulted to free drivers though... it always seemed to in the past.

I have one of the brand new HP laptops with the AMD A8-3500M APU.  It works fine on 11.04, but not 11.10.

Anyone know if they plan on re-rolling this release as a point update once all of this is sorted?  I would still rather have some sort of usb drive to test with first before commiting to the update process and really screwing up the computer.

I think this is my sign that next time I'll stick to the LTS releases.  I just hope I can get to 12.04.....

---

### Post by viniciuspt on 2011-10-19
> **dotnick said:**
> I am having similar issues.  I've tried many of the different options with the livecd with no luck getting graphics up.  I would have thought the LiveCd would have defaulted to free drivers though... it always seemed to in the past.

I have one of the brand new HP laptops with the AMD A8-3500M APU.  It works fine on 11.04, but not 11.10.

Anyone know if they plan on re-rolling this release as a point update once all of this is sorted?  I would still rather have some sort of usb drive to test with first before commiting to the update process and really screwing up the computer.

I think this is my sign that next time I'll stick to the LTS releases.  I just hope I can get to 12.04.....

I have the same problem and have the same HP laptop with the AMD A8-3500M APU.

I tried to run the Kubuntu LiveCD using nomodeset option on the boot. I received a screen where it is possible select between Instalation or Try Kubuntu. When I select one of this options I receive a blank screen (or black screen #-o).

---

### Post by Old Marcus on 2011-10-19
Just tried upgrading via the upgrade tool, and messed it all up. On Windows atm, is there already a bug report for this issue or shall I make one? And if I do, will it have any effect whatsoever on the version we download?

---

### Post by ru2044 on 2011-10-19
I confirm that method in post #2 works on desktop AMD A8-3850 APU.

---

### Post by viniciuspt on 2011-10-22
> **ru2044 said:**
> I confirm that method in post #2 works on desktop AMD A8-3850 APU.

I confirm too. This method worked fine in my notebook with A8-3500M APU.

I could install using a graphical installer. I put nomodeset option on the LiveCD boot option and select Install.
Now I have a functional notebook hehehehehe :lolflag:
Thanks **collisionystm **!

---

### Post by Old Marcus on 2011-10-23
Unfortunately nomodeset did nothing for me. Even text mode conks out after a few minutes. I guess it's an incompatibility between my GFX card and the default display drivers.

---

### Post by viniciuspt on 2011-10-27
The FGLRX drive in Ubuntu 11.10 is Catalyst 11.8.

I you try to help you Marcus.

I needed to reinstall kubuntu 11.10 from zero!!! :popcorn:
The first boot I received a blank screen, ok !!
After, I rebooted my note and pressed SHIFT key after HP Logo show.
I selected recovery mode and pressed ENTER key and pressed SHIFT after (immediately).
In this moment, I received a text mode.
After, I install fglrx drive using Ubuntu repository (although APT).

I hope to have helped !

Vinicius

---

### Post by SmallWorld on 2011-12-10
Just did a dual-boot install of Ubuntu 11.10 32-bit on a:

HP Pavillion DV6-6140us
AMD A8-3500m with Radeon HD 6620G

Thanks much to collisionystm for Post #2, that did wonders for me and the system is now working.

One variation though - rather than use the Alternate installer, I booted the regular installer from a USB drive.  When the boot menu showed up, I selected the first option in the Ubuntu loader ("Try Ubuntu" or whatever), hit tab, appended:
```
nomodeset
```
after the --, and let it load until I got a command line.  Then:
```
sudo -s
apt-get remove xserver-xorg-video-radeon
```
Confirm, let it do it's thing, then:
```
service lightdm start
```
This allowed me to load Ubuntu from the USB.  It was nice to confirm that the GPU did work with Ubuntu, and I was able to run the GUI installation program that shows up on the desktop.  Once Ubuntu was installed, I was able to boot into Recovery mode as Post #2 suggests and follow the instructions on Post #2 from thereon.

I just did a more extensive writeup on [http://ubuntuforums.org/showthread.php?p=11527811](http://ubuntuforums.org/showthread.php?p=11527811)

---

