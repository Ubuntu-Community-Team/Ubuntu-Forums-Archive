---
title: "Before-Dist-upgrade checklist"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by vexorian on 2008-04-24
So, after my failure to move to gutsy I decided it is about time to move, getdeb is already making me unable to get the newest candy since my distro is oldish...


My plan for hardy is as folows: Download the CD (So I can seed it and also reinstall later) and then do a dist-upgrade, if dist-upgrade fails :( Do a from scratch install for hardy, like I did with feisty (it was a little sad since I lost a lot of settings)


So, I'd like to increase the probability for dist-upgrade to work this is the plan right now:
- Do a complete backup
- reinstall ubuntu-desktop (cause I have removed that package some long ago)
- uninstall kubuntu-desktop and xubuntu-desktop, will get to them later.
- Uninstall virtualbox (keep the harddrives ) and nvidia's driver 

- remove third party repos ( I only got WINE and some for compiz which I no longer use)

So here go my questions:
- AM I missing something?
- What tool do you recommend me for a complete backup/ Is there one?
- How do you actually uninstall an nvidia driver you installed from their site (compiled) and not from the restricted manager?

---

### Post by Partyboi2 on 2008-04-24
To back up you could use something like timevault
[http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10](http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10)
or sbackup
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
or
[http://www.arsgeek.com/?p=637](http://www.arsgeek.com/?p=637)

---

### Post by agent8131 on 2008-04-24
A couple of things that are on my checklist:

1. Make sure that /etc/hosts has an entry for your hostname (without domain) to prevent sudo from breaking due to bug #32906.

2. If you are using apt-get or aptitude to do the upgrade use the -d flag first which downloads all the packages locally and gives you a final chance to review before starting.

3. If you use truecrypt make sure you've upgraded to version 5 or later (5.1a is the latest).

Anyone else have suggestions?

---

### Post by agent8131 on 2008-04-24
Oh, and,

4. Don't upgrade any Xen DomU's until bug #218126 is resolved.

---

### Post by vexorian on 2008-04-24
> **agent8131 said:**
> 2. If you are using apt-get or aptitude to do the upgrade use the -d flag first which downloads all the packages locally and gives you a final chance to review before starting.


Anyone else have suggestions?

Does this also allow me to resume later?

--
Got more: Uninstall .debs of software/versions that are now included in the distro, for example, I am uninstalling transmission (I used feisty so it wasn't on the repos, had to install a .deb)

---

### Post by agent8131 on 2008-04-25
> **vexorian said:**
> Does this also allow me to resume later?


Yes, you can run with -d the first time to get all the packages, if it fails, or you cancel you can just run it again.  Once the download is complete you can perform any review steps, then run again without -d and the upgrade will proceed.

---

### Post by vexorian on 2008-04-28
> **agent8131 said:**
> Yes, you can run with -d the first time to get all the packages, if it fails, or you cancel you can just run it again.  Once the download is complete you can perform any review steps, then run again without -d and the upgrade will proceed.

That's nice.

I got a problem people.

How do you actually upgrade to hardy? update-manager only got a upgrade to gutsy button... I did a sudo apt-get update and nothing.

---

### Post by Archmage on 2008-04-28
> **vexorian said:**
> How do you actually upgrade to hardy? update-manager only got a upgrade to gutsy button... I did a sudo apt-get update and nothing.

Thats normal. You can only upgrade from Feisty to Gusty. After that you can upgrade from Gusty to Hardy.

---

### Post by vexorian on 2008-04-28
> **Archmage said:**
> Thats normal. You can only upgrade from Feisty to Gusty. After that you can upgrade from Gusty to Hardy.

So, I'll have to download twice the packages, that's just ... lame guess I will have to do an install from scratch, feisty is already being discriminated package-wise, ouch.

---

### Post by agent8131 on 2008-04-28
You can upgrade straight from feisty to hardy but you have to do it by manually updating your sources.list and I would suggest upgrading via the command line to deal with any issues.  Still that's what I would do in that situation.

---

