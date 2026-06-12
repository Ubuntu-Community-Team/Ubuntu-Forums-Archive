---
title: "X Windows Not Starting"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gdonwallace on 2009-10-22
When I started my laptop this morning, I spent about 45 minutes running fsck to fix a whole host of problems with directory structure errors and inode problems.  I was finally able to get my laptop to boot without any additional errors from fsck, but now X-Windows will not come up.  I get to a normal "Unix" style text login, and am able to login that way and manually start X-windows.  

Any thoughts on what may have happened?  My original thought was that fsck fixed something that did not need fixing, but if that is the case, I'm not sure what that could have been.

thanks in advance.

I just saw the following errors when I login at the text login prompt:
    -bash: [Desktop: Command not found
    -bash: Manager: Command not found
    -bash: Manager: Command not found
    -bash: XFCE: Command not found
    -bash: X-Gnome-Bugzilla=GNOME: Command not found
    -bash: X-Gnome-Bugzilla-product=gnome-bluetooth: Command not found
    -bash: X-Gnome-Bugzilla-component=applet: Command not found
    -bash: X-gnome-Bugzilla-Version=2.28.1: Command not found
    -bash: X-Ubuntu-Gettext-Domain=Gnome-Bluetooth2: Command not found

I can type "startx: after this and I am able to get X-windows to start.

---

### Post by iponeverything on 2009-10-22
do a "sudo apt-get install sysv-rc-conf"

Then run "sudo sysv-rc-conf"

and check that gdm is still set for runlevel 5.

gdm may have been damaged during your file system issues. So after a fresh boot where it comes up to a command line, take a look at:

/var/log/Xorg.0.log

You can use the package manager to remove and reinstall gdm if it is damaged. I would be more concerned about cause of the file system corruption.

---

### Post by gdonwallace on 2009-10-22
I agree, I am concerned about what may have caused the system corruption.  I have not downloaded anything from the repos in the last couple days, so I am not sure what has caused it.  Right now when I run fsck everything comes back good.

Anyway, I tried what you suggested.  I ran sysv-rc-conf and gdm was not set to run at any level; so I set it to run level 5.  Also unistalled and reinstalled gdm.  Still getting the same thing.  If you look at my first post, I edited it so that it shows the errors I am getting after I login from the text prompt.

---

