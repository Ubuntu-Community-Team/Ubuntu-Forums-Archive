---
title: "Xubuntu, A host of Startup Issues"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Micrll on 2007-09-04
Requesting Help from the Ubuntu / Xubuntu Community

Unable to get Xfce to start under normal boot.

Hello All, I just spent a good portion of today trying to get Xubuntu to run on a older compaq laptop, me and my roomate though that it would be worth putting linux on it.
The specs of the laptop are as follows
1024x768 Screen
60GB hard drive (upgraded)
300Mhz P2
192MB of RAM
CDROM Drive
No ethernet onboard
1 Ethernet PC card

The exact model is that its a Compaq 1672

Here are some problems we have encountered and are still experiencing.

Using the original 7.04 installer failed, it would boot into Xfce and it would freeze at a blue screen with the mouse frozen.
Additionally it would sometimes freeze at the verbose portion of the startup with various errors relating to ALI15x3, other times it would continue on.
Read some posts on this message board and downloaded the alternate install.
It took forever and a it hung once on the ethernet card.  Removed it and managed to complete the text based installation.

GRUB bootloader shows up just fine
Selecting Ubuntu, normal boot (the first option) causes it to load but again freeze at a blue screen with the mouse frozen.
If I select recovery mode it will load into the terminal line.
I can use startx to load Xfce but I am unable to really do anything with it.  It seems to load and work just fine, a little slow but not too bad.
I try to access some of the system controls, not the Xfce controls, but it says I don't have privileges.  Strange though, considering that when I look at the file system it says I am logged in as root.  So I can't access any of the hardware control panels.

If I click quit, I am given only two options.
	Switch User
	Log Out

If I select switch user it says that the gnome manager is not loaded.
Logging out will take me back to the command line.

Just while writing this it is now hanging at startup even on recovery mode.
Last time it hung at a fsck check (for over 15mins)
It just now hung at recovery mode at a little after loading manual drivers.

**Can anyone give me some help / recommendations.**  I am willing to format the linux partitions and install a different distro.

The laptop did run a old knoppix 3.3 cd just fine (though slow through the CD drive)

Also, playing the audio examples in the built in media player causes x to crash.

---------------
Thoughts on experience...

So right now I am frustrated, I tried using linux about 2-3 years ago and had a host of issues with it then.  I figured I would give it some more time and come back later, and this experience has been even worse.  As a sophomore CS major I really thought I would be able to set this up easily enough but Linux still fails at this.  I know people who have gotten it working but it never seems to work for me...  Additionally the documentation on Xubuntu is sparse and really hard to find.   I would get on IRC but my univerity is blocking all IRC chat, I have tried various OS's clients and servers but I can't get IRC traffic out, so that support option is gone.

Again can anyone help me get this working or suggest another option for this old laptop?  I would really like to get something other than windows 98 running on it.

---

### Post by kerry_s on 2007-09-04
try debian, it's alot better on older systems->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)
make sure when your burning the iso, your burning at 4x so you get a good burn.

i recommend when you get familiar with debian, do a custom install with a lighter setup.

you might also try DSL linux, as it's built to be small and fast on old hardware with limited resources.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Micrll on 2007-09-04
> **kerry_s said:**
> try debian, it's alot better on older systems->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)
make sure when your burning the iso, your burning at 4x so you get a good burn.

i recommend when you get familiar with debian, do a custom install with a lighter setup.

you might also try DSL linux, as it's built to be small and fast on old hardware with limited resources.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

The biggest problem that appears there is that Iwill not have a working connection to the internet on that machine when its installing.  Our school's network requires you to authenticate on a webpage before you can get access.  Will Debian still install without a net connection?

---

### Post by kerry_s on 2007-09-04
> **Micrll said:**
> The biggest problem that appears there is that Iwill not have a working connection to the internet on that machine when its installing.  Our school's network requires you to authenticate on a webpage before you can get access.  Will Debian still install without a net connection?

yes, it will.
that's not the net installer, that's the regular cd, it's like installing xubuntu.

---

