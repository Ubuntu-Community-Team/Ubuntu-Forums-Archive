---
title: "Install Dapper from ISO on USB key"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by schmappel on 2006-02-28
After wrecking yet another company CD-R, I'd like to install Dapper from an ISO on a USB key for a change. However, bios can't boot USB, so I'd like to boot from floppy and then start the Ubuntu install from the USB key.
What would be the best floppy bootloader? And how should I prepare the Dapper ISO on the USB key?

Tia,

Schmap

[edit]Whoops, perhaps not the best area for this post.. Sorry about that.[/edit]

---

### Post by mr_mop on 2006-02-28
Buy your own CD-Rs and you can waste as many as you like :)

---

### Post by schmappel on 2006-02-28
Well, let's just say I'd be out of CD-R's in no-time. I'd like to be able to freely experiment without having to waste any CD-R's.

---

### Post by lcg on 2006-02-28
[QUOTE=schmappel]Well, let's just say I'd be out of CD-R's in no-time. I'd like to be able to freely experiment without having to waste any CD-R's.[/QUOTE]
That's why someone invented CD-RW. Really great for experiments!

Lars

---

### Post by schmappel on 2006-02-28
[QUOTE=lcg]That's why someone invented CD-RW. Really great for experiments!

Lars[/QUOTE]

Ok, let me try to paraphrase my question.. :) Suppose, hypothetically (that is to say: by hypothesis), my dog ate both my CD-RW drives, yet i would like to run the Dapper (or Breezy) installation ISO *from* an USB key, on a computer with a BIOS *lacking* USB-boot support. Would I - hypothetically - be able to do such a thing? And if so, how?

Tia,

ap

---

### Post by lcg on 2006-02-28
[QUOTE=schmappel]Suppose, hypothetically (that is to say: by hypothesis), my dog ate both my CD-RW drives, yet i would like to run the Dapper (or Breezy) installation ISO *from* an USB key, on a computer with a BIOS *lacking* USB-boot support. Would I - hypothetically - be able to do such a thing? And if so, how?[/QUOTE]
Well, hypothetically speaking, you should probably take your dog to a veterinary first. :)
As for the USB stick, it might be possible to create a boot disc which mounts the ISO from the USB stick via a loopback device and then starts the installation from there. I don't know how to achieve this, though.

Lars

---

### Post by ShiftyPowers on 2006-03-06
I'm actually desperately trying to figure out if this is possible.  I know you can do this on Mandriva but I'd really like to install Breezy or Dapper this way.  I only have a laptop whose CD drive went bonkers and the replacement drives are nowhere to be found.  My only option is a USB key type installation.

---

### Post by schmappel on 2006-03-07
I assume the option 'boot from USB device' is available in your BIOS?

---

### Post by ShiftyPowers on 2006-03-07
yes i definitely have the option to boot from BIOS and all, and I've managed to install Mandriva this way.  I couldn't install ubuntu because i couldn't fit the entire CD on my 512mb USB stick

---

### Post by schmappel on 2006-03-07
I actually meant to write "I assume the option 'boot from USB device' is *_not_* available in your BIOS?", but if it is, then lucky you :)

As to your problem, you could try [this](http://www.bigmaninjapan.com/2005/10/16/install-ubuntu-510-breezy-from-a-flash-disk/). I haven't tried it myself, but it looks promising.

---

### Post by ShiftyPowers on 2006-03-07
awesome, I think that might work, I'll give it a try, thanks for the link

---

### Post by schmappel on 2006-03-07
No problem, glad to have helped!
Let us know how you're progressing, ok?

---

### Post by soonindallas on 2006-03-07
this dude did exactly that the other day.

[http://www.ubuntuforums.org/showthread.php?t=136338](http://www.ubuntuforums.org/showthread.php?t=136338)

then he wrote it up in the wiki.

[https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies](https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies)

---

### Post by ShiftyPowers on 2006-03-07
problem with that wiki report is that you need a floppy right?  My laptop doesn't have a floppy drive

---

### Post by soonindallas on 2006-03-07
[QUOTE=schmappel]After wrecking yet another company CD-R, I'd like to install Dapper from an ISO on a USB key for a change. However, bios can't boot USB, so I'd like to boot from floppy and then start the Ubuntu install from the USB key.
**What would be the best floppy bootloader? And how should I prepare the Dapper ISO on the USB key?**
[/edit][/QUOTE]

[QUOTE=shifty]problem with that wiki report is that you need a floppy right? My laptop doesn't have a floppy drive[/QUOTE]

@shifty  I was replying to the OP. Get your own thread if you want answers to your questions.

---

### Post by ShiftyPowers on 2006-03-07
easy buddy, didn't mean it as an insult, thought you were replying to me.

---

