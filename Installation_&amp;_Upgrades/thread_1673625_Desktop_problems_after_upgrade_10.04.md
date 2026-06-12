---
title: "Desktop problems after upgrade 10.04"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by teddiebeer on 2011-01-22
I have upgraded the 3rd of my machines (desktop) from 9.10 to 10.04 using the upgrade/update manager.

Whilst busy with the installing section the machine locked up and I had to reboot. The upgrade wasn't fully done yet.

I then installed a new kernel for 10.04 and updated the grub loader to load the newly installed kernel (2.6.35-22).

The problem I have is that once you log into a user, the desktop (Gnome) does not display applications correctly. There is no option to X=Exit -=minimize etc at the top of the display i.e. Firefox, or Terminal etc.

There is also just one desktop and you cannot create more desktops nor open them.

I then created a new user. The same problem occurred. I then logged into the one user and whilst being logged in I logged into the other user. Now the desktop was correct, but the machine is very slow and tends to hang up.

Once you log out or re-boot the machine, it reverts to the problem.

It seems as if there is a conflict in the programs running on the desktop. You cannot e.g close any application by clicking on the "x" as there is now x on any screen. Also if you open eg Firefox and a terminal in the one desktop, you cannot type anything in the terminal, it freezes up.

Any idea how to try and fix this without doing a clean install....

---

### Post by zvacet on 2011-01-23
> The upgrade wasn't fully done yet.

Maybe you can try 


```
sudo dpkg --configure -a
sudo apt-get -f install
```

and see if that will correct your problems.

---

### Post by teddiebeer on 2011-01-23
I have tried that and there is 0 updates..

The strangest thing is that if you log into the first user the problem is there. On Firefox or any application there is no a proper heading line. There is no X or _ at the top.

Then you stay logged in and log into a second user (one I created for testing) then the correct Firefox is displayed. 

Upon restarting the machine the machine reverts to the problem display.

I have a feeling that the gnome desktop had a glitch uon the installation process.

Any help as I am a bit at wits end.

---

