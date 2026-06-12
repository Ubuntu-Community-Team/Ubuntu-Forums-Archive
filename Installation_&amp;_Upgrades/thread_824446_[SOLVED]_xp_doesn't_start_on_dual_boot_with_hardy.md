---
title: "[SOLVED] xp doesn't start on dual boot with hardy"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by tayran on 2008-06-10
Hi. I have installed kubuntu 8.04 after a fresh install of windows XP SP2. Most of the time when i switch from kubuntu to xp it is locked in the boot process after grub menu. Status bar in the xp boot screen is animated for a while and then locks. After that system does not respond, HDD light stays on and i have to hard reboot. After that when i use a boot cd to perform chkdsk or simply when i open windows in safe mod problem is gone and i can boot again directly into xp.
    I first thought it is because of a corruption with unmounting process since i use ntfs partitions mounted r/w in kubuntu but later i tried this:
First I selected kubuntu in grub menu. But just after that i have restarted pc with ctrl+alt+del. Then i experienced the same problem. When i booted into safe mode and restart problem was gone. So it looks like problem is related to grub. Prior to Hardy I was using Gutsy on same machine and similar partitions and there was no problem like this.

    My system is:
Acer Aspire 5024 laptop, 1.5 GB RAM, 160GB PATA HDD
First two partitins (15GB and 20GB in order) belong to windows and formatted with NTFS. The other two are in ext3 and used by kubuntu only. No swap partition for kubuntu. I have oracle server installed in first windows partition but i don't think it can cause such a problem.

---

### Post by hal8000 on 2008-06-10
> **tayran said:**
> Hi. I have installed kubuntu 8.04 after a fresh install of windows XP SP2. [COLOR="Red"]Most of the time[/COLOR] when i switch from kubuntu to xp it is locked in the boot process after grub menu. Status bar in the xp boot screen is animated for a while and then locks. After that system does not respond, HDD light stays on and i have to hard reboot. After that when i use a boot cd to perform chkdsk or simply when i open windows in safe mod problem is gone and i can boot again directly into xp.
   
    My system is:
Acer Aspire 5024 laptop, 1.5 GB RAM, 160GB PATA HDD


What happens at other times, system boots normally?

I think I know what your problem is and here is how to prove it.

After you have used kubuntu, dont restart or reboot into windows but shut down completely. Then power on and load windows, I think windows will load ok.

What is happening is that your laptop display is being driven at a slightly different refresh rate or resolution to the rates used under windows. The hardware doesnt "release" these settings, so when windows loads you experience a freeze.
Only a cold boot, i.e. power down and then load windows will cure this.
I had the same problem once on an old Dell laptop with Debian.


If cold booting does fix this, then you need to start looking at the display resolution under kubuntu, hope that helps.

---

### Post by tayran on 2008-06-13
I think you shown me the right path thanks. I also have a random display problem in kde after reboot. So these two are the same. I am looking for a solution to a refresh rate problem now thanks. I will write here the solution if i will be able to find it.

---

