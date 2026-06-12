---
title: "download Ubuntu image?"
date: 2014-12-05
forum: Installation &amp; Upgrades
---

### Post by dave_moss on 2014-12-05
Total new guy.... studying for a CCNA, starting to set up a lab. Have an older blue screened computer from a bad hard drive. just installed a new hard drive, but now no OS.... would like to install Ubuntu, using this to console into Cisco routers and switches. originally had Vista on it, and then replaced it w/XP.... obviously nothing now with new hard drive..... didn't see anything about loading an image on the Ununtu site, don't want to replace 8.1 on my good PC. any ideas?....

---

### Post by Darth Riker on 2014-12-05
This thread should help you with putting one iso/distro/image onto a cd/usb in order to try before installing: [URL="http://ubuntuforums.org/showthread.php?t=2230389"]http://ubuntuforums.org/showthread.php?t=2230389

[/URL]And this thread is a guide to using Ubuntu with older machines: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by dave_moss on 2014-12-06
that was fast and right on the $$$$ ... thanks alot....

---

### Post by Darth Riker on 2014-12-06
Cheers.

I've just been going through the motions of trying out Ubuntu myself (I'm a Ubuntu and Linux rookie too) so I had the links handy. :)

---

### Post by grahammechanical on 2014-12-06
Did you miss this?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

On the web site Home page I see "Download" and "Download Ubuntu." Both links have other links that provide information about downloading Ubuntu and burning to a DVD or USB memory stick from either Ubuntu, Windows or OSX and also installation instructions.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Regards.

---

### Post by dave_moss on 2014-12-06
more excellent stuff.... thanks.... and i'm talking to a guy in england.... these things really make the world small....

---

### Post by dave_moss on 2014-12-06
put it on a zip drive w/the Pendrive utility, and loaded it perfect to the PC w/the new hard drive.  But..... (there's always a but.....)

Couldn't get it to write to a DVD-R?.... got the message 'error 0x8007045D'  ... saw this at Windows as error when loading Win 7?

dunno.... the older laptops i wanna use won't boot from USB in BIOS..... ??

---

### Post by oldfred on 2014-12-07
If laptop is that old you probably cannot run Ubuntu, but need Lubuntu or Xubuntu which have lighter weight gui. My laptop from 2006 boots from USB, but Intel video chip just does not have enough horsepower to run Unity. I do install 64 bit Ubuntu and then install fall-back or gnome-panel which is like the older Ubuntu version gui before Unity.

check that download is good:
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Cannot use CD any more with full Ubuntu, but I think Lubuntu will fit on CD. But instructions are the same either way.

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)


       Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

      
 [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by dave_moss on 2014-12-07
thanks for the info... you're probably right about the laptops being that old, didn't think about that.... one's a toshiba, and one's a HP, but BIOS in both of them won't boot from USB...they will boot from a disk tho....

my problem was that i kept getting that error when i tried to burn the DVD-R.... did it a couple of times.... should be able to burn a disk?

will try w/the other versions and see if i get better results...

i just wanna get these up and running and load Tera Term and Putty so i can use them as consoles in to the Cisco gear.....

---

### Post by ian-weisser on 2014-12-07
Try running your console from a Live environment without installing.
If the Live environment won't run, then installing a GUI won't work.

You can also use the [Minimal Image]("https://help.ubuntu.com/community/Installation/MinimalCD") and a CD to install a non-GUI environment. Even your old hardware can do that. You don't need a GUI to run a terminal.
You can also install using [NetInstall]("https://help.ubuntu.com/community/Installation/Netboot") instead of a CD, DVD, or USB.

---

### Post by Bucky Ball on 2014-12-07
As Ian just mentioned, the mini.iso may be more up your alley. Installs just the Ubuntu base kernel, you install the rest (e.g. a lightweight desktop environment like xfce4 or lxde if you want it). Then you install anything else you might want (Putty, etc). This will avoid bloat and unecessary resource usage on the old dears. 

Good luck whichever way you go. ;)

Here's a few of my collected links which will help if you want to go the mini.iso route:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

First boot basic install from above link:
```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
sudo service gdm start
```

My example post-OS install line:
```
 sudo apt-get install xfce4 synaptic lightdm
sudo startxfce4
```

For the second command some recommend 'xfce4-session'. I've never tried it myself and no idea which is best.

---

### Post by flaymond on 2014-12-07
If you failed to burn the disc image into your DVD-R/CD, you should check this out - [http://www.7tutorials.com/burning-iso-or-img-disk-images-windows-7](http://www.7tutorials.com/burning-iso-or-img-disk-images-windows-7)

---

### Post by coldraven on 2014-12-08
It's not quite the answer you were looking for but if you do want to put an image on your Win 8 box you could try this. It will not affect your Win 8 in any way other than using up some disk space.

Install VirtualBox: 
[https://www.virtualbox.org/](https://www.virtualbox.org/)

Then install your iso of chioce into VB or download a ready made Virtualbox image
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

Import the image into VB and you are good to go. It is maybe overkill for what you need but it is good for learning new possibilities.

---

### Post by dave_moss on 2014-12-08
> **InterProg said:**
> If you failed to burn the disc image into your DVD-R/CD, you should check this out - [http://www.7tutorials.com/burning-iso-or-img-disk-images-windows-7](http://www.7tutorials.com/burning-iso-or-img-disk-images-windows-7)

thanks..... that's good stuff, pretty much what i was looking for....

what's in there is what i did... w/the 8.1 OS, you just hit Burn from the file , and it starts... started fine for me, but it kept getting that 0x8007045D error... did it 3 times, don't want to waste anymore disks....

still working at it....

---

### Post by flaymond on 2014-12-08
It's always happen to Windows user because the permission is denied for some files to burn. You should check the ISO file if it really fully downloaded. Corrupted ISO is cannot fully installed to the DVD. Here is the links (solutions) to your problems.


Test Partition for error - [http://www.7tutorials.com/test-partition-errors-check-disk](http://www.7tutorials.com/test-partition-errors-check-disk)

Using Command Prompt (CMD)to repair corrupt files - [http://www.7tutorials.com/command-prompt-repair-missing-or-corrupt-files](http://www.7tutorials.com/command-prompt-repair-missing-or-corrupt-files)

Windows 8 Official Support - [http://support.microsoft.com/kb/2748977](http://support.microsoft.com/kb/2748977)

Some tips - [http://www.avoiderrors.net/how-to-burn-an-iso-image-in-windows-8/](http://www.avoiderrors.net/how-to-burn-an-iso-image-in-windows-8/)

 Another tips - [http://windows.about.com/od/windowsforbeginners/a/How-To-Mount-Or-Burn-Iso-Files-In-Windows-8.htm](http://windows.about.com/od/windowsforbeginners/a/How-To-Mount-Or-Burn-Iso-Files-In-Windows-8.htm)

How to burn Ubuntu ISO file to the DVD in Windows - [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)



* Did you checked the "*** Verify Disk After Burning*** " . The error is mean the disk is not verified. Especially, to an ISO file. You better check that and see if it burning succesfully.
* Make sure your DVD is ***Fully Blank***.

---

### Post by dave_moss on 2014-12-10
still at it.... thank y'all for all the great ideas....

had no problem burning both Lubuntu and Xubuntu.... Lubuntu didn't seem to be too stable on the old laptops, just trying Xubuntu now, and it seems to be running alot better..... gonna try it some more.... i'm thinkin' that Xubuntu is the  ticket.... i gotta fire up these routers and see if i can connect w/some IP's....

---

### Post by coldraven on 2014-12-10
As Interprog said it is always a good idea to check that the iso downloaded completely.

Here is a quick way that does not involve trying to read a long and complex number.
First get the md5sum, use the tab key to auto-complete the file name.
```

cd Downloads
md5sum xubuntu-14.04-desktop-i386.iso 
ccd326466b705bc324a20dd45cb3de82  xubuntu-14.04-desktop-i386.iso


```
Then highlight the md5sum and copy it into the clipboard.
Browse to the web-page where the md5sum is
[http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/MD5SUMS](http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/MD5SUMS)
In Firefox the shortcut to "Find" is the forward slash key (Tip: it also has the symbol "?")
In probably all browsers you can also use Ctrl+F
Then just paste the md5sum into the search box and if they match the relevant string will be highlighted on the page.
If not then you have a broken download.

---

