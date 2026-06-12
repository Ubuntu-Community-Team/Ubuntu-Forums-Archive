---
title: "Microcenter winbook series and bay trail installs via 32bit efi"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by mtndrgon on 2015-01-14
):PCommented on a few posts regarding specifically the WinBook series 8.1 Windows Tabs. No takers on responding back.. but this is a HUGE community. That said.. I have found many tips and tricks on 32bit uefi installs and have had decient success with both building my own grub2 and ia32.efi as well as using some of the prebuilt downloads. Also read in a Dev thread that there is no intent on official support for the BayTrail systems due to some propietary bs and intel.. /facepalm. At least most of the intel wireless adapters are available through their installer app.. however not through a ppa. I would like to get this sorted as there are more and more of these dirt cheep but very capable tabs. Especially as the Tw100 w/ keyboard is less than $250us and more expected in ultrabook formats as shown at CES

I will not relink every thread I pulled info out of as there are many and this is over 60 hours of testing/coding. It is all out there for the reading. 
Major sources of step by step help are in the asus t100 threads and Dell Venue 8. HOWEVER both have bcm wireless. Newer systems look to be intel sdio HCI devices.

Getting a 32bit efi usb was easy. Both a 32 to 64bit os and 32 to 32bit. 
1: Build your own *32.efi.
2: Boot/test
3: Install
4: reboot back to the USB and command line use the usb grub to boot the new install
5: rebuild *32.efi into the new install
6: reboot without the usb [-o<
7: desperately try to grab boot errors :confused:
HCI bus, and no communication to firmware being the biggest. (no HCI=no pci anything)
8: try the bcm install instructions from intel minipi internal memo
9: install intel installation package
10: reboot\
try to do stuff and watch the cpu cook.. shutdown FAST

the fedlet install starts at 3. Used Custom 33 from the venue forum
kernel panic from the usb during install attempts primarily if the keyboard timeouts and it kicks to screensaver. (occurs post install as well)
HCI errors still. Although the community patches got a battery management up with % charge only and touch .. although single point and x/y inverted and reflected

I MAY have cooked a CPU core to unuseability in all this. Full wiped and deep formatted the mmc card. Ran windows recovery and reinstall from the backups made prior.
Now have some charging issues and system lag and random core3 fails. ;) oops.

---

### Post by oldfred on 2015-01-15
Supposedly the 3.15 kernel will have mixed mode support built in.

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

---

### Post by kellyvotrenom on 2015-01-19
Saw your reply in my thread regarding Linux on a Winbook.  Not to brag, but I was sent a coupon in the mail and got mine for $30!!!  Even so, having to deal with Windows again still makes me feel like I got ripped off :mad:.

Your Linux skills are way above me, but I still hope to get Ubuntu running on this thing some day.  The only help I can provide is this link to a MicroCenter thread.

[http://www.mctsol.com/phpBB3/viewtopic.php?f=17&t=889](http://www.mctsol.com/phpBB3/viewtopic.php?f=17&t=889)


Don't know if if this provides any more clues, but I hope to continue to follow this idea until somebody comes out with a Linux tablet.

Thanks

Mark Springer
industrial arts

---

### Post by mtndrgon on 2015-01-21
$30?  /cry.. ah well. Ya 'dropped from the sky' is an understatement.  may have to get another one or 3 as I did indeed damage this one.

> **oldfred said:**
> Supposedly the 3.15 kernel will have mixed mode support built in.

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)

Indeed it does. Tested and verified out to the 3.18. I had a 3.14.? that worked as well, but was having too many core errors in 64bit to even pull error logs. the 32bit was fractionally more stable on the winbook to get a partial trace on errors and actually view a log or 2.

Back again with an update. Gave up on ubuntu straight on the Winbook. Messing with 15.04 is still signifigantly more stable than 14.10 but only boot 1 out of 3 times. 
However! With my handy wifi dongle...
[https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/](https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/) to start. Image has 32bit efi burned in.

upgrade kernel with
 sudo yum install kernel --nogpgcheck

running 3.19 rc5 fc21 as it looks like the battery and some sensor patches were upstreamed from the original fedlet.
No wifi or bt yet and I still have the MP-BIOS bug to IO-APIC, GPIO errors, no propper i2c-HCI and APCI has limited function but screen timeout and screen saver works.

fix inverted and reflected touch with
sudo yum install xinput_calibrator
xinput_calibrator --output-type xorg.conf.d

YAY! more stable by far. looking into a google+ thread on fedlet kernel into an ubuntu install.. more to be determined on that one. I just like ubuntu more than fedora.. but thats just me. Gotta work with what I got

---

### Post by sbennettgso on 2015-01-28
I hate to say it, and I bought my Winbook 10" with keyboard/case fully intending to install Ubunutu/Kubuntu on it, but after messing with it for a few days I'm starting to come to the conclusion that Windows 8.1 Metro/Modern is what KDE and Unity should be.  Which is a hard thing for me to say, because I have never been a big fan of Micro$oft (nor Apple neither), so I've always tried to use alternatives where available.

It does what I want, and with the shift to web-based "apps," I don't feel like I have to open a browser to do anything, unless I want to.  Apps look like apps, not an open browser window.  Just like my Android phone (which I'll never give up).  With the larger available screen area on a tablet, I like live tiles.  Unity I feel wastes all that open desktop space.  KDE at least tries with Plasma, but there aren't nearly enough apps/widgets, and most of them don't work all that great.

Someone talk me down...

---

### Post by mtndrgon on 2015-01-28
hmmmmm.. Not going to talk you down on that. Just point out a couple things. 
1 GNOME isn't on that list and using it w/ the fedora is kinda slick. 
2 Unity is a workstation base and not really designed for touch as much as use as workstation which would typically use mouse/keyboard. Using a wacom tab on Unity is AMAZING.. close but not touch and a nice ease of use between multiple monitors.

All that aside, I have ubuntu Touch on and my nexus7 and love it. The UI is designed around and specifically for a touch interface as W8 was. The swipe and movement options are even easier to pick up than w8 or even android. The wife Demanded I not remove it and her mother took to it very well.. Almost thought it was an entirely different device even though she had a nexus7 herself. 

Now all that said, my system is in no means stable running anything BUT M$ crap on this Winbook. Until i have the spare $$ to rip into this and actually scope the chipsets for individual drivers, i still do not have HCI dev, limited ACPI andsingle point touch only. The gnome interface with fedora works rather  well though.

---

### Post by masnatacion on 2015-05-28
Hi
I got it this error during install:
Executing grub-install /dev/mmcblk0 failed

ubuntu 15.04
disable secure boot


can u help me?
greetings

---

### Post by Jon_Thomas on 2016-03-10
> **mtndrgon said:**
> hmmmmm.. Not going to talk you down on that. Just point out a couple things. 
1 GNOME isn't on that list and using it w/ the fedora is kinda slick. 
2 Unity is a workstation base and not really designed for touch as much as use as workstation which would typically use mouse/keyboard. Using a wacom tab on Unity is AMAZING.. close but not touch and a nice ease of use between multiple monitors.

All that aside, I have ubuntu Touch on and my nexus7 and love it. The UI is designed around and specifically for a touch interface as W8 was. The swipe and movement options are even easier to pick up than w8 or even android. The wife Demanded I not remove it and her mother took to it very well.. Almost thought it was an entirely different device even though she had a nexus7 herself. 

Now all that said, my system is in no means stable running anything BUT M$ crap on this Winbook. Until i have the spare $$ to rip into this and actually scope the chipsets for individual drivers, i still do not have HCI dev, limited ACPI andsingle point touch only. The gnome interface with fedora works rather  well though.


I have the 8" TW801 model.  I have tried Gnome on it via USB, and agree it is slick, though the  default on-screen keyboard doesn't want to come up by default.  Going to try Onboard OSK and see if that will work.

Too bad Ubuntu Touch wasn't available as an x86 image.  Would be interesting to try on my 801.

---

### Post by oldos2er on 2016-03-10
Old thread closed. If you have a question about a current Ubuntu version, please start a new thread.

---

