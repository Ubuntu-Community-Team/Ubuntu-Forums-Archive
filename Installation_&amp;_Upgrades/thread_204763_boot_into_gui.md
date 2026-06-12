---
title: "boot into gui"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by shmengie on 2006-06-27
hey, can you guess how green i am at this? very! okay, the live cd is cool and wonderful. so, i dl'd the server install iso, burned it and installed it. as you can guess, the os is coming up in text mode. let's forget about the fact that i don't know how to start the gui from the cli for a sec (i'm currently perusing linux-tutorial.info)...

1) shouldn't ubuntu boot into gui by default?
2) okay, what's the command to start the gui?

btw, i did check the stickies and first 4 or 5 pages of the forum. i figure this HAS to have been asked and answered a billion times, so i apologize.

thx!

(ah, guess i should mention, this is the x86 install).

**edit**: btw, i put this in the install forum cuz this is like a 'right outta the box' kinda issue. i haven't even gotten into the os yet, so i just figured, ya know? if a mod feels this belongs elsewhere, by all means...

---

### Post by Dr. Nick on 2006-06-27
You should just be able to install it from the livecd aslong as its the new 6.06 ver, no need to download the server cd. The server install doesnt come with a gui "out of the box"

At this point you have a few options. Reload the live cd and install from that and overwrite what you have now (probably best/fastest)

Or boot into the cli and run

sudo apt-get install ubuntu-desktop 

to install the gui, but that will require more downloading.

---

### Post by FredB on 2006-06-28
Yes, but the kernel won't be the right one for a "desktop" computer.

The simplest is to install from a desktop version and install it. And do a little upgrade after installation.

---

### Post by shmengie on 2006-06-29
thx, dr. nick (and fred b.). yes, it was that simple. here's why/how i made it so difficult: while checking out ubuntu, i was also checking out kororaa. the kororaa live cd also has an install option, which doesn't work. i just happened to mix up which was which. ubuntu installs like a dream...

anyways, been busy reading linux-this and linux-that. i'll be compiling my own binaries before you know it (or whatever it is that you linux geeks do!) :D 

thx again!

---

### Post by francis.pilon on 2006-09-02
Now if we wanted the opposite: Ubuntu boots automatically into GUI and we would like it to boot in CLI.

How would that be done?

Thanks
francis

---

### Post by Herman on 2006-09-02
From your desktop, try pressing 'Ctlr'+'Alt'+'F1'... or F2, F3,F4,F5, or F6.

Then, to return to GUI mode (desktop), Press 'Ctrl'+'Alt'+'F7'.

Does that do what you want? :D
Regards, Herman

---

### Post by francis.pilon on 2006-09-02
Herman,

Thank you for your reply. 

What I actually mean is: how can I configure Ubuntu to **boot directly into CLI** and startx whenever deemed necessary rather than booting into GUI and flipping to CLI?

Cheers
Francis

---

### Post by skymt on 2006-09-02
* Install sysv-rc-conf (sudo apt-get install sysv-rc-conf).
* Run it (sudo sysv-rc-conf).
* Scroll to gdm and uncheck all the boxes. Arrow keys navigate, space bar checks-unchecks.

That's it!

---

### Post by francis.pilon on 2006-09-02
Thanks for your reply **skymt**.

Two things:

[LIST=1]
[*]when installing sysv-rc-conf, I get the following:
   "Package sysv-rc-conf is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source 
   E: Package sysv-rc-conf has no installation candidate"

   See [**i3dmaster**'s post on http://www.ubuntuforums.org/showthread.php?t=89491&page=17]("http://www.ubuntuforums.org/showthread.php?t=89491&page=17") for solution. After that, it all went well.


[*]Now, if I were to manually edit file(s) that allowed for this, what would I be looking for?
[/LIST]

Thanks again
Francis

---

### Post by skymt on 2006-09-03
Can you install bum (boot up manager)? It does pretty much the same thing as sysv-rc-conf, only with a GUI.

It's not recommended to do it manually, but if you have to, it would be: 'sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm'. See the [sysv-rc-conf project page](http://sysv-rc-conf.sourceforge.net/) and [this Red Hat page I got from Google](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-boot-init-shutdown-sysv.html) for more.

---

### Post by francis.pilon on 2006-09-04
Cool. Thanks.

Francis

---

