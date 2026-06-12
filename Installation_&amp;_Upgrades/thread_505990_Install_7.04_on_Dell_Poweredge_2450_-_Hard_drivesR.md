---
title: "Install 7.04 on Dell Poweredge 2450 - Hard drives/RAID not found"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by Pitt Stains on 2007-07-21
Hi,

I am trying to install 7.04 (Fiesty) server edition on a Dell Poweredge 2450.  During the installation process, Ubuntu fails to recognize the hard drives.  I've got four of them going with a RAID card, but I get the feeling that the Ubuntu installer wants some sort of driver to help it identify the hard drive(s) (via the card).

Any suggestions?  Anyone able to get the installer to see the hardware correctly?

Thanks!
-Pitt

---

### Post by bkann on 2007-08-14
I, too, have the same problem.  I have installed Windows versions without any problem, but the *only* Linux distro I can find that works is Kubuntu 6.06 from the Alternate Install image.  I haven't been able to upgrade successfully from that on this box.

On an attempted install of Ubuntu 7.04, I get the following:

[INDENT]/bin/sh: can't access tty; job control turned off
(initramfs)
sda: asking for cache data failed
sda: assuming drive cache: write through
... same again, then a long pause, then (often, but not always), something like:

sd 0:4:1:0  I/O rejected to offline device[/INDENT]

To the best of my knowledge, I have controlled for every setting on the RAID card and in the BIOS now.  The RAID hardware in the Dell PowerEdge 2450 is the PERC2 DC/2, which was manufactured by what was at the time American Megatrends, but I understand LSI has taken this product over.

Any help would be very much appreciated.  I am a technology professional, but still somewhat new to Linux... so in other words, feel free to talk to me like I'm four.

Thanks!

---

### Post by begeland on 2008-03-19
I have a Poweredge 2450 I'm setting up as a MythTV backend.  I tried 7.10 desktop, and Myhtbuntu 7.1 which hung at the graphic screen after I selected install.

7.10 server went to installation and hung at "retrieving libc6-udeb"

I'll keep working on this and see if I can come up with a solution.  If anyone has experience with this, let me know.

---

### Post by pfwd.tech on 2008-03-24
> **bkann said:**
> 

[INDENT]/bin/sh: can't access tty; job control turned off
(initramfs)
sda: asking for cache data failed
sda: assuming drive cache: write through
... same again, then a long pause, then (often, but not always), something like:

sd 0:4:1:0  I/O rejected to offline device[/INDENT]

Im getting the same error.
Did you guys get this working in the end?

---

### Post by bkann on 2008-03-24
I was doing this for the same reasons as begeland... a MythTV backend to sit in the basement.  I searched and searched for answers to this, but with little luck.  I ultimately found that driver support was dropped for the earlier generation PERC (PERC2 and PERC3) cards with the 2.6 kernel.  Why?  No idea, and no one has been able to tell me.  Seems ridiculous to me to drop support for such widely-used hardware.

It was some time ago when I stumbled across this information about driver support, so I can't remember where I found it to cite it.  Sorry.

Anyway, I was kind of able to resolve the problem, although not exactly satisfactorily:

First, I tried a PERC3 card, no luck.  When that didn't work, I removed all RAID cards from the box and plugged the backplane directly into the Adaptec AIC-7899 that's on board the PE2450's mobo.  Having done that, I was able to install Ubuntu from the 6.06 alternate image.  No other 6.06 image worked, nor did later versions (6.10, 7.04, etc.).  They all fail as pfwd describes, by hanging at 21%, retrieving libc6-udeb.

With 6.06 installed, I upgraded sequentially all the way to 7.10, ie., 6.06 -> 6.10 -> 7.04 -> 7.10.  I did all this with online updates, not from discs.  With only a couple of hours in the evening to fuss around with this, it was a multi-day process.  It resulted, though, in a working 7.10 installation.

My hope was to be able to use an external 200s RAID array with the PERC card.  I have since abandoned that idea, and hope to re-purpose it with a 6.06 install.  To that extent, this has been a failure.  As for just running 7.10 on the PE2450, I guess you can call it a success.

I have not been able to try a PERC4 card.  There is anecdotal information that it should work, but I'm not investing again in something that might not.  If anyone can confirm on a known working hardware RAID card, I'd love to know.

---

### Post by pfwd.tech on 2008-03-24
Thanks for the reply.  Im going to try 6.06 server lts and see if that work.
I have heard that SUSE10 and FREE BSD work but I don't really want to move away from Ubuntu.

Is there way way to find out what PERC version im using?

---

### Post by bkann on 2008-03-24
Please do let us know how it goes.

My understanding is that the PE2450 shipped with the PERC2 controllers.  Other than Googling the part number (which would probably work very well), I don't know how to tell one PERC from another.

Also a reminder that I never had any success with the PERCs installed.  I had to physically remove them and use the AIC-7899 that's on the mobo.  It might require that you enable it in the BIOS as well.

---

### Post by pfwd.tech on 2008-03-24
Hi I had one last go tonight and managed to get the to configuration the DHCP section before the OS installs. However I had to go out and so I stopped at that point.  
I used Ubuntu 6.06 LTS Server with al the standard default settings.  I didnt physicaly remove the PERC's. 
If all goes to plan I hope to get the server running in the next few days. (I only have  a few hours in the evenings to play with it)

---

### Post by begeland on 2008-03-27
The only version of ubuntu I've gotten to go on my Dell Poweredge 2450 with SCSI/RAID is 6.06LTS alternate install.  The destop and server editions do not work.

All other versions hang at various install points.  I think it is something specific with ubuntu as Debian installs fine to latest release (4.0r3), as does debian+kde: [http://pkg-kde.alioth.debian.org/](http://pkg-kde.alioth.debian.org/)

Hope this helps somebody, as I spent 3 or 4 days sequentially installing OS's until I found these to work.

---

### Post by irinipaci on 2008-05-03
Hi Everyone,

I have a Dell 2400 I got from work (they were getting rid of it).  I had the same problem with the initramfs showing up when I was trying to install Ubuntu 8.04 Desktop.  I eventually got it working just now by going into BIOS (F2), and then going to the second page (Alt+P) and disabling primary SCSI while enabling secondary SCSI (by default they were both enabled).  I don't know if work changed stuff inside the machine or not (this is my first time working with SCSI) but once I did this it worked (this is after going to Ctrl+M and setting up a RAID 1 array).  I hope this helps.

Peter

---

### Post by bkann on 2008-06-11
Hi -  A long while in the making, but I attempted the most recent recommendation.  My PE 2450 appears to have different BIOS options from Peter's 2400, so I was unable to disable SCSI as he described.  

Even so, I was able to simplify the install process somewhat.  As before, I can only install the 6.06 Alternate image from CD.  8.04 failed just like all the others.  However, there is a direct upgrade path from 6.06 --> 8.04, so I installed 6.06 and, after doing all of the automatic updates, I was able to upgrade directly to 8.04.  Nothing seemed to break in the process and all of my devices work, in fact some seemingly better than before.

This saved me several hours over the point-upgrade method I described several posts ago.  It's not exactly ideal, but for me it's an acceptable work-around.

---

