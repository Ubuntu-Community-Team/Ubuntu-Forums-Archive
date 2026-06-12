---
title: "Unable to resize partition"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Dazappa on 2008-04-26
So I have this drive.. it's ntfs partitioned. Ok first thing I wanted to was pop in a ubuntu cd. I did, it ran, it gave me errors trying to resize. I downloaded the other iso (has no gui), stuck it in and attempted the same thing. Also had a problem with resizing. Then I tried openSuse (dunno why..) and it ALSO had a problem resizing. And lastly, I downloaded the visparted iso, and it could not resize the partition.. Now; that's EVERYTHING I could think of, I'm not an experienced linux user, but I DID back up my hdd. Do you think I could just wipe the drive and create the ntfs partition, then leave the rest blank and try sticking in the ubuntu cd?! :S This is very frustrating.. I doubt any of you had this happen to you :confused: (and by little linux experience, I mean that the only thing I ever did with linux was installing DSL and then the programs for a webserver..) I do know how to use vi to the most basic extent, and I can burn cds, and I can try whatever you throw at me.

---

### Post by obidose on 2008-04-26
Are you trying to dual boot from the drive or does it just have some data on it?

---

### Post by lemming465 on 2008-04-26
Did you try running "chkdsk c: /f" from windows first?

---

### Post by Herman on 2008-04-26
I agree with lemming465.
I'm not a Windows user, I'm only using NTFS for testing the Ubuntu installer in test computers.
I recommend using your Windows installation CD and booting it to a Windows Recovery Console. [XP recovery console.]("http://www.kellys-korner-xp.com/win_xp_rec.htm")
I always run CHKDSK /R on my NTFS file systems in test installations to tidy up the file system first and after I do that, then I try again with the Ubuntu installation. 
 The Ubuntu partitioner always resizes mine as easy as pie once the file system is clean.
This has worked every time for me in tests installs.
It is normal for it to need CHKDSK /R run on it again afterwards too, that's recommended in the GParted LiveCD web site for resizing NTFS partitions.

---

### Post by Dazappa on 2008-04-26
> **obidose said:**
> Are you trying to dual boot from the drive or does it just have some data on it?

The drive already has data on it, but I cleared off about 10 gig and I want to shrink the file system down to that space I cleared. I'm trying to dual boot windows and linux.. as you might have guessed.

- I will try chkdsk c: /f and then chkdsk c: /r. Thanks for the suggestions.

---

### Post by neyuru on 2008-04-26
I have the same problem... (see my previous post [http://ubuntuforums.org/showthread.php?t=769604](http://ubuntuforums.org/showthread.php?t=769604))
I already did the checkdisk but to no different end. I cannot install (resize the partition first) with either the Live CD or with Gparted even after the checkdisk.

---

### Post by Dazappa on 2008-04-26
/r doesn't exist as a parameter for chkdsk. Also ran chkdsk /f, no errors were found, and it still didn't resize the partition correctly.

---

### Post by Herman on 2008-04-26
> /r doesn't exist as a parameter for chkdsk.:confused: Really? [Chkdsk]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/pref_tts_ffgh.mspx?mfr=true") - Microsoft

---

### Post by Dazappa on 2008-04-27
Oh I think I might have been doing chkdsk /r and not chkdsk c: /r. Well I let it run, tried to resize again and it still failed =|

---

### Post by claudio64 on 2008-04-27
Hi,

If You want to use Win and Ubuntu at same computer, use wubi installation that shall by easier.

While running win, put the Desktop CD, define the disk size, user password and let it work for you.

This procedure worked under Vista.

Good luck!
Claudio H.

---

### Post by Dazappa on 2008-04-27
I guess my desktop cd doesn't have wubi; when I pop it in under windows it just shows some applications I can install; nothing abou t wubi or installing ubuntu

-- Ok I found wubi on the cd. I stick it in, and it says that  it must run in low graphics mode. I click the continue box and nothing else happens. It just sits at a blank terminal flashing the underscore.

---

### Post by lemming465 on 2008-04-28
Have you tried rebooting onto the desktop CD as a live linux?  That will help clear up the question of whether or not there are hardware compatibility issues.  Without touching the hard disk, so it's a safe experiment.

---

### Post by Slim Odds on 2008-04-28
Try defragging the NTFS partition

Resizing partition is a little bit of magic

---

