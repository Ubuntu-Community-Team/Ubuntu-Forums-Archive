---
title: "How to setup encrypted LVM installation on Lubuntu?"
date: 2022-01-03
forum: Installation &amp; Upgrades
---

### Post by signsoflove on 2022-01-03
Good day!

I'm looking to dual-boot Lubuntu on my laptop. The setup I was planning to use was "LVM-on-LUKS" or an LVM set up inside a LUKS container.

Unfortunately, I can't figure out how to get this setup using the Calamares installer bundled with the Lubuntu ISO. [This article]("https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html") shows how I normally would go about getting this setup, but the Calamares installer is very uncooperative in this manner.

i. Creating a LUKS container and creating a volume group inside said container isn't possible using the partition manager in the installer. I couldn't find an option to assign the LUKS container as an LVM, and even if I succeeded, the installer doesn't seem to let me create logical volumes.

ii. Setting up the volume group before I enter the installer doesn't help either, as the installer doesn't let me encrypt them unless I format them, undoing all that work and bringing us back to (i).

iii. Setting up the LUKS container and volume group beforehand results in an error if I proceed with the installation. I can't recall the specifics, and I didn't remember to screenshot it at the time, but I vaguely recall the error message being something about the grub installation failing.

 How should I go about getting what I want? Is there an alternative ISO I could use that would let me use the Ubiquity installer but for LXQt?

---

### Post by TheFu on 2022-01-03
Manual install is the only way I know with a dual boot setup.

Perhaps putting one OS on the drive and having the others running inside virtual machines would work for you?  I've been running virtual machines for my main desktop over a decade.  To my knowledge, only programs that need direct GPU access have problems with that configuration.

"Paddy" in these forums has a long guide for manual encryption setups.

---

### Post by guiverc on 2022-01-03
> **signsoflove said:**
> I can't recall the specifics, and I didn't remember to screenshot it at the time, but I vaguely recall the error message being something about the grub installation failing.

 How should I go about getting what I want? Is there an alternative ISO I could use that would let me use the Ubiquity installer but for LXQt?

Without specifics it's hard to provide specific help.

The only *alternate* ISO produced by Lubuntu used the *debian installer* being for systems that had 768MB of RAM or less; ie. too little to run a *live* ISO and installer (`ubiquity` at that time) at the same time. [Lubuntu no longer aims at really old & limited machines thus the *alternate* ISO was dropped]("https://lubuntu.me/taking-a-new-direction/") but it existed to get around RAM issues and running the installer on a *live* system.

Ubiquity is GTK+ with a Qt skin that is hardcoded for KDE/Kubuntu; so non-Kubuntu but Qt5 based *flavors* don't use it; why Lubuntu has used `calamares` since using Qt5 from Lubuntu 18.10 & later, plus Ubuntu Studio since 20.10 onwards (*when they switched from Xfce/GTK3 to KDE/Qt5*) .

If you want to use `ubiquity` you'll need to use another flavor (Xubuntu, Kubuntu..) as they need to be GTK+ based or Kubuntu/KDE.  I have installed Xubuntu on a laptop with encrypted home partition, then added `lubuntu-desktop` to it without issue so as to have Lubuntu/LXQt, but the result may not be as lean (*I like XFCE too so was perfectly happy to have both; Xubuntu being used as a QA-test which is why I think it was used*)

---

