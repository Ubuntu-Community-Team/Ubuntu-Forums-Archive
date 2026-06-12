---
title: "Lubuntu 14.04 to 16.04 LTS upgrade; lxde desktop/panel &quot;hiding&quot;"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by dtheurer on 2016-09-19
I'm attempting to upgrade Lubuntu 14.04 to 16.04. I am running Lubuntu as a virtualbox host with Windows 8.1 and Lubuntu guests. I successfully upgraded the Lubuntu 14.04 guest to 16.04. However, after attempting to upgrade the Lubuntu 14.04 host to 16.04, the desktop is now "hiding" behind the 16.04 default wallpaper along with two directory shortcuts I normally have on my lxde desktop. I did manage to get a sort-of menu to expose a Logout option. The reason I say "hiding" is because if I elect to Logout, the logout dialogue shows the proper desktop, my custom wallpaper, panel, icons, and autostarted programs.

I haven't been able to determine where to even start fixing this. (I have backups of the VMs, so could re-install if absolutely necessary, but the host is on a bootable raid 1 setup so is rather more involved to re-install.)

A couple of things I've tried:
- re-install lxde via apt-get (no errors, but no change)
- the Guest account behaves exactly the same way ("hides" the normal lxde desktop, panel, etc.)
- downloaded the 16.04.1 iso and made a bootable USB drive. It also boots into something with no panel, menu, etc.

TIA so much for any and all suggestions.

Dirk

---

### Post by dtheurer on 2016-09-21
What I found very odd is that while the lxde desktop is "hiding", some applications will be visible/accessible (firefox, LXTerminal, pcmanfm), while others "hide" (are invisible and inaccessible) (Synaptic, Task Manager, Open Box {anything}).

I've had a chance to try a few things:

[LIST]
[*]16.04.1 on live USB: does this "hiding" thing; 
[*]fresh install of 16.04.1 from live USB; does this "hiding" thing; 
[*]14.04.5 on live USB: does this "hiding" thing; 
[*]fresh install of 14.04.5 from live USB; does this "hiding" thing; 
[*]14.04 (not .x) on live USB: does **not** do this "hiding" thing and everything appears to be OK; 
[*]fresh install of 14.04 (not .x): does **not** do this odd hiding thing and everything appears to be OK; 
[*]upgrade fresh 14.04 install to 14.04.5: everything appears to be OK; 
[*]upgrade fresh 14.04->14.04.5 install to 16.04.1: does this "hiding" thing. 
[/LIST]
I've had to re-install 14.04 and allow it to upgrade to 14.04.5 and everything appears to be OK now.

Hardware is:
[LIST]
[*]CPU/GPU: AMD A10-5700 / Radeon HD 7660D 
[*]Motherboard: MSI A88XM-E45 (MS-7721)
***Correction: MB is Gigabyte GA-F2A88XM-D3H **(though, so far, it appears the MSI behaves the same way)* 
[*]Memory: 16GB 
[*]HD: WD3200LPVX-2 (320GB x 2) 
[/LIST]
There is definitely something funky about the 14.04.5 and 16.04.1 ISOs as well as the 14.04.5 to 16.04.1 upgrade - at least on my hardware. :confused:

Dirk

---

### Post by ronnie-vc10 on 2017-02-14
Yes, I have the same "hiding" problem on upgrading to Ubuntu 16.04 LTS (not Lubuntu)

This "hiding" was confirmed when I took a Screenshot of the blank desktop, but the Screenshot showed Folders!

I am considering a complete re-install, but any advice would be appreciated.

Ronnie

---

### Post by dtheurer on 2017-02-14
As I mentioned above, I could not find any way to get 16.04 installed. I couldn't upgrade from 14.04 or do a fresh install. :( Only thing I could accomplish was install 14.04 and upgrade to 14.04.5.

NB My last attempt at this was in Sept (as noted). I have not had an opportunity to try again since.

---

