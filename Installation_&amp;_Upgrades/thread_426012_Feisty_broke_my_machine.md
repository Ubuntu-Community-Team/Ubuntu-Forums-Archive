---
title: "Feisty broke my machine"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by johngrinham on 2007-04-28
I had edgy installed, spent a couple of hours trying to install Beryl for nvidia, finally succeeded.!
Then I made the mistake of upgrading to Feisty, about 4 hours via the net, now the best I can get is a command line, even after un-installing Beryl.
What do I need to do to regain a Gui.? Do I have to re-install edgy?
If a re-install is the only anwer then Beryl has cost me a lot of wasted time.

---

### Post by MikeDX on 2007-04-28
I would say that the easiest way is to press escape at the grub screen and select the older kernel (press down twice) and then hit return

that'll do it ;)

---

### Post by josephus on 2007-04-28
sounds like a problem with xorg crashing, maybe a problem with your video drivers or xorg.conf configuration.  are you getting any error messages after you boot up.  it's not clear from your description how far you get into your boot process, do you see the login manager, or does it crash and send you to the console?  check your system logs for error messages (/var/log/ or dmesg).

---

### Post by johngrinham on 2007-04-28
esc, down twice, exactly the same result.
Error screen is (roughly, as I'm using a windows machine while linux is down)

'Failed to start X server(your graphical interface). It is likely that it is not set up correctly.
Would you like to view the X server output to diagnose the problem'

I don't understand the output so that is of no use to me.
I'm guessing that the problem is in a file that was copied to a .back file and then modified. But I haven't found the original instructions and can't remember the name of the file.

---

### Post by josephus on 2007-04-28
post your /etc/X11/xorg.conf and also /var/log/Xorg.0.log

---

### Post by josephus on 2007-04-28
i'm guessing that if you just want to get back your gui you can edit xorg.conf

```
sudo pico /etc/X11/xorg.conf
```

and change the nvidia driver to nv in the device section. you'll lose the 3d acceleration, but at least it's easier to debug your system when the desktop is present.

---

### Post by johngrinham on 2007-04-28
Changed xorg.conf
Bingo, I have a desktop. Thank you
However I'm very hesitant about installing the nvidia driver again.
Is installing 3D always this difficult. Is there a better graphics card.?

---

### Post by josephus on 2007-04-28
i don't know too much about video cards, but i'm under the impression that nvidia cards are generally well supported.  there might be an issue related to your specific card - just do a search of your card on the forums.

you can also try using envy to install your drivers.  i'm sure if you spent a little bit more time you can get beryl working.   

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by johngrinham on 2007-04-28
Thanks for your help, I'll do some research before attempting beryl again.

---

