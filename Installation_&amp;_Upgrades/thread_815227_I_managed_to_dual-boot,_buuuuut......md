---
title: "I managed to dual-boot, buuuuut....."
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by Rubix_hax on 2008-06-01
THAT F*CKIN HARD DRIVE CLICKING NOISE! 

GOD DAMNIT!

Ok so last night I was THE jolliest man alive, using my linux and all, then I'm about to get off, but then....the hard drive makes that one noise where it spins up then clicks. 

I. HATE. THAT SOUND. :mad::mad::mad::mad:

This is what happened. Last night, I popped in my XP cd. After loading the main screen, it gives you options to delete, create, repair partitions. So I delete ALL partitions, so there was 75.5 gb of free space (in other words the whole hard drive).

Then I made a partition of 40gb, and installed windows in that partition. Finish windows setups, it boots up just fine.

THEEEEEEEEN, I take my handy ubuntu 8.04 cd, restart the comp, then go to install option. 

Now, during the partition, where is gives you the option to use the whole disk, guide, or manual, I said:

Guided - using the most continuous free space (So anything after the 40gb partition I made for windows)

So it installs, then restarts, and I see the grub menu and I get an orgasm b/c it worked, I saw both XP and Ubuntu.

But this hard drive clicking noise is pissing me off. I just attempted the boot the pc up this morning, and when the grub menu came up, and chose XP and it just froze.

WHAT. THE. FU*K.

Btw, I have installed xp/linux well over 5 times on the disk, the disk isn't messed up is it?? :lolflag:



p.s. 

I never installed ANY DRIVERS FOR XP AFTER THE FIRST BOOT!

---

### Post by chex_m8 on 2008-06-01
Can you boot to ubuntu?

---

### Post by Rubix_hax on 2008-06-01
> **chex_m8 said:**
> Can you boot to ubuntu?

No, it says "Error 16: Inconsistent filesystem structure


             Press any key to continue..._"


OOOOO, and when I attempt to go the Ubuntu's recovery mode, its says....:

"Error 18: Selected cylinder exceeds maximum support by BIOS

Press any key to continue..._"


Both time it throws me back the the grub menu.

---

### Post by cariboo on 2008-06-01
Time for a new hard drive.

Jim

---

### Post by Rubix_hax on 2008-06-01
> **cariboo907 said:**
> Time for a new hard drive.

Jim


Why do you say that?

I always wanted a sata hd!!! :guitar::guitar:

---

### Post by cariboo on 2008-06-01
If your drive is clicking its an indication that some thing is wrong with it, plus the error messages you're getting are an other indication. Go do you hard drives manufactureer web site and download the diagnostic tools and run them. Sometimes the tools can fix a problem and other times at least it will give you and error code. Depending on what make of hdd you've got it might still be under warranty. 

Jim

---

### Post by getmeR on 2008-06-01
You are just right to try to have one more reading, I used to get many items on this blog, it helps a lot. Check [http://www.123cruises.blogspot.com](http://www.123cruises.blogspot.com)
Wish you luck!

---

### Post by Rubix_hax on 2008-06-01
> **cariboo907 said:**
> If your drive is clicking its an indication that some thing is wrong with it, plus the error messages you're getting are an other indication. Go do you hard drives manufacturer web site and download the diagnostic tools and run them. Sometimes the tools can fix a problem and other times at least it will give you and error code. Depending on what make of hdd you've got it might still be under warranty. 

Jim

Ya, I will download their tool(s) and hopefully pull up and error code, and wdc has a list of error codes, their meaning, and if possible, how to fix it.

Thanks man! I will keep you guys posted! (Not that anyone cares but ya know)

---

### Post by Rubix_hax on 2008-06-01
Ok, so I couldn't get access to windows, so I could NOT use a diagnostic tool DUH lol

But, I used Gparted :D, and I delete all partitions on my hard drive.

Then, I put in the XP disc. I then did NOT install, but instead, did recovery. Then the recovery brings a dos propmt, so this is where you need to know ur shizz. Well, kinda.

So the prompt started of with C:\

I had to work from there.

So I just type in format C:\ and BAM!

Asked if I was sure about formatting, said yes, formatted it, then throgh me back to main setup screen (not the blue screen, but the one that has a nice gui where you choose your regional settings) 

So ya, GPARTED SAVES LIVES! AND MONEY!

thanks for ur guys' help!

---

