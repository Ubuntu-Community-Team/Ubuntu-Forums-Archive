---
title: "URGENT! Upgrade to Ubuntu 19.10 Stuck at Package Configuration! Can't do anything!"
date: 2019-10-29
forum: Installation &amp; Upgrades
---

### Post by dee-2019 on 2019-10-29
Hi, my upgrade to Ubuntu 19.10 has hit disaster, and stopped, giving gdm3 configuration message saying I have multiple display managers and please select which one etc and then mutliple display managers can run simultaneously if they are configured and that I need to edit them in /etc/init.d scripts and disable check for default display manager! Problem is that I couldn't agree and press 'OK', there was no option to highlight ok and agree, so I remained stuck on the screen, not knowing what to do. Now I don't know what to do or how to edit the display managers in /etc/inti.d scripts or how to disable check for default display manager! I've opened the gdm3 script but don't know what I should do! I'm right in the middle of the upgrade and can't do anything. If I stop it, I will end up with a broken system and now the configuration message is minimised and nothing seems to be happening. Just says 'applying changes' but I'm stuck at terminal on package configuration. PLEASE help if anyone know what on earth I should do and what I need to change in /init.d files before my system gets destroyed. Thanks in advance. :confused:

---

### Post by ajgreeny on 2019-10-29
I have never been in your situation but I suspect that tapping the Tab key will move the activated item around; keep tapping until it gets to the OK then hit Enter.

---

### Post by dee-2019 on 2019-10-29
@ajgreeny, Thank you so much!! You're a genius. That worked and now it's continued the upgrade. I've spent ages trying different commands (and panicking), etc and that one simple thing was all I had to do. :p

---

### Post by SeijiSensei on 2019-10-29
The installer can throw up some similar screens depending on the packages you install.  They all work with the Tab key. It was a mystery to me, too, my first time out.

---

### Post by dee-2019 on 2019-10-29
Unfortunately although the upgrade continued after pressing tab, I've now got worse issue. Stopped completely and disconnected from WiFi, so after 5+ hrs I am left with a failed install. Stopped at 'configuring apparmor'. Didn't realise why it was taking so long. Any ideas what to do? I've reconnected wifi but it's gone, nothing happening. Is it possible to get upgrade to continue? Thanks

---

### Post by Impavidus on 2019-10-29
5 hours? I could have done 10 fresh installs in that time.

A release upgrade is a fragile process. On a clean system, it usually works. On my computer it has always worked. But I've learned that if it doesn't work, you shouldn't try and fix it. Just nuke the system and make it a fresh install.

---

### Post by dee-2019 on 2019-10-29
Yes taken that long and thought it strange. Did give warning though at start it could take several hours. Think fresh install is the only thing now, as probably won't be able to recover everything. I had a lubuntu desktop on it, as it was light weigh desktop, and before I started upgrade didn't uninstall that - so possibly why this has happened.

---

### Post by rsteinmetz70112 on 2019-10-31
Can you get to an terminal prompt or an emergency session? You may be able to salvage your upgrade. It probably failed to download and configure some pacakges.

---

### Post by dee-2019 on 2019-10-31
Yes eventually got into GRUB yesterday but choose wrong option (choose to fix downloading packages instead of the option for root), so it continued installing but got stuck even worse as I couldn't get back to recovery menu options. After a lot of troubleshooting I edited the GRUB recovery so that I got into a root directory but not terminal. I did a few things there and from there eventually got into login screen with 19.10 and ran some update commands. So is working fine.

---

