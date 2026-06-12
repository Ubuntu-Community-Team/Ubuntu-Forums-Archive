---
title: "keyboard not working in BIOS"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by vistanarvas on 2012-06-09
hi

i just installed Ubuntu and when i try to select it in the dual boot menu my keyboard doesn't work
but my keyboard woks when its asking me if i like to go to the boot menu en other stuff

i like to get this working and if it cant be done by installing/changing setting or something i like to know how to only boot Ubuntu and remove windows

i hope some one can help me
vista

---

### Post by codemaniac on 2012-06-09
Have you tried upgrading to get the updates of grub bootloader ?
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by vistanarvas on 2012-06-09
> **codemaniac said:**
> Have you tried upgrading to get the updates of grub bootloader ?
```
sudo apt-get update && sudo apt-get upgrade
```

im a new to all of this and very noob
what am i suppose to do with the code?

---

### Post by codemaniac on 2012-06-09
> **vistanarvas said:**
> im a new to all of this and very noob
what am i suppose to do with the code?

Sorry vistanarvas , i did not realize .

press alt+ctrl+T to open up a terminal and paste the above code .

---

### Post by vistanarvas on 2012-06-09
> **codemaniac said:**
> Sorry vistanarvas , i did not realize .

press alt+ctrl+T to open up a terminal and paste the above code .

OK but i can open Ubuntu because the keyboard doesn't work when selecting os and it goos to windows

---

### Post by oldfred on 2012-06-09
It may also be a BIOS setting which is before you boot anything. You should get a BIOS screen for just a few seconds and it should say which key to use to get into BIOS. Often del key but many vendors use other keys.

In BIOS you may have something that turns on USB keyboard & mouse. It seems both Windows & Ubuntu use their own drivers but grub uses the BIOS setting as it does not loader special USB keyboard drivers. I had this issue a couple of years ago and plugged into the ps/2 ports just for booting and then switched back until I learned I had a BIOS setting.

---

### Post by vistanarvas on 2012-06-09
> **oldfred said:**
> It may also be a BIOS setting which is before you boot anything. You should get a BIOS screen for just a few seconds and it should say which key to use to get into BIOS. Often del key but many vendors use other keys.

In BIOS you may have something that turns on USB keyboard & mouse. It seems both Windows & Ubuntu use their own drivers but grub uses the BIOS setting as it does not loader special USB keyboard drivers. I had this issue a couple of years ago and plugged into the ps/2 ports just for booting and then switched back until I learned I had a BIOS setting.

it worked thanks for the help

---

