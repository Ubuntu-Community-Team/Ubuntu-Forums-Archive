---
title: "Failed install, no longer booting anything or giving an output."
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Nemisis_101 on 2008-06-07
Hello,

I really need your help; i was installing Ubuntu onto my external hard drive in the hope of having a duel booter with Windows XP which is already on my computer. I downloaded the file, put it onto a bootable CD and it loaded the install screen, i selected it to install fully onto my external hard drive, clicked next etc. and it went onto the "creating partitions" loading box, it quickly went to 5% before staying there for about 2 hours 15 mins, by now the mouse had froze and the CD draw was displaying an orange light, it usually displays green when it is reading etc. I had to restart the PC. Unfortunately, now it wont boot windows or give any output to the monitor, just gives 3 beeps followed by 1 from the mother board. Please help, what should i do? (cry)

I can hear the PC reading the ubuntu install disk and there is a green light but no monitor output.

Thanks very much,

(It's an HP Pavilion 750)

---

### Post by PmDematagoda on 2008-06-07
Those beeps seem to suggest something more than a software problem, do you have the manual of the PC? If so, find out what those beeps mean, that can help you.

---

### Post by damis648 on 2008-06-07
Assuming you are NOT using an OEM Windows installation and have a Windows XP CD, you can boot up with that and choose the recovery console by pressing R at the prompt. Choose your installation from the list and enter your administrator password. Enter
```
fixmbr
```
and answer yes to the next question.
That should get you into windows and fix you MBR when you reboot. If this works, we can get on to installing Ubuntu.

---

### Post by damis648 on 2008-06-07
> **PmDematagoda said:**
> Those beeps seem to suggest something more than a software problem, do you have the manual of the PC? If so, find out what those beeps mean, that can help you.

Yes, but could they possibly suggest a corrupt MBR? That is what my previous post if for.

---

### Post by dodgybob on 2008-06-07
Sounds like you've had a hardware failure of some sort which just happened to occur as you were installing. You'll need to find out what the beep codes mean, open up the box, find the motherboard manufacturer and model, from their site you should be able to find out which BIOS is in the machine, from there you should be able to find out the beep codes.  There will be a pattern to the codes which should match and that will hopefully be the only problem that you've got.
Before you do all this I'd do a quick run though devices connected, remove anything not required, reseat any cards etc and see if it's as simple as a loose connection somewhere.  
Good Luck!
Bob.

---

### Post by Nemisis_101 on 2008-06-07
Thanks all,

The exact structure of the beeps is as follows -

```
longbeep-shortbeep-shotbeep-pause-shortbeep & floppy drive opens
```

Not a good sign, unfortunately i don't have the manual as it is a friends old PC etc. I will have a look on the web. I cant type anything as there is no output to the monitor, absolutely nothing. And i also dont have the windows XP install disk either, altough i am hoping that drive is OK as it wasent involved in the ubuntu install, although nothing is booting.

Cheers,

---

### Post by quinnten83 on 2008-06-07
Does the live CD boot?
I would start by making a backup of everything on the computer.

---

### Post by PmDematagoda on 2008-06-07
When you start the PC, are you able to see the POST? And are you able to enter the BIOS?

---

### Post by Nemisis_101 on 2008-06-07
The live CD does make some churning sounds and acts like it is being read. But no, i cant see a damn thing on the monitor; it does change off stanby.

---

### Post by damis648 on 2008-06-07
> **PmDematagoda said:**
> When you start the PC, are you able to see the POST? And are you able to enter the BIOS?

Yes... this would signify a BIOS or hardware error.

EDIT: I mean if you could not see it... you get the point

---

### Post by Nemisis_101 on 2008-06-07
sorry hit the reply button twice. :(

---

### Post by PmDematagoda on 2008-06-07
> **Nemisis_101 said:**
> The live CD does make some churning sounds and acts like it is being read. But no, i cant see a damn thing on the monitor; it does change off standby.

Then it must be broken, because even if the problem is a broken MBR the PC should be able to show the POST and you should be able to enter the BIOS. So it's time to break out the warranty card, I do hope you have it.

---

### Post by DM was on fire! on 2008-06-07
I'm siding on the BIOS or Hardware error.

[http://www.pchell.com/hardware/beepcodes.shtml](http://www.pchell.com/hardware/beepcodes.shtml)

---

### Post by damis648 on 2008-06-07
Hm.. sounds like hardware or BIOS, although I wouldn't know what to do to troubleshoot this. I used to have a similar problem... seemed to be the MB or Power Supply, but it didn't even beep. The computer would start, but there would be no output. Just the fans would spin. I never did have enough patience to get that fixed.

---

### Post by Nemisis_101 on 2008-06-07
Dont say that, (cry cry cry)

The PC is very old and no warrently, i must be able to fix it somehow. What about [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php) .

---

### Post by damis648 on 2008-06-07
This will not help if you can't even start the system or get to the BIOS configuration. Probably BIOS or hardware is what I am still thinking, and I am pretty sure of it.

---

### Post by PmDematagoda on 2008-06-07
> **Nemisis_101 said:**
> Dont say that, (cry cry cry)

The PC is very old and no warrently, i must be able to fix it somehow. What about [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php) .

How can you do that if you can't even see the POST, let alone enter the BIOS? You will have to get the PC checked and fixed, or at least open it up, clean it, reseat the RAM, VGA card, the lot and try again.

---

### Post by DM was on fire! on 2008-06-07
Perhaps try flashing your BIOS, see if that works?
I know it's risky, but it's worth a shot.

[http://www.pcstats.com/articleview.cfm?articleID=1605](http://www.pcstats.com/articleview.cfm?articleID=1605)

---

### Post by Nemisis_101 on 2008-06-07
You don't have any idea how to fix that at all, i mean now my external hard drive is also broken cause it is now formatted (or should i say partially) to a linux format and i only have a Vista laptop (what i am using right now to be on this forum) so there is no way to recover that. Any ideas what i should do?

I can get a new PC, and don't have the warrenty anymore.

---

### Post by damis648 on 2008-06-07
Sure, but he cannot start the system! He would have to take the physical CMOS out and flash it somehow like that because there is no acess to a prompt or anything.

EDIT: @DM was on fire!

---

### Post by PmDematagoda on 2008-06-07
> **Nemisis_101 said:**
> You don't have any idea how to fix that at all, i mean now my external hard drive is also broken cause it is now formatted (or should i say partially) to a linux format and i only have a Vista laptop (what i am using right now to be on this forum) so there is no way to recover that. Any ideas what i should do?

I can get a new PC, and don't have the warrenty anymore.

Use the Ubuntu Live CD(it won't harm, take my word for it) and once you reach the desktop open the partition editor in System>Administration, plug in your external drive and format it in the way you want.

---

### Post by Nemisis_101 on 2008-06-07
Great!!!!!!!!!!!!

It's loaded windows for some reason beyond me, i don't know why, i just tried booting it again (for about the 25th time!). 

What should i do now, how should i install ubuntu and what do i do if it freezes again?

Thanks very very much guys,

---

### Post by PmDematagoda on 2008-06-07
> **Nemisis_101 said:**
> Great!!!!!!!!!!!!

It's loaded windows for some reason beyond me, i don't know why, i just tried booting it again (for about the 25th time!). 

What should i do now, how should i install ubuntu and what do i do if it freezes again?

Thanks very very much guys,

It looks a lot like hardware failure, seriously, take it to be checked and fixed, that is the best you can do.

---

### Post by damis648 on 2008-06-07
> **PmDematagoda said:**
> It looks a lot like hardware failure, seriously, take it to be checked and fixed, that is the best you can do.

I AGREE. The problem I describe earlier seems EXACTLY like yours, but without the beeps. Sometimes it would never start, and sometimes it would after trying like 80 times... I am serious. Go take it to have it checked. I will say now, it IS a hardware failure.

---

