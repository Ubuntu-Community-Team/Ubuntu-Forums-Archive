---
title: "Installing Mathematica = problems"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by lilla667 on 2007-01-28
Hi!


I have a copy of the 5.1 version I want to install on Ubuntu, but I have problems when the terminal asks
Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/5.1:
I press Enter, I have this answer:
Error: Cannot create directory /usr/local/Wolfram/Mathematica/5.1.
I m a new Linux user, so I don t know what I have to type... :confused: 

If I follow what s explained here:
[http://documents.wolfram.com/mathema...xAndLinux.html](http://documents.wolfram.com/mathema...xAndLinux.html)
I m not sure to know what to do either...

Hope you can help me!

Thank you very much!
Lilla

---

### Post by kidders on 2007-01-28
Hi there,

Unfortunately your link is b0rked, so I couldn't take a look.

In any case, it seems like you probably don't have permission to modify /usr/local. In Linux, normal users are not usually permitted to modify *any* system files ... a very useful security precaution. If I'm right, there are two possible solutions:

1. Run your terminal command as a user that *can* modify system files. This is _not recommended_ unless you are aware of the risks involved, and know how to assess them. (Essentially, you would be placing complete confidence in the author of the installer script/app not to screw up, or intentionally damage your system, and trusting that it has not been maliciously modified by someone else.)

2. Install Mathematica somewhere different, that you *can* write to. This would most likely prevent other users of your PC using the same Mathematica installation.

---

### Post by spvo on 2007-01-31
Did you try installing mathematica with sudo?  Thats the only way your going to be able to write to /usr/local

Basically go to the install script and run
sudo ./mathemticainstall  , or whatver the install script is.

---

### Post by raul_ on 2007-01-31
Anyway, i would consider installing it in the /home folder.

---

### Post by mikesf on 2007-02-03
Easy fix:
type
sudo -i
to get a shell with a root prompt
then navigate to /media/cdrom/Unix/Installer
then type
. MathInstaller

the reason you have to do this is because you need the "source" command e.g. the "dot" and it's tricky to get that working with sudo
if you do it this way, then mathematica will be available to every user (on your box), not just you

---

