---
title: "Timeshift missing on new install"
date: 2018-09-15
forum: Installation &amp; Upgrades
---

### Post by Lewis Balentine on 2018-09-15
I have been running Linux Mint with the Mate desktop Environment for several years. 

Every year I come back and check out the latest version of Ubuntu Mate, Testing applications, UI, Hardware etc. The past couple of days I have been working with "ubuntu-mate-18.04-desktop-amd64.iso" and I am pleasantly surprised. So I ran a backup, installed a new HardDisk in My laptop and installed it as my OS ...

Wait a minute where did "timeshift" go? Complete missing ...
no worries I can install it with "apt-get install timeshift" ... 
uhhhhhhhh, no I can not. Seems it no longer exist in the Ubuntu distribution.

Well I need to restore my users files anyway so I run the menu item "backups" (*which just happens to be deja-dup*).
It looks and operates completely different and will not recognize my backup files (*which is "2018-09-14-2344-backup.tar"*).

I will admit to getting old and senile (*and I was not too bright to begin with*) but I really believe something funny is going on.

---

### Post by Lewis Balentine on 2018-09-15
oops  ...  the back up was made with "**mintbackup**" ... too much going back and forth between distributions.

---

### Post by deadflowr on 2018-09-15
timeshift has never been in the Ubuntu repositories.
fyi

---

### Post by Lewis Balentine on 2018-09-15
My apologies ... I thought that I had read that is had been included in the 18.* releases.

---

### Post by deadflowr on 2018-09-15
> **Lewis Balentine said:**
> My apologies ... I thought that I had read that is had been included in the 18.* releases.

On mint, maybe.(?)
They do have their own repositories beyond the Ubuntu repositories they use.
So maybe they package it there.

(5 seconds later...)
Ah, found it, yes it's in mint's repos:
[http://packages.linuxmint.com/search.php?release=any&section=any&keyword=timeshift]("http://packages.linuxmint.com/search.php?release=any&section=any&keyword=timeshift")

---

