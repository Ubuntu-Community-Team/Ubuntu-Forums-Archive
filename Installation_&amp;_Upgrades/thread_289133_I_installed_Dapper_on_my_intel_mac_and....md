---
title: "I installed Dapper on my intel mac and..."
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Kevomiller on 2006-10-30
Hey guys!

I installed Dapper on my intel mac and I'm having some problems.

To Install it, I erased my entire hard disk etc so I am talking from my second computer which is windows.

Anyways,

When I boot up my computer it boots into Ubuntu, but it only gets so far as:

"Loading GRUB" and it just sits there forever.

Is this normal? 

I am currently reinstalling Linux, but I am not sure if it is normal for it to do that.

Any info would be great.

Thanks.

---

### Post by Kevomiller on 2006-10-30
So, yeah, does anyone know what's up?

I reinstalled and it's still not working.


"Grub Loading"

and a cursor just sits there flashing forever.

What is up with that?

---

### Post by hikaricore on 2006-10-30
That's definately not normal.   It sounds like something is wrong with either your grub config or you linux boot image.  I don't know much about macs, but check and see if your hard drive is mountable from the dapper live cd.  Open a terminal and:

sudo mkdir /media/harddrive
sudo mount /dev/h??? /media/harddrive

^where the ??? is the device ID of your drive, on PCs with only one drive and a single partition this is USUALLY /dev/hda1

But like I said I'm not too great with macs so I 
don't know.  I had a few old macs that used scsi drives so they
would be /dev/sda1 or something of the such.  You can also check the
Disks tool under the system menu/administration at the top of the live
cd's interface.  IF for any reason you find the device name and can not
mount your drive, there may be a physical problem.  But if you can mount the drive and post the contents of: /boot/grub/menu.lst

Someone might be able to help you figure it out.  This is a long shot but I wanted to say something since no one else has been able to reply to you yet.


*edit* One last thing make completely sure that the version of dapper you're installing is compatible with your system.  I know that probably isn't the case, but stranger things have happened.  :)

---

### Post by phersotty on 2006-10-30
use lilo for dapper or download edgy which has support for grub on the macbook.   here is the guide I used for a triple boot configuration. [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

---

### Post by Stefan Daniel Schwarz on 2006-11-06
Shameless plug again: Check out my Edgy guide - it works better than Dapper!

[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Discuss it here: [http://ubuntuforums.org/showthread.php?t=290710](http://ubuntuforums.org/showthread.php?t=290710)

Hope it helps!

See ya
-- sds

---

