---
title: "How to save my windows? Ubuntu install failed"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by cyro on 2007-05-20
Ubuntu 7.04 install failed, when the installation tried to install the grub bootmanager,
finish "94 % installing grub bootmanager" was written there for 20 Minutes ... nothing happened,
so I rebooted and retried the Installation ... still the same ...
this time the automatic disk partitiontool made another partition ...
so I started again the installation and made manual mode in the partionstep ...
deleted all linuxpartitions ... so that only my 2 windows partitions rest (first OS, 2nd just Files).
But when rebooting an error message came up it didn't find the os ...
when I started win2k from cd and made recoverycheck and then gone to the recoveryconsole and typed in 'fixmbr' and 'fixboot' restarted the system, and still an error message 'can't find disk',
well I don't know what to do now? How can I make my Windows 2000 boot again?
Everything is working so fine in my windows environment, I really do not want to delete everything and do a reinstallation ...

---

### Post by raja on 2007-05-20
Have you looked at [supergrub]("http://freshmeat.net/projects/supergrub/")? I havent tried this myself, but think it might help.

---

### Post by jdelphin on 2007-05-20
try it again but with just fixmbr

---

