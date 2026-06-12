---
title: "Compaq Presario F700 extremely slow boot after 10.10 install [5 minutes bootup]"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by banago on 2011-02-16
I made a clean install of Ubunto 10.10 on my Compaq Presarion F700, nVida graphics, AMD Turion 64x2.

Installation was fine.

When I boot, it takes a lot of time, 5 minutes or more. Also, after the system loads I get those applet errors I've attached. Sometimes I get all the applet errors and sometimes it get few of them.

I tried several configs of "GRUB_CMDLINE_LINUX_DEFAULT" but still no luck.

Please help me - thanks very much

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181043&d=1295008704[/IMG]

---

### Post by mörgæs on 2011-02-16
Does this describe your problem?

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/537383](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/537383)

If so, then it would be good if you reopen the bug report (as 'confirmed') and add any relevant information you have.

---

### Post by banago on 2011-02-16
No, that does not describe my problem. Acutualy, my problem is really slow boot. This kind of booting makes the icons crash. I know for sure the problem lies with GRUB_CMDLINE_LINUX_DEFAULT settings on /etc/default/grub. I tried many options and I left it empty at least. It works fine now. No incons crash and the boot is much more faster, even though not the speed Ubunto boot normally has. 

So, GRUB_CMDLINE_LINUX_DEFAULT settings is my issue and I don't know the right ones, expced that empty works better than any other combination.

---

