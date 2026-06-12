---
title: "[SOLVED] Confused whether to use GParted or Killdisk"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by kalikid on 2008-05-11
My Ubuntu 8.04 won't reboot my windows xp disk so I can reinstall windows & opt for a dual boot instead of exclusive Ubuntu.

I was advised to download GParted & did so. My desktop booted into the GParted disk, but once there I got confused what to do with all the options.

I later read about Killdisk on this forum, which some techies advise to wipe the disk clean & then reinstall whatever OS. 

Which would be better in my case? Killdisk seems easier to follow. Believe me, I'm not technically inclined & need a simple-to-follow procedure. And I'm a little leery of screwing up my hard drive.(I've got the bios set up to boot first off cd.)

So I thought I'd ask you guys for your advice. Thanks for your help.

---

### Post by logos34 on 2008-05-11
Sounds like the cdrom is having trouble reading the windows install cd at boot, if I understand you correctly, since you're able to boot the gparted live cd. 

If you decide to reinstall you can just use the version of gparted on the ubuntu live cd to delete all the partitions and start out fresh.  Or if you want to wipe it absolutely clean, instead of killdisk or dban just run this command in a terminal:

sudo dd if=/dev/zero of=/dev/hda conv=notrunc

(replace hda with your drive)

---

### Post by kalikid on 2008-05-12
Thanks, logo, that helps clarify it for me--and I appreciate the command tip. Simplifies things a bit.

---

