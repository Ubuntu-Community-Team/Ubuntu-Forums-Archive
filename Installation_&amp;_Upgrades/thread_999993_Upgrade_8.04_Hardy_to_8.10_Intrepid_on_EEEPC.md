---
title: "Upgrade 8.04 Hardy to 8.10 Intrepid on EEEPC"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by dccrens on 2008-12-02
I have the ASUS EEEPC 1000h. I have it set up using dual boot (grub) with a small Windows XP partition and the rest of the 160GB hd taken up by Ubuntu 8.04 Hardy. I have the Hardy install on several partitions (Root, Home, Var, etc, etc). I have EVERYTHING working, hardware, software etc. I am also using Adam's EEEPC install of the kernel/Ubuntu. 

My question is, has anyone upgrade an EEEPC running 8.04 to 8.10 and if so, how did you do it? I am not looking to do a "clean" install but a true upgrade if possible. I want to be able to preserve some of the changes I have made to the init scripts, etc.

---

### Post by snowpine on 2008-12-02
Dave, I am pretty sure you can upgrade by the usual method ('sudo apt-get dist-upgrade' or through the Update Manager), but that you should temporarily use the generic kernel until after the upgrade, at which point you can download the Intrepid version of the eeepc kernel using a wired connection. 

Check it out: [http://forum.eeeuser.com/viewtopic.php?id=47847](http://forum.eeeuser.com/viewtopic.php?id=47847)

I must confess I've used both Hardy and Intrepid (with Adam's kernel) on my eee, but I did a fresh install, not a dist-upgrade.

---

