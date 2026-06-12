---
title: "no gui after install"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by jack5656 on 2010-03-12
Hi,
I_ve just installed ubuntu 9.10 netbook remix on my netbook (medion akoya 1210). I also have Windows 7 on another partition. The installation finished without any errors, but after rebooting the GRUB loader only pops up very shortly and then I get this:

/dev/sda7: recovering journal
/dev/sda7: clean, 2419/305824 files, 84756/1220932 blocks
fsck from util-linux-ng 2.16
/dev/sda8: recovering journal
/dev/sda8: clean, 17/415334 files, 306702/16601161 blocks
* Setting preliminary keymap...
* Starting AppArmor profiles
* Setting up console font and keymap...
Ubuntu 9.10 netbook tty1

netbook login:


Apart from not getting to ubuntu's GUI, I also can't choose anything else (Windows) in the boot menu.

Can anyone help me with that? This is the first time I'm trying to use Linux, and I have no clue what I could do now...

Thanks!

---

### Post by akand074 on 2010-03-12
weird, type in your login, then your password and it will log you into terminal mode. type "startx" and it should activate the gui.. maybe troubleshoot from there. Best I can do for now, sorry I can't be of more help.

---

### Post by jack5656 on 2010-03-12
Thanks for the quick answer. I tried that and this is what happened:

The login works, but when I type "startx", it said that this was not installed, but I could install it by entering "sudo apt-get install xinit".  I did that, the installation went through, and I entered "startx" again.  Now I'm not in console anymore, but get a white box with this text:

"Xsession: warning: xrdb command not found: X resources not merged."

From there I can use the touchpad, and when I click OK I'm back at console.

:-(

---

### Post by htdw3 on 2011-03-20
sounds like your running "Ubuntu Mini Remix"
instead of "Ubuntu Netbook Remix"
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

whoops that said march 2010

---

