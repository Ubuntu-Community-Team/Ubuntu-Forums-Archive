---
title: "Old Dell, new software."
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by btophek on 2011-09-27
I have this older Dell computer, probably from around 1998.  Since it's older and has older chip sets and a slower processor, I've upgraded to 833 MHz it won't accept a 1 GHz processor for some strange reason or more memory?  I can't quite figure this out?  I'm sure it has something to do with with the older bios?  Do you guys know of a way of reconfiguring or talking to the bios so it will accept a faster processor and more memory?
 
  Anyway, this isn't my main question.  My main question is on a boot it will display and error message that says something to the effect of 1999 bios cutoff and then loads Ubuntu 9.04 fine.  I can't seem to upgrade to newer version of Ubuntu without the computer behaving strangely.  I'm sure it has to do with the older chip sets and the newer software written for more modern computers?  Is there a way around this?  The computer doesn't receive updates anymore because of the older software that I'm running.   I'd certain would like to take advantage of a newer version of Ubuntu if I could.    If I format the hard drive and load in something like Ubuntu 10.04 LTS the computer just doesn't work right. I'm not quite sure how Ubuntu code is written for older machines.  Perhaps you guys would know?

---

### Post by papibe on 2011-09-27
Hi btophek.

Unfortunately, 9.04's support ended on 23 October 2010. So that's the reason why you're not getting updates.

Because of that hardware, I would recommend a lighter version of Ubuntu like Lubuntu.

Could tell us a little more about the machine?
CPU? RAM? HD?

Regards.

---

### Post by btophek on 2011-09-27
Well, let's see if memory serves me well.  The processor is an Intel slot processor, originally a 600 MHz.  Upgraded to an 800 or 850MHz I have a 933MHz I'd like to put in but the computer won't let me.  It comes back with error code lights on the back of the machine indicating where the problems are.  Same thing with the memory also.  If I install larger memory sticks the error lights or LED's change color indicating that there is a problem.  I can't quite recall what type of memory it has I want to say SIMMS or DIMMS but can't quite recall I'll have to check on that.  I know it has 3 slots for memory sticks and I can't stick anything larger than a 256K memory stick in without causing the LED's to change color indicating that there's an error.  I'm running two 40Gig hard drives.  One drive is dedicated to Windows XP and the other is Ubuntu 9.04.  The GRUB boot loader works great if I wish to switch between the two drives.  I use to run a dual boot system on one drive but found it more efficient to segregate the OS's on two drives due to hard drive space.  I don't really use the Windows hard drive all that much unless I decide to use some proprietary software that runs in Windows more efficiently than in WINE.  I certainly don't browse the internet with Windows due to all the problems and viruses that are out there.  Which reminds me, I can't get WINE to work all that great on this machine either or maybe I don't know how to use WINE at all.  I'd really like to get away from using any Microsoft products.  They just plain suck!!!!  I'm not quite sure of the mother board's architecture except when the computer boots it's running Phoenix bios.

---

### Post by papibe on 2011-09-27
I think [Lubuntu]("http://lubuntu.net/blog/lubuntu-1104-released") 11.04 would be the perfect candidate for that machine.

I'm running Lubuntu in an old PIII Dell laptop just fine. Chromium comes as default and works great (you can install Firefox if you want). Of course some things won't be perfect (youtube videos run, but with a VERY low fps).

Hope that helps,
Regards.

---

### Post by lykwydchykyn on 2011-09-27
Usually limitations on RAM and processor compatibility are just built in to the motherboard.  Sometimes these things can be upped by a BIOS upgrade; I'd check Dell's website to see if you're running the latest BIOS for this model.

More than likely, though, you're just hitting the upper cpu/RAM limit for this model.  You can look it up at [http://support.dell.com](http://support.dell.com) to make sure.

I agree that Lubuntu would be a good fit for this system.  You might even get more mileage from Debian Stable running LXDE, though the software will be a bit older.  Regular Ubuntu 11.04 is going to be dismally slow.

---

### Post by btophek on 2011-09-28
Okay guys, I'll give it a shot, that is try 11.04 Lubuntu.  I guess I'll have to go to Dell support and see what I can do as far as processor speed and RAM upgrade.  I'm sure I'm reaching the upper limit for this machine.  It's probably time to upgrade anyway.  This is my main internet machine at home so if it blows up I have to use my backup machine which is a Gateway with a 1.6 GHz processor.

---

### Post by mörgæs on 2011-09-28
Yes, Lubuntu is a good candidate. After installing this, applying Flashblock to your browser(s) will also increase speed.

---

