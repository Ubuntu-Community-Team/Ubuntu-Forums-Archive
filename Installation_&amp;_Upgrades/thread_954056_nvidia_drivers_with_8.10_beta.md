---
title: "nvidia drivers with 8.10 beta"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2008-10-20
It appears with the latest version of the 8.10 beta with the updates complete that neither the nvidia drivers provided by Canonical nor the drivers downloaded from the internet form nVidia's site will operate in the beta.

With the release date just around the corner it is difficult to see them at this point still.  Also, anyone know why the beta 2 hasn't come out yet?

Also, the hype about the wireless functioning isn't justified.  Wireless support still isn't there.

---

### Post by tuxxy on 2008-10-20
Intrepid is still in Beta stage for a reason, for a fully functioning system Hardy is for you.

---

### Post by mikewhatever on 2008-10-20
> **jimbo99 said:**
> It appears with the latest version of the 8.10 beta with the updates complete that neither the nvidia drivers provided by Canonical nor the drivers downloaded from the internet form nVidia's site will operate in the beta.

Hope you wrong, but we shall see in 10 days.

> With the release date just around the corner it is difficult to see them at this point still.  Also, anyone know why the beta 2 hasn't come out yet?

Who said there was a beta 2 planned?
[https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)

> Also, the hype about the wireless functioning isn't justified.  Wireless support still isn't there.

Well, certain wireless drivers (broadcom, atheros) has been added to kernel 2.6.27. If you want your problems fixed, filing bug reports would be much more productive.

---

### Post by jimbo99 on 2008-10-22
I've been using Linux for 5 years and I have many machines running Ubuntu 8.04.

Again, my point stands.  Yes, I know it is beta.  Unfortunately we are very very very very very very very very very very close to the release.

There should have been a second beta by now.

---

### Post by jimbo99 on 2008-10-22
> **mikewhatever said:**
> Hope you wrong, but we shall see in 10 days.



Who said there was a beta 2 planned?
[https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)



Well, certain wireless drivers (broadcom, atheros) has been added to kernel 2.6.27. If you want your problems fixed, filing bug reports would be much more productive.

There is a significant variation on broadcomm's chipset even though they are from Broadcomm.  Also, you will still need the firmware to make it work and that firmware isn't in anyway stable enough to handle all the variations on the chipsets.

---

### Post by sloan1919 on 2008-10-22
> **tuxxy said:**
> Intrepid is still in Beta stage for a reason, for a fully functioning system Hardy is for you.

I have to agree with JimBo, this is just too close for comfort! Not enough time to fix all the little nasties. This is a HUGE problem for this late in the game.

Sloan

---

### Post by Ayuthia on 2008-10-22
> **jimbo99 said:**
> There is a significant variation on broadcomm's chipset even though they are from Broadcomm.  Also, you will still need the firmware to make it work and that firmware isn't in anyway stable enough to handle all the variations on the chipsets.

There have been improvements to the b43 driver since the Hardy release.  The firmware has changed and it appears that the b43 driver has also improved.  The 4311 rev 01 card speed on the b43 now matches the speed of ndiswrapper and the wl driver.

The wl driver is now included in 8.10.  It covers the 4311, 4312, 4322, and 4328 cards.  It is Broadcom's proprietary driver.  It does not need any firmware so now people with those Broadcom cards can activate the driver after the install and it will work without any additional install.  I have seen some issues with encryption on some chipsets, but I can't verify where the problem lies.

So there are now some Broadcom cards that will work out of the box which is nice to see.  It will be nice when the b43 developers can get the open source firmware working so that their drivers will work out of the box.

As for the Nvidia issue, which versions of the nvidia packages did you use?  I see that there are now more than one option for the nvidia cards.  

The release candidate is supposed to come out on Thursday.  All I know is that there have been a lot of updates coming through during the past few days.

EDIT:
> It appears with the latest version of the 8.10 beta with the updates complete that neither the nvidia drivers provided by Canonical nor the drivers downloaded from the internet form nVidia's site will operate in the beta.nVidia generally does not release any fixes for their drivers until the kernel is officially released.  So there should not be a real surprise that the nVidia supplied driver was not working when the beta was released.  I don't think that the 2.6.27 kernel was officially released until 9 October.

---

### Post by claypole on 2008-10-25
On my test box (using an NVIDIA FX5200) I still cannot start X since upgrading to 8.10 a week or so ago.  Has anyone managed to resolve this problem yet or is it still broken in the kernel?

I keep getting the "Saw, signal 11. Server aborting" error at best or "no screen found" at worst, although either way I still have no X.  This PC does have an internal graphics card (not connected) and a PCI NVIDIA card, which is what I am using.  The NVIDIA card is identified in some earlier xorg.conf's as 'BusID    "PCI:1:0:0"' in the device section, with the internal card identified as "PCI:0:2:0", as far as I can see this is no longer explicitly required in the current xorg.conf although I have tried adding this, to no avail.

I don't even care about using the NVIDIA driver right now, just being able to use X at this stage would be good! :(

I understand the debate about being beta etc here.  The problem I have is that every single time I have upgraded this PC (and often others) to a new release of Ubuntu (official or beta), it manages to break X and I spend ages just trying to get GDM back!  Now, I love Ubuntu, have used it exclusively (bar my work laptop with, and I hate it, Vista) for a number of years, but why oh why does X break so easily and why is it so damn difficult to fix??  Even going back over 15 years, Windows has never just left me stranded at a command prompt, sure the graphical environment may be slow, cumbersome, blue screen often or occasionally, even in Vista, but at least I always get a mouse pointer!  Why is this so difficult in Ubuntu :confused:

If anyone has any straightforward troubleshooting advice or links on getting GDM back, it would be highly appreciated :)

---

### Post by claypole on 2008-10-27
The release candidate is out and still no joy.  Has anyone found a resolution to this yet?

---

### Post by senectus on 2008-10-27
Oddly enough the upgrade went smoothly for me except it refused to load the 8.10 kernel

It's still running 
> desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux


---

### Post by mmcmonster on 2008-10-27
I think this is the same problem I got.

A fresh install of Intrepid worked fine.  I upgraded to the nvidia drivers (the one that was recommended by System->Administration->Hardware Drivers).

On reboot, I just get a horizontal line a few pixels high at the top of the screen.

What now?

---

