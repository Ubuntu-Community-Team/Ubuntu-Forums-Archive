---
title: "gawk required to run bootinfoscript on edgy eft"
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by classacted on 2016-05-29
hello,

I tried to execute bootinfoscript on an edgy eft installation, and it didn't work.  the terminal said the reason was 'gawk could not be found'.  just to satisfy curiosity, I also tried to run bootinfoscript on hardy heron.  though hardy didn't have gawk either, bootinfoscript DID work.  here is the explanation from the terminal:

**"'gawk' could not be found, using /usr/lib/initramfs-tools/bin/busybox awk instead"**

bootinfoscript generated a nice text file, though it also stated 'the results may be unreliable'.  I found the file to be very accurate after a considerable examination (I could post it here, but it's large and doesn't really contribute to the issue I am here for).  here is my reason for posting:

since 'busybox awk' worked adequately for hardy heron, could it be used on edgy eft?  would there be any harm?  how difficult would this be?  would it be better to use gawk?  how much work is that?

any info or expertise would be most appreciated.

---

### Post by grahammechanical on 2016-05-29
How will you install busybox when Edgy Eft (Ubuntu 6.10) reached end of life April 2008? The 6.10 repositories are now closed and they have been archived and are now at a different location. You will need to follow part of the instructions for doing an End Of Life upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


And then it will all depend on busybox being in the 6.10 repositories.

Would there be any harm? What is the worse that could happen? I assume that you are doing this as an experiment or for some educational reason. When an experiment goes bang the experimenter rebuilds the experiment. 

On the other hand, if this is a working install of Edgy Eft (6.10) and you are trying to fix some problems with it, then I do not think that this forum can provide support for an installation that has been out of life for 8 years. This forum started about that time. The forum posts are archived. I just did a web search for "edgy eft" and it came up with a forum discussion as to what an "eft" was. So, if you are trying to solve a problem then a web search might be helpful.

Regards.

---

### Post by classacted on 2016-05-29
hello grahammechanical,

**"I assume that you are doing this as an experiment or for some  educational reason. When an experiment goes bang the experimenter  rebuilds the experiment."**
you assume correctly.  it's a project where I use grub4dos to 'patch in' hard drives and focus on linux and linux resources to boot them with other bootable hard drives.  my choices of computers are limited and since the computer that is dedicated to the project is old, I thought an older OS would also be necessary.  I am kinda 'throwing it against the wall and see what sticks'.  though the OS's are old, things are actually going better than expected.  since I have never heard of 'gawk' or 'busybox awk', I came here after a google search was in vein.
I understand the dilemma that you are hinting at, that the software may no longer be obtainable.  it's a shame because it limits the bootinfoscript tool.
thanks for the reply.

---

### Post by oldfred on 2016-05-29
If you open bootinfoscript with gedit, you will see a link to this. 
Script was not really developed until 2008 to simplify all the terminal requests for more info for boot issues.

The birth of Boot Info Script:  
[http://ubuntuforums.org/showthread.php?t=837791](http://ubuntuforums.org/showthread.php?t=837791)

But also over time it has been improved, but most of those improvements are based on current systems.

If you have old hardware best to use current version Lubuntu or Xubuntu.

 Older hardware suggestions - mörgæs
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by sudodus on 2016-05-29
***awk*** is an old unix tool, so I would assume that is is available in early versions of Ubuntu. I don't know when ***g**awk* arrived.

- Would it work with awk, or does your script need gawk?

- Is there an available C compiler in your Edgy? In that case you might be able to compile it (in Edgy).

-o-

But as has already been written, there might be better alternatives 'still supported or at least more recent' ultra-light linux distros that would work in your computers. If you tell us about the computers (the hardware specs), we can give you some tips :-)

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card

---

### Post by grahammechanical on 2016-05-29
@classacted

That wiki page about upgrading from an end of life release explains the changes we need to make to the sources.list file to be able to access the edgy repositories at old-releases.com. And if busybox is in the the repositories you can install it and see what happens.

You need to change the URLs in /etc/apt/sources.list to this

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse


And then run

```
sudo apt-get update
```

and see if it throws any errors.

Regards

---

### Post by classacted on 2016-05-31
thank you gentlemen for all the info.  it seems that my decision to use old distros has brought difficulties to my project.  none of the OS's I installed will surf the web.  I don't know if the old distros are to blame for the inability to use the web, but I think the chance is better than 50%.  the ethernet cable HAS service, and if I plug the cable into any other computer I can surf.  the lack of internet connection complicates matters too much for a newbie, which I am.  there may be a way to get the connectivity to work, but how much time do I invest that I could spent on the grub4dos project.  
I have other hard drives and as soon as I conclude this project, I will reinstall up to date distros for the next project.  I use blacklablinux xfce version quite often, which is very near xubuntu, so I can say for sure that it's an excellent choice and a distro that I can work with.  lubuntu is not bad either.  also linux lite.
it will be interesting to see what I can do with bootinfoscript with my next project.

---

### Post by oldfred on 2016-05-31
With newer systems better to use the latest fork of bootinfoscript.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

Or use Boot-Repair's summary report. It actually uses the newest bootinfoscript & adds a lot of other useful info.
       
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by classacted on 2016-06-01
thanks old fred.  I did everything I could to grab everything there.  you never know when those things are no longer available.

---

### Post by grahammechanical on 2016-06-01
If the hardware is newer than the OS then the OS may not have drivers for the hardware. Each version of Ubuntu comes with the newest Linux firmware (kernels  & driver modules). That is how Ubuntu keeps up to date with newer hardware. 

Regards

---

### Post by classacted on 2016-06-03
good point, grahammechanical.  I think the computer is older than both OS's.

---

