---
title: "Trying to dual boot 11.04 and a very old WinXP Professional"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by s0nicfreak on 2011-09-16
Computer was working just fine with only 11.04 on there, but my husband insists on having WinXP on there too. Since I know not installing WinXP first causes trouble, I did that. But now I can't install Ubuntu. It's a very old version of WinXP Professional and I can't update it because it doesn't have the right drivers for the NIC (I figure if my husband wants xp to work he can make it work himself, and I don't know what drivers it needs anyway). This disc worked on this same computer (wubi started) with a different, updated version of XP when I first got it. But when I try to start wubi from it now it says "This application has failed to start because the application configuration is incorrect." If I try to just install Ubuntu by booting from disc, the instillation either fails to copy boot files or crashes. Is there anyway to make this work?

---

### Post by mörgæs on 2011-09-17
First of all, please give a complete hardware description.
Which version of Ubuntu are we talking of?
Does it run well in a live boot?

---

### Post by s0nicfreak on 2011-09-17
2 IDE drives, tried formatting in different ways, tried installing on the same HD and separate ones, always the same result. 
AMD Athlon G4 Processor 3000+ 1.81 GHZ
  1 GB of RAM
Radeon 9250


Ubuntu 11.04 32 bit CD install iso on a DVD (tried 2 different DVDs, one -R one +R and tried 2 different DVD drives, some result no matter what I use). 

Does live boot mean without installing? It runs just fine if I do that.

---

### Post by Hakunka-Matata on 2011-09-17
> **s0nicfreak said:**
> 2 IDE drives, tried formatting in different ways, tried installing on the same HD and separate ones, always the same result. 
AMD Athlon G4 Processor 3000+ 1.81 GHZ
  1 GB of RAM
Radeon 9250


Ubuntu 11.04 32 bit CD install iso on a DVD (tried 2 different DVDs, one -R one +R and tried 2 different DVD drives, some result no matter what I use). 

[COLOR=Red]Does live boot mean without installing? It runs just fine if I do that[/COLOR].

Boot into LiveCD means to boot using the Ubuntu install CD, and then choosing either install or "try without installing".
You can run fine when choosing "try without installing", good, everything can be accomplished from that mode of operation. 
What does not work when you try to install Ubuntu to a partition?

---

### Post by pndragon on 2011-09-17
I am having a very similar problem. See the thread: [http://ubuntuforums.org/showthread.php?t=1844303]("http://ubuntuforums.org/showthread.php?t=1844303")

After trying every release since version/release since 9.04, I was unable to use any install disk except kubuntu alternate oneiric and it was incomplete. (It failed on "Select and Install Software" but would load a grub). This was after I used a boot-repair-disk ([http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download]("http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download")) to fix the MBR of Windows partition that had been corrupted.

I have since managed to load most the necessary packages piece by piece. But at some point WinXP has decided decided to start crashing after the initial splash. In that regard I really don't know what to do at this point.

---

### Post by s0nicfreak on 2011-09-18
> **Hakunka-Matata said:**
> What does not work when you try to install Ubuntu to a partition?
It either 

- says "Failed to copy boot files" and then gives me options (continue without boot files, cancel install, or something else I don't remember) but will do nothing no matter what i pick 

- says the installer crashed

---

### Post by Hakunka-Matata on 2011-09-18
Yeah, easy to see that as a problem.  
Have you verified the md5sum against the hash?

please post the output of 
```
sudo sfdisk -luS && sudo fdisk -lu
```

---

### Post by s0nicfreak on 2011-09-18
Thanks for trying to help. We just gave up on xp, removed it and Ubuntu installed fine.

---

### Post by Hakunka-Matata on 2011-09-18
good idea,

---

### Post by mörgæs on 2011-09-18
Fine, please mark the thread 'solved' using 'thread tools'.

---

### Post by s0nicfreak on 2011-09-20
Okay done, although I think that is a bit misleading, anyone else looking for a solution to this problem is going to be upset by this answer :P

---

