---
title: "Gutsy Gibbon installation fails for seemingly no reason"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Beacon11 on 2007-11-27
Hello all. I am a first-time poster, but not really new at Ubuntu. However, I have honestly never had an installation problem before- albeit I'll admit, and some of you will agree, that this time I'm using new / not really documented hardware. Before I start in on my problems, let me give you a brief overview of the hardware I am using, and how it is set up.

     Motherboard: Via EPIA PX (Pico-itx)
     Processor: C7 1.0 GHz (specific for motherboard, small form-factor)
     HD: Seagate Momentus 5400RPM 160GB 2.5-inch 44-pin IDE
     CDROM: Pioneer DVR-K05 slimline optical DVD-RW
     (At this time I am using only an Apple Extended USB keyboard, no mouse)

Now... this motherboard is about 7 x 10 cm. It's tiny. Because of this, it only has 1 44-pin IDE connection, and 1 7-pin SATA connection. So, since my hard drive is IDE, I hooked it up via the 44-pin connection. Because I used that connection up, and so as to avoid any potential speed loss from having two devices on one IDE cable, I got a 50-pin slimline optical to SATA adapter, and hooked the CDROM up via the SATA connection. However, when I booted and looked at my bios, this is what I saw:

> IDE Channel 0 Master     [PIONEER DVD-RW   DVR-]
> IDE Channel 0 Slave      [ None]
> IDE Channel 1 Master     [ST9160821A]
> IDE Channel 1 Slave      [ None]

Notice it puts my CDROM as primary master, and HD as secondary master. Also notice that the CDROM, which is hooked up via SATA, is listed as IDE. What in the world? Okay... so you know that much. This might be my problem, I don't know. How to solve it, I haven't figured out yet.
     Now on to installation:

     I am attempting to install Gutsy Gibbon. At the installation screen, I pressed F6 and deleted the silent install option, so I could see everything as it was happening. It was quick, but from what I saw, there were no errors, and suddenly, after it said the following:

...
...
[   53.361307] usbcore: registered new interface driver usbhid
[   53.361365] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

It said:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

     I honestly have no idea what initramfs is. After I let it sit for a while, at that prompt, it says:

(initramfs) [   112.109884] hda: lost interrupt
_

and it won't let me type anymore. I guess hda is my CDROM drive, and hdc is my HD. I've tried earlier versions of Ubuntu, and I've tried Gentoo, which gives a different error, being unable to partition the hard drive (although it does know it's hdc). I can be more specific if you like, but Ubuntu gave me better error messages. What do you think? Do you have any suggestions? Any advice you give would be greatly appreciated... I'm just lost here. Thank you so much!

---

### Post by Pumalite on 2007-11-27
I think your hard drive should be 1rst master and CD drive 2nd master. Beyond that, you'll have better luck with the Alternate CD if you are going to have any luck at all.

---

### Post by Beacon11 on 2007-11-27
Thank you for the reply :) . I thought the order might be a problem. However... I have absolutely no clue how to change this. My hard drive is set to master. My optical drive has no way of setting it either way. So my motherboard is saying "SATA comes first". Do you think that's a BIOS setting? I've hunted around the BIOS but can't find anything.
Also, I tried the alternate CD and did a text install. However, after I pressed enter at that point, all I got was a black screen. Not a thing happened. Any suggestions?

---

### Post by Pumalite on 2007-11-27
Go to BIOS and make the changes if you can. Otherwise you are stuck.

---

### Post by Beacon11 on 2007-11-27
I can't seem to change that in the BIOS. Do you have any other suggestions? Perhaps get a SATA HD and an IDE adapter for this optical drive? Or would you advise a new motherboard?

---

### Post by Gzus666 on 2007-11-27
your IDE drives have to have short pins of some sort on the back, thats the only way you can set master and slave. just short the hard drive as master. depending on whether you have 2 IDE ports or 1, you will have to adjust the optical to slave or master. if you only have 1 IDE, make the HDD the master, and short  the optical to slave and use the same ribbon. if you have 2 IDEs, just short them both master, and it should auto recognize when you post bios.

---

### Post by Beacon11 on 2007-11-28
> **Gzus666 said:**
> your IDE drives have to have short pins of some sort on the back, thats the only way you can set master and slave. just short the hard drive as master. depending on whether you have 2 IDE ports or 1, you will have to adjust the optical to slave or master. if you only have 1 IDE, make the HDD the master, and short  the optical to slave and use the same ribbon. if you have 2 IDEs, just short them both master, and it should auto recognize when you post bios.

Huh? I know about jumpers, but I'm a little confused as to what you just said... so let me clarify what I have real quick.

I have one IDE hard drive, hooked up to the only IDE slot on the mobo. HD is set as Master according to jumpers.

I have one slimline optical slot load CDROM, hooked up to the only SATA slot on the mobo. This CDROM has no way (to my knowledge) of setting slave or master.

The way it translated to my BIOS is: optical SATA drive is now Primary Master, and HD is now Secondary Master. Even though I set the HD to Master, it considers SATA of higher priority... or so it seems. So... knowing this, could you customize your post a little to my setup?

---

### Post by Beacon11 on 2007-11-28
Oh, also: I have learned that on my motherboard, IDE Channel 0 is the SATA port while the IDE port is channel 1. Perhaps this will help?

---

### Post by leetrefz on 2007-11-29
Despite the funny connector I *believe* that opticals of more than a very little age must be IDE, I'd get an ide adapter, set the hard drive to slave & put them on the same line. 

for anything else this is the place to look:
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77966&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=77966&enterthread=y)

---

### Post by kjaada on 2007-11-29
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
I got the same error and it turned out the Bios required to be reset to defaults then all ok

---

