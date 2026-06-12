---
title: "Install Questions - 1st timer"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by audrey_osu on 2007-10-21
Hello - I posted a similar question but got no answers because people with different questions took over the thread.

When I try to install Gutsy (and I've tried it with Feisty also) it doesn't recognize my Vista Ultimate install on the settings migration screen.  Here are my questions:


- Is there a way to make it so that my Vista install is discoverable so that I can migrate my settings?

- If I proceed from here, am I going to be able to dual boot with Vista if Gutsy isn't recognizing my Vista install?

(I've dual booted systems before and never had this much trouble... perhaps thats a bad omen?)

Thanks for any help!!!

Audrey

---

### Post by audrey_osu on 2007-10-21
bump...

---

### Post by hal8000 on 2007-10-21
> **audrey_osu said:**
> Hello - I posted a similar question but got no answers because people with different questions took over the thread.

When I try to install Gutsy (and I've tried it with Feisty also) it doesn't recognize my Vista Ultimate install on the settings migration screen.  Here are my questions:


- Is there a way to make it so that my Vista install is discoverable so that I can migrate my settings?

- If I proceed from here, am I going to be able to dual boot with Vista if Gutsy isn't recognizing my Vista install?

(I've dual booted systems before and never had this much trouble... perhaps thats a bad omen?)

Thanks for any help!!!

Audrey


I think Vista is your bad Omen. The difference between Vista and XP is that Vista checks the MBR when booting so grub or lilo is out of the question.
You can dual boot linux and vista, but you have to use bcedit to control the boot loader in Vista,
heres a good link from google:

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

There may be other links, but this one specialises Ubuntu and Vista.

---

### Post by audrey_osu on 2007-10-21
That article isn't really helpful as I have vista installed already not ubuntu.  I think I'll just stick with Vista... this appears to be too much of a hassle.

---

### Post by ElSeeDee on 2007-10-21
audrey_osu, I have an HP laptop that came with XP. I eventually installed Vista Ultimate (got a free copy from MS for being a beta tester) on the laptop in place of XP. That was about the time I started playing with Ubuntu. So I figured, why not dual-boot? I followed [these]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") instructions and everything works wonderfully. I am dual-booting Vista (installed first) and Kubuntu. I am using the GRUB menu. After the Kubuntu install, I had to do nothing to Vista to 'fix' anything that Kubuntu or GRUB did. Works great. Hope it works for you too. One thing, where the instructions say "Manual - use the largest continuous free space." they actually mean "**Guided** - use the largest continuous free space."

---

### Post by audrey_osu on 2007-10-22
Thank You So Much!!!!

---

### Post by audrey_osu on 2007-10-23
OK, it still doesn't work.  In the step where it is ready to install it doesn't list my vista install like the walk-through says it should.

Is it going to screw everything up and am I not going to be able to boot?  :-( It would really make me happy to be able to ease into ubuntu with my vista there as a backup...

---

### Post by audrey_osu on 2007-10-24
anyone?

---

### Post by svamppi on 2007-10-29
I have the same type of problem:

Firstly, I haven't found a very good guide on how to partition my disk. I have a 500 GB HD. It came with three NTFS partitions on it. I deleted one of them and thought I was gonna use that free partition to create a swap partition and a / partition.

I think I managed to create those partitions ok, but I'm not 100% sure. I tried a few different approaches too. Only using the ubuntu installation partitioner and using the vista "disk configuration" tool or whatever it's called to remove the partition for example.

The biggest problem I guess is that the ubuntu does not list any found operating systems on the last "summary" page of the installation.

Since I had read something about vista not liking having its MBR overwritten and that it was supposed to be safer to put the boot loader on the newly created partition I tried to do that too by entering for example "(/dev/sda6)" in the advanced box at the last summary page.

:(:(:(

---

