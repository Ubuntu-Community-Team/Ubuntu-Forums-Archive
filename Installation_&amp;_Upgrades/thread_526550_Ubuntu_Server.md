---
title: "Ubuntu Server"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by lockled on 2007-08-15
:confused:Downloaded the ISO file, burned it to a CD. Booted this on a new Dell Optiplex 320. It appears to see all the hardware just find, configures the keyboard and then proceeds to load the OS. After the install in finished and the machine reboots, all I have on my screen is a blinking dash. At this point I can't don anything I can't type anything and I don't have a GUI. What as I missing?:confused:

---

### Post by ddrichardson on 2007-08-15
I have 7.04 running on an optiplex 320 with no problems - what graphics card have you?

Try pressing CTRL+ALT+F2 and logging in at the prompt. Do:
```
sudo dpkg-reconfigure xserver-xorg
```

Answer all the questions and hopefully your card will be set up correctly.

---

### Post by Tux Aubrey on 2007-08-15
The server version does not have a gui.  It is an absolute minimal install.  If you want a gui you will have to determine which one you want and then > sudo apt-get install the package/s you want.

---

### Post by craigsharp on 2007-08-15
I feel your pain...
My first few attempts at installing ubuntu failed with the same problem, at least it seems to be.  A little information about your setup will help out.  Size partitions, motherboard, processor...  Things like that might help out.  I had problems when I left unallocated space on my hard drive.  My bootloader didnt start up, sounds like the same problem.  From what you said you don't even get to a login.  With the Server Edition, once you get it booted, all you'll have is a command prompt style interface.  Login, and type "sudo apt-get install ***-desktop"  where *** is either ubuntu or edubuntu or kubuntu... you get the picture.  But if you left empty space on your HDD, reinstall and use entire disk.  It took trial and error on my part, and then that was the one thing I changed and voila!

I hope this helps...

Craig Sharp

---

