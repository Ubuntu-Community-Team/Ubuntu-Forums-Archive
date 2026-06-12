---
title: "No desktop menu, but an error message Gnome Power Manager"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2010-10-13
I have upgraded my EeePC from 9.10 to 10.04 and got now a black screen after I can login.
On the right upper corner, I find an error message:

> 
Install problem!
The cnfiguration defaults
for GNOME Power Manager
have not been installed
correctly.
Please contact your
computer administrator.

On the bottom bar I selected English / USA / GNOME for Language / Keyboard and Session

Above is the best I ever could come, but most of the time I only can type in the password, and it stops there, without bottom bar (language/keyboard/session), but with the Error.

What hould I try ?

---

### Post by conradin on 2010-10-13
Can you login to a terminal session with out error?
I would try to install the gnome-panel

---

### Post by ELMIT on 2010-10-13
sudo apt-get install gnome-panel
...
gnome-panel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

It is installed, but what is the 9 not upgraded????

---

### Post by ELMIT on 2010-10-13
I tried:
sudo apt-get update
(ended normal)

sudo apt-get upgrade

The following packages will be upgraded:
  erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl
....
Do you want to contuine [Y/n]   y
(Reading databse ...
dpkg: warning: files list file for package `sun-java-plugin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-xml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.31-21-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `inserv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsigc++-2.0-0c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screem' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xdg-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file forE: Sub-process /usr/bin/dpkg returned an error code (2)


It seems to be that before I have not solved above, I cannot fix anything, ... or am I wrong?

---

### Post by conradin on 2010-10-14
So, because you can use commands, you can login. Also, aside from the graphical bits not working you appear to have at least some functionality. The packages listed are not to my knowledge critical ones. I would try rebooting into the recovery mode and then try repairing packages. Or try
```

sudo dpkg -a --configure

```

---

### Post by luvshines on 2010-10-14
Can this help:
[http://ubuntuforums.org/showthread.php?t=1589730](http://ubuntuforums.org/showthread.php?t=1589730)

---

### Post by ELMIT on 2010-10-14
luvshines: File system has enough space.


conradin: I did already several times `sudo dpkg -a --configure' what just ends fine, but did not help.

In recovery mode I do not see what I could do that would improof the situation:

* resume   Resume normal boot
* clean    Try to make free space (I don't have a space problem)
* dpkg     Repair brocken packages

this runs fine, just at the end it wants to install the 9 packages, which comes back to the errors.

* failsafeX   Run in failsafe graphic mode

try to use low graphic mode for one session
login and while the login box is present I see another box saying:
A program is still running:
Unknown
Not responding

[Logout Anyway]

try to reconfiger graphic
login and while the login box is present I see another box saying:
A program is still running:
Unknown
Not responding

[Logout Anyway]

black screen with cursor ;-)

* grub Update grub bootloader

* netroot
* root

---

### Post by ELMIT on 2010-10-14
During login you get the chance to use another 

FailSafe Gnome   gives me a black screen
Gnome   gives me a black screen
Ubuntu Netbook Edition  gives me a red(brown)/grey flashing screen
[B]Ubuntu Netbook Edition 2D  gives me the desktop, but NO panel on the top
[/B]

---

### Post by conradin on 2010-10-14
hmm, perhaps you should remove the package giving you troubles. 
[http://packages.ubuntu.com/maverick/i386/powermgmt-base/filelist](http://packages.ubuntu.com/maverick/i386/powermgmt-base/filelist)

---

### Post by ELMIT on 2010-10-14
I solved a couple of things:

To get rid of the errors, which prevented to change anything (remove, add, reinstall of packages) I found that the file /var/lib/dpkg/info/linux-headers-2.6.31-20.list
was corrupt and removing it let me install all the packages that were reported could not be upgraded.

I found that if I use Ubuntu Netbook Edition 2D as my screen settings during login, I can get the icons, WITHOUT the panel and each window has no decoration (to move/close that window)

I installed xfwm4 and starting it, gave me the frame around the windows.
It is gone with each reboot, where do I set that permanent?

I started gnome-panel and got the panel.
It is gone with each reboot, where do I set that permanent?

When I try to click on System / Main Menu nothing happens.
When I click on System / Windows I get the error message:
Cannot start the preferences application for your window manager

Window manager "xfwm4" has not registered a configuration tool.

Last problem I found still is that the scrollbar on the desktop is only working with the scroll wheel on the mouse, but not with a click on the scroll bar.

At the beginning I still get the message about the Gnome-Power-Manager, which disappears after a few seconds I logged in.


Any idea how I can fix these last problems?

---

