---
title: "How to boot live cd in vesa mode ?"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by ViereinhalVs on 2012-03-03
Heho,

I know this thread is old, but I have exact the same problem here.

I started from an Ubuntu Persistent LiveCD 11.10 (USB) and reach the "Installer Boot Menu"

A normal boot won't work, because my monitor has the "out of range" message after I choose anything in the boot menu.

So I hit the TAB-Key to see the boot params:

```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot-casper persistent initrd=/casper/initrd.lz splash --
```I changed it to
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot-casper persistent  initrd=/casper/initrd.lz vga=791 --
```as well to
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot-casper persistent  initrd=/casper/initrd.lz xforcevesa --
```but it doesn't solves my problem.

Any othr ideas?

thanks in advance
Michael

---

### Post by overdrank on 2012-03-03
Hi and welcome, I have moved your post to it's own thread. No need to revive a two year old thread. :)

---

### Post by mastablasta on 2012-03-03
have you tried the nomodeset option?

---

### Post by ViereinhalVs on 2012-03-03
> **mastablasta said:**
> have you tried the nomodeset option?
Nope,

how does it work?

thanx
Michael

---

### Post by ViereinhalVs on 2012-03-03
You are talking about
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot-casper persistent  initrd=/casper/initrd.lz nomodeset --
```
Doesn't work ... :(

A lot of logs, but than a reboot ...

Michael

---

### Post by MAFoElffen on 2012-03-03
> **ViereinhalVs said:**
> You are talking about
```
/casper/vmlinuz noprompt cdrom-detect/try-usb=true  file=/cdrom/preseed/ubuntu.seed boot-casper persistent  initrd=/casper/initrd.lz nomodeset --
```Doesn't work ... :(

A lot of logs, but than a reboot ...

Michael
Michael,

Here is what I do- Mostly on Servers where they only have VGA Graphics or for older Desktops...  add the vga switch as 
```

vga=268

```Which is VESA, but not recognized in Linux. It displays an error message, but offers instead a text menu with display options in VESA VGA modes. Select a basic option (will be type a letter from the menu, then <Enter>).

Hope this info helps.

What video chipset do you have?

---

