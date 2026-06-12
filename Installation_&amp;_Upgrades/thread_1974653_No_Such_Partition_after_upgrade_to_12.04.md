---
title: "No Such Partition after upgrade to 12.04"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by King_Koopa on 2012-05-06
I attempted to upgrade my Ubuntu installation to 12.04 yesterday, and when I reboot my machine I received the error "no such partition."

Is there a simple solution to this, or am I SOL?

When I get the GNU Grub selection screen, none of the available options will boot. They all give me the same "no such partition error."

Any help is appreciated.

---

### Post by Prescilla on 2012-05-06
Same thing happened to me.
Even with previous kernel versions, the same error "no such partition" appeared.

Try this
[http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204]("http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204")

---

### Post by OldnBlue on 2012-05-09
Used that link to fix my 12.04 install.  Worked great thanks.  :p

But ....  why does it fail in the first place ?  :mad:

And ....  shouldn't you add a warning note to the release ?  :-k  ( as I nearly cr@pped myself when my PC wouldn't boot in Windows or Ubuntu)

Overall though, you have a great OS.

well done.

---

### Post by skaman9876 on 2012-05-11
I'm at a total loss now... I can't figure out what is going on I'm having the same error i went to that link but i've tried booting from live CD (properly burned iso image to DVD shows casper folder and all that), also created a bootable USB stick from another ubuntu computer i formatted an 8GB usb downloaded ubuntu-12.04-desktop-i386 used the ubuntu utility to create startup image on usb.  

WHERE I GET STUCK:  When i try to boot from USB I just get a black screen with blinking cursor in top left.  I verified MD5 and all was good there but can't get passed a blinking cursor i pull the usb out and it gives me Operating System load error.  The DVD that I burned that should be able to run ubuntu off of does essentially the same thing it just hangs then goes back to that grub screen and get the error no such partition.  

Cannot for the life of me figure it out... any help would be greatly appreciated! thanks in advance

---

### Post by OldnBlue on 2012-05-11
Hi Skaman,

I'd suggest creating a new Live disk, on another machine if necessary.

Think these upgrades are in need of some TLC !

Cheers
Oldn

---

### Post by wilee-nilee on 2012-05-11
Posters if you have a problem and you want help start a thread all your own, title it appropriately to your situation, kick back with a cup or glass of your favorite beverage and reap the rewards. :)

Piling on a single thread makes it difficult to help.

---

### Post by skaman9876 on 2012-05-11
I made a new CD on my other ubuntu computer of 12.04 I also tried making a USB bootable image and neither are getting me anywhere unfortunately.

---

### Post by skaman9876 on 2012-05-11
I made a new CD on my other ubuntu computer of 12.04 I also tried making a USB bootable image and neither are getting me anywhere unfortunately.  Looks like i have to make a new thread and see if there is a way to get this resolved :(

---

### Post by skaman9876 on 2012-05-11
Well for my particular case it was a very odd one... It appears there were two major issues.  A) Grub was messed up but i think we all agree that was the main issue, B) it appears it wasn't booting to the right hard drive first i hard to reorder the boot partition sequence.  The odd problem with me is that no ubuntu live CD's would work for me it wouldn't take.  

STEPS TAKEN TO RESOLVE ISSUE:

[LIST=1]
[*]  Disable hard disk from boot sequence leaving just CD-ROM as only option to boot from
     (I was then able to boot to live CD but it would then just freeze as soon as i click "Try Ubuntu")
[*]  Went to [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and acquired the rescatux hybrid iso image
[*]  Burn image to DVD
[*]  Boot from said DVD
[*]  Hit enter on "Rescatux Auto-Detect"
[*]  It booted up to the rescatux and from there was able to retrieve "bootinfoscript_log.txt"
[*]  On the Main screen clicked on (+)GRUB -> Restore GRUB -> choose proper partition
[*]  Reordered the boot partition it was trying to boot to wrong hard drive, it allowed me to reorder it right there after restoring GRUB
[*]    Reboot, remove DVD 
[*]  Sit back and relax
[*]  VICTORY!  Ubuntu 12.04 booted right up with all my original configuration from 11.10 everything fully functional and fully fantastic.
[/LIST]



A ENORMOUS THANKS TO adrian15 from rescatux @ [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) for all his help and getting me back to working order.  Would recommend it to anyone.  It worked miracles and was very simple and effective.

---

### Post by wilee-nilee on 2012-05-11
> **skaman9876 said:**
> Well for my particular case it was a very odd one... It appears there were two major issues.  A) Grub was messed up but i think we all agree that was the main issue, B) it appears it wasn't booting to the right hard drive first i hard to reorder the boot partition sequence.  The odd problem with me is that no ubuntu live CD's would work for me it wouldn't take.  

STEPS TAKEN TO RESOLVE ISSUE:

[LIST=1]
[*]  Disable hard disk from boot sequence leaving just CD-ROM as only option to boot from
     (I was then able to boot to live CD but it would then just freeze as soon as i click "Try Ubuntu")
[*]  Went to [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) and acquired the rescatux hybrid iso image
[*]  Burn image to DVD
[*]  Boot from said DVD
[*]  Hit enter on "Rescatux Auto-Detect"
[*]  It booted up to the rescatux and from there was able to retrieve "bootinfoscript_log.txt"
[*]  On the Main screen clicked on (+)GRUB -> Restore GRUB -> choose proper partition
[*]  Reordered the boot partition it was trying to boot to wrong hard drive, it allowed me to reorder it right there after restoring GRUB
[*]    Reboot, remove DVD
[*]  Sit back and relax
[*]  VICTORY!  Ubuntu 12.04 booted right up with all my original configuration from 11.10 everything fully functional and fully fantastic.
[/LIST]



A ENORMOUS THANKS TO adrian15 from rescatux @ [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) for all his help and getting me back to working order.  Would recommend it to anyone.  It worked miracles and was very simple and effective.

It is a shame you did not do this in your own thread with a coordinated thread title and could have been set as solved, as it is this your information will be lost, hardly as helpful as it could have been

---

