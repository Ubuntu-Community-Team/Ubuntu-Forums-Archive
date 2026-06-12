---
title: "After upgrade Ubuntu graphics not displaying correctly/too large"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by Jeff_Pass on 2015-01-15
Well I finally got the GRUB menu working again thanks to advice here, and can get into Ubuntu after my ill-fated 14.04LTS upgrade.

But now the graphics are stuck at a huge 1024 x 768, only one setting is available.  I've tried various fixes online but managed to do little more than render the OS unbootable... xdiagnose for one (recommended, but a bust).

Got things back to 'normal' and my huge screen, half the icons off the side.  
If I do:

lspci | grep -i VGA -A 12

I see:

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)


I've seen at least one page that claims my graphic controller isn't supported in 14.04, which would only underline the stupidity of me pressing the 'Upgrade' button... which has had me hunting for web articles and performing inept installation surgery for the last 4 days.  Surely that can't be the case?   Another recommended booting into an earlier kernel version, but all the options I've tried off GRUB hang at a blank purple screen unless I select 'Recovery Mode', which is the only way I'm able to get into Ubuntu now.

Synaptic Package Manger recommends NO 'Additional Drivers'.   How do I get the old screen resolution back I used to have?  
Has anyone else come across this problem after upgrading.
As if to goad me, the Wine programs that prompted me to upgrade actually work now.... only they inform me they can't run because my resolution isn't set correctly.   
:(

---

### Post by Jeff_Pass on 2015-01-15
Well I found this website:

[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7)

This had a downloadable application for Ubuntu 14.04 64 bit, since I have an Intel video card:

[Graphics Installer 1.0.7 for Ubuntu* 14.04, 64-bit]("https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.7-0intel1_amd64.deb")

The page indicated to run these commands before executing:

>>>
**Signatures - Ubuntu***

 In order to "trust" the Intel® Graphics Installer for Linux*, you  will need to add keys to Ubuntu's software package manager ("apt"). Open  a terminal, and execute these line:
 wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -

sudo apt-key add -wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -
>>>>


Ran these, and got "OK".
Then executed:

# intel-linux-graphics-installer


I got a graphical interface with a "Begin" button.  It ran some checks and said OK, then Install.

several errors-

First:

 W:GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366, W:Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

And then a very dramatic green, green, green, RED:

Ensuring consistent system... OK
Listing packages... OK
Setting up repositories... OK
Installing packages...
    Updating package cache... FAILED
&#55357;&#56667; Installing packages... : Failed  [  ] &#9702;


So I rebooted the PC and it hung at a blank purple screen again.
Booted into "Recovery Mode" and back to the stretched off to the right screen, but at least I can get on the internet.

Sure looked like that was going to work...... disappointment.

---

### Post by Jeff_Pass on 2015-01-15
1

---

### Post by Jeff_Pass on 2015-01-15
I fail to see why the exact same computer that displayed perfect 1600 x 1200 resolution this morning with an earlier version of Ubuntu, now will only display in 1024 x 768 with the upgraded Ubuntu 14.04 LTS.    Same video card, same machine.

Isn't an upgrade supposed to be better than the old version?

What in the world could possibly be missing?  

I don't want to be an Ubuntu tech..... I just want to surf the Internet and run programs and have everything stay the same as it was and work.
My god this is absolutely maddening.

---

### Post by Jeff_Pass on 2015-01-18
You can close this I finally just backed up my files, made the jump and installed Linux Mint..........   after a few issues making their USB iso bootable it loaded right up, everything is working (including the Wine programs) and resolution is a full 1600 x 1200 again.   I have a working PC!!!  whew what a week.
I hated to leave Ubuntu but its just too frustrating with the upgrades, I went through a lot last year too.   I still have another PC with Ubuntu 12 on it but that is not being upgraded.
Maybe when all the bugs with 14.04 are wrestled out I'll take a look at it again someday.  :/

[https://soundcloud.com/fororchestra/ray-charles-hit-the-road-jack-for-orchestra](https://soundcloud.com/fororchestra/ray-charles-hit-the-road-jack-for-orchestra)

---

