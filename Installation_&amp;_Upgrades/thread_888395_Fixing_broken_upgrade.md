---
title: "Fixing broken upgrade"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by _jj on 2008-08-13
Whilst visiting my parents I started the online upgrade process on their computer, from gutsy gibbon to hardy heron.  Unfortunately I left before it completed and have since been informed that the upgrade froze, leaving them with no choice other than to restart the computer.  Although the computer still works (just about), it seems many packages are broken, so for example the screen resolution is completely wrong etc.

What should I tell them to do to attempt to fix this?  As usual, due to them not listening when I tell them to back up important stuff, there are some unbacked up files, that while not vital they would like to keep.
Precise instructions would be appreciated as I will be relaying them down the phone.  They should be able to cope with command line instructions if necessary.

I have already got them to try loading previous versions on the boot screen and also seen if they can see anything obvious on the update manager to try and redo the update.

[edit]solved by booting up a previous version from the grub menu and redoing all the update via the konsole as per the advice on this and several other threads

---

### Post by Partyboi2 on 2008-08-13
Try booting into recovery mode and typing
```
 dpkg --configure -a
```
then
```
apt-get upgrade
```

---

### Post by kdcoetzee on 2008-08-13
if you have problems with broken packages try

```
sudo apt-get -f install 
```

and 

```
sudo  dpkg --configure -a 
```

just check that the source.list points to the correct ubuntu version.

And to reconfigure xorg.conf

```
sudo dpkg-reconfigure xserver-xorg 
```

To fix the menu.lst of grub I am not shore. So please read a bit before you try this. I know of this command. that checks what kernels there are in you /boot folder and aplies global settings to them.

```
grub-update 
```


Hope this helps


EDIT:
Damn... the window was open for a long time. and I didn't see there was already a reply.

---

