---
title: "Please help...I can't install 10.04!"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Copperline on 2010-05-03
Hi I'd really appreciate some help on this if possible!

I have been trying to fresh install Lucid on a clean (tested and fully functional) drive but the install keeps failing at the start. The CD doesn't get to the installation menus...I get a box appearing that says 'The installer encountered a fatal error. You will now be given a desktop session so that you can resolve the problem.'

I have now downloaded the iso twice from different server locations and burnt it using two different programs (K3b and Nero) on two different brand new CD-ROMS...with two different DVD drives and at the slowest speeds (just to be sure) and still no luck.

This has happened a few times now and I'm at a loss...the system runs quite well from the live cd and I can use everything quite happily - I just can't install it.

Could anybody perhaps shed some light on what's happening here? This is the first time I've had problems with any Ubuntu install and I don't understand what is going wrong!

Very Many Thanks.
Copperline

---

### Post by wilee-nilee on 2010-05-03
You might try the alternate install ISO, without a little information on your actual computer hardware, it is difficult to tell whats going on. From the live cd run
sudo fdisk -l   l=small case L.

---

### Post by Copperline on 2010-05-03
Thankyou for your reply regarding the live CD.

I am in the process of downloading the alternate CD at the moment and will try it - but if possible I would rather use a GUI.

I'm sorry - I should have included some hardware information.

I have a Shuttle XPC SN21V10
Phoenix BIOS v6.0
AMD Athlon(tm) 64 Processor 3800+ (but I run 32 bit software)
2GB RAM
NVIDIA GeForce 6100 onboard graphics

3 Hard drives: 
320GB Seagate (Windows 7)
200GB Samsung (XP and Ubuntu 9.04 dual boot)
200GB Maxtor (XP)

---

### Post by wilee-nilee on 2010-05-03
> **Copperline said:**
> Thankyou for your reply regarding the live CD.

I am in the process of downloading the alternate CD at the moment and will try it - but if possible I would rather use a GUI.

I'm sorry - I should have included some hardware information.

I have a Shuttle XPC SN21V10
Phoenix BIOS v6.0
AMD Athlon(tm) 64 Processor 3800+ (but I run 32 bit software)
2GB RAM
NVIDIA GeForce 6100 onboard graphics

3 Hard drives: 
320GB Seagate (Windows 7)
200GB Samsung (XP and Ubuntu 9.04 dual boot)
200GB Maxtor (XP)

The multiple operating systems and hard drives are what I was curious about, in whats really there. Post this boot script in code tags it will give the lowdown on whats going on.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This will give much more information then the fdisk command.

I would also post this before attempting any more installations, and wait for the pro's to chime in.

---

