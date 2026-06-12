---
title: "New Install Hangs on Load"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by Kulek on 2012-10-06
I just loaded Ubuntu 12.04 64-bit onto my machine along side Win 7 Home Premium 64-bit. When it finishes installing it goes to reboot and hangs. If I hit escape I can log in via the command line, but if I try to load X via xinit or X it fatal errors.

i5-2500k
Raedon 6970 x2
16 GB RAM

I had it installed via Wubi before, and uninstalled it before this attempt, but it was being wonky and I wanted more than 30 gigs of room.

Really, really need this to work so I can do my OS classwork at home.

---

### Post by ajgreeny on 2012-10-06
You will undoubtedly need the proprietary driver for your video card, but the first thing to do is a full update of the system.

Login at the command line you get with username and password (password will not show on screen but will be there) then use commands ```
sudo apt-get update
sudo apt-get upgrade
```
Now try booting again to see if that is any better, but if not reboot again and hold shift at boot to get the grub menu, and on the line you want to boot (usually the first line) use the E key to edit the lines of the boot stanza for ubuntu.  Go to the kernel line that ends "quiet splash" and delete those two words and replace with "nomodeset" which may get you to a GUI, even if it is the wrong resolution.  There are many other boot options to try as well as nomodeset so search around for them as well.

Now you should be able to use the "additional drivers"  item in the menu, or dash in 12.04, to get the video card driver needed.  You can even do it from the command line if you are comfortable with that using ```
sudo apt-get install <*package*>
``` but regrettably I don't know what the package name will be for you to use.

---

### Post by Kulek on 2012-10-06
Thanks for the reply. I guess swearing at it for 30 minutes had an effect and I am now logged into the GUI after getting sidetracked by my wife during a reboot.

That said while trying to update the graphics driver, thanks dev's for that nice little popup, I got a crash report very similar to the one I received while trying to load X from the command line.

I am currently running the update/upgrade instructions you posted and will then give her a reboot and try for those video drivers again.

---

### Post by Kulek on 2012-10-06
Well thanks for the help. 

I have no clue what happened for it to work, but it works.

\m/ :guitar:

---

