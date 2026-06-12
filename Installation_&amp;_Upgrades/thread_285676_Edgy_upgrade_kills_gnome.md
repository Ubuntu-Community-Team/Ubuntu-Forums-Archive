---
title: "Edgy upgrade kills gnome"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Stochastic on 2006-10-27
Hi, I just did an Edgy upgrade from Dapper through apt-get update apt-get dist-upgrade.  Now upon reboot it gets to the login screen and works perfectly for my IceWM session but the default Gnome logs in then logs right back out after some weird flashes (I do get to see the gnome splash-screen with the icons for synaptic and the file browser and such loading *edit - it only gets to the third icon (nautilus)*) comes back into the login screen.  My old XGL install allows me into a gnome environment but compiz won't start and I thus have no window borders etc.  Also, all the icons look to have a different font face/size in the xgl environment.  Any ideas on where to start fixing this?

Compaq Presario V2436
AMD Turion 1.8ghz
512mb ram (only actually 384mb after the shared video memory is taken out)
ATI Radeon Xpress 200m

Thanks.

---

### Post by oled on 2006-10-27
I'm having a similar problem with my htpc! It has an onboard ati xpress gfx, so i'm thinking mabye there is a driver problem! I only have gnome installed so I can't try other sessions.

---

### Post by kingcharles1666 on 2006-10-27
Same problem here, i have been trying to solve it since a few days but even with a clean install the problem comes back. I feel it is a X problem because I tracked some errors regarding sessions failing to communicate to the display driver, at that point the system reverts to gdm. My graphics card is a voodoo3 / tdfx driver.
I think I will leave edgy for what it is and re-install dapper

---

### Post by ejo on 2006-10-27
As I noted in a thread a few below these, I'm having pretty much the same problem.  I have a Voodoo3 card tho.

---

### Post by Stochastic on 2006-10-27
So is the general consensus that the ati driver is at fault?  Why would ubuntu release a distro with a buggy driver?

---

### Post by Gannin on 2006-10-27
Problems with the ATI driver is a known issue, and they're working on it.

---

### Post by Stochastic on 2006-10-27
> **Gannin said:**
> Problems with the ATI driver is a known issue, and they're working on it.

Why don't they warn us before asking if we want to upgrade?  How do I get Dapper back now?

---

### Post by kingcharles1666 on 2006-10-31
> **Gannin said:**
> Problems with the ATI driver is a known issue, and they're working on it.

Not just the ATI driver, because people using the tdfx driver have issues also!

---

### Post by Gannin on 2006-11-01
In your xorg.conf file, in the driver section, try replacing whatever you have there (ati, etc.) with radeon and see how that works.

---

### Post by luismo on 2006-11-02
Yes it is definitely a problem with tdfx driver. I've changed to vesa driver and it is working fine (slow, very slow drawing, but working).

I've been checking xorg site and seems that driver has not being changed since 1 year ago, what I don't understand is why the hell it doesn't work properly now.

And.... the best..... the graphical installation CD doesn't work on my computer, problably by the same reason, so... I suppose that a clean install won't solve anything.

---

### Post by spandon on 2006-11-02
Hi,
Think you may have come accros the same problem I encounted upgrading from dapper to Edgy.
The machine ran perfectly in breezy & Dapper, yet refused to load Live CD, so I entered the following command at boot-up of the live CD
**boot: vga 771 noapic nolapic**
The live Cd then worked perfectly (the resolution defaulted to 1280x1024 with other options available.
I was then advised to download and install from the Alternative CD, this I did, installing using the above commands, everything went fine, and I have not noticed any change in speed.
Hope this helps
Don

---

### Post by luismo on 2006-11-04
> **spandon said:**
> Hi,
Think you may have come accros the same problem I encounted upgrading from dapper to Edgy.
The machine ran perfectly in breezy & Dapper, yet refused to load Live CD, so I entered the following command at boot-up of the live CD
**boot: vga 771 noapic nolapic**
The live Cd then worked perfectly (the resolution defaulted to 1280x1024 with other options available.
I was then advised to download and install from the Alternative CD, this I did, installing using the above commands, everything went fine, and I have not noticed any change in speed.
Hope this helps
Don
Spandon....

Are you using a Voodoo video card? The solution you applied was working only for the live CD or for the installed distribution after the upgrade?

---

### Post by got_nix on 2006-11-16
I'm having a issue i think is related to this but i wont blame the drivers. gdm starts fine which needs xorg so thats definatly not the prob i think compiz and dapper just not compatable i need to remove all the compiz stuff but i need to log into gnome to remove em from session start up as well and i cant.. :(

---

### Post by Gannin on 2006-11-16
Have you tried to log into Gnome in safe mode?

---

