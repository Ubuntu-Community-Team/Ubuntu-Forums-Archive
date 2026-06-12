---
title: "Installation Problems"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by krs000 on 2012-09-20
[COLOR=Red]**EDIT: **[/COLOR]After solving some of the problems with the created USB stick (now I just use [PLOP]("http://www.plop.at/en/bootmanager/index.html") to boot my USB device). I solved my final mistery. Hanging installation on Prepare setup!

To  get some information about the error I had to use for install the  alternative version. From that I could see that the problem was created  by some bad sectors (that no amount of chkdsk was able to fix). After  some more investigations it turned out that the sector was *in Master File Table* or *MFT* . Hard format the problematic partition... ubuntu installed like a charm.

Wy suse and windows had 0 problems with that bad MFT and why Ubuntu was hanging instead of gracefully giving back some error information... is another story.

------------------------------------------------------------------

I was having serious problems setting up a dual boot Ubuntu 64 / Windows 7 from a live CD (USB). After days of trying ZERO success. Here my list of issues maybe it will save someone some trouble in the future.

Let me say first I had ZERO problems installing OpenSuse. This will weed out some possible causes (This to avert lots of posts like check your USB stick, check md5, check motherboard booting capability, etc. Done all of those already a couple of times).

Here my list of encountered problems:

**First with the regular x64 desktop version.**

1. Cannot create a bootable USB Stick from windows with unetbootin / Universal USB Installer. 

Background: My motherboard is *ga-ep45-ds3r* and can boot from USB in two ways. Detects stick as a bootable device and I can directly select it, or it does not detect it, but I can still boot from it if I check the *boot from USB-HDD* option.

So from windows using unetbootin I cannot create a direct detectable boot device (can only boot using 2;nd option). **From Suse using unetbootin no problems.**

2. Installations hangs at Preparing Installation.

So I managed to boot the live CD (USB) and clicked install. Needless to say it hangs forever at Preparing Installation menu with no error message whatsoever. (Hardisk activity led bright red).

Possible suggested issue Partition table problems. Ran chkdsk from windows a lot of times fixing some errors. Tried install anew... again same problem hangs at Preparing Installation.

Now the weird thins gparted shows me all ntfs partitions have errors. Reboot the live CD gparted shows me only one partition has errors... go figure.

**Second with the alternate x64 version**

This one is even worse... it will not boot.* "Unknown keyword in configuration file"* followed by: *"Cannot recognize kernel"* for every command I try. See [here ]("http://ubuntuforums.org/windows how to check if the disck is dinamic")for more similar problems. None of the suggested solution worked for me.

So after much anticipation and excitement to come back to linux after some years... reverted back to windows pretty much disappointed on the maturity of this product.

---

### Post by spjackson on 2012-09-20
Welcome to the forum. You don't sound as though you are looking for help, but I am curious. Since you "had ZERO problems installing OpenSuse", why did you decide to abandon Linux and revert to Windows?

---

### Post by krs000 on 2012-09-20
> **spjackson said:**
> Welcome to the forum. You don't sound as though you are looking for help, 

I posted here for 3 reasons mainly:

- I had to share my frustrations gathered in the past few days.

- Share the problems I had and the solutions I found so that they do not lose the same insane amount of time trying to fix things that were working from the beginning.

- and last. I've posted also in the faint hope that someone encountered my problems and has a solution to them. I still really really want to have Ubuntu on my system since I am 100% open source / freeware anyways.

> but I am curious. Since you "had ZERO problems installing OpenSuse", why did you decide to abandon Linux and revert to Windows?
 
- because playing 1080p content seems not to be an option in Suse. Unlike Ubuntu were I found some posts describing enabling of some hardware stuff for nvidia (PPA I think).

---

### Post by jrog on 2012-09-20
It seems to me that this could be a problem with unetbootin rather than with Ubuntu, though I can't be sure. I haven't had any problems using Ubuntu from a Live USB, but perhaps I'm just lucky. Are you interested in trying other methods of creating a bootable Live USB?

---

### Post by penreturns on 2012-09-20
Have you check your md5 iso? Are you sure your iso is not corrupt? Please check back. If all ok, when booting from cd, choose **Try Ubuntu**. Check all hardware, wireless, sound, etc. Then click install button from there.

---

### Post by krs000 on 2012-09-20
> **penreturns said:**
> Have you check your md5 iso? Are you sure your iso is not corrupt? Please check back. If all ok, when booting from cd, choose **Try Ubuntu**. Check all hardware, wireless, sound, etc. Then click install button from there.

*"to avert lots of posts like check your USB stick, check md5, check  motherboard booting capability, etc. Done all of those already a couple  of times..."*

So yes I did all that already a couple of times.

---

### Post by krs000 on 2012-09-20
> **jrog said:**
> It seems to me that this could be a problem with unetbootin rather than with Ubuntu, though I can't be sure. I haven't had any problems using Ubuntu from a Live USB, but perhaps I'm just lucky. Are you interested in trying other methods of creating a bootable Live USB?

You convinced me to give it another try... I had PloP Boot manager in mind.

[Plop boot manager]("http://www.plop.at/en/bootmanagers.html") works like intended. Allows me to boot from all of my USB pen drives. Doing alternate install all goes well until... grub checking for other installed systems. Needless to say like suspected it hangs. In another terminal lots of disk errors. The thing is the drive was cleaned in windows with chkdsk /r /f 2 times. First time corrected errors... second time none were found. And again why is suse installing (grub and all) with no problems...

I will do a chkdsk a last time... will report back (in ~24 h :( ).

---

### Post by jrog on 2012-09-20
> **krs000 said:**
> You convinced me to give it another try... I had PloP Boot manager in mind.

[Plop boot manager]("http://www.plop.at/en/bootmanagers.html") works like intended. Allows me to boot from all of my USB pen drives. Doing alternate install all goes well until... grub checking for other installed systems. Needless to say like suspected it hangs. In another terminal lots of disk errors. The thing is the drive was cleaned in windows with chkdsk /r /f 2 times. First time corrected errors... second time none were found. And again why is suse installing (grub and all) with no problems...

I will do a chkdsk a last time... will report back (in ~24 h :( ).
I have zero experience with Plop, but was the USB drive that you tried to boot using Plop still the one that you created with unetbootin? I was thinking that perhaps unetbootin itself is having a problem creating an appropriate Live USB from the Ubuntu 12.04 ISO, in which case you'd need to create the USB using a different method.

---

### Post by krs000 on 2012-09-21
> **jrog said:**
> I have zero experience with Plop, but was the USB drive that you tried to boot using Plop still the one that you created with unetbootin? I was thinking that perhaps unetbootin itself is having a problem creating an appropriate Live USB from the Ubuntu 12.04 ISO, in which case you'd need to create the USB using a different method.

Unetbootin experience was for the **desktop!** ubuntu (ubuntu-12.04.1-desktop-amd64.iso). The same Ubuntu live "CD" created on the same 1GB USB stick did not boot if created from windows 7 and did boot correctly if created in opensuse.

Clearly it is also a MB issue but if it works from Suse... 

Here the use cases I encountered:

- the device is always listed correctly if I leave the stick formatted as NTFS. (not booting linux though)
- If I format it as fat32 and use opensuse netbootin - the usb stick is listed correctly and booting with no problems.
- If I format it as fat32 and use windows netbootin - the usb stick is not listed correctly and not booting. (left stick untouched and installed PLOP on HDD, stick boots like a charm)

---

### Post by krs000 on 2012-09-22
All problems solved! The ugly one came from a bad MFT that chkdsk did not correct. Read EDIT in first post if you are interested in more details.

---

### Post by jrog on 2012-09-22
> **krs000 said:**
> All problems solved! The ugly one came from a bad MFT that chkdsk did not correct. Read EDIT in first post if you are interested in more details.
Thanks for giving the details. Glad you got the problem worked out!

---

