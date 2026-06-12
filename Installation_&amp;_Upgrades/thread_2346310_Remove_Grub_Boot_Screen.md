---
title: "Remove Grub Boot Screen"
date: 2016-12-13
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-12-13
After upgrading to UbuntuStudio v16.04 LTS, I now have a GRUB Bootloading Screen to choose OS. Never had this before and I ONLY have 1 OS. Don't know why this was put there, now I have to wait till it comes up, choose the ONLY OS on the system, to finally get past the screen to Boot and Run my computer.

Anyone know how to get rid of it so my computer just boots up to Logon Screen ???

Thanks!
:popcorn:

---

### Post by #&amp;thj^% on 2016-12-13
What dose this show:

```
gedit /etc/default/grub
```
Use the text editor you favor replacing **"gedit"** with that.

---

### Post by Rick St. George on 2016-12-13
Actually, I know why it is there. Because of the option to choose "Low Latency" or regular boot. Is it really necessary?
Here is the output requested;

> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


---

### Post by #&amp;thj^% on 2016-12-13
If you change this "GRUB_TIMEOUT=10" to "GRUB_TIMEOUT=0" then update your Grub
So you would:
```
sudo -H gedit /etc/default/grub
```
Change the value as shown above save and close your editor.. that "should" work.
```
GRUB_TIMEOUT=0
```
 
Followed by:
```
sudo update-grub
```

You can have other settings also. If you want to allow 1 second to press Shift (some computers leave you very little time between the keyboard initialization and the OS boot), make this

```
GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=0
```

or if you prefer to see the menu for 1 second:

```
GRUB_HIDDEN_TIMEOUT=
GRUB_TIMEOUT=1

```

I hope this was not a overload of information...just more options is all.:D

---

### Post by Rick St. George on 2016-12-13
Thanks! Here is what I did and how it looks;

> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


Don't see it on Bootup, but I can still access it by the "SHIFT" key.

Peace!

---

### Post by #&amp;thj^% on 2016-12-13
Cool>>> Good Job!:)

---

