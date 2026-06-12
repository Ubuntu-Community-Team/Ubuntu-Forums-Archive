---
title: "USB Live Boot works on some systems but not another (Kernel Panic blah blah)"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2018-11-23
So, a little update on my Ubuntu World.
A) my new system call it A (on which I inadvertently blew everything away, and after reinstalling W7 and 18.04 did not show me the classic boot options menu) after a Boot Repair, is happily running Ubuntu 18.04. all good there.

B) my laptop (call it B) which as W7 and 16.04 working happily BUT on which I stupidly didn't separate the /home location on first install. So I would like to push /home to the spare 400gb space on the HDD.  and I might do that simply by Live Booting 18.04 from USB (which works on this laptop) re-partitioning etc. and voila!

C) this is the weird one. This was my old workhorse (16.04 with a dual W7) but here I also stupidly didn't seperate /home. and I would like to do that. here. BUT the LIve  Boot USBs (i have made 2 of them and I have reburned them each twice) which Live Boot on A and B above, does not Live Boot on C. I get the Kernel Panic not syncing error which is widely discussed elsewhere.

But I don't think it can be the USB sticks themselves. They work on two other systems, one of which also has 16.04 and W7. 

Now this is a backup system and so I might just figure out how to get by without the live boot. I don't NEED to upgrade to 18.04 and I can probably figure out how to migrate /home to another location. 
but it bugs me that I can't Live Boot. That seems like a principle of Ubuntu. When In Doubt Go to LIve Boot. and I can't make it happen.

suggestions?

Peter

PS. I am so happy to have my Ubuntu back functioning well. It's been a "learning" week. thank you all for your help.

---

### Post by oldfred on 2018-11-23
What brand/model system?
Some systems need boot parameters.
Sometimes settings in UEFI/BIOS can make a difference also.

And some just do not like one flash drive or another. Or will only boot from one port, but not another.
       Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208) 

This user had installer modify flash drive, creating issues.
[https://ubuntuforums.org/showthread.php?t=2366670&page=2](https://ubuntuforums.org/showthread.php?t=2366670&page=2)

---

### Post by pjstock on 2018-11-23
originally this was an HP Compaq DC5800
[https://support.hp.com/ca-en/document/c01358056](https://support.hp.com/ca-en/document/c01358056)

I'm surprised that computer systems would differentiate between drive makers or which USB port. BUT I will try some other brands and I will try the other ports. (hmm, have I tried a DVD yet? I burned one but I am not sure tried it yet.)

can the version of the ISO be a factor? I burned an 18.04 ISO because I wanted to upgrade to that, but I guess I would be as happy just reinstalling 16.04 if it gave me the opportunity to reconfigure the /home location.

---

### Post by oldfred on 2018-11-23
That is an older BIOS only system?
How much RAM?
You may be better with only of the lightweight flavors like Lubuntu?

       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by pjstock on 2018-11-24
Indeed it's pretty old. AMD 2.2ghz with 4gb of ram.
I've limped along pretty well it for the last few years bit in the last 6 months it started failing - frequent grey outs, freezes, needs for reboots daily...

I was never sure if it was the specs or that i had used root partition also for /home And so was often running out of space.

When my interest in a reinstall with a newer version (or lighter)  and /home isolated.

And now I am just curious about this USB boot fail.

---

