---
title: "can't install ubuntu 7.0.4"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by josephwahba on 2007-08-24
Hi,

i just purchased a new laptop HP Pavilion dv2000, whan i tried to install Ubuntu from live CD or from DVD for version 7.0.4  i got the following message during the boot process
Failed to allocate memory resource 
then the splash screen appears then the installation stops and the following message appears
Can't access tty; Job control turned off 

any ideas??

---

### Post by Pumalite on 2007-08-24
Try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign that says: 'Start Download'

---

### Post by josephwahba on 2007-08-25
I tried 2 CD's and one DVD for installation (one of the CD's was downloaded and checked for MD5 sum and the is a magazine CD)

---

### Post by merlinus on 2007-08-25
Just to be sure, you tried the Alternate text-mode cd and got the same error?

-merlin

---

### Post by Aishiko on 2007-08-25
I'm having similar issues on a older Server mother board made by Tyan (tiger133) and the alterante did the install but like the live CD I'm also getting the tty error and now I get it just trying to boot into my new installation.

---

### Post by merlinus on 2007-08-25
Boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

-merlin

---

### Post by Aishiko on 2007-08-25
I get this message on booting into Recovery mode:

checkroot=bootrag cat /poc/cmdine
ormissing modules, devices: cat /procmodlues ls/dev

ALERT! /dev/diskby-uuid/086d3c80-6068-4399-aa2a-29bc32ce54f9 doesnot exist.  Dropping to a shell! 

BusyBos v1.1.3 (debian 1: 1.1.3-3ubuntu3)builtin shell (ash)
enter 'help' for a list of built in Commands.

bin/sh: can't access tty: job control turned off
(initramfs)_




-------------------------------------------------------------------------------------------------------------
ANyone have anyideas?  I'm so close and I don't want to have to give up now;
Specs for the system are [here.]("http://ubuntuforums.org/showthread.php?t=534191&page=2")

thank you in advance.

---

### Post by Pumalite on 2007-08-25
[http://ubuntuforums.org/showthread.php?t=415009&highlight=can%27t+access+tty%3A+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=415009&highlight=can%27t+access+tty%3A+job+control+turned+off)

---

### Post by merlinus on 2007-08-25
The ALERT seems to be that ubuntu cannot find its partition.

Did Ctrl-Alt-F1 get you to a system prompt where you could login and enter the code in my previous post?

Or Ctrl-Alt-F2?

-merlin

---

### Post by Aishiko on 2007-08-25
no it didn't but then I was never able to get a login splash I'm loading Konoppix right now to see if I can find and edit that file thru Konppix that I know works on my computer.  Say do you know where that file might be found?

---

### Post by family on 2007-08-25
Somebody mentioned text-mode. Press esc and type "live acpi=off" enter. this is with the not-alternate CD

---

### Post by Aishiko on 2007-08-25
Well, I've given up trying to the the 7.04 working and instead have found the 6.06 CD is working I might try upgrading to 7.04 if I think it won't cause me to have to reinstall again.  so far it's formatting the drive and so I guess that is step 5/6 and step 6/6 is the final installation, hopefully my next post will be from my Ubuntu 6.06 isntallation.

---

### Post by family on 2007-08-26
Is it possible to wait for Gutsy for you? It could have better support for your comp:(

---

### Post by Aishiko on 2007-08-27
> **family said:**
> Is it possible to wait for Gutsy for you? It could have better support for your comp:(

when does Gusty come out?

As I need a working computer again ASAP.  Also I've been told (here in the forums) that gusty will auto update, if that is true I'd need to know how to make it not auto update to the newest version as if it's sable I'm loath to do any major changes to it.

---

### Post by family on 2007-08-28
Ooo, srry: Oct. 18

---

### Post by Aishiko on 2007-08-29
Well I have Redhat EL4 installed right now and it isn't user friendly however! it does reconginze my USB card, NIC, and sound card.  However the 2 USBports on the Motherboard are still not recognized, and I know they are turned on.  Until 1 of 2 things happens, Either, I get a new Mobo/CPU/RAM set-up however I would Adore anyone that could give me a complete list of supported North and South bridge chipsets so that I can chosse a compatable motherboard.  I figured mine would be and have turned in a bug report as was suggested to me, in it I gave 2 text files, one with the ubuntu lspci, dmesg, lshw information with the lspci having 3 different modifiers (-vv, -n, -b, and of course no modifier) and then the same for the working Redhat installation).  and I'm actually sending this from my first Linux only booting computer.  A bit nervous but I figure if I have to use windows I have my old laptop and as long as it doesn't require a huge amount of video abilities it will do fine.

I can't get any repos to work, I can't get apt or synpatc to work, also I can't get any multi-media files to work so I'm a bit unhappy about that.  Also can't get an iptables gui to play nice or be anywhere as nice and easy to set up as my zonealarm.  Also, I can't find anything to see if SMP is working or RAM/CPU loading is like.  But that is the joy of learning a new OS, you know nothing and every sucessfully won battle to get the computer to do what you want it to do is a victory worth of song and dance, my SCA is showing eeppp!, and every defeat is tempoary as you, retreat, read more, and plan your next flanking manuever.  Sorry I'm a historian, and military campaigns can't but, be seen as major events that influnced all of history, just look at the development of techonlogy from say the US Civil War, the gattling gun was invented back then.  Or the development of jets during WWII and the Nuclear bomb, or how about the furthur advancements in filtration (for subs) of the Cold war, or the Medical advancements that revolutionized the way surgery was done during the Korean and Veitnam wars?   In anycase, trying to seige the OS to make it do what you want won't work, you need to try a different angle or attacking the problem.  Also psychological warfare is equally infective, for they are like the BORG (yes, my brother was a trekie and since we had all of 2 channels in english, or TV options growing up were quite limited). :P

All in all I'm hoping that most of the command line stuff I learn now will serve me once the much more user friendly Ubuntu.

Now if had a patch that I could apply to the 6.10 to get it to see the PCI bus I have the files to make all the cards work, (I think), I could download the patch put it on a CD-R and then make Ubuntu work and do everything I need it to do.

Ohhh and my bug report is #135377 if anyone cares to take a look.

---

### Post by Pumalite on 2007-08-29
Motherboard: Intel D975XBX NVIDIA 7600 GT

---

