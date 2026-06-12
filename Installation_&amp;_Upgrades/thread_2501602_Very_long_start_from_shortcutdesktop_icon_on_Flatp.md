---
title: "Very long start from shortcut/desktop icon on Flatpak, Ubuntu 24.10"
date: 2024-10-14
forum: Installation &amp; Upgrades
---

### Post by inzaghi89 on 2024-10-14
Hello,

Since I've updated my Ubuntu from 24.04 LTS to 24.10 I see very annoying issue regarding to latest Firefox (131.0.3) installed via flatpak.

The issue occurs while I tried to start firefox via flatpak icon (desktop or program menu). When I take an action to start firefox it takes 30 seconds to few minutes sometimes to take start.

What is interesting: when I start browser from the terminal (flatpak run org.mozilla.firefox) - it works without any problem and starts immediately.

I've also tried solutions from this thread [https://support.mozilla.org/bm/questions/1442927](https://support.mozilla.org/bm/questions/1442927) - no success.

Before update all works well. Also I'm using thunderbird (on flatpak too) and it starts ok.

---

### Post by 1fallen on 2024-10-14
This worked for me, but your MMV
```
mv ~/.local/share/flatpak/  /flatpak-OLD
```
You need to reboot now.
now check if there is a flatpak folder.
```
ls ~/.local/share/flatpak
```
Now run this:
```
sudo flatpak repair
```
Now open firefox.

---

### Post by ubfan1 on 2024-10-14
Are you running xorg or Wayland (choice made at login with the gear icon)?   Launchpad bug 2042301 causes some delay (30-45 seconds) on displaying the contents of some windows (or even starting the first terminal).  Wayland does not display the problem, only xorg.

---

### Post by inzaghi89 on 2024-10-15
> **1fallen2 said:**
> This worked for me, but your MMV
```
mv ~/.local/share/flatpak/  /flatpak-OLD
```
You need to reboot now.
now check if there is a flatpak folder.
```
ls ~/.local/share/flatpak
```
Now run this:
```
sudo flatpak repair
```
Now open firefox.

I've already done something like that - fully unistalled all flatpak packs 
```
flatpak uninstall --all
apt purge flatpak
apt autoremove
```

After reboot installed again. No success. Same issue only with Firefox and still starts normally from terminal 

> **ubfan1 said:**
> Are you running xorg or Wayland (choice made at login with the gear icon)?   Launchpad bug 2042301 causes some delay (30-45 seconds) on displaying the contents of some windows (or even starting the first terminal).  Wayland does not display the problem, only xorg.

I'm on Wayland.

---

### Post by 1fallen on 2024-10-16
"Something like that" is not the same as I suggested, and I'm on Wayland now as well.

---

### Post by inzaghi89 on 2024-10-16
I've also done what you've mentioned. Doesn't help. Finally I've removed firefox from flatpak and install from mozilla repo. I'm not the only one with this issue [https://github.com/flatpak/flatpak/issues/5968#issuecomment-2416816126](https://github.com/flatpak/flatpak/issues/5968#issuecomment-2416816126) but didn't tried other browsers.

---

