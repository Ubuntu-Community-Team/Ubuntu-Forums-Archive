---
title: "First time with Ubuntu... won't install."
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by urbanriot on 2012-03-23
I'm primarily a Windows user but I have extensive experience with FreeBSD. I wanted to evaluate Linux distros to toss on a new 'all in one' touch based PC we've built so I decided I'd start with what's advertised as the easiest, most intuitive distro to demo to people...

... unfortunately my first experience is a bad experience. The installation routine stops at "Installation type" and shows no devices and I can't click 'New Partition Table...' and clicking "Install Now" produces "No root file system is defined.  Please correct this from the partitioning menu." 

Well, I would love to correct this but I can't click anything to correct. 

I dropped to shell and could mount the drive, saw my previous Windows 8 data on it...

I ran fdisk, deleted all the partitions and rebooted, in the event something Windows 8 was preventing this install from working.

Still no luck. 

Can anyone make a suggestion for me?  Thanks.

---

### Post by Rubi1200 on 2012-03-24
Hi,

I suggest you post the results of the boot info script so we can get a better overview of the current setup.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by urbanriot on 2012-03-24
> **Rubi1200 said:**
> 
There is a link at the bottom of my post with instructions.


Your script isn't working for me, unfortunately.

I get the version, date, ""gawk" could not be found" message and a blinking cursor until I break. 

No results.txt

---

### Post by Rubi1200 on 2012-03-24
Ok, so try installing gawk first and then run the script (can also be done on a LiveCD):

```
sudo apt-get install gawk
```

---

### Post by cybpabeofm on 2012-03-24
I cant even get to the live CD. As of now it stops and freezes before it reaches the graphical interface. I will post the error. The problem with openSUSE was with the "nouveau" drivers I believe this is something similar however im unsure. thanks for the replies!

---

### Post by jayshomebrew on 2012-03-24
I'm not sure which version you're trying to install, but I highly suggest you try multiple 'live-cd's of the different versions first.   Running a live-cd first would give you confidence that the installer would work fine.  
This thread may help you: [http://ubuntuforums.org/showthread.php?t=1946145]("http://ubuntuforums.org/showthread.php?t=1946145")

Read the portion about 'boot options'.

---

### Post by QIII on 2012-03-24
I don't mean to offend, but sometimes it's the simplest of things...

Did you check the md5sum of your download and check the integrity of the burned disk?

---

### Post by urbanriot on 2012-03-24
> **urbanriot said:**
> Your script isn't working for me, unfortunately.

I get the version, date, ""gawk" could not be found" message and a blinking cursor until I break. 

No results.txt

> **Rubi1200 said:**
> Ok, so try installing gawk first and then run the script (can also be done on a LiveCD)

Same problem... no more msg re: gawk but still blinking cursor until I break.

---

