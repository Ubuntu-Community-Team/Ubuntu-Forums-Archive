---
title: "&quot;Kernel Panic&quot; error on install"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by Ex_Nihilo on 2006-04-07
So I created a paritition for ubuntu to install to, and booted up the 5.10 GNOME install CD that I downloaded. Everything starts ok, but as soon as I hit enter to commence with the normal install, I get this message:

"Kernel panic - not syncing: no init found. Try passing init= option to kernel"

I'm new to linux based systems and I have no idea what it means. Anyone know how to get past this little bump and continue with my install?

Thanks!

---

### Post by Requiem on 2006-04-07
[QUOTE=Ex_Nihilo]So I created a paritition for ubuntu to install to, and booted up the 5.10 GNOME install CD that I downloaded. Everything starts ok, but as soon as I hit enter to commence with the normal install, I get this message:

"Kernel panic - not syncing: no init found. Try passing init= option to kernel"

I'm new to linux based systems and I have no idea what it means. Anyone know how to get past this little bump and continue with my install?

Thanks![/QUOTE]

Hi! I'm new to GNU/Linux based systems too but let's see what we can do...
Kernel panics are things that happen when "teh linux" and i mean the kernel, fails, init is linux's configuration file, and not finding it means that either:

1) It doesn't exists
  a) Because there was an interruption in the installation process
  b) Because you haven't installed ubuntu yet.
2) Linux is looking for it in the wrong place.
  a) Because the booter, named grub, told linux to look in the wrong place
      i ) Because there was already another grub installed prior to this
      ii) Because grub got confused about where your linux is.
  b) Because you mounted your '/boot' directory somewhere else.

Now I have some questions for you:
 a) how many operative systems have you installed on this machine?
 b) have you installed any linux on this machine before?
 c) have you tried ubuntu with a liveCD on this machine before?
 d) does the machine have SATA or other new types of drives?

Ubuntu installer is actually a mini linux system that runs on ram, it is booted by the bios, not grub and the init is there on the cd.

My guess? Either the kernel is trying to autodetect hardware and finding it too exotic, or your bios is not correctly booting the cd.

---

### Post by Ex_Nihilo on 2006-04-07
I also have XP on this machine. I've never installed a linux system before.

I guess it could be a problem with the autodetect of the hardware, since that's the point in which it basically stops.

---

### Post by Requiem on 2006-04-07
[QUOTE=Ex_Nihilo]I also have XP on this machine. I've never installed a linux system before.

I guess it could be a problem with the autodetect of the hardware, since that's the point in which it basically stops.[/QUOTE]

Seriously, I urge you to try a liveCD first, do you have any? Also, it could be a problem with a scratched disk, have you cheked the crc?

---

### Post by theclifster on 2006-04-08
Hi I am new to this!

I have a old pc. Asus Motherboard, 512 Ram, with Win XP on it.

I want to preserve winxp in a partition and install UBUNTU on the other partition.

I am following [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) and found that after enter I get the same error as listed in this Thread.

I got the CDs direct from UBUNTU and have tried three so it is not the CD.

Error:
4294668:920000 Kernel Panic, - Not Syncing: No init Found - Passing Init option = 0 to kernel 
4294668:920000 _
( it hangs here)

Any suggestions other than uninstall XP or use the live disk??
Cheers
](*,) ](*,)

---

