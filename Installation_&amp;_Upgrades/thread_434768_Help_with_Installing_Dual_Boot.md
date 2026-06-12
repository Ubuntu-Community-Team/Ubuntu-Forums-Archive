---
title: "Help with Installing Dual Boot"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by redcitrus on 2007-05-06
I'm desperate to try and install Ubuntu on my desktop machine, but I'm terrified that by doing so I'll inadvertently  erase my Windows installation and all my precious files. My machine is an AMD Athlon 64, and I have downloaded the ISO for Feisty. My machine has some kind of SATA array (I'm no expert, so don't really understand what this means).

My question is as follows...

Is it possible for me to install Feisty on an external USB2 hard drive and then have the option to boot into either Windows or Ubuntu when I start the machine up? I have got part way through installing Ubuntu, but lost my nerve when I was presented with the disk partition bit, although both the internal drive and the external drive were given as options for where to install Ubuntu.

Thanks in advance for your advice.

Russell

---

### Post by starcraft.man on 2007-05-06
Easy enough! First answer to your question, you can install to a USB drive if your computer is able to detect and boot into it, will have to check your bios to be certain. To do that, click F2 / F12/ F10, at boot up, it varies by bios maker.

When you get to the partitioner, you will see your NTFS partitions I assume as Windows. 

Basicallly all you need to do is make 3 partitions here to get things running, the first and most important is the root partition, this is where all the OS files will be installed. I will list below a short point form of what you need to make the 3 drives.

Mount : /
Format: Ext3
SIze: 6GB minimum should be enough, more if you like.
Type: Primary
Bootable Flag: On

Mount: /home
Format: Ext3
Size: X (as much as you like, if your using external storage or a swap fat partition make it only a few gigs, otherwise you should make it the left over of your space, all your music and personal files will be stored here.)
Type: Logical
Bootable Flag: Off

Mount: swapfile
Size: 2 GB
Format: swapfile

Now, as for installing it to your USB, I assume your using the Live CD, when you get to the partitioner you should see all the available drives (I guess one hda in your comp and the other a usb) just pick the USB drive and make the 3 above. You can later switch drives via the top right drop down which tells which drive your looking at.

I hope that answers your quetions. :)

---

### Post by Sef on 2007-05-06
**Back up** your data first.  Nothing is 100% fool proof.

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") for the Live CD (Desktop) install.

Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") for the alternate (text-based) install.

---

### Post by mikewhatever on 2007-05-06
It is certainly possible to install Ubuntu to an external drive. Have you already searched for a how-to in the tutorials and tips forum? I think you should not rush with the install, but read around and ask questions until you feel comfortable with partitions and all.
Here are some useful links for you:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?t=308027&highlight=usb+install](http://ubuntuforums.org/showthread.php?t=308027&highlight=usb+install)

---

### Post by redcitrus on 2007-05-06
Thanks for your help, guys.

In answer to your question, I can indeed boot from the external USB drive, no problem. In fact, when I first plugged it in I had to reconfigure the BIOS so that the system didn't default to it when booting.

I'm using the AMD-64 Alternate install disk (although I have the Live CD also) as it seemed simpler to use the text-based interface. It might just be me, but this seems a lot more friendly than the Live CD version.

I'll let you know how I get on once I've had a chance to read the articles you suggested.

Cheers

Russell

---

### Post by starcraft.man on 2007-05-06
> **redcitrus said:**
> Thanks for your help, guys.

In answer to your question, I can indeed boot from the external USB drive, no problem. In fact, when I first plugged it in I had to reconfigure the BIOS so that the system didn't default to it when booting.

I'm using the AMD-64 Alternate install disk (although I have the Live CD also) as it seemed simpler to use the text-based interface. It might just be me, but this seems a lot more friendly than the Live CD version.

I'll let you know how I get on once I've had a chance to read the articles you suggested.

Cheers

Russell

Just a thought russell, you may want to use the 32 bit version... I've still yet to really see a reason to use the 64 bit version, there are some programs that you may have trouble with, and some that just don't support 64. 

And yes, I like the alternate installer too. You'll find the partitioner is very straightforward :)

---

### Post by bulldog on 2007-05-06
And one of the most important things,don't know if it is mentioned yet,
**install GRUB on the USB device (should be (hd1) and not on (hd0) which is default**

Otherwise you get all sort of problems when your USB disk is off or disconnected!

---

### Post by redcitrus on 2007-05-06
I didn't realise that, but it makes sense. Cheers for the advice.

---

