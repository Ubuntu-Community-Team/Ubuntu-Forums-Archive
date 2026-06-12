---
title: "Best way to upgrade an Wubi Ubuntu install"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by James2k on 2010-09-16
I'm running Ubuntu 10.04 via Wubi and when the time comes I will want to upgrade to 10.10, however because I'm on a wubi install I'm a little worried that things can go wrong, particularly with any update to GRUB2, as it doesn't behave in the same way as a dedicated partition install.

Can any Wubi users give me any tips on a smooth upgrade?

---

### Post by bcbc on 2010-09-16
1. Back up the root.disk. If you have other virtual disks back them up too.
2. Grub2 has modified some of the pieces used to boot wubi for 10.10, so backup the wubildr* files in root and the \ubuntu\winboot\* files.
3. If you get a grub-pc update window that warns you that you have not chosen to install grub, check the checkbox to proceed anyway and click Forward. If grub asks you to pick a device to install to, do not do select any. 

Then if anything goes wrong in the upgrade, just copy the files back over. That's about it. 

I'd monitor some of the wubi bug reports on launchpad for any upgrade issues and also monitor the forums for any issues. This can help minimize the pain.

---

### Post by James2k on 2010-09-17
Thanks for your reply bcbc.

I will make sure I follow your steps. I don't plan on upgrading to 10.10 till it's final release anyway, but I will check Launch Pad and the forums for issues regarding Wubi and 10.10.

Thanks!

---

### Post by garvinrick4 on 2010-09-17
[LEFT]This will upgrade your  /etc/apt/sources.list to maverick and then update and dist-upgrade your install. As said before make sure 10.10 Wubi is a stable OS before unless you do not
mind doing a set-up. After doing a few you get quick at it. Just keep your Home folder backed up and no grief.


[/LEFT]

```
[LEFT]sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

[/LEFT]

```

---

### Post by bcbc on 2010-09-17
You don't need to do anything on the command line to upgrade. Upgrade manager will do it. In fact I strongly recommend not doing it manually.

If you're on an LTS (i.e. 10.04) you just need to uncheck the box in Software Sources that says to only notify about new long term releases. Update manager will notify you that an upgrade is available and you just click on Upgrade.

This will only work after 10.10 is released - upgrading while in beta is not advisable unless you are prepared for data loss or worse. (This still does not require manual editing of software sources).

---

### Post by James2k on 2010-09-17
I usually just go to update manager and it will say "New Distribution 10.10 Avaliable" when the time comes.

---

