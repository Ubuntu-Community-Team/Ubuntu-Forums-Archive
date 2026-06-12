---
title: "Live CD brings me to blank screen with nothing but a mouse cursor?"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by nawk168 on 2007-01-29
I am trying to install Ubuntu on my Toshiba Satelite M45 S265 laptop but I ran into some problems:

I tried running the Ubuntu 6.10 Live CD and it loads everything fine until I get to a blank peach colored screen with nothing but a mouse cursor. The cursor moves around but there is nothing to click on. Right clicking does not do anything.

I don't think it's the display settings because when I exit out of this blank screen with Ctrl+Alt+Backspace, it brings me to a Ubuntu login screen which displays fine. When I try to log in though, it brings me to the same blank screen. I've tried using the Default option, Gnome, Gnome Failsafe, and Terminal Failsafe. They all bring me to the same blank screen with a cursor except for the failsafe ones which open up a box.

If the Live CD can't run on my computer, does that mean this OS would not work on my computer without a lot of modifications? I am a windows user and don't know much about Linux. I thought Ubuntu would be user friendly enough for me to use.

---

### Post by kebes on 2007-01-29
Hmm... that's quite strange. Chances are that the system will work once installed. Linux (like Windows) can sometimes be weird to install.

Something else to try at this point would be different versions of the install disk. If you go to the Ubuntu download page:
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

And pick a mirror location, you should see a link for "Other Installation Options."

From that link, scroll down and you'll see there's an "Alternate Install CD". This is a text-based installer (still pretty easy to use), and works better in some cases.


Another possibility would be to install Ubuntu 6.06 (Dapper Drake) instead of Ubuntu 6.10 (Edgy Eft).

---

### Post by land0 on 2007-03-30
[LIST=1]
[*]When the boot disk first starts press F6
[*]A list of options will come up
[*]add acpi=off before the two hyphens example--> acpi=off --
[*]Now hit the enter key
[*]Now it should boot into Ubuntu a-live 
[/LIST]

---

### Post by pball on 2007-04-03
Had same problem - followed suggestion of land0 -this indeed works
curious as to what fix does

---

### Post by WiredPig on 2007-05-21
I have my M45-S265 set to boot with pci=noacpi added to the boot command line.

Glenn

---

