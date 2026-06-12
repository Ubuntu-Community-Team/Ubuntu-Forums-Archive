---
title: "Ubuntu Dapper/Edgy will not install"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by stooo on 2007-03-14
I'm having problems getting Ubuntu dapper or edgy to install on my Asus Laptop. I've tried the standard install CD as well as the alternatives for both relesaes.

On selecting install, install text mode, or OEM install I get loading  vmlinuz, initrd.gz then just get a black screen with a flashing cursor in the top left - it can sit in this state indefinitely!

I've read about problems with the ATI 200M, but they seem to relate to users with ubuntu already installed, obviously this isn't relevant to me.

Any suggestions or ideas?

Thanks.

---

### Post by zvacet on 2007-03-14
Try ctrl+alt+backspace and if it doesn´t help then ctrl+alt+F1
```
sudo /etc/init.d/gdm start
```
and if you see no progress type
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by stooo on 2007-03-14
Sorry if this is a stupid question, but how can I do what you specified if other than the installer menu screen, and the blank screen with flashing cursor I have no 'Linux' command line to be able to use sudo.

---

### Post by louieb on 2007-03-14
Have you tried some of the common boot options?
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
A larger list of cheat codes can be found on the Knoppix site. They work for Ubuntu too.

---

