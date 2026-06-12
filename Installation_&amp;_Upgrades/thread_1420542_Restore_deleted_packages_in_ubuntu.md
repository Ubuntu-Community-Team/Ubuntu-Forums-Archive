---
title: "Restore deleted packages in ubuntu"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by gayavasu on 2010-03-03
Hi,

I am using Ubuntu i386 and I deleted all the packages by mistake. I actually wanted to uninstall one package from the synpactic manager but by mistake all packages got deleted. So I am not able to boot Ubuntu in gui.. I am also not able to connect to the internet because the network driver packages also got deleted. Can anyone suggest how I can restore the pckages?

---

### Post by OrangeCrate on 2010-03-03
> **gayavasu said:**
> Hi,

I am using Ubuntu i386 and I deleted all the packages by mistake. I actually wanted to uninstall one package from the synpactic manager but by mistake all packages got deleted. So I am not able to boot Ubuntu in gui.. I am also not able to connect to the internet because the network driver packages also got deleted. Can anyone suggest how I can restore the pckages?

Assuming that you clicked "All" to return to the full list of packages, the only thing I can think of doing, is to boot a Live CD, and reinstall.

Someone might come along and offer another solution, but personally, I can't think of what that might be.

---

### Post by nothingspecial on 2010-03-03
Did you try and remove evolution?

Get a wired connection

```
sudo ifconfig eth0 up
sudo dhclient
```
```

sudo apt-get install ubuntu-desktop
```

---

### Post by gayavasu on 2010-03-03
Hi, 

@[nothingspecial]("http://ubuntuforums.org/member.php?u=491516")

Those 2 commands worked like magic....!!!!
Thanks very much.. You have been of great help

Just a small change.. sudo apt-get -f install did not work with the error-
"Unmet dependencies", so I used upgrade instead of install 

Thanks,
gayavasu

---

