---
title: "Dealing with i915 Issues Before Install"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by whackdoodle on 2007-03-14
Trying to install Edgy on Toshiba Satellite M65-S9062 laptop, which has Intel 915GM/GMS 910 GML chipset which uses the the Intel Graphics Media Accelerator (GMA) 900.  Installation fails almost immediately (well, actually after about 4 minutes of horrible-sounding CD grinding) before X windows can even load.  The error says something to the effect of "I810: No matching Device section for instance (BusID PCI:0:2:1) found.  I810(0): No video BIOS modes for chosen depth ... no screens found."  All of this before I've even had a chance to tell it "No! That's not what I want."

So after a few hours of scouring the Internet and learning a bunch about my chipset and processor and esoteric things like northbridge and southbridge, I think I'm supposed to do something with "915resolution" ([http://www.geocities.com/stomljen/)](http://www.geocities.com/stomljen/)).  And the instructions are reasonably clear, but they seem to assume that I already have Ubuntu or some other Linux distro installed.  Which I don't.

Here's where it gets fun:  I have a 60GB drive, with 36.1GB configured as a Primary NTFS partition that currently has Vista Ultimate running in it.  Then there's a little more that 10GB that's unallocated to anything right now, since I was planning to give that to Ubuntu.  Whatever else I do, I'd really like to NOT lose the Vista installation since it works almost flawlessly in my opinion, and it's taken me a week to load up all the software and settings just the way I like.  (Incidentally, despite all the trash in the trade rags to the contrary, the Vista installation itself was so easy and error free my grandpa could have installed it.  I'm really wishing Ubuntu had been so simple ... but I'll give Ubuntu however long it takes to prove itself.)

But I digress:  How do I get Edgy installed since I can't seem to get the install to recognize my video?  

This is my first attempt to install Ubuntu.  I'm not a Linux user, so you'll have to explain this process to me using small words and short sentences.  :)   Am I going to have make a custom boot CD/DVD in order to achieve the desired results?  If I need to make some tweak to my video BIOS, is that going to affect Vista?  Will I have to make the tweak every time I start Ubuntu?  Does this tweak apply to Gnome and KDE as well as X Windows?  And after I get past this problem, what will be the next problem I face?  (ATA100 issues? Wireless setup problems?)  What are the other critical steps in the installation process that I can research and prepare myself for now?  

And after I get it all installed, will I be able to get my new Microsoft USB Fingerprint Reader eventually working?  Will I ever be able to sync my Windows Mobile 5.0 smartphone (Verizon XV6700) with Ubuntu?  Can I play the WMA tracks I bought from the now defunct MSN Music?   (Perhaps you're beginning to see now just how "diehard Microsoft" I am.  But flame me not!  I'm trying to learn what, by all accounts, is the most brilliant distro of Linux to come along in many years.)

Thanks in advance!

---

### Post by Arby on 2007-03-14
This is a tricky one. The error you are seeing means that X cannot detect your monitor properly. This can be fixed by editing the file /etc/X11/xorg.conf but if it won't even let you finish the install I'm not sure how we can do that.

It seems odd that Ubuntu completely fails to finish the install, I could understand X not coming up. So, a few questions. Can you boot Ubuntu from a LiveCD (if you don't know how to do this just ask)? Secondly, after you see the error from X what is shown on your screen? Do you get a command prompt? Something like
```
you@yourcomputer:~$
```or ```
root@yourcomputer:$~
```. If you can see this then your install probably has worked and it's just X windows not starting correctly. If you have a command prompt then we have something to work with and we can get this fixed.

Xorg can be a temperamental beast but it can be tamed. If  we can establish that it is definitely Xorg that's the problem then we can fix it without any risk to your Vista install.

We can deal with your other concerns once you get the install up and running but just a few comments to reassure you.

> What are the other critical steps in the installation process that I can research and prepare myself for now?  Do some research about your wireless card. What make/model is it? What driver does it use? Is there any documentation for your card under linux. The ease of getting things to just work is directly dependent on your hardware. If it's an Intel wireless card it should be straight forward (no promises)

> Can I play the WMA tracks I bought from the now defunct MSN Music? Yes as far as I know.
> will I be able to get my new Microsoft USB Fingerprint Reader eventually working?  Again depends entirely on the hardware. I've never tried this myself but I'm lead to believe that fingerprint readers can be made to work under linux. I don't know about your specific one.

However, first things first. Lets fix your basic install. If you can answer my first questions we'll see where to go next.

Be patient, it's a learning curve but it's worth it.

Arby

---

