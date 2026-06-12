---
title: "Upgrade Win-XP to Win7, now can't boot into Ubuntu"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by Riverglen on 2012-12-09
I had my old HP laptop configured for dual booting either Windows XP or Ubuntu (ver. 11.04).  I upgraded the Windows installation to Win-7, which boots fine, but I've lost the ability to boot Ubuntu.  Its pretty clear that Windows just went ahead and overwrote the boot record, but I don't know how to restore the dual boot.  The pre-existing boot manager was the legacy version of Grub, which I was perfectly satisfied with, although I realize the world has moved on to Grub 2.

---

### Post by papibe on 2012-12-09
Hi Riverglen.

The easiest way to reinstall grub would be to use the Ubuntu CD/USB as a live CD and use Boot-Repair. Take a look at this [tutorial]("https://help.ubuntu.com/community/Boot-Repair").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by arpanaut on 2012-12-09
This should help: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Although having grub legacy on your install may jump up and bite you...
I'm not sure of the possible conflicts.

---

### Post by Riverglen on 2012-12-10
I've tried both methods suggested for running Boot-Repair, with no success.  The following summarizes my experience running from a Boot-Repair CD.  But I also tried the approach of running a live 11.04 CD and had very much the same results.  The .iso file I used to create the CD was for the more limited version of Boot-Repair, which among other things apparently doesn't support Wi-Fi.

After booting up, I was presented with the Boot-Repair dialog.  I decided to change one "advanced" option, to make Windows the default OS.

The repair process seemed to start ok, but I wound up with an error box (paraphrasing a little, but close):

apt-error detected, please open a terminal and enter the following command:

sudo chroot "/mnt/boot-sav/sda2 apt-get -f install

(I should note here that it was FAR form obvious how to get a terminal window from the very sparse desktop presented, but after digging around a while, I figured out how to do it.)

Running that command resulted in a long list of output lines that made it pretty clear that something had gone off the rails.  The last line of the output before I was returned to the command prompt was

E: Unable to fetch some archives, maybe run aptget update or try with --fix-missing?

So, I went back to the Boot-Repair window and selected the option for creating a bootinfo summary.  The process provided me with a url and an address to send it to, or optionally post to a forum.  The last of several times I've gone through this routine the url provided was [http://paste2.org/p/2587111](http://paste2.org/p/2587111).

Out of curiosity, I opened the provided url (from one of my earlier failed attempts) in Firefox and got what looked like a search results page.  One of the options took me to a page for a school budget report from someplace in Montanna!  Haven't tried it with the one in this post.

So, to say the least, I'm still perplexed.

---

### Post by oldfred on 2012-12-11
If you set Windows as the default it will not boot Ubuntu.

You seem to still have grub legacy with menu.lst. Grub legacy was last used as the standard with 9.04, but if you upgraded from that or forced grub legacy you can still have it, if it works. Grub2 supports a lot of new features with newer computers.

Boot repair will not fix grub legacy but will offer to uninstall it and install grub2. But you have to have to good Internet connection as it has to download new files.
Edit-
10.10 expired last April, so you cannot download new files. All you really can do is use your liveCD to reinstall grub legacy.

If you just want to manually reinstall grub legacy.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Riverglen on 2012-12-11
Thanks for your info.  You are correct that I was still using Grub legacy.  I don't believe that I was ever offered the option to graduate to Grub 2 as I stepped along the upgrade path.  I don't know much about Grub 2 other than that it seems to offer a bunch of options that I'm not likely to care about.  I haven't looked carefully at the link you referred me to yet, but the focus seems to be on Grub 2.  Would I be better off going to Grub 2 or sticking with the legacy version?  My laptop is around 5 years old, so the "newer computers" relevant features are probably moot for me.

---

### Post by oldfred on 2012-12-11
Both my systems are 6 years old, but I upgraded to grub2. 

At first I did not like it as I was multi-booting with chain loading and had grub in every PBR. Grub2 does not like to install to PBR, but actually works better as it can directly boot every install. Also at first we did not understand grub2 and it has a lot of changes. I dual booted with XP until this year.

If you do a new install, which is about your only choice, you will get grub2. Bigger issue will be Unity. I installed gnome-panel or fallback which is almost like gnome2. Others may suggest Kubuntu, Xbuntu or Lubuntu or some of the off shoots like Mint.

---

### Post by Riverglen on 2012-12-11
Been reading around in all the Grub documentation and discovered a section titled Reverting to Grub legacy.  It is based on selecting the appropriate option in the Boot-Repair tool, but it of course assumes that the system had been using Grub 2.  It seems to imply that it will replace Grub 2, broken or not, with Grub legacy.  Question is, will it also fix a broken grub legacy on a system that has never run under Grub 2?

---

### Post by Riverglen on 2012-12-11
Well, your latest remarks have given me something to think about.  My current installation is 11.04.  I believe that this is the first version with the Unity interface.  I think that Unity is the most God awful abomination I've ever seen.  (Windows 8 is a close second).  In 11.04 at least, you can configure system boot options to come up in Ubuntu classic.  I came to the conclusion somehow that in subsequent versions of Ubuntu you can no longer go that.  That was the reason I stopped upgrading when new versions come out.  It's Unity or nothing?  If that's the case, then its nothing.  I will NOT run under Unity under any conceivable circumstances.  And the reason I finally upgraded to Win-7 was to avoid the prospect of ever having to live with Windows 8.

I had been considering the possibility of just scrubbing the Ubuntu partitions and reinstalling with the current version.  But there's no way if that would stick me into Unity Land.

---

### Post by oldfred on 2012-12-11
I think Boot-Repair will walk you thru a chroot which then is a un-install of grub & grub2 and a reinstall of which every one your want. If you do not have something installed the uninstall will just not work, but then reinstall should.

Doing your own chroot.
HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

I still have Unity in my 12.10 install but use that so little and I just cannot get used to it. But my 12.04 install which may be my working install for a while   due to spouse discussion of too many changes.  :)

Off topic of thread:
But with fallback it is just like gnome2 with some minor changes. I thnk fallback was gnome2 without Unity and gnome-panel is gnome3 without Unity, but if you install fallback in 12.04 it really installs gnome-panel.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)
# for gnome2 prior to 12.04
sudo apt-get install gnome-session-fallback

---

### Post by Riverglen on 2012-12-11
Well, I tried the purge and replace option as described in the link in your last post (HowTo: Revert from grub2 to Legacy Grub or grub to grub2). No joy.  Pretty much the same result as my previous attempts.

Got the same request to execute the chroot command from a terminal

Got lots of output as a result, but the last line in that output was different:

    E: sub-process /usr/bin/dpkg returned an error code (1)

Quit out of the tool and was informed "No operation was performed" and the state of the machine is apparently unchanged.  So...?

If I understand you correctly I could do a clean install of the latest version of Ubuntu and then install either fallback or gnome-panel to get the classic desktop back?  If so, I may wind up doing that.  I have Ubuntu running on my desktop as well, and the laptop copy is sort of my sacrificial environment for experiments of this sort.  Nothing on the laptop is worth worrying about loosing.

---

### Post by oldfred on 2012-12-11
I think the update on 11.04 will not work as it has expired as of         28 October 2012.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

