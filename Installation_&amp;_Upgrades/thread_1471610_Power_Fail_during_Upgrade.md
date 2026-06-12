---
title: "Power Fail during Upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by wide-load on 2010-05-03
The other evening I was in the lengthy process of upgrading from Ubuntu 9.10 to version 10.04.  It had downloaded all the packages and was in the process of upgrading when a thunderstorm blew in.  The power failed momentarily.  The system crashed and the installation did not complete.

The system is dual boot to Windows XP.  From GRUB when I try to boot Ubuntu the display goes dark, after a few seconds of the white Ubuntu logo. If I hit ENTER I get a flashing Cursor. I can boot to System Restore and get the Recovery Menu.  I don't know if there is something I can do from there to repair/finish my upgrade, or even revert to version 9, when I could restart the upgrade.

Can I burn a Live CD for version 10.04 and finish the upgrade?  This would salvage the settings, printer drivers, and other programs that I have installed.  If I have to make a brand new installation I have to rebuild all of the things I spent many hours getting setup.

Any advice would be appreciated.

---

### Post by squaregoldfish on 2010-05-04
From the recovery console, try:

```
sudo dpkg --reconfigure -a
```This should attempt to configure everything that's been downloaded but not installed.

(Not sure whether you need sudo from the recovery console, but it can't do any harm.)

Steve

---

### Post by wide-load on 2010-05-12
When I tried that I got an error message that said --reconfigure wasn't an option.

When I boot to System Recovery there is an DPKG option.  I tied that.  It seems to be recovering.  After a while it quits and says there is too many packages to recover (or something to that effect).  Now that I run DPKG I can login in to Shell.  However if I run STARTX that doesn't work.  Where I'm at now can I recover the installation using a LiveCD?  I happen to be running 10.04, using a LiveCD as I type this.

---

### Post by dino99 on 2010-05-12
i think its better to make a clean install again

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by squaregoldfish on 2010-05-14
I agree with dino99 - sounds as though it's time to cut your losses!

Steve

---

### Post by kansasnoob on 2010-05-14
> **wide-load said:**
> When I tried that I got an error message that said --reconfigure wasn't an option.

When I boot to System Recovery there is an DPKG option.  I tied that.  It seems to be recovering.  After a while it quits and says there is too many packages to recover (or something to that effect).  Now that I run DPKG I can login in to Shell.  However if I run STARTX that doesn't work.  Where I'm at now can I recover the installation using a LiveCD?  I happen to be running 10.04, using a LiveCD as I type this.

It's possible you could recover in a chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I'd mount and chroot the Ubuntu root partition and run:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

And possibly at any time:

```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

Note: any of those commands might provide clues as what to do next.

You may have to repeat any of the above commands depending on where things stall, so don't be afraid to rinse and repeat :)

You could actually run the same commands in terminal from recovery mode.

If you need more detailed help please post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

