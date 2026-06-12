---
title: "new to Ubuntu - installation sadly fails"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jerry1970 on 2011-05-02
Hi all,

I am completely new to Ubuntu and linux, but am so fed up with M$ that I want to try it. Unfortunately, the installation does not work...

I have a laptop with pentium pro processor, 1GB RAM, 80 GB disk. Should be enough, right? Boots from CD ROM, so the i386 installation ISOs are the ones for me, I guess. I use Nero to burn the CDRs from ISOs on a WIN machine. All CDRs start OK, so I assume it's not the burning process.

First I downloaded 10.10 Desktop ISO. That gave different errors during installation. I checked the hard drive for errors - none found.

In the meantime 11.04 was released, so I downloaded the 11.04 Desktop ISO. Now only one error: bootloader could not be installed in /dev/sda. I could not skip it and could not stop the installation.

But this one gave me an error of "partman" not being able to install. I assume that is Partition Manager or something, so pretty important.

Then I tried the 11.04 Alternate ISO. But that one is now asking me this:

[FONT=Courier New]Please insert the disc labeled: 'Ubunti 11.04 Natty Narwhal_ - Release i386 (20110426)' in the drive '/media/cdrom/' and press enter.[/FONT]

I tried the first 11.04 CDR I downloaded, but that didn't work. Then I downloaded the ISO with a release date of 2011-04-28 (I couldn't find one released 2011-04-26, though the Alternate was released 2011-04-26).

Can someone tell me what to do exactly? Which files do I have to burn on CDR to make this work?
What should I do with the disk before I start? I removed Windows, then I tried the Use Whole Disk in 10.10 and 11.04. Should I also tried manual (sda1 75 Gb, linux swap 5 Gb). Nothing works...

I only want to have Ubuntu on the machine, so bootloader does not sound necessary. But I cannot skip it.

Any help is much appreciated!

Thanks,
Jerry

---

### Post by cogier on 2011-05-02
Jerry,

Your computer looks a little old so I would stick with 10.10 or 10.04 for the moment. 

To get more help can you tell us the error messages you are getting and the make and model of computer.

---

### Post by Dutch70 on 2011-05-02
Edit: Can you run Ubuntu from the live cd???

I don't think Nero works well for burning Linux cd's. I would try a different program or a usb stick.

It's also a good idea to stick to 10.04.2 Lucid Lynx as it is the most stable and supported longer than any current release. 
Including the one that was just released. 

You can get it here.
[[COLOR="Red"]http://www.ubuntu.com/download/ubuntu/download[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download")

You should also check the md5sum of the .iso before burning it to disc.
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Then check the cd for defects.
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

As I said though, if you've got a usb stick & your computer can boot from it, I'd go that route.

BTW, Welcome to UF :)

---

### Post by jerry1970 on 2011-05-03
Thanks for the replies! I'll check the details of the laptop (Fujitsu Lifebook is what I know, details not sure) (EDIT: it's probably 5 or 6 years old now, never had any big issues with it being slow, though I *am* used to windows of course ;)) when I get back home.

Yes, I have been running 10.10 and 11.04 from the live CD without any problem. I tried installing using the desktop icon when running from the live CD as well as rebooting and installing directly from the CD. That's why I thought it wasn't the burning process that is causing the problems.

Running from USB stick - didn't think of that. I am going to try that. Also a lot easier than burn a CD every time... ;)

Cheers,
Jerry

---

### Post by deconstrained on 2011-05-03
Use Xubuntu or Lubuntu, preferably an LTS release as has been suggested (10.04 is the most recent one). Lighter window manager, lighter desktop manager, comes with less default-installed bloat.

I recently set up Xubuntu on a 5-year-old laptop (an Acer Aspire) for my old man and it runs like a breeze, even running off an LVM on top of full-disk encryption.

---

### Post by vanquishedangel on 2011-05-03
I am a fan here of Lubuntu, I have it running on a Compaq presario 1500, 1.6 ghz processor, 1 gig ram, and an ATI mobility radeon 7500 with 64 mb video ram, it is running natty now quite well with the LXDE desktop and the lxdm desktop manager. That laptop is over 10yrs old and it is running better than new. xubuntu is about 1/2 the resource weight of a normal Ubuntu, and lubuntu is about 1/5 of a normal Ubuntu.

When I used window's many years ago, I used cdburnerxp pro to burn Linux iso's here is the link

[http://download.cnet.com/CDBurnerXP/3000-2646_4-10409086.html](http://download.cnet.com/CDBurnerXP/3000-2646_4-10409086.html)

P.S. burn at a slow speed and use the error protection (i forget what it is called)

here is the link to lubuntu 11.04

[http://people.ubuntu.com/~gilir/lubuntu-11.04.iso](http://people.ubuntu.com/~gilir/lubuntu-11.04.iso)

and here is more info on lubuntu and downloads from distro watch (and has a LTS version as well)

[http://distrowatch.com/table.php?distribution=lubuntu](http://distrowatch.com/table.php?distribution=lubuntu)

good luck with it and I hope this helped.

---

### Post by jerry1970 on 2011-05-03
> **vanquishedangel said:**
> I am a fan here of Lubuntu, I have it running on a Compaq presario 1500, 1.6 ghz processor, 1 gig ram, and an ATI mobility radeon 7500 with 64 mb video ram, it is running natty now quite well with the LXDE desktop and the lxdm desktop manager. That laptop is over 10yrs old and it is running better than new. xubuntu is about 1/2 the resource weight of a normal Ubuntu, and lubuntu is about 1/5 of a normal Ubuntu.

Thanks for the info - I wasn't even aware of lubuntu and xubuntu. But lubuntu sounds like the way to go for me.

I still have to get to learn about an OS with different possible DEs on top. Hey, I am a still win user... ;) I am a computer programmer and know several OO languages though, so it easy to understand, but I can't oversee the consequences of one choice or the other.

I can't find any good comparison tables for all different DEs, so I'll just ask here then. First of all - many thanks for replying and helping me out. I am sure this is going to work and be an ubuntu fan, too. ;)

I am going to use my laptop mainly for working on websites (PHP) using NetBeans, and listening to music or watching movies would be nice (I am used to VLC). I share music via utorrent, edit WAVs using Audacity, write docs and sheets using OpenOffice, browse sites and read mail using Firefox and Thunderbird. Does any of these mean I should use one DE or should not use another?

I assume I need packages of the programs I would like to use written for or compiled in the DE that I choose, right?

Thanks again!

---

### Post by dino99 on 2011-05-03
i'm ruuning ubuntu on an older laptop (512 Mo only): natty i386 run smootly on it, so yours is ok too

follow this help for install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Dutch70 on 2011-05-03
I like Lubuntu & it's a surprisingly nice system for computers that have really low resources.
[[COLOR="RoyalBlue"]http://en.wikipedia.org/wiki/Lubuntu[/COLOR]]("http://en.wikipedia.org/wiki/Lubuntu")

If you have at least 512MB of RAM, you would be better off with [[COLOR="RoyalBlue"]Xubuntu[/COLOR]]("http://www.xubuntu.org/get").

One thing to do as I mentioned earlier. Is try them from a usb stick. It's easier, cheaper & faster than a cd. 
This site has the download & instructions for creating a live usb.
 [[COLOR="RoyalBlue"]unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

---

### Post by vanquishedangel on 2011-05-03
> **jerry1970 said:**
> Thanks for the info - I wasn't even aware of lubuntu and xubuntu. But lubuntu sounds like the way to go for me.

I still have to get to learn about an OS with different possible DEs on top. Hey, I am a still win user... ;) I am a computer programmer and know several OO languages though, so it easy to understand, but I can't oversee the consequences of one choice or the other.

I can't find any good comparison tables for all different DEs, so I'll just ask here then. First of all - many thanks for replying and helping me out. I am sure this is going to work and be an ubuntu fan, too. ;)

I am going to use my laptop mainly for working on websites (PHP) using NetBeans, and listening to music or watching movies would be nice (I am used to VLC). I share music via utorrent, edit WAVs using Audacity, write docs and sheets using OpenOffice, browse sites and read mail using Firefox and Thunderbird. Does any of these mean I should use one DE or should not use another?

I assume I need packages of the programs I would like to use written for or compiled in the DE that I choose, right?

Thanks again!

Yes in any desktop you choose you can install what ever you want in it through software center or synaptic and all dependencies will get installed, Lubuntu and xubuntu has their own programs for alot of things, like instead of thunderbird you get sylpheed, and for movies you get mplayer, cd burning is xfburn but they all have the same functions and work well in my experience. but you can install thunderbird, vlc and brasero if you wish.

---

