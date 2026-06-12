---
title: "slow install/update"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by BobBeatley on 2011-04-26
I am installing 10.10 on an amd3200 sempron w/256mMB ram,40 gig partition, is that too small of a machine? It seemed like it installed ok then the update manager came on and is updating for 4 hrs. lots of HD activity.

---

### Post by KegHead on 2011-04-26
Hi!

256k is the absolute minimum.

Once you install, any chance you can add ram?

It will make a huge difference.

Keghead

---

### Post by tommcd on 2011-04-27
> **BobBeatley said:**
> I am installing 10.10 on an amd3200 sempron w/256mMB ram,40 gig partition, is that too small of a machine?
You can do a minimal install of Ubuntu that would be a better fit for a low end computer: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
If you could upgrade to at least 1GB memory you would get much better performance for a relatively small investment.

And welcome to the Ubuntu forums!

---

### Post by BobBeatley on 2011-04-29
Maybe I'll add more ram, but my goal was to make this a nice running open source machine. I think In this situation less is definatly more as far as operating sysytm goes. I'm suprised it ran with XP and I really think I can find an OS that will do the job.  by the way, after that day long update (yes it did Finish) there are now two ubuntu OS's when I boot up. The old one works better. Isthere a way to just remove one of them?

---

### Post by tommcd on 2011-04-30
> **BobBeatley said:**
> Maybe I'll add more ram ... I'm suprised it ran with XP
Just 256MB memory is barely enough for XP. You must have been using XP's swap file (virtual memory) quite a bit. I ran XP with only 256MB memory at one time and I remember how it was.
> **BobBeatley said:**
> 
... and I really think I can find an OS that will do the job.
You could try one of the mini distros like Puppy or Slitaz. Zenwalk may also be an option since it is much faster and lighter than Ubuntu.
> **BobBeatley said:**
> 
 ... there are now two ubuntu OS's when I boot up. The old one works better. Isthere a way to just remove one of them?
How did you end up with 2 Ubuntu installs? You must have installed Ubuntu twice.
If you want to keep the old one, just boot the Ubuntu live CD (which will run slow on your machine no doubt), open GParted, and delete the new one you do not want. Be sure you correctly identify which partition is the one you want to remove. You could also use a Parted Magic live CD for this. [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)
A Parted Magic live CD would also likely run faster than the Ubuntu live CD.
Since the new Ubuntu's grub likely controls the MBR, you will have to reinstall grub2 for the old Ubuntu to the MBR from the Ubuntu live CD after removing the new Ubuntu. See this: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

