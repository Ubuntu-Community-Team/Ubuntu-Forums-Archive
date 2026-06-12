---
title: "Ubuntu installation fails"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by systemlord on 2006-08-14
Hi everybody

I have tried breezy and drake desktop versions but the install never starts up properly. (It fails during 'hardware drivers' before the install even starts).

My current configuration is this:

Intel Celeron 2.8 Prescott
512MB RAM
Nvidia Geforce Fx5200 running as a secondary card (Onboard card disabled via BIOS)
WinXP pro running on primary drive

At first I had a regular kernel panic during the setup, but after specifiying the noapic nolapic and pci=noacpi kernel startups I am one step closer but still not there :) 

Any ideas?
R

---

### Post by hexion on 2006-08-14
Try deactivating the integrated ethernet of your mobo (if you have one).

I had problems with dapper installation because it tried to conect to the internet, and after a while stopped responding..

Good luck

---

### Post by systemlord on 2006-08-14
Thanks, but that didn't do it either.

R

---

