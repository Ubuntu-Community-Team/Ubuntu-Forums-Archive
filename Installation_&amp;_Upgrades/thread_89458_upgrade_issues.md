---
title: "upgrade issues"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Treebeard on 2005-11-12
Hello,

I was upgrading my laptop from hoary to breezy, but before it was finished, my battery was dead (much sooner then expected :oops:). 

Obviously I had to fix some packages that where broken. I have some experience with fixing broken .deb packages.. but still something unexpected happened.

First I removed all the x-based packages (I use aptitude instead of apt-get):
1/ aptitude remove ubuntu-desktop
2/ aptitude upgrade
3/ apt-get --reinstall install ubuntu-desktop
4/ all the packages where installed
5/ reboot

After reboot gdm started normally, but I couldn't type anything. The only keys that worked where ctrl+alt+backspace (restart gdm).
I checked /var/log/gdm/* entries and saw following error messages:
...
expected keysym, got XF86_Switch_VT_1: line 8 of xfree86
...
> Warning:          Multiple interpretations of "NoSymbol+AnyOfOrNone(all)"
>                   Using last definition for duplicate fields
...
expected keysym, got XF86_Switch_VT_1: line 51 of pc/pc
..etc.

Kinda like [http://lists.ubuntu.com/archives/ubuntu-bugs/2005-June/062439.html](http://lists.ubuntu.com/archives/ubuntu-bugs/2005-June/062439.html)

I then reinstalled xlibs-data, but it didn't help.
Anyone with similar experiences? Or should I reinstall breezy from scratch? ](*,)

Thanks in advance!

---

### Post by teaker1s on 2005-11-12
grub hit esc and run recovery then
sudo dpkg-reconfigure xserver-xorg
it will allow you to reconfigure keyboard screen mouse

---

### Post by Treebeard on 2005-11-12
[QUOTE=teaker1s]grub hit esc and run recovery then
sudo dpkg-reconfigure xserver-xorg
it will allow you to reconfigure keyboard screen mouse
[/QUOTE]

Thanks for the advice. I already tried a reconfigure, without luck :(

I also tried using the 'keyboard' driver instead of 'kbd' in /etc/X11/xorg.conf. This results in a change of resolution with every key stroke..

---

