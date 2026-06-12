---
title: "[SOLVED] Installation Super Problems"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by 71fnRVVm on 2008-07-03
Hi everyone,

I'm trying to install Hardy on my brand new Alienware system that came today... but it's not working.

When I run *any* of the CD's options during boot, it sometimes shows the Ubuntu logo, sometimes not... but always ends in the Bash-like command line interface.

It's currently running Vista on a Raid 1 (hardware) array of two 500GB drives.

I tried both my Hardy and Gutsy LiveCDs that Canonical mailed directly to me...

Is there a way for me to run an install on that interface?  Is there any particular reasons why it won't run the LiveCD?

Any quick help is appreciated!

Thanks

---

### Post by spike_strip on 2008-07-03
It sounds like you have verified the system bios is set to allow boot from cd-rom drive?

---

### Post by 71fnRVVm on 2008-07-03
Verified?  I guess, since I actually choose "Ubuntu" instead of "Windows Vista" from the boot loader?

One of the problems here is this computer is so fast I don't have a chance to read any of the BIOS stuff or respond to "press [x] key" prompts... it took me forever to get it to load from CD because I had to do update the BIOS from within Windows since I couldn't figure out what key I had to press.

Thanks

---

### Post by spike_strip on 2008-07-03
It should be the delete key and just hold it down the entire time it is starting up; do not try to guess! Have you got it working?

---

### Post by 71fnRVVm on 2008-07-03
Right, that works.  But it still goes through the "Ubuntu loading" screen... ending in a Bash command line.  This happens in "Run from CD", "Install Ubuntu", and "Check for defects".

On both Gutsy and Hardy LiveCDs.

Thanks

---

### Post by spike_strip on 2008-07-03
Vista is currently installed on the system? 

Is there a way you can remove that OS and re-try the Ubuntu install. 

Something like reformat the hard drive first and the attempt to install Ubuntu. Just an idea...I know this is not common procedure, however I have in the past had an issue with systems that have MS OS installed on them not allowing a complete new install of a different OS type.

---

### Post by 71fnRVVm on 2008-07-03
It's not that it's not allowing an install...

It's that **Ubuntu refuses to work**.  As I said, I have the same problem *not just when attempting to install*, but running it "Live" or checking the CD's data integrity...

I highly doubt this is a Windows issue.  There's something else wrong here...

---

### Post by spike_strip on 2008-07-03
Also have you attempted to run a command at the 'bash command line' type grub or something?

---

### Post by 71fnRVVm on 2008-07-03
Are you not reading what I'm telling you?

I can get into grub because I had the LiveCD install Grub prior to installation attempts (because of my whole "superfast load" problem).

Commands work, but it's a very limited set of choices.

Which brings me back to my _original question_... **is there a way to install Ubuntu from this command line**?

---

### Post by avtolle on 2008-07-03
[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid) may give you some ideas. Note that with a RAID install, the "alternate install" disk is to be used, not the Live CD.

---

### Post by wpshooter on 2008-07-03
My "guess" would be that the system is having problems reading the CDs.

I know they are directly from Canonical BUT I think I would still download my own ISO and burn it at 4x or less.

Might want to possibly consider cleaning the drive even though it is new.

Might want to see if there is a firmware update for the CD drive.

Sometimes drives have a preference as to what CD-media they like, maybe they don't like the Canonical media.

Yes, I agree, use the ALTERNATE version.

---

### Post by spike_strip on 2008-07-03
Relax; I have given you an option an you refused it a without merit. OK; I do not see that you have a better idea. 

What are your command choices? 

Have you tried 'boot cdrom' at CLI.

---

### Post by spike_strip on 2008-07-03
> **wpshooter said:**
> 
Might want to possibly consider cleaning the drive even though it is new.


Same thing I suggested!

---

### Post by spike_strip on 2008-07-03
> **71fnRVVm said:**
> Are you not reading what I'm telling you?

And yes I do plenty of reading...Thank you!

---

### Post by spike_strip on 2008-07-03
> **wpshooter said:**
> I would still download my own ISO 

This would have been my next suggestion! I concur!

---

### Post by 71fnRVVm on 2008-07-03
spike_strip:  you obviously have no idea what you're talking about.

wpshooter: those might have been valid suggestions if this wasn't a brand new setup that was pre-configured with all updates to Vista, firmware, drivers, etc.

avtolle: right.  I thought it might be something like that... I'm downloading it now, hopefully I can figure it out with that tutorial.  Thanks!

---

### Post by 71fnRVVm on 2008-07-03
avtolle:  it's working... but I have an [optical drive problem now]("http://ubuntuforums.org/showthread.php?p=5315617")...

---

### Post by wpshooter on 2008-07-04
> **71fnRVVm said:**
> spike_strip:  you obviously have no idea what you're talking about.

wpshooter: those might have been valid suggestions if this wasn't a brand new setup that was pre-configured with all updates to Vista, firmware, drivers, etc.

avtolle: right.  I thought it might be something like that... I'm downloading it now, hopefully I can figure it out with that tutorial.  Thanks!

Just because it was "pre-configured" does not "necessarily" mean that it has the latest firmware !!!

You can get a brand new computer from Dell, IBM, or anyone else and that does not necessarily mean that everything is on the latest versions.

---

