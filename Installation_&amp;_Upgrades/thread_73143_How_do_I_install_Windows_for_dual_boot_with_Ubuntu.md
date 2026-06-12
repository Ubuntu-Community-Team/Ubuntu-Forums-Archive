---
title: "How do I install Windows for dual boot with Ubuntu?"
date: 2005-10-08
forum: Installation &amp; Upgrades
---

### Post by phm on 2005-10-08
Hi,

Now that Ubuntu seems to be mostly OK, I'd like to set up the Windows ME that used to be on this machine, as not all programmers are converted to Linux, yet. However, most explanations seem to assume that either I've already destroyed my Ubuntu boot and need to recover it the hard way, or that I have a Live CD present, which I don't.

- How should I prepare Ubuntu for installing Windows?
- When installing, are there settings to take into account?
- What do I need to do on Ubuntu and on Windows afterwards?

Thanks,
........................................................................................................ PHM

---

### Post by aysiu on 2005-10-08
[QUOTE=phm]
Now that Ubuntu seems to be mostly OK, I'd like to set up the Windows ME that used to be on this machine, as not all programmers are converted to Linux, yet.[/quote] First of all, let's make sure this is really the best solution. I'm not anti-Windows or anything--after all, I dual-boot with Windows XP--but Windows ME has to be one of the worst operating systems out there. What are these programs you think are Windows-only? It's very possible that these programs can either be used through Wine or have good Linux equivalents. Let us know what you *real* problem is, and we'll help you find the solution.

> 
However, most explanations seem to assume that either I've already destroyed my Ubuntu boot and need to recover it the hard way, or that I have a Live CD present, which I don't. I'm sorry, but you are going to need a live CD of some kind if you're going to be doing some repartitioning. Do you have a broadband internet connection and a CD burner?

---

### Post by phm on 2005-10-08
[QUOTE=aysiu]First of all, let's make sure this is really the best solution.[/QUOTE]
Thank you for your offer. However, I trust you'll accept that I follow my own judgement here.

>  I'm sorry, but you are going to need a live CD of some kind if you're going to be doing some repartitioning. Do you have a broadband internet connection and a CD burner?
Yes, I do have a continuous internet connection; no, I do not have a CD-burner anywhere near it. I do have a running set-up of Ubuntu, which did hard disk  partioning on the installation, so some software must be present somewhere.

There's probably no need to *re*-partition, BTW, since I reserved the first 40 G of the disk for this purpose when I installed Ubuntu. It should merely be matter of selecting an appropriate size and indicating it as bootable. (Set up the File System from Ubuntu, or will the Windows Install ignore that, anyway?)

If that's the only purpose for the live CD, then I guess things are beginning to look sunnier.

Thanks,
............................................................................................................... PHM

---

### Post by phm on 2005-10-10
Hi,

OK, I set-up Webmin (had it's own little twist), and have set up a partition and made GrUB recognise it. It's now a bootable DOS partition. Will installing Windows ME modify this set-up in a way that will prevent me from booting by way of the GrUB?

Thanks,
.................................................. .................................................. ........... PHM

---

