---
title: "Difficulty creating 16.04 bootable USB after failed upgrade"
date: 2016-09-03
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2016-09-03
I run a desktop machine & two laptops, all were happy on 14.04 LTS. Details below. And I use Ubuntu because I like the principle, and it means my elderly machines keep going, not because I understand much of it. I don't! So this is a jargon-free zone, please :-)

I tried the offered 16.04 upgrade on my Samsung laptop. Result =  laptop which only gets as far as a very distorted password screen, then puts itself into sleep mode.
So I  downloaded 16.04 from the Ubuntu site to try a clean install, using my Desktop to do so. I verified the ISO and that seems good; used Startup Disk Creator to load it onto  a new 4 GB USB memory stick.
The Samsung still allows me to change boot order, so inserted it and get this message:

    Missing parameter in configuration file.   Keyword: path

  gfxboot.c.32: not a COM32R img

The second line of this keeps repeating every few seconds.
 When I try the same stick in my Acer laptop, I get the same result. Haven't  tried it on the desktop machine, it's our main "everything" machine and don't want to risk upsetting it, but it seems this fault is thus now within the USB stick.


Not sure I'm going to risk updating anything else yet, but would like to get the Samsung working again, and would like to try 16.04 on it if possible.
Any patient guidance welcome, please.

   
**Samsung R50 laptop**
 
 Processor: Intel (R) Pentium (R)
  CPU Speed 1.73Ghz
Memory 2048MB
OS type: 32 bit to the best of my knowledge.  It's not telling me much at present!

   
**Acer Aspire 5313 laptop**
 [FONT=Gill Sans]Memory: 2.0 GiB[/FONT]
Processor:  Intel® Core™2 Duo CPU T5550 @ 1.83GHz × 2 
Graphics : Intel® 965GM x86/MMX/SSE2
OS type: 32 bit
  Disk: 155.3 GB

   
[FONT=Gill Sans]**Desktop:**[/FONT]

 [FONT=Gill Sans]Memory: 2.0 GiB[/FONT]
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2  
Graphics : Gallium 0.4 on NV86
OS type: 32 bit
Disk: 155.3 GB

Thank you.

---

### Post by Dennis N on 2016-09-03
This problem is discussed at:
[http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image)
with possible workarounds.

---

### Post by Richard_York on 2016-09-03
Thanks, I'll read carefully and have a go.

---

### Post by Richard_York on 2016-09-03
I followed the "long version" suggestion on your given link, which is clear and good to follow - thanks again for this.  On "boot" prompt I entered "live" and got "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU".  Which I guess means that the version I downloaded needs a 64-bit processor. This surprises me, as I'd specifically aimed to select a 32-bit version.  
Presumably I'd better go back and start again with a new download!  Doh...

---

### Post by Richard_York on 2016-09-04
Update: I'm stuck again with a sleeping machine.
 New 32-bit ISO downloaded, verified, then I erased and re-burned USB stick; I then used the "long version" mentioned in that link. Whilst the stick was present all was well. I installed 16.04, and all seemed good until the re-start when all I got was very similar to the original query in that link, where it gives 
SYSLINUX 4.04 EDD 20110518 Copyright (C) 1994-2011 H. Peter Anvin et al


Then some more which I was too tired to copy.

So I erased and re-burned the USB stick again, to rid it of the altered Syslinux download. The short work-round suggested in the link was just to enter "live" at the boot prompt.
 I did that, and after a wait it woke and worked, so once again I installed 16.04, using "erase disk" option.

But now it's effectively back to where it was after the original online update: the machine starts, the 5 Ubuntu dots appear through one colour change, then very briefly it shows something like
"recovering journal
/dev/sda1 clean  [...then two strings of figures...]  block"
This vanishes after a couple of seconds, and the machine goes into sleep mode.
Waking it up leads quickly to a distorted version of the password screen. Entering the password instantly puts it back to sleep.
This cycle just goes round.
So I'm stuck again. Any more guidance would be much appreciated, please. 

Or maybe I'll just try & re-load 14.04 and leave it at that, if it will let me!
Thanks.

---

### Post by sudodus on 2016-09-04
I suggest that you use a better tool for creating the USB boot drive. Cloning tools are more robust, so you can use [mkusb](https://help.ubuntu.com/community/mkusb), (or the Startup Disk Creator version 0.3.3 in Ubuntu 16.04.1 LTS).

-o-

You may have problems with the graphics or wifi. Please specify the brand name and model name/number of the graphics chip/card and the wifi chip/card/device, and we may be able to help.

You can start with some boot option, for example **nomodeset**. See this link: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808).

But there is time to go for Ubuntu 14.04 LTS. It is well debugged by now, and it works in your computer :-)

---

### Post by Richard_York on 2016-09-04
Thanks for this.
 I can't make it tell me what the graphics card is, just the info I posted originally about the Samsung.
 I'm thinking that with my limited understanding of processes once I'm beyond the fairly easy, I may well go with the 14.04 option for now. As you say, I know it has worked on this computer. I just hope all this hasn't somehow messed up its ability to install a decent 14.04!

---

### Post by sudodus on 2016-09-04
If you want to be sure, you should ***select 14.04.1 LTS*** (the first point release with the Trusty kernel) and update && upgrade it. The other alternative is 14.04.5 LTS (with the Xenial kernel), but it might suffer from the same problems as 16.04.1 LTS, which has the native Xenial kernel).

-o-

You can try ***hardinfo*** to find your graphics. Install it into your live system (when booted from DVD or USB),

```
sudo apt-get install hardinfo
```

See the attached screenshot.

---

### Post by Richard_York on 2016-09-04
I had the 14.04.01 LTS download still on my desk-top hard drive from when I installed it on these three machines originally, so simply loaded that onto the USB stick, and the Samsung now seems quite happy with it - currently loading all the updates since this was issued. 
I'll have another go with 16.04 some time, when the information here may well help.
Thank you.

---

### Post by mörgæs on 2016-09-04
> **Richard_York said:**
> On "boot" prompt I entered "live" and got "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU".  Which I guess means that the version I downloaded needs a 64-bit processor. This surprises me, as I'd specifically aimed to select a 32-bit version.  
Presumably I'd better go back and start again with a new download!  Doh...

If your hardware is 32 bit then Ubuntu could be too heavy. X/Lubuntu or Mate are good alternatives.

---

### Post by Richard_York on 2016-09-05
These two links are both truly useful and thorough, and what I've read so far suggests that they're also aimed at people like me who don't know the jargon, which is great! Thank you mightily.
At present the Samsung machine is once again running on Ubuntu 14.04LTS, and seems happy with it, so for the time being I'm leaving it there - other things in life need doing. But I'm going to come back to it, as our old machines are all going to be overtaken by increasingly heavy software at some point, so this could be a way forward.

---

### Post by sudodus on 2016-09-05
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

