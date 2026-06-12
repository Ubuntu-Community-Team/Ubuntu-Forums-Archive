---
title: "edgy upgrade"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by elmugrat on 2007-02-23
Is upgrading to 6.10 from 6.06 a major upgrade (like Mac OS X 10.2 to 10.3) which will wipe all my files and settings, or is it a smaller upgrade (Mac OS X 10.3.8 to 10.3.9) that will maintain my existing files and preferences?

---

### Post by LotsOfPhil on 2007-02-23
It might not perfectly preserve all settings and preferences (I seem to remember losing my custom splash screen) but it definitely won't delete your files.

---

### Post by jimbren on 2007-02-23
It depends on how you do it.  You can do a dist-upgrade, which will download all the edgy packages and do an upgrade inline, or you can do a fresh install from a CD, which would wipe most everything and reinstall it.  If you have /home on it's own partition, you can specify that that partition not be touched and preserve all of your settings. 

Either way, it is an excellent idea to do a backup of your /home directory beforehand, if you can.  I did both upgrade methods on my laptop just for fun, and they went off without a hitch.  (I have /home on a seperate partition though, and didn't have to restore anything.)

To upgrade without the CD, here's what I did from the terminal:
1) Make sure your system is completely up to date and everything is working properly:
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

2) Then make sure you have your complete desktop environment installed.  (I saw this recommendation on [debianadmin.com ]("www.debianadmin.com")and I think it saved a lot of headaches.)

```
sudo apt-get install ubuntu-desktop
```
(I use Kubuntu, so I replaced 'ubuntu' with 'kubuntu' in the above line.

3) Now you want  to edit your sources.list using your favorite text editor...mine is nano.
```
sudo nano /etc/apt/sources.list

**If you use gedit or some other graphical editor to edit your sources.list, make sure you invoke it properly with *gksudo***.

And replace every occurance of *dapper* with *edgy*.  Save the file.

4) Now you're ready for the upgrade.

[CODE]sudo apt-get install dist-upgrade
```

It will take about 30-45 minutes to complete the upgrade.

5) Now double check that the process was finished properly and you won't get any surprises when you reboot.
```
sudo apt-get -f install
```
and
```
sudo dpkg --configure -a
```

You're done.  Reboot, and you're in Edgy.

Hope this helps.


jimbo

---

### Post by elmugrat on 2007-02-26
I did the upgrade yesterday, and everything went fine after I commented out an extra repository.  The only thing that seems slightly messed up is the boot progress page.  Instead of a smooth progress bar and information, all it shows me is a fuzzy black and white "Ubuntu" and a broken up progress bar.  I can live with it, but having the  real boot display would be nice.  Thanks for the help!

---

### Post by Irony on 2007-02-27
Yes I have this to. Is there a way to sort this and also can I make it scroll a list of what is loading like in Dapper;


[PHP]title		Edgy hda12
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.17-11-386 root=/dev/hda12 ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot[/PHP]

---

### Post by Irony on 2007-02-27
Apparently deleting the word 'quiet' will give me a verbose/text mode - not quite what I had in mind, I wanted it like Dapper but I'll see if it actually works first.

---

### Post by Irony on 2007-02-28
Changing the kernel section had the desired effect;

[PHP]kernel        /boot/vmlinuz-2.6.17-11-386 root=/dev/hda12 ro splash vga=794[/PHP]

I thought it would be entirely text but the progress bar is still there but text scrolls underneath it like in Dapper.

The word Ubuntu is however still black and white outline and split into 2 bits Ubun and tu!

---

