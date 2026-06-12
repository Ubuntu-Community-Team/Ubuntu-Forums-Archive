---
title: "Installing windows after installing ubuntu"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by Souljah on 2007-01-21
Hi guys,

Ok I'm on ubuntu and I have been on it for a very long time. I want to reinstall windows. Now I know you guys say it's not a good idea to install xp after installing ubuntu as that overwrites the GRUB boot loader. What I need is a guide or some help in getting ubuntu back after installing windows xp? Thanks.

Ryan

---

### Post by bulldog on 2007-01-21
If you want to reinstall GRUB after your windows install,just use the live cd.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by Souljah on 2007-01-21
Thanks, I'm going to bookmark this.

---

### Post by Sef on 2007-01-21
Also check this out:  [Recovering Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing Windows.

---

### Post by Souljah on 2007-01-21
> **Sef said:**
> Also check this out:  [Recovering Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing Windows.

I was also looking for this link. Thanks a lot man.

---

