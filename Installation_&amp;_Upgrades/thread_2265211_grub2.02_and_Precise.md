---
title: "grub2.02 and Precise"
date: 2015-02-13
forum: Installation &amp; Upgrades
---

### Post by Byb on 2015-02-13
Hi
I have an old laptop that must remain with precise because of video. For years I have an issue, after posts, as soon as grub starts very noisy beeeps are sent util the menu is shown. Because of this, the menu remains waiting until I select an OS to start, even there has been no crash before (of course I have commented out the before-last if fi statement in /etc/grub.d/10_linux to display the menu always and required changes in /etc/default/grub for this to work fine). It only does when I set "Extended POSTS" in my BIOS, but they are too long to allow this as a workaround. Whichever the POSTS setting is, I see a stealth error (roughly: "error: no video mode activated" ) just before the menu displays, then the beeeps end.  This king of infinite pause prevents me from remotely restarting the laptop.

So I'd like to know if I can have grub upgraded to 2.02, maybe it will resolve the issue. A cool side effect would be I could use the new GRUB_DISABLE_SUBMENU=y and revert to a standard 10_linux.

Thank you

---

### Post by mörgæs on 2015-02-13
> **Byb said:**
> 
I have an old laptop that must remain with precise because of video. 

Let's see the details. Please post the output from ```
sudo lshw -C video
``` in CODE tags.

---

### Post by Byb on 2015-02-14
```
*-display               
       description: VGA compatible controller
       produit: NV28M [GeForce4 Ti 4200 Go AGP 8x]
       fabriquant: NVIDIA Corporation
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       version: a1
       bits: 32 bits
       horloge: 66MHz
       fonctionnalités: pm agp agp-3.0 vga_controller bus_master vga_palette cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       ressources: irq:11 mémoire:fc000000-fcffffff mémoire:f0000000-f3ffffff mémoire:fd000000-fd01ffff

```
I enabled upgrade to 12.0.5 in which I found my video is not supported... and grub2.02 neither. I reverted back to 12.04 with much sweat.
More, I see that I thought badly, thinking grub was just a small independant package. It seems deeply intricated within the distribution, with a lot of dependancies from each other, so I feel I can't get it to 2.02.

---

### Post by mörgæs on 2015-02-14
This is really old stuff. Maybe [this]("http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687") will help for 14.04.1.

I'm aware it's not the same graphics adapter but still worth a try.

---

### Post by Byb on 2015-03-06
It won't : nouveau won't work with nv28**m** and precise HWE Stack doesn't support nvidia-96 anymore.

---

