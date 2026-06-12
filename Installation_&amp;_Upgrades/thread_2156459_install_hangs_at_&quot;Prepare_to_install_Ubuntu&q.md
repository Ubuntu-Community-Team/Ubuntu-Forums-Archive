---
title: "install hangs at &quot;Prepare to install Ubuntu&quot; gives black screen with lists of numbers"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by AnnabellaMoorlord on 2013-06-21
I downloaded the 12.04 Ubuntu ISO and wrote it to disk, I have successfully installed it on one laptop computer (therefore install cd is good). I have wiped the hard disk with DOD standards (one of the free recommended wipe disks out there). This is the same method I used to prepare other computer. I have successfully installed the Linux mint 14 on this problem laptop (therefore the hard disk is good, also it's a brand new disk drive).  This problem laptop is an OLD Dell inspiron B130 laptop. Please see [http://www.dell.com/support/troubleshooting/us/en/19/Servicetag/8v77rb1](http://www.dell.com/support/troubleshooting/us/en/19/Servicetag/8v77rb1) for full specs.  When I used the mint 14 install I had to do a sudo apt-get remove ubiquity-slideshow-mint to stop the install slideshow from crashing the install.

I have tried to install from the live disk (boot into Linux "desktop" and click on the install icon there) and have also chose to install now instead of try now prompt. So at the welcome screen I choose install ubuntu option, I get the perparing to install screen and I've tried with and without the additional stuff and get the same results, but do have all 3 green checkmarks. I click continue, get the little spinney cursor, the cd is spinning away, and I get a black screen with LOAD of info but the last line is

[   512.928084]   EIP:   [<f910c512>]   wdev_priv.part.7+0x3/0x5  [wl]  SS:ESP  0068:c6b75cec

So now let me tell you that I am brand spanking new to Linux.  I know that there are different loaders, installers, desktop managers.  I know that grub loads my os at start up for most Linux (i think). I know that I can bring up a terminal with ctr alt l.  I have been a windows user since it was dos based. The command line does NOT scare me, I just make lots of typo so I prefer icons (you can't miss type a click!!) I wrote Basic A code when I was in middle school, BUT I do NOT know the commands for Linux.  SOOOOooooo I need step by step instructions (I found a solution I think for this problem, but when i did the df/dev/sdc it didn't like that code and that was the first step in the instructions).  I'm having a feeling to do the df/dev/sdc I would first have to "mount" the c drive because I don't have an os installed yet and just running off the live disk right??? and my basic understanding is that I can run off the live disk , but none of my computer devices are actually installed and operational really so there for to make a change or scan them before the os I would have to do a "mount" thingy to get it recognized by the live disk (I could be very wrong).

So can someone  tell me what is wrong and how to fix it so I can get Ubuntu installed on this computer (just trying to get it running for a girl that needs a computer in 3rd grade, only need web browsing and basic word processor, and this old but cheap, ok free computer will do the trick).

---

### Post by mörgæs on 2013-06-22
Ubuntu is too heavy, but L/Xubuntu is a good option.

It seems like it could need a little more memory. As a first test with the present memory I would try the alternate Lubuntu 13.04.

---

### Post by AnnabellaMoorlord on 2013-06-22
Great, Downloading now, will give it a try.

---

### Post by StephSG on 2013-07-01
I also have the exact same problem as AnnabellaMoorlord (that's why I found this Thread !) : 
the PC is an old Dell Inspiron 1300 with CeleronM 1,5MHz and 1Go RAM...

With Ubuntu 13.04, after the "preparing to install" screen, same type of black screen with numbers, and a last line similar to Annabella's one...
I just noticed that after a while, the screen shut down, and after reactivating it by moving the trackpad, no more black screen, but the "preparing to install" again, with spinning cursor... After 30min, I have no enough patience for waiting any longer, so I tryed to install Lubuntu

With Lubuntu 13.04, the situation is exactly the same !
The same black screen with identique numbers, after the validation of "preparing to install".

On this PC, I already installed Ubuntu Server 12.10 without any problem. (Upgraded in 13.04 since)
Just one more precision : I use a bootable USB stick for the installation in both case.

Does anyone has any idea of what could be the source of this problem ?
Next step for me is to test a Mint install...

---

### Post by StephSG on 2013-07-01
No problem with Linux Mint...
I suspect an installer problem with some particular hardware configuration.

An other solution may be to install an Ubuntu Server, and then install a GUI over it, with :
```
sudo apt-get install ubuntu-desktop
```or kubuntu, xubuntu...
Not a very clean solution, but have good chance to work !

---

### Post by Tweakbl on 2014-01-21
I know that I am replying to a post that is several months old and that it is in Jan 2014. But Google returns this thread up at the top of search results for this issue.
I am going on a Dell B130 as well. That had been upgraded with a little faster CPU and bit more ram then the original specs.
I to encountered the OP's issue, but during live cd/dvd install, using Gparted to delete and format the hard disk completely (all partitions) the installer then goes thru and I am able to install Ubuntu Gnome. (I went from Windows XP to Lubuntu then decided to give Gnome version a whirl) :-)  Ubuntu Gnome seems to not like to install over a previous OS.
You still need to do the install procedure for the Broadcom Wifi card found here. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)  (It is available on the Install Disc, and I am having some issues getting the Ubuntu Repository App to use the STA driver off the DVD.) So You may need to jack in to the cable to grab the package that way thru the net. And yep, I checked marked the software sources box to allow the use of the Restricted Drivers from the CD/DVD. It says waiting on source but never completes. So it looks like its Cable time.
I am currently using 13.10 Build.

---

### Post by Tweakbl on 2014-01-21
PS- Update to this. I navigated to the DVD and clicked the file in Pool/restricted/source/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_i386.deb and it found it as source for driver. But as i have a BCM4318 Card, I may needa jack in to cable anyway due to it not being compatible. So you will needa be aware of your chipset.

---

### Post by Tweakbl on 2014-01-21
It also is doing the same thing with Xubuntu. Without Gparted app to blow away Ubuntu Gnome, making it hard to install to. It is like the Disk tool that helps install, fails to pick up on the Disk and or does not want to over write the previous Install of Ubuntu. (When I went from WinXp to Lubuntu first time, it had no issues).

---

### Post by Tweakbl on 2014-01-21
Seems to be a issue with the "Install Third Party Software" being Checked for the Fluendo MP3 Plugin. When this is Checked, it hangs at the point at which you select "Continue"
Leaving it unchecked allows you to bypass the hang. But will omit the software.
If you Mount the drive, select the "Install Third Party Software" it will prompt for Dismount allowing to bypass this hang. And allowing the "Install Third Party Software" to take place.

If it (The Plugin) is important enough for the Devs to put it in the installer then I most likely will need it in future to listen to my tunes.

---

### Post by mörgæs on 2014-01-22
One can always add the restricted packages later with the command 
```
sudo apt-get install xubuntu-restricted-extras
```
Does not have to be during install.

---

### Post by Tweakbl on 2014-01-25
Awesome man, I will try that on the next install I do. (Will be soon) :)
I currently set up this Dell B130 as a test bed. I wanted to see what was new all the UI's and basically did a Kubuntu install as base and then did the "Xubuntu-destop/Ubuntu-desktop/unbuntu-gnome-desktop and Lubuntu-desktop" package installs to see those and basically learn. (I learn by screwing things up, then fixing them) Also learning what packages do what and also finding the names for the apps is another challenge. An example is with Java and Flash, I need those packages for certain tests I do, and there is a little learning curve with it. (I do love the various Software managers that are available). And the only real bad issue I have had was with Lubuntu and Xubuntu and Samba. But that is a topic that is address at length in other threads. Suffice it to say, I subscribe to the K.I.S.S mentality and thats why my fav distro so far is Kubuntu (I like the automagic that happens with Samba in it) :-)

---

