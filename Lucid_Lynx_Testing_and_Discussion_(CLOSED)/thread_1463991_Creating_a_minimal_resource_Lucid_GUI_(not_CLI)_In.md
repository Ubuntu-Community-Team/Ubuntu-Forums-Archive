---
title: "Creating a minimal resource Lucid GUI (not CLI) Install"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-04-27
...To get the basic OS and maximum functionality of desired applications while using the least hardware (disk space and RAM), and also to keep system temps down!

  
There are a few posts on this - for netbooks and older systems, and in reading them, here's what I have found - comments and ideas? 

[I]use "Minimal Install" option when installing to get ans then Apt-get install at CLI:
gnome-core gdm gnome-utils gnome-system-tools x11-xserver-utils
[/I]then:[I]
plymouth-x11 plymouth-theme-ubuntu-logo plymouth-label gnome-themes-selected
[/I]then:[I]
gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver
[/I]then:[I]
network-manager-gnome nm-applet startupmanager
[/I]then:[I]
firefox synaptic
[/I]and other addidional applications as desired.

Haven't been able to try this but will be playing around with it next week after the final release is out.

---

### Post by Irihapeti on 2010-04-27
I've found that "aptitude -R" is a very useful command.

It doesn't pull in all the unrelated files that are more suited to a full install. Very handy if you want basic LXDE or xfce4. You can then decide which other programs you want instead of having that decision made for you.

I've got an install based on Openbox and a few programs that I use regularly. It's on my eeePC 900.

---

### Post by emarkay on 2010-04-28
Thanks - will be away for a few days - was just wanting a confirm that the above post of mine will give a  minimal install with GUI to then add from Synaptic what additional; I want.

---

### Post by k3lt01 on 2010-04-29
I did my server last week with the Lucid mini CD. Apart from having to set DNS it was absolutely flawless. I'll probably do my laptop with the mini install this weekend and only install things that are an absolute necessity.

---

