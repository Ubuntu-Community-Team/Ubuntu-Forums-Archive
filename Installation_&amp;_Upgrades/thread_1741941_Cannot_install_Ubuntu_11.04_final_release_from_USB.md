---
title: "Cannot install Ubuntu 11.04 final release from USB drive"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by liekomg on 2011-04-28
I can't install Ubuntu 11.04 32bit Desktop edition on my Dell Mini 10v. I followed the instructions from the Ubuntu website and made a bootable USB drive using the universal USB installer for windows. I put the usb drive on my netbook and prompted the boot options to boot from the usb drive. Once I got to the installation screen and attempt to install ubuntu on my hard drive it goes blank for a few moments, and a wall of text floods my screen and it stops installing. Anyone knows how to fix this problem?

---

### Post by aljazek on 2011-04-28
I have a different problem. I made bootable USB and started the installation. Everything works fine till end when the installer is "Removing extra packages" or something similar -> then installer crashed. Every single time. I get "installer crashed" window recommending me to report the bug and also copy two files, one is 'partman'.

---

### Post by Hedgehog1 on 2011-04-28
> **liekomg said:**
> I can't install Ubuntu 11.04 32bit Desktop edition on my Dell Mini 10v. I followed the instructions from the Ubuntu website and made a bootable USB drive using the universal USB installer for windows. I put the usb drive on my netbook and prompted the boot options to boot from the usb drive. Once I got to the installation screen and attempt to install ubuntu on my hard drive it goes blank for a few moments, and a wall of text floods my screen and it stops installing. Anyone knows how to fix this problem?

Your ISO may be damaged (particularly on a busy server day like today) - please re-downloaded using bit torrent.

If a new clean ISO dosn't solve it, next try a differet brand of USB stick.

***The Hedge***

:KS

---

### Post by liekomg on 2011-04-28
I've installed from the Ubuntu website and distrowatch.com using the direct download and torrents with the same result.

---

### Post by Hedgehog1 on 2011-04-28
Next step is to try a different brand of USB stick.  Most, but not all, work well for a LiveUSB.  Yours may be one of the unlucky ones (they can also slowly fail over time).


***The Hedge***

:KS

---

### Post by liekomg on 2011-04-28
I just tried using a different usb stick, but still no luck. I'll try later when hopefully the servers are less congested.

---

### Post by markymark64 on 2011-04-28
Have you tried installing with a CD yet? If not, maybe download the ISO and make a bootable CD. That may work for you. I haven't installed the latest version yet because this will be my first time upgrading from the last version. Still, maybe try downloading the iso file and make a bootable cd. Hopefully, that will work for you.

---

### Post by liekomg on 2011-04-28
My Dell Mini 10v has no CD drive since it's a netbook. My only way of installing it is from a USB drive.

---

### Post by liekomg on 2011-04-28
I put Ubuntu 10.04.2 on my flash drive and it's installing as normal, so it's possibly an .iso issue, not the flash drive. Will test it out again later. Thanks for the advices though.

---

### Post by sikander3786 on 2011-04-28
Please follow step by step.

Check the MD5SUM of your downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Use UNetbootin for creating the Live USB. You'll need the latest version of UNetbootin for Natty images. Don't install it from the Repositories if the source PC is Linux.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

Check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If you are unsure about your USB drive's health, try a new one. I know you've tried an alternative, just a tip :-)

Still if it doens't work, make sure your netbook is not overheating. Move it to a cooler environment and try again.

Else, let us see the output of this command from your live session's Terminal.

```
sudo fdisk -lu
```

---

### Post by Guitar John on 2011-04-28
> **liekomg said:**
> I put Ubuntu 10.04.2 on my flash drive and it's installing as normal, so it's possibly an .iso issue, not the flash drive. Will test it out again later. Thanks for the advices though.

Once you have 10.04 installed, you can upgrade from there.  You will first have to upgrade to 10.10, though.  You may want to wait a day or two.  Release day is to the servers what Black Friday is to a Wal*Mart.

---

### Post by liekomg on 2011-04-28
I did the MD5SUM and the hash matched correctly. 

I downloaded the latest UNetbootin to create a live usb but still no luck installing 11.04.

I cannot check the disk for any defects because it does the same thing when I try to install it; a wall of text floods the screen and then it stops. 

Netbook is not overheating. Used two other usb drives. The first one I used I also put on 10.04.2 and was able to install; so it must mean the usb drive is still functional. 

I'm not sure exactly how to copy the log for the live session terminal and paste it on the forums for you to see. I type in the command you provided but nothing happens.

---

### Post by cobra11 on 2011-04-29
I have same problem, i try too create usb key with 3 different programs but no luck! Try 2 different keys,no luck soo it is problem with system because 10.04 works normaly from usb key but 10.10 or 11.04 not..

---

### Post by sikander3786 on 2011-04-29
> **liekomg said:**
> I cannot check the disk for any defects because it does the same thing when I try to install it; a wall of text floods the screen and then it stops. 

I'm not sure exactly how to copy the log for the live session terminal and paste it on the forums for you to see. I type in the command you provided but nothing happens.

Can you please take a screen-shot of the text that floods on your screen so that we can have an idea what is happening there.

And for the other command, there should be some output for it. Did you type it correctly?

---

### Post by coffeenas on 2011-04-29
I'm having the same issueon a Shuttle XS35GT trying to install the AMD64 desktop version. MD5 is good. USB stick is good. 10.04/10.10/Openelec/ElementOS/Mythbuntu beta/10.10/ all installed fine. Even the beta and nightly builds installed fine...used the latest directions and the latest universal USB installer (the older ver didn't work either). Tried it using the install new syslinux iso way and also by selecting Ubuntu 11.04. On the first way...it boots straight to the install screen (no boot menu) and about 75% through I also get a wall of text, then locked up. On the second install way, first time I get a desktop with an "install ubuntu 11.04" icon (live session)...I use that, same result. Next attempt...from boot menu and I used "install to hard disk" option...I was hopeful, but now I'm stuck at "Saving installed packages."  

On these attempts I was downloading updates and manually partitioned. Next attempt, from live session, I didn't...wall of text...screenshot attached.


:confused:

---

### Post by recluce on 2011-04-29
I have been following the development branches for several releases now. 

With Natty, install from USB has **not been working** for me and many others right from alpha1. I posted in the forums, no real feedback. A couple of bugs on launchpad, nobody cared.

This is, unfortunately, the foreseeable result. Install from USB still does not work for many people.

I am frustrated with the current lack of quality control in Ubuntu and utter lack of care by the developers about show stopping bugs. As long as it works on *THEIR* system, there is no problem. :sad:

---

### Post by Dmitrey on 2011-04-29
I've tried to update KUBUNTU 10.10 to release 11.04 and now my system doesn't boot at all (fortunately I have windows installed on my computer). 

Now I try to install KUBUNTU 11.04 from USB and it's also buggy as Florida swamp at August; I haven't sucseeded yet.

definitely +1 vote for UBUNTU developers to improve their quality.

---

### Post by runegang on 2011-04-29
I do as well have these problems with text flooding my screen. I have installed Ubuntu 11.04 beta from USB, but the final version does not work. 

I boot from usb, it shows the ubuntu loading, uses some minutes but never logs in. The text is flooding over the screen before I even got to log in. :-S

AS I have said it worked with the latest beta.

---

### Post by liekomg on 2011-04-29
This is what I mean

---

### Post by coffeenas on 2011-04-29
Wow!!! You beat my wall of text....I'm soooo jealous. :guitar:

---

### Post by liekomg on 2011-04-29
Well, since none of my other usb drives wont install 11.04, I had to buy a new one, and lo and behold, the installer is running normally. I'll wait and see if 11.04 will launch after installation.

---

### Post by liekomg on 2011-04-29
Ubuntu installed normally, thanks for the advices.

---

### Post by sikander3786 on 2011-04-29
> **liekomg said:**
> Ubuntu installed normally, thanks for the advices.
Glad you got it sorted and Happy Ubuntu-ing with Unity :-)

---

### Post by runegang on 2011-04-29
I got it working as well, with another memory stick. I have never had this problem with that memory stick before. The memory stick I used first was a SanDisk 16GB. Now I used a Kingston 8GB SD memory card. Working perfectly.

---

### Post by michaelvoss on 2011-04-29
I had the exact same problem with both a memory stick and a CD. The installation went as described in this thread and ended with tons of text. 

Since it's not the USB - because same result happened with CD - it must be the file.

---

### Post by sikander3786 on 2011-04-29
> **michaelvoss said:**
> I had the exact same problem with both a memory stick and a CD. The installation went as described in this thread and ended with tons of text. 

Since it's not the USB - because same result happened with CD - it must be the file.
It can be the iso. Did you check the MD5SUMs?

---

### Post by xastxast on 2011-04-29
I have tried 3 usb sticks witout success and installed with the 4th one.Other 3 usb memory arent faulty I think its choosing usb.

---

### Post by coffeenas on 2011-04-29
Only installation problem I ever had was this AMD64 11.04...used many other types of builds.

I'm  not running out and buying another 2-10 USB sticks to replace my  perfectly excellent one because 11.04 wants to play its own "guess the  mystical USB game."

So I think I may have a simple workaround...but be prepared to wait awhile for the install.

Since  I planned on using mythtv anyway, I installed the 64-bit MYTHBUNTU  11.04 like a charm. Then I just added the Ubuntu Desktop (Mythbuntu  Control Center>System Roles)

The system freezes on configuring libgdata1.7-cil...hard restarted and ran

sudo apt-get update
sudo dkpg --configure -a
sudo reboot

used synaptic to reinstall unity & ubuntu-desktop

from  settings>login screen , choose ubuntu session. I can get there, and I  have sound, but there's no launchers, nothing...just the  background....I'll have to keep trying at this...seems the most  promising solution so far...

---

### Post by aljazek on 2011-04-30
I found the reason for my ubuntu installer crashing at the end of installation (when "removin extra packages"). I guess it's some kind of a bug, because I had to be connected to internet or else installer crashed. Maybe the reason is I checked out "Install Fluendo...".

---

### Post by cobra11 on 2011-04-30
I think they really ****** everything up in this version. Version 10.10 was disaster and this one is disaster also.

---

### Post by eks on 2011-04-30
So I was browsing the forum trying to find someone having a wall of text then busybox prompt from a USB install and found this thread. Turns out my problem is exactly the same. The wall is the same as liekomg posted. I've posted a similar one here:

[http://ubuntuforums.org/showthread.php?t=1744679](http://ubuntuforums.org/showthread.php?t=1744679)

I'm also not fond of going out trying to find another USB stick (for the record, mine is a SanDisk 8gb Cruzer). I will try to install Kubuntu 10.10 then upgrade it to 11.04.

Anyone has a launchpad bug link? I would like to add a "me 2" there. :)

---

### Post by coffeenas on 2011-05-02
This finally worked for me...try disabling the wireless LAN in BIOS before you install...then enable it again after install. Worked like a charm.

---

### Post by Kangarooo on 2011-05-22
With USB Flash 8GB made with MultiBoot i installed Ubuntu 11.04 on one computer but on another i got bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/773304)
Since it was Multiboot with 10.04.2 10.10 and 11.04 both Xubuntu and Ubuntu i tryd all installing- all worked exept Ubuntu 11.04 Yes Xubuntu 11.04 worked
I checked MD5SUM of Ubuntu 11.04 and it was the correct one. Tryd again formating and again with Multiboot making new Usb with just Ubuntu 11.04 and installing again the same- crashing in middle.
Then with Ubuntu startup disk creator made formated and new again Ubuntu 11.04 and still the same.

> **cobra11 said:**
> I think they really ****** everything up in this version. Version 10.10 was disaster and this one is disaster also.

I installed Ubuntu 11.04 with CD and then after 1h removed it couse its buggyst version ever- screen black so needed a monitor to attach and updates didnt fixd that and also this **** Unity witch im beeing forced into using. and slow.
So i put 10.04.2 thats better and LTS

---

### Post by _sleeper on 2011-06-08
For what it's worth I had the same problem as all the guys and the only workaround without messing with the BIOS settings was to install the alternative image into my usb. It isn't as ridiculously easy as the live cd install, but if you can read and understand simple sentences, you should pull it off.

---

### Post by Expander on 2011-06-14
Thanks for the advice "Sleeper". The only workaround is to install from the alternative version.

For 64-bit:

[http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-amd64.iso.torrent)

For 32-bit:

[http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-alternate-i386.iso.torrent)

---

