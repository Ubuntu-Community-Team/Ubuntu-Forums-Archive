---
title: "Weird clicking, can't get into my account"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by darundal on 2010-03-04
I did a dist-upgrade from 9.10 to 10.04 alpha 3. Whenever I try to boot normally, it starts loading ubuntu normally, then at some point the mouse "waiting" icon appears, and the hard drive starts spinning and stopping, with the head obviously making some sort of movements as evidenced by a clicking noise. It will continue to do this until I restart the machine. This does not happen when I go into a root console through recovery mode, although if I attempt to resume a normal boot it will. It should be noted that the system will, by default, log into my account automatically. Does anyone have any idea what might be causing this issue?

---

### Post by ratcheer on 2010-03-04
> **darundal said:**
> I did a dist-upgrade from 9.10 to 10.04 alpha 3. Whenever I try to boot normally, it starts loading ubuntu normally, then at some point the mouse "waiting" icon appears, and the hard drive starts spinning and stopping, with the head obviously making some sort of movements as evidenced by a clicking noise. It will continue to do this until I restart the machine. This does not happen when I go into a root console through recovery mode, although if I attempt to resume a normal boot it will. It should be noted that the system will, by default, log into my account automatically. Does anyone have any idea what might be causing this issue?

My system has the same, or a very similar problem. I have described it as "a horrible growling click" kind of noise, repeating 6 times every 5 seconds. A couple of times, I have tried to let it go on for a while to see if it will get past it and complete booting, but it never has.

I have looked for bugs like this on Launchpad, but haven't found anything. You are the first person I think I've heard mention the problem.

Tim

---

### Post by ronacc on 2010-03-04
I get that growling sound on some boots but not on all . It sounds like a drive going bad , I thought it was my dvd drive . so far it has not prevented me from booting .

---

### Post by darundal on 2010-03-04
Well, now that I know I am not the only one, I feel a little bit better. Does anyone out there have any idea how to fix this, or what might possibly be causing this?

---

### Post by ratcheer on 2010-03-04
> **darundal said:**
> Well, now that I know I am not the only one, I feel a little bit better. Does anyone out there have any idea how to fix this, or what might possibly be causing this?

Like I said, I have searched and searched, but I cannot find out anything about it. I have suspected plymouth and ureadahead, but I cannot find anything specific.

Tim

---

### Post by darundal on 2010-03-04
Well, assuming the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=1343648") are right, then I can pretty safely say it is not an issue with ureadahead. 

Oh, and part way during an update, it started giving me the same issues it normally does during a standard boot, and started complaining about /dev/sda1 not being usable, then proceeded to work normally, albeit at an amazingly decelerated pace. After restarting my system, and going back into a recovery root session, the system became as responsive as it normally would be.

---

### Post by darundal on 2010-03-05
Well, apparently, it will boot. I thought calling it at 20 minutes was more than safe, but apparently it takes more than 20 minutes to boot. The system is as responsive as it normally would be once it finally boots, it just takes forever to get there. Does anyone have any idea what logs I could dig into to figure out what is causing this?

---

### Post by darundal on 2010-03-06
Yay, I gots a bootchart!



Just a note, the chart lies. It claims a time of a bit over 7 minutes, it is well over 20. Also, the iSpud is not usually plugged in during boot.

---

### Post by ratcheer on 2010-03-06
So, any idea what that means? Does it lead to a fix or workaround? I am not going to listen to my disk grinding away at itself for 20 minutes plus.

I just go to boot recovery mode >> root prompt >> service gdm start, and I am up in less than a minute. I don't know if this causes anything to be missing, but everything seems to work, just fine.

Tim

---

### Post by hugmenot on 2010-03-19
Seriously, check the drive. Best would be with badblocks, from a Live CD or Live USB.

I had bad sectors on my old hard drive and it did this too. When it tries to access the bad sectors it stalls for a very long time and emits these clicks.

Just check "dmesg" and grep for DRDY errors. Or, just grep for ata like this:

```
dmesg | grep -i ata
```

---

### Post by darundal on 2010-03-21
idn't show anything. Just reinstalled 9.10 and everything works fine again.

---

### Post by Calash on 2010-03-22
I just got this during an upgrade.  Finally got around it by resetting my sata mode in BIOS to compatibility (Combonation in Dell Bio lingo)

Booted right up without the drive clicking.  Performance may suffer a bit, and you will lose access to any Windows XP partitions until you change it back but as a short term fix it seems to be working.

---

