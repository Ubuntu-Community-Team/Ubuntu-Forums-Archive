---
title: "Fix swap partition or reformat?"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Nickemans on 2010-09-15
I have a laptop with a fairly small Windows XP partition, a bigger Ubuntu partition and a regular swap partition.
Now, my swap partition somehow has corrupted and I'm not sure how to fix this.
So unless I find a way to do this, could I technically reformat my hard drive using a Windows or Ubuntu disc and choose to use the whole drive for that one OS, or would that mess things up?

Thanks!

---

### Post by mikewhatever on 2010-09-15
It wouldn't mess anything up, apart from deleting all data from the disk. If that's ok with you, the godspeed.

---

### Post by Nickemans on 2010-09-15
Well I have everything backed up on an external hard drive, so the data loss isn't that big of a problem. But if there was an easier way to fix things rather than having to reinstall everything, that would save a bit of time :P

---

### Post by mikewhatever on 2010-09-15
Well, there may be an easier way, but you'll need to reveal some more info on the problem. Why do you think the swap partition is corrupted?

---

### Post by Nickemans on 2010-09-15
Ummm. It was a while ago when it happened, but I think I was installing something through Synaptic and suddenly my computer froze up. After a few minutes I forced it to shutdown and it's been playing up ever since.

Whenever I start up my Ubuntu partition now it takes ages and displays some output from fsck, yet after about 5 to 10 minutes it does arrive at the login screen and I can login as normal. Howeverrr, from time to time it will hang for a few minutes at a time, or the CPU is at 100% if that makes sense (I have that app you can add to a panel which displays CPU activity...)

---

### Post by garvinrick4 on 2010-09-15
Swap is used as scratch drive for Ram when system needs more.
Look in another area for problems.

---

### Post by Nickemans on 2010-09-15
> **garvinrick4 said:**
> Swap is used as scratch drive for Ram when system needs more.
Look in another area for problems.

What areas would I look for though? I'm not very technical I'm afraid lol...

---

### Post by garvinrick4 on 2010-09-15
open system monitor and see what is running so as to make your processor go up to 100%
System/Admin to system monitor.
run this in a terminal
```
sudo apt-get install -f
```
```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get install -f
```

This is just trying to get any broken packages fixed.
Cannot tell you this will do it, but seems good place to start and never
know might get lucky and will not hurt anything.

---

### Post by mickwombat on 2010-09-15
It's unlikely to be a corrupted swap, but you could try to turn it off buy usinf the following

```
sudo swapoff -a
```

If everything work fine, then reformat the swap space using GParted or something else.  If there is no difference, the have a look at some of the log files and syslog, generally located in /var/log/*

Check to UUID of the swap partition by using ```
sudo blkid
```.  Ensure that the UUID matches the entry in /etc/fstab

```
sudo swapon -a
``` then ```
sudo mount -a
```

Not sure if both of these are needed, but won't hurt.  Maybe give a reboot to see if there is any difference.

Good luck

---

### Post by Nickemans on 2010-09-15
@mickwombat Would I have to do this using a Live Disc or can I just try to do this using the normal login?

---

### Post by Nickemans on 2010-09-15
@garvinrick4 I'm pretty sure I already tried that at some point, unfortunately didn't fix anything =/
I also never seem to see any processes that actually cause the CPU to be so busy in the System Monitor...

---

### Post by mikewhatever on 2010-09-15
> **Nickemans said:**
> Ummm. It was a while ago when it happened, but I think I was installing something through Synaptic and suddenly my computer froze up. After a few minutes I forced it to shutdown and it's been playing up ever since.

Whenever I start up my Ubuntu partition now it takes ages and displays some output from fsck, yet after about 5 to 10 minutes it does arrive at the login screen and I can login as normal. Howeverrr, from time to time it will hang for a few minutes at a time, or the CPU is at 100% if that makes sense (I have that app you can add to a panel which displays CPU activity...)

Yeah..., right..., ok.... So, why did you say there was something wrong with the swap? Oh right, you didn't.:p
I suspect that nothing is wring with the swap, but you might wanna check the root partition. You have to do it from the live cd, and the command to use is as follows
```
sudo fsck -y -V /dev/sdXY
```

X and Y are the identifiers of the root partition, could be sda1 or sda2, etc. Run **sudo fdisk -l** to find out. If possible, post the outputs of the above.

---

### Post by mickwombat on 2010-09-16
you could do it using normal login.  Not having swap shouldn't be an issue given that most systems these days have more than enough ram.  Just don't load up other programs or play games when you're dong it. ;-)

---

### Post by Nickemans on 2010-09-19
@mikewhatever I knew there was something wrong with the swap because it showed up as "Unknown" or something in GParted =)

Unfortunately, I just ended reformatting my hard drive x)

But thanks to all of you anyways!

---

