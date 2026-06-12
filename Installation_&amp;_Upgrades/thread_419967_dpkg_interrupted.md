---
title: "dpkg interrupted"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by twygly on 2007-04-23
I get a parse error in file '/var/lib/dpkg/updates/0028' - is it safe to delete the updates directory? What then to resume from a failed upgrade?

---

### Post by Rob_H on 2007-04-23
I also got a crash during upgrade to Feisty, while it was installing the new Samba package. The system is still functional, but I don't dare reboot it. How can I retry or resume the upgrade?

---

### Post by Rob_H on 2007-04-23
I think I managed to bring mine back from the dead. First, I tried running:
```
sudo dpkg --configure -a
```
But I got an error saying the database was still locked. Since I'm using Kubuntu, I ran:
```
sudo ps -ef | grep -i adept
```
And then killed any process that looked upgrade-ish. I saw three. Then I ran dpkg again:
```
sudo dpkg --configure -a
```
It churned for a while and thankfully didn't blow up. Then, to tie up loose ends (I hope), I ran:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get dist-upgrade    # <-- Yes, one more time.
sudo apt-get -f install
sudo dpkg --configure -a     # <-- Yes, one more time.

```
The last few commands were lifted from the [manual upgrade guide]("https://help.ubuntu.com/community/FeistyUpgradesManual"). Next i held my breath and rebooted. KDE came back up! So I finished with:
```
sudo apt-get autoremove
```
Things appear to be working for me. Hope this helps you.

---

