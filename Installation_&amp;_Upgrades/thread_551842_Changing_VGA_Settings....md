---
title: "Changing VGA Settings..."
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by Seelei on 2007-09-15
Hello!

I've been attempting to install Ubuntu on my computer, and am being blocked with a blank screen. I'm pretty sure that it is some VGA/Monitor issue, as I have the same problem loading the live CD, unless I change the VGA settings with the UI. Unfortunately, there is no such option loading Ubuntu itself. Is this changed in grub? If so, what is the command or process?

Thank you!:guitar:

---

### Post by Pumalite on 2007-09-15
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver. Then: startx

Ctrl+Alt+F1 to get a command line.

---

### Post by w4ett on 2007-09-15
From the Grub menu select recovery mode....this will get you into a command line interface.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

The next question is: what video card/chipset are you using?

Good luck!

---

