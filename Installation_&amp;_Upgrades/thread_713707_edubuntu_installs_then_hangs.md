---
title: "edubuntu installs then hangs"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by redback on 2008-03-03
Hi folks,
New to ubuntu not new to unix.

I am a I.T. teacher trying to prove to my bosses that we can ditch windows.  I want to have a unix operating system in my school.

I am trying to install Edubuntu 7.1 on a Toshiba Satellite laptop currently running XP.

Edubuntu is not helping me.  The install seems to go ok but the machine hangs on the reboot.  Blank screen, no error messages.  I have left it overnight and it still had a blank screen.  Hit the power buttton and get a fleeting error mesage saying that DHCP something had failed.  The machine then shuts down.

The error message looks like one of the rc scripts is hanging then exiting when I hit the power buttton.

I have searched this forum and cant find a similar problem.

I have tried to break out of the hang using every key combination I can think of.  The only remedy is to power the machine off.

I performed a workstation installation and specifically stated that DHCP would be configured later.  I just want a stand alone machine right now.

Normally I would reboot  in recovery  mode, mount the rc directory, edit the rc scripts then reboot properly but I dont know what to mount in recovery  mode.

There is also the wider question.  Why should I need to hack scripts just to get the OS to install?  Give Billy Gates his due, XP is easy to install.

Any suggestions gratefully received.

Red

---

### Post by redback on 2008-03-03
Hi folks,
based on a hint from another posting I booted into recovery mode and tried running startx.
The laptop hung dead as a dodo.
The problem on the other posting was about a laptop screen hanging when trying to run startx.  Looks like I have the same issue.
I am currently installing a different laptop.  Same model but different machine.

I am a clever computer geek.  Been doing this a long time.  Not impressed so far.  

Would I get a clean install going back a release?

Red

---

### Post by jrusso2 on 2008-03-03
It might be helpful to post some error messages or symptoms you have gotten

---

### Post by redback on 2008-03-04
Hi jrusso2, thanks for the interest,
I have posted all the info I can. 

The install looks like it has gone ok.  I then reboot the machine, no messages of any sort.  The disk light flashes and then nothing.  No error messages.  The machine just hangs dead.  No response from keyboard. 

The only way to get a response of any sort is to hit the power button.  Then the machine SOMETIMES flashes a message which says something about dhcp failed.  It looks just like a failed rc script.  The machine then goes through an orderly shutdown with normal messages on screen.

It looks like the machine has booted properly but the screen is dead.  This hypopthesis is supported by the other posting.

My idea was to search through the rc scripts and put exit 0 in all scripts which relate to dhcp just to get the thing to boot.  I now suspect that wont work as I suspect there is a problem with X and toshiba laptop screens.
I installed again and specified the lowest possible screen resolutions during the install.
In any case I cant go to my boss with this as a solution.  He would laugh me out of his office.

Red

---

### Post by jrusso2 on 2008-03-04
I don't know almost sounds like a hardware issue or an incompatibility.  Was it able to run the live cd?

Does this laptop by any chance run ATI graphics chip?

Maybe try another distro and see if that helps maybe something not based on Ubuntu.

Just as a trouble shooting step.

---

### Post by redback on 2008-03-05
hi jrusso2,
I tried xubuntu, it failed too.  So did gos, suse and fedora.

I tried xubuntu installation on slightly newer laptops and it worked perfectly.

I can only conclude that the older laptops will not run linux.  I suspect the video hardware is just too old so I wont be flogging that dead horse any more.  I will try to impress my boss on the newer machines.

The old laptops are toshiba satellite L100 machines.  1.2 GHz Celerons, 256 mb memory and onboard graphics.

Thanks for all help.  Much appreciated.

Red

---

