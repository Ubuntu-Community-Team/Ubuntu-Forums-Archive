---
title: "Computer wont boot ubuntu DVD or USB???"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by b18turboef on 2011-01-04
Brand new build, top of the line components, windows 7 x64 installed and working flawlessly. I've got the boot order with cd rom first, usb 2nd, hard drive 3rd. I've got a good DVD in the blu ray drive, and it does not boot from the drive. Also same issue when the USB is in. Its using a SSD and I almost get the impression its checking things too fast then just heading to the SSD to load windows. Any ideas?
 
I've put the DVD into a crappy old laptop I have and it boots from it so I know its functional (the laptop shows some error for kernel or something but regardless it does get the ball rolling).

---

### Post by b18turboef on 2011-01-04
I should also add that once the machine boots into win7 I can open the blu ray drive and see all the files, and it looks correct. Its NOT just an .iso file on the dvd. Everything looks correct to me.... Just spinning my wheels over here!

---

### Post by b18turboef on 2011-01-04
Alright after scratching my head thinking it MUST be the dvd or usb having bad files etc. I put the win7 dvd in the drive and rebooted the computer. It doesn't even try to boot that????? Is this a known issue when using a SSD??? The bios seem to be just fine?? I'm lost now!!!

---

### Post by darkhelmetchris on 2011-01-04
> **b18turboef said:**
> Alright after scratching my head thinking it MUST be the dvd or usb having bad files etc. I put the win7 dvd in the drive and rebooted the computer. It doesn't even try to boot that????? Is this a known issue when using a SSD??? The bios seem to be just fine?? I'm lost now!!!

I think I have seen this problem before.  Is it possible that you have set your SATA ports to be RAID or AHCI, or rather, changed the setting since the last time you successfully booted from DVD or CD?  Perhaps try setting the SATA controller for a different mode - I think sometimes some mainboards don't see the drive as "a bootable optical drive" depending on the way the BIOS setting is - but this is a cloudy memory, so I could be wrong there.  Or, perhaps, have you moved the drive to a "secondary" SATA controller?  My mainboard has 3 different SATA controllers and so far for me, only the first one is optical-drive bootable, the secondary and tertiary controllers are not checked for CD/DVD boot media.

I also note that the Ubuntu .ISO file is a CD image, not a DVD image, and I have seen *some* drives fail to boot if the intended boot-type is the wrong emulation.  You might try burning the iso to a CD instead?  I doubt this matters, but it's worth mention.  I would be more confident in the first suggestion than this one.

---

### Post by b18turboef on 2011-01-04
Smartest man alive right there... First idea was dead on. I do have AHCI turned on, as I read it was important for the SSD. So I just moved the blu ray drive to sata6 and problem solved. Anything bad about running my blu ray drive in IDE mode? Thanks again!!!!

---

### Post by darkhelmetchris on 2011-01-04
> **b18turboef said:**
> Smartest man alive right there... First idea was dead on. I do have AHCI turned on, as I read it was important for the SSD. So I just moved the blu ray drive to sata6 and problem solved. Anything bad about running my blu ray drive in IDE mode? Thanks again!!!!

Woohoo, glad to hear you got it solved.  That's great news.

Well, not really "bad" about running it like that in IDE mode.  It will just be a slower throughput for the data.  I would suggest doing your bootable needs, then putting it back to AHCI as it will be faster, and perhaps less CPU intensive.  But, it's really just a matter of opinion.  There would likely be no side effects, except maybe burning at high speed might overrun your BD/DVD drive buffer and get you a nice coaster for your beverage.  Pick what you think makes you happy and let me know how it goes.

---

### Post by b18turboef on 2011-01-04
If there isn't anything overly bad about it then that's fine, I very rarely use the drive at all.

On a side note, how well does ubuntu utilize multi core processors? I've got an amd x4 in there but planned to order an x6, only time I need that kind of processing power is when I rip two dvd's at a time in handbrake, but if ubuntu won't benefit from it otherwise I may just save myself $100..

---

### Post by darkhelmetchris on 2011-01-04
> **b18turboef said:**
> On a side note, how well does ubuntu utilize multi core processors? I've got an amd x4 in there but planned to order an x6, only time I need that kind of processing power is when I rip two dvd's at a time in handbrake, but if ubuntu won't benefit from it otherwise I may just save myself $100..

I would guess that you probably don't really need the x6.  However, this really depends on what you're using the computer for.  If you're just working with DVDs, you're probably fine.  I would suggest that having more cores is more useful if you're using multiple operating systems virtually, if you're gaming, or performing some kind of higher multiprocessing.  This is, of course, opinion.  You'll want to choose what's right for you.

---

### Post by mörgæs on 2011-01-04
You will most likely not reach the full benefit before the new Linux kernel is released. More here:

[http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1)

---

### Post by b18turboef on 2011-01-04
> **mörgæs said:**
> You will most likely not reach the full benefit before the new Linux kernel is released. More here:

[http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1)

That looks great and very promising, and please do forgive the ignorance but when it is released, or any future update, how does ubuntu handle that? Can it handle some updates, but then major version releases need a fresh install? Or do updates bring you to the current version (let's say the next was 50.50).

---

### Post by mörgæs on 2011-01-05
As far as I know, it is to late for the patch to enter the regular Ubuntu 11.04, but it will be standard in 11.10. 

If you don't mind some manual work you can apply the fix to the present Ubuntu. 

I would never upgrade any Ubuntu, always do a fresh install. I know that not everybody agrees on this one, but I think it is silly to do anything else than a new install, since it only takes one hour.

---

