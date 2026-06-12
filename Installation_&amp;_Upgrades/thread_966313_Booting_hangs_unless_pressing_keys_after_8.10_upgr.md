---
title: "Booting hangs unless pressing keys after 8.10 upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by elaar on 2008-11-01
Hi Everyone,

I was wondering if anyone now has the same weird problem as myself.

Upon booting the system stalls/hangs multiple times during the boot process, it does this for an infinite amount of time until I press a key.

I am currently pressing the enter time about 20 times just to get it to boot. It stalls at the Sata, Ata, Network initialisation, swap file stages to name just a few. Not sure if this is related, but it starts doing this after "Clocksource tsc unstable" after Ata detection.

I also get the 4GB Aperture problem but I don't think these are related.

Any advice would be gratefully received.

Thanks,
Elaar

---

### Post by elaar on 2008-11-01
Right, it now boots flawlessly but only with acpi=off, which isn't an ideal solution as i'm using it on a laptop. I can't see the power/recharge bar and obviously I have no energy saving facilities.

---

### Post by thedavid on 2008-11-01
This happens to me with my HP DV6000 laptop as well.  Not a show stopper, but I can't start the system and leave it to startup on its own.  It's the only hitch in the entire upgrade process from 8.04

---

### Post by thedavid on 2008-11-01
Another issue: when I close the lid of the laptop, it goes to sleep well. When I reopen, it turns the computer on and immediately locks. This means it's effectively useless in a university environment (opening and closing it a bunch, tossing it into my bag, etc..)

I dropped to a console to see the bootup sequence when this happened, and after every item it pauses... no matter what it is (usb, keymappings, etc). This seems to happen UNTIL the acpi is loaded.

It's obvious that it's something to do with power management that's causing this, since both areas deal with that directly. If I could get that fixed all would be well and I could look into using it fulltime. Because it's not, I'll have to keep vista around, at least for now.

---

### Post by bookmarc on 2008-11-01
> **elaar said:**
> Hi Everyone,

I was wondering if anyone now has the same weird problem as myself.

Upon booting the system stalls/hangs multiple times during the boot process, it does this for an infinite amount of time until I press a key.

I am currently pressing the enter time about 20 times just to get it to boot. It stalls at the Sata, Ata, Network initialisation, swap file stages to name just a few. Not sure if this is related, but it starts doing this after "Clocksource tsc unstable" after Ata detection.

I also get the 4GB Aperture problem but I don't think these are related.

Any advice would be gratefully received.

Thanks,
Elaar

I am having exactly the same  problems including the message about the 4GB Aperture problem.  I just upgraded my ubuntu to 8.10 from 8.04 on an AMD 64 machine.

Any suggestions?

---

### Post by TheBlackNoodle on 2008-11-02
I just want to get on record saying that I am also having these exact problems, both boot stalling/errors and freezing on suspend. This worked fine in Hardy. I have an HP dv9750us laptop. I'm going to look into downgrading power management tools to see if there's a temporary fix...

---

### Post by KermitJr on 2008-11-04
Ditto for the problem for me.  I had this issue with the LiveCD as well.  My hanging starts as soon as the Boot Splash starts. I have to keep pressing keys in order to boot.  And 8.10 doesn't poweroff, either, for me.  

This is a laptop so acpi=off isn't ideal.  Still having the problem after the kernel upgrade.

Hopes someone comes up with a solution!

KermitJr

Edit: Here are two others with similar issue:
[http://ubuntuforums.org/showthread.php?t=965334](http://ubuntuforums.org/showthread.php?t=965334)
[http://ubuntuforums.org/showthread.php?t=964041](http://ubuntuforums.org/showthread.php?t=964041)

---

### Post by KKop on 2008-11-04
Just wanted to add my voice to this:; same problem of hanging during boot, both from LiveCD and from install (both upgrade from 8.04, and clean 8.10 install).

If I keep pressing keys until it boots, it will eventually show the login screen, but mouse nor keyboard will work :-(

---

### Post by wribeiro on 2008-11-04
I have the same problem with my HP Pavilion dv6000.
Progress bar in bootsplash freezes and only move while a key is pressed (even a ctrl or shift keys).
When the login screen appears, everything begin to work ok.
It happens with live CD as well with the installed version.

---

### Post by KermitJr on 2008-11-08
With recent update, I noticed it isn't quite as bad... that is, I only have to hit the key on 2 or 3 hangs vice the whole thing... Anyone got ideas?

---

### Post by cdtech on 2008-11-08
Me too!

I have to hold my shift key to kick start it as well........

---

### Post by packman1234 on 2008-11-08
I have Ubuntu Studio that shows when booting and I also have to press keys to make the system boot up.. How do we fix this??

---

### Post by revchris on 2008-11-11
This is a bug with the kernel.  I saw a thread on bugzilla for it, but I can't remember where exactly.

---

### Post by pndragon on 2008-11-12
There are multiple postings for this bug. One of them, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247"), recommends that you add the parameter "hpet=disable" to menu.lst instead of anything involving your acpi. What this particular parameter does is disable the newer HPET timer in favor of the older PIT timer.

So far, after making this change, I haven't noticed any nasty side effects and I still have my power management.

--- Jim

---

### Post by cdtech on 2008-11-12
Thank you for the find. Checking it out now.

Bad link...........

---

### Post by cdtech on 2008-11-12
I added this "hpet=disable" to my kernel variables and lo and behold it worked.

Thanks for the find.....

---

### Post by revidnus on 2008-11-12
I upgraded from 8.04 last night and have the same problem with a laptop hp pavilion 9610us. I haven't tried a fix for it yet. Everything else went ok.

---

### Post by cdtech on 2008-11-12
> **revidnus said:**
> I upgraded from 8.04 last night and have the same problem with a laptop hp pavilion 9610us. I haven't tried a fix for it yet. Everything else went ok.

This fix should get you going.......

---

### Post by thedavid on 2008-11-12
The fix works for resolving the issue with the bootup sequence needing keypresses but not the resume issues I've been having, unfortunately.

---

### Post by rjkola on 2008-11-23
Thanks, I'm running 8.10 under wubi on hp6704. The fix seems to be running fine. I had upgraded and the cyclops eye froze. I had to keep pressing keys to advance till cursor showed.

-- If you don't walk on the railroad tracks, you don't get hit by the train. - Bart Maverick

---

### Post by rolodoom on 2008-12-05
Using "hpet=disable" did fix the problem at my dv6721la laptop.

---

### Post by Qwertinsky on 2010-05-07
> **pndragon said:**
> There are multiple postings for this bug. One of them, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247"), recommends that you add the parameter "hpet=disable" to menu.lst instead of anything involving your acpi. What this particular parameter does is disable the newer HPET timer in favor of the older PIT timer.

So far, after making this change, I haven't noticed any nasty side effects and I still have my power management.

--- Jim

I Just picked up an EeePC 900A Netbook. The stalling at start-up is still a problem even with Ubuntu 10.04

"hpet=disable" and "ACPI=off" both fixes it (ACPI=noirq did not)

The hpet=disable is the better solution as ACPI still works fine.

---

### Post by weasel5i2 on 2011-02-22
What worked for me (so far, on a Toshiba NB305 netbook) was this:

```
(hit ESC at first Ubuntu install menu)
boot: live-install noapic nolapic noapm irqpoll

```

and the touchpad actually works! About to do the install and see if that works.. My original problem was the lack of CPU polling as mentioned by other replies, wherein I would have to hold down SHIFT or keep hitting CTRL in order to make the installer respond. Hope this helps someone.

EDIT: it looks like simply using "nolapic" caused the CPU polling to work. Just tried it with only that and it works. However, the installer was still hanging with the method described above. Trying it now with just "nolapic"..

--W5i2

---

