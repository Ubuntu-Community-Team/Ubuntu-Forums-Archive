---
title: "Can't Load Live CD"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Kamikaze78 on 2006-11-26
I have tried Ubuntu Live CD, Ubuntu Alternatives Live CD, and the Ubuntu Live DVD. And they all have this problem, when boot with it, it gives me the error 

/bin/sh: can't access tty: job control turned off
(intramfs)

Or something to that extent. I have tried every version of install from all discs, and everyone of them have an issue detecting my DVD-RW/CD-RW Drive. I can excute limited commands from the (intramfs) prompt and can use the Live DVD to enter a Console but dont know what to do with it after that. I am currenly using SimplyMEPIS 6.0. 

I can boot with the discs but it seems like after the ubuntu splash screen that it turnes of or unmouts the Drive making it unusable. Also after that point I get no DVD or HD lights on my system.

Any help on this would be nice. Thanks

---

### Post by Progressive on 2006-11-26
I am getting the same exact problem... I just posted a thread about it here:

[http://ubuntuforums.org/showthread.php?p=1811855](http://ubuntuforums.org/showthread.php?p=1811855)

no replies yet either... I may have to switch distros if this problem isnt resolved

---

### Post by Kamikaze78 on 2006-11-27
Try Fedora 6 or SimplyMEPIS... both have easy installers, no errors for me... and the Desktop Effects in fedora 6 is cool.

---

### Post by drtvasudevan on 2006-11-27
me too on the same boat.
what is surprising was none has answered.
is it such a perplexing problem that no one has any idea about it?

---

### Post by brianc1969 on 2006-11-27
I have the same issue.  I'm trying to install from the Kubuntu DVD iso and  have downloaded and burned it twice.  I have noticed that on my working machine, I can't even mount the DVD.  The MD5 checked out fine, and K3B verified the written data on both burns.  

I finally gave up and installed 6.06 which went just fine.  There's something about 6.10 that is failing miserably.

My system is an Intel core2 duo with dual SATA 250GB drives.  The only IDE is my DVD drive.  

To clarify the problem, I get the error noted above when trying to boot into the live CD.  If I attempt the text mode installation, I get to a point where it tries to mount the CD (DVD) and it fails to mount it.  The installation fails there.

---

### Post by Kamikaze78 on 2006-11-27
Makes you wonder why Ubuntu is #1 on Distro watch huh?

---

### Post by drtvasudevan on 2006-11-28
> **brianc1969 said:**
> 
My system is an Intel core2 duo with dual SATA 250GB drives.  The only IDE is my DVD drive.  
.

what is your mother board?

---

### Post by brianc1969 on 2006-11-28
> **drtvasudevan said:**
> what is your mother board?

Now that I am home... 

The motherboard is an Abit SG-80DC.  It doesn't have the infamous Intel chipset, but instead sports a SiS 661FX chipset.

After reading the forums yesterday, it sounds just like the problem with the Intel chipsets though.  It's as if it gets to a certain point and loses access to the CDROM drive.

Since this computer is a christmas present, it is now put away until said day.  After it gets unwrapped, I will try the upgrade from 6.06 (which is what I finally loaded).  If the upgrade doesn't work, I'll either install Debian or wait till the next release.

---

### Post by Progressive on 2006-11-28
I also have a Core 2 Duo, and my motherboard is an Asus P5W DH Deluxe

---

### Post by Kamikaze78 on 2006-11-28
I am running a IC7MAX3 with a P4 2.4GHz and a Memorex DVD-RW/CD-RW Combo And a Western Digital SATA Hard Drive. Myself... just so you all know. 

This problem is very simple to slove... really... for the people that know Linux... me being a noob I dont know what to do with this. But for the Linux Lifers out there... they have to have an answer. Maybe a direction of where to find an answer is needed. In the live CD install you can hit F6 and add options to the install line. So my question is. What command can I add to that to not change the mount point, or to specifiy the mount point.

The fact that once the splash screen hits, I get no HD or DVD lights, so It reads from the DVD, loads into ram, then runs from ram, somewhere... not mounting drives properly.

---

### Post by Progressive on 2006-11-28
I also have a Western Digital SATA hard drive. I have a Raptor.

---

