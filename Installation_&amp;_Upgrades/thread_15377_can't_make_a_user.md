---
title: "can't make a user"
date: 2005-02-14
forum: Installation &amp; Upgrades
---

### Post by Janus on 2005-02-14
When the 2e stage of the installation begins, you are prompted to make a user.  It just keeps looping there,  it requests over and over to make the same user.  So I just cancelled it then to move on to the next step.  Everything fine, then it start, of course Xserver crashes :s but then I have to login.  Of course this is where it hangs,  there are no user.

Next to this problem, there also another.  I have 2 hd's, one Sata and one Pata.  On the sata there is windows and I wanted linux on the pata.  But  when I booted the cd, everything went fine.  At the end of 1st stage you are prompted to remove the disk and the system will reboot with GRUB.  Well there's the thing, my computer just booted into windows.  It is only when I set in the bios to boot from the pata that I got into the 2e stage of installing.

Any thoughts anybody?

Thx

---

### Post by dejot on 2005-02-14
Where did you install GRUB?

No Idea why it loops in creating the user...
But without a user your only chance to get into your Ubuntu is to chroot from e.g. an ubuntu-live-cd and add a new user or change the root password.

Dejot

---

### Post by Janus on 2005-02-14
[QUOTE=dejot]Where did you install GRUB?

No Idea why it loops in creating the user...
But without a user your only chance to get into your Ubuntu is to chroot from e.g. an ubuntu-live-cd and add a new user or change the root password.

Dejot[/QUOTE]

Well, I'm kinda completely new to linux.  So forgive the stupidity ;)

I just followed the normal install procedure, so GRUB was installed automatically (I think) because it detected windows.

---

