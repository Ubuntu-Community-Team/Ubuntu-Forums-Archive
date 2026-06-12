---
title: "gutsy upgrade problems"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by halln on 2007-12-10
I upgraded my system from feisty to gutsy few weeks ago and after the upgrade installation, I've noticed that the system clock runs way too fast so i search for a fix, and i stumbled this fix.. kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro quiet splash noapic acpi=off and restart and after that the clock is back no normal speed but when i click quit the system wont shutdown so i looked for a fix again like apm=force, apm=power off, etc. yes some of those work in shutting down my system but the system clock will run way too fast again. So either i have a normal clock or a system who can shutdown properly to live with.  I hope somebody could help me with this coz i really love my ubuntu. " be gentle with me, I'm just a copy and paste person"

---

### Post by PmDematagoda on 2007-12-10
Just a suggestion, but did you try doing a clean install of Ubuntu?

It seems to me that your upgrade may not have gone well since some people do get problems like this when they upgrade Ubuntu.

---

### Post by halln on 2007-12-10
nice suggestion but I already tried it but for no avail I dont have any success in doing it I tried for how many times untill now still tryin but I ended up with this black/blank screen I did everything I can find in this forum eveything fail, unfortunately.. but Im still hopeful I can get a better fix for this one. The only thing works is loading 7.04 then upgrade to 7.10 tru the synaptic. My final plan I think.. is stay with 7.04 untill hardy.
AMD 64 3200
NVIDIA 600 series
Abit motherboard
homebuilt
DDR2 1gig

---

### Post by PmDematagoda on 2007-12-10
About the clean install, do you get the blank screen when trying to use the Live CD or after Ubuntu is installed?

---

### Post by halln on 2007-12-11
> **PmDematagoda said:**
> About the clean install, do you get the blank screen when trying to use the Live CD or after Ubuntu is installed?

I did a clean install using the live cd but after the moving bar finish loading the screen went blank/black i can still hear the welcome music on the backround though, I tried to use the alternate cd the screen went black when it reach welcome stage thing. I have tried the latest release of linux mint that is derived from ubuntu gutsy recently but same thing happen. I dont know why feisty seems to  work fine on my computer, no glitches or any major problems at all and gutsy should be the latest release.. need help to all comp whiz kids out there. TNX

---

### Post by PmDematagoda on 2007-12-11
Your problem is the Nvidia VGA driver being setup improperly.

When you reach the end of the boot process of Ubuntu do Ctrl+Alt+F1 to bring you to a terminal. Once there do:-
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

After reconfiguration is done do:-

```
sudo startx
```

That should bring you back to a GUI from where we can proceed to installing the Nvidia drivers properly.

---

### Post by halln on 2007-12-11
I tried that already, I change my resolution to 1024x768 32bits and select vesa and type the code startx but i think i forgot to use sudo as SUDO STARTX i will try that again later. Im trying now to upgrade from feisty to gutsy using the alternate cd "i'm on the process right now see what will happen" This is the only thing works for me upgrading from feisty to gutsy but I encountered this clock that runs way to fast thingy and so on.. read my thread,:confused: tnx

---

### Post by halln on 2007-12-11
upgraded 7.10 tru alternate cd everything seems to be ok except the clock still way to fast than normal. pls needed help here

---

### Post by alpianon on 2008-01-17
Same problem (upgrade from feisty to gutsy with an ABIT motherboard).
The only solution I have found is downgrading the kernel to the old feisty's one (2.6.20-16)
(in my case, the upgrade did not uninstall it, so I just changed the default entry in grub; in any case, you can download the packages from packages.ubuntu.com and re-install it)
This is certainly a bug of the new gutsy kernel, let's wait 'til they fix it... ](*,)

---

### Post by alpianon on 2008-01-27
I forgot one thing: if you downgrade the kernel, you have to downgrade also the package gnome-mount (for some reason, gutsy's one doesn't work, so you have to download and install feisty's one, always from packages.ubuntu.org)

---

