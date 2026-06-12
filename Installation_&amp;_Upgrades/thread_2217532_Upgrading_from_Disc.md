---
title: "Upgrading from Disc"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by baileyrock on 2014-04-17
I am attempting to upgrade my Desktop Ubuntu installation from 12.04 LTS to 14.04 LTS.

When tryng to upgrade ubuntu from the terminal using "do-release-upgrade" and through the upgrade manager failed. Not wanting to wait to upgrade, I burned an ISO of the new ubuntu to upgrade it using a disc.

Using the disc installation, I chose the option to upgrade from 12.04. I got to the part where it asked to name the computer and setup a main account and password. Not knowing why it was asking for a main account as this was an upgrade and I already had a main account, I quit the upgrade to boot to my 12.04 ubuntu installation.

After the bootloader, I was taken to GRUB to choose an OS (a step that normally happened automatically). After choosing any version, Linux begins to load but then says "target filesystem doesn't have requested /sbin/init" and goes into a limited shell.

The installation disc no longer recognizes another version of Ubuntu. I can still find my /home directory with all data intact.

---

### Post by jbaerboc on 2014-04-17
Yeah as far as I know the Installers don't have the option to upgrade. You'd need to run the updater [from your current Ubuntu 12.04 LTS and during the process it should say "hey there's a new version, want to upgrade?" Granted you have the last LTS so I'm not sure if your experience will vary from what a 13.10 user would see. Maybe someone else can offer a definitive answer?

---

