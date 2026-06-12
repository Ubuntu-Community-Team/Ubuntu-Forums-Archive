---
title: "Kubuntu Alternate CD Upgrade to 7.04 from 6.10 - don't bother it's rubbish!"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by markofealing on 2007-06-03
Having upgraded 3 Kubuntu/ Ubuntu 6.10 systems (2 successfully, 1 not) off the internet, I though I would experiment on a 4th Kubuntu 6.10 PC using the Alternate CD.

Well using the upgrade command "gksu "sh /cdrom/cdromupgrade" from konsole to upgrade off the CD worked eventually after installing gksu (not standard in Kubuntu). Except it complained about some of the modules during the upgrade and aborted.

Okay, I thought dump the idea of a CD upgrade and do it from the internet. So removed the CDROM0 line from adept and ran the upgrade. It stated that 3 packages were going to be installed and 411 removed, I said okay and it promptly started to remove packages like openoffice, konsole, etc. I canceled the upgraded only to discover that KDE desktop was rather crippled.

So did a reboot and got a command prompt tried updating from the command line, it promptly removed the remaining components  (nice!). I've tried apt-get install kde but it complains that I've got missing dependencies (hundreds).  I'm very disappointed that Kubuntu is so useless when it comes to upgrading from CD. Maybe Mark Shuttleworth can tell me "How do those Kububtu users in Africa upgrade between didtros, considering high speed internet access is rather limited?", Clearly this is something which is still very much work in progress which is pretty damm scary.

I'm on the verge of re-installing from the Live 7.04 CD, does anyone know how to recover from this trashed upgrade, or is it easier to just re-install afresh,

Thanks

---

### Post by zvacet on 2007-06-03
Was your Edgy up-to-date when you start upgrade?It is very strange (to me) that upgrade from Cd doesn´t work.I know that you cheked Cd but....You can allways do fresh install with alternate CD you allready have.Sorry for not been much of help.

---

### Post by markofealing on 2007-06-05
I patched 6.10 before attempting the upgrade to minimise the risk of it going wrong. From what I can work out the CD upgraded started, but then failed and I guess the upgrade backed itself out (I would hope so!). I have a horrible feeling that when I then did the internet upgrade adept though it was updating 7.04 hence it found 3 updates and decided there was a lot of "old" packages still present so it decided to remove them which is fair enough except those "old" packages were essentially the guts of my install.

If I can I'll double check the repositories and see what version it thinks it is running!

---

### Post by zvacet on 2007-06-05
Maybe you have bad download.If you want you can chek and fix it by downloading with torrent.Direct download to the folder where your iso is and torrent will chek it.If you have any corrupted files they will be replaced with good ones.After that burn iso very slow.To chek wich version you are runing 

```
lsb_release -a

```

or in system>about Ubuntu

---

### Post by stchman on 2007-06-11
> **markofealing said:**
> Having upgraded 3 Kubuntu/ Ubuntu 6.10 systems (2 successfully, 1 not) off the internet, I though I would experiment on a 4th Kubuntu 6.10 PC using the Alternate CD.

Well using the upgrade command "gksu "sh /cdrom/cdromupgrade" from konsole to upgrade off the CD worked eventually after installing gksu (not standard in Kubuntu). Except it complained about some of the modules during the upgrade and aborted.

Okay, I thought dump the idea of a CD upgrade and do it from the internet. So removed the CDROM0 line from adept and ran the upgrade. It stated that 3 packages were going to be installed and 411 removed, I said okay and it promptly started to remove packages like openoffice, konsole, etc. I canceled the upgraded only to discover that KDE desktop was rather crippled.

So did a reboot and got a command prompt tried updating from the command line, it promptly removed the remaining components  (nice!). I've tried apt-get install kde but it complains that I've got missing dependencies (hundreds).  I'm very disappointed that Kubuntu is so useless when it comes to upgrading from CD. Maybe Mark Shuttleworth can tell me "How do those Kububtu users in Africa upgrade between didtros, considering high speed internet access is rather limited?", Clearly this is something which is still very much work in progress which is pretty damm scary.

I'm on the verge of re-installing from the Live 7.04 CD, does anyone know how to recover from this trashed upgrade, or is it easier to just re-install afresh,

Thanks

I have never had luck using the upgrade path.  A clean install seems to always work better.

---

