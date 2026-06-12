---
title: "Partitioning issues, trying to install ubuntu 9.10"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by camdozer on 2010-02-09
I don't know how or why this happened, but when I came home last night and tried to boot up my laptop (Toshiba Satellite L305D) which was running the last Ubuntu build, (Jaunty Jackelope? I think) it appeared as if the hard drive had been wiped clean.

It said there was no boot device, and I needed to insert the disk and press any key.

Naturally I was distressed, but after a moment's despair, I figured this would be a good opportunity (or excuse) to install the new 9.10 Karmic Koala build. I had my gf download and burn the .iso for me and began installing my fresh OS.

Everything was going fine until I came to the partitioner. There was nothing coming up in the 'prepare partitions' menu, and when I just tried to click Forward, it gave me the following error message:

No root file system is defined.

Please correct this from the partitioning menu.

I have no idea what to do, because there is no root file system. My hard drive was wiped clean. Is there anything I can do? I am halfway to just buying windows, but I hate windows and would really rather find a solution, and install linux.

---

### Post by darkod on 2010-02-09
It seems the hdd is not detected at all, probably why it said there is no OS in the first place instead of booting Jaunty as you expected.
Boot again the 9.10 cd and select Try Ubuntu first, load the live desktop and open Gparted to see if it can see the hdd as present at all.
It might be a good idea to get a tool from the hdd manufacturer website and run it to check the hdd.

---

### Post by camdozer on 2010-02-09
bump

---

### Post by camdozer on 2010-02-09
> **darkod said:**
> It seems the hdd is not detected at all, probably why it said there is no OS in the first place instead of booting Jaunty as you expected.
Boot again the 9.10 cd and select Try Ubuntu first, load the live desktop and open Gparted to see if it can see the hdd as present at all.
It might be a good idea to get a tool from the hdd manufacturer website and run it to check the hdd.

How do I go about opening Gparted?

---

### Post by darkod on 2010-02-09
> **camdozer said:**
> How do I go about opening Gparted?

Once the live desktop is loaded, Gparted is in System-Administration.

---

### Post by camdozer on 2010-02-09
K I just opened Gparted, and it's saying "no devices detected" at the bottom of the window.

---

### Post by darkod on 2010-02-09
> **camdozer said:**
> K I just opened Gparted, and it's saying "no devices detected" at the bottom of the window.

Any chance to check the hdd with a manufacturers tool? HDD manufacturers provide these tools.

---

### Post by camdozer on 2010-02-09
> **darkod said:**
> Any chance to check the hdd with a manufacturers tool? HDD manufacturers provide these tools.

I am sorry I am such a noob, and I truly appreciate your help. I am just not sure what hdd even means, lol. Would I go to Toshiba's website and try searching for like... an HDD detector or something? Haha, again I really appreciate your help.

---

### Post by darkod on 2010-02-09
> **camdozer said:**
> I am sorry I am such a noob, and I truly appreciate your help. I am just not sure what hdd even means, lol. Would I go to Toshiba's website and try searching for like... an HDD detector or something? Haha, again I really appreciate your help.

Hard Disk Drive. If your computer is toshiba it doesn't necessarily mean the hdd would be too unfortunately. :)
And now it's not booting to check.

---

### Post by camdozer on 2010-02-09
Oh God... so my computer is not even detecting the hard drive?! Yikes, this could be worse than I thought...

Does that mean I need a new hard drive?

---

### Post by darkod on 2010-02-09
> **camdozer said:**
> Oh God... so my computer is not even detecting the hard drive?! Yikes, this could be worse than I thought...

Does that mean I need a new hard drive?

I really can't say like this. I can't advise you to just go and buy a new one, then it turns out it wasn't needed. :)
Is it under warranty? If it is, it might be better to take it to the service centre to have it checked out.

---

### Post by camdozer on 2010-02-09
I took my computer to my local MicroCenter, and apparently the only problem was that the HDD was loose. Literally just wasn't in all the way. Thank you so much for setting me down the path to recovery, though. Without your advice I would have had no idea what the heck the HDD was, let alone that it was the problem! You rule!

---

### Post by darkod on 2010-02-09
Well, good news. :)

---

### Post by n0njy on 2010-02-19
Hold on a moment... loose hard drive?  Ummm I don't think so.  Not necessarily in your case, but I upgraded from 8.04 the other day to 9.10.  Then I realized I was set up in a dual boot situation on the hard drive with XP.

I wanted to remove XP.  After backing up what little important data I had last night, I plopped in my 9.10 desktop disk I had made at work yesterday.

Went ALL the way through the install process and then the laptop kicked the CD rom out, and said "Press Enter to reboot now".  

It rebooted - and lo and behold I got a very similar message.  "No boot device" with some numbers (Sorry, didnt write that down, was tired and figured I'd work on it today when I get home).

Point being, there's no WAY I have a "loose hard drive" on that laptop. I am the one that replaced the drive last time it was bad, and the machine hasn't been moved from my desk in months, if not a year.  ....

So.... let's revisit this?  Any other ideas why I'd be getting the same message someone else got?

(The machine is a Compaq Presario with a 160 gig HD)

---

### Post by zappadragon on 2010-02-19
Its funny because I am having the same problem on a new computer build. After several trys I put windows disk in and it finds the drives as well as the bios. Windows 7 installed fine. I am still not able to see the drives if I try to do the Ubuntu install, with 1 or 2 drives.

---

