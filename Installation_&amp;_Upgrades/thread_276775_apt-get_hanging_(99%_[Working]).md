---
title: "apt-get hanging (99% [Working])"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by tmasman on 2006-10-13
I installed a fresh LAMP server (Ubuntu Dapper Server CD).

It seems to be working fine (apache is working) & I can ping external sites... (Those are just an example of what I know is running/working)

Anyhow, I'm still very green in the Linux world & I'm trying to install the desktop.
So I did:
> sudo apt-get update
sudo apt-get install ubuntu-desktop

It downloaded all the packages, but every now & then I'd see a message :
> hdc: drive not ready for command

When it downloaded the last package, it stopped & has been hanging with a message of:
> 99% [Working]
And every now & then it will through up the "hdc" error...

[LIST]
[*]Anybody got any ideas?
[*]Is there any way to make apt-get use the packages it just
downloaded instead of trying to download them all over again?
[/LIST]

TIA for any help.

---

### Post by littlefat on 2006-12-05
I met exactly the same problem as you. I use base installation of Ubuntu server instead of LAMP Server. However, I tried to install xubuntu desktop by using
"sudo apt-get install xubuntu-desktop",
,then the installation process started, but everything just stopped when "99%[working]" is displayed when it was trying to 
"Get:454 [http://**.archive.ubuntu.com](http://**.archive.ubuntu.com) dapper/main xubuntu-desktop 1.32 [8232B]".
I tried a second time, but the same error happened again.
Anyone who has any ideas about this?

---

### Post by littlefat on 2006-12-06
Hi, I already solved the problem by updating first before trying to install the desktop.
"sudo apt-get update"

---

