---
title: "Need some help before installing ubuntu 10.04"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by jsvidyad on 2010-08-25
Hi!!

  I am currently running ubuntu 9.10(amd64). I am planning to do a fresh install of ubuntu 10.04(amd64). I have a dual boot sytem with windows xp in addition to ubuntu. I'd like to keep the windows os even though I only use it once in a while. I was looking at the website [www.ubuntuguide.org](www.ubuntuguide.org) . There, the following info is given: "DO NOT USE the Lucid Lynx Desktop edition LiveCD as an installer if you use a boot partition, use more than 2 operating systems, or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it." Does this mean that if I use a separate partition for /boot, I shouldn't use the liveCD as installer? I like to keep a separate /boot partition and I don't want to have to deal with re-installing windows, re-installing grub etc. Can someone give me some input regarding this? I didn't face any issues when installing ubuntu 9.10 with a separate partition for /boot. I was able to boot into windows after installing ubuntu 9.10. Has anyone installed ubuntu 10.04 with this configuration?

    Thanks in advance.

---

### Post by Noo 2 Ubuntoo on 2010-09-05
No I haven't, but I want to do a fresh install after having problems with evolution in Lucid and I dual boot too (Windows xp pro & Ubuntu).

Unfortunately for both of us I think you have more technical expertise than me. Just thought I'd post to let you know your not on your own and I'll keep an eye on this thread for the answer. I don't want to make things worse than they already are and find I've lost my Windows partition.

---

### Post by Noo 2 Ubuntoo on 2010-09-05
> **Noo 2 Ubuntoo said:**
> No I haven't, but I want to do a fresh install after having problems with evolution in Lucid and I dual boot too (Windows xp pro & Ubuntu).

Unfortunately for both of us I think you have more technical expertise than me. Just thought I'd post to let you know your not on your own and I'll keep an eye on this thread for the answer. I don't want to make things worse than they already are and find I've lost my Windows partition.

Forgot to say I upgraded from Jaunty to Lucid via Update Manager originally.

---

### Post by GenBattle on 2010-09-05
I just did a full install of 10.04 recently with a Win7 install on another partition, and GRUB does fine at detecting and booting the Win7 install. That said there may be some problems with XP, but i doubt it.

If the worst comes to pass you can always just restore the windows bootloader from the windows install CD? But as i said, i've never had an issue after overwriting the boot sector with GRUB. That said, i've never used a separate /boot parition.

---

