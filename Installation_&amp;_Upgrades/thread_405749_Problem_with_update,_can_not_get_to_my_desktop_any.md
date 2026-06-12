---
title: "Problem with update, can not get to my desktop anymore"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by darkzom on 2007-04-10
Hi everyone! 

This is my first post as this is the only problem I have not managed to fix myself by looking at forums. I'm new to linux and been around 3 months now with 6.10, everything flawless, except for a thing that happened to me yesterday;

I updated some progs as the flashing icon notification that appears on the tray was already one week flashing, I usually try to remember which programs am I updating but this time as it was before going to sleep I failed to check it. Everything fine as long as I remember and then shutted down the pc to sleep some hours...

Now I cannot boot as the x server crashes when booting, once you see the screen which shows that nautilus, etc... is loading, it crashes and keeps trying to boot back, bringing the login screen, and once you login it happens the same again.

Tried to login in recovery mode, nothing, it keeps crashing.

I talked today with a friend and he told me that the same is happening to him, and that he thinks that is an update he installed 2 days ago which involved gnome. I don't know.

Is there any way to reverse this update, or to fix this problem? I do not know which config file should I try to modify or if it happened to somebody else, I searched on the forum but found nothing, which is strange...

Please, I would be very grateful if you could help me, as I am trying really hard to learn how to use linux and would like to solve this in a nice and elegant way, as I suppose there is some way to fix this instead of reinstalling.

Best regards,

---

### Post by aa.ivanov on 2007-04-10
Hi!

You can see what packages you have installed/deinstalled in /var/log/dpkg.log

But if your X server is crashing you should check what's going wrong with it. It's log file is /var/log/Xorg.0.log Look for lines that start with '(EE)' code.

If you can see the login manager, but after login X server crashes and X.org log file is useless - most likely it has something to do with GNOME or Nautilus. You can try logging in from a text terminal (recovery mode should be ok) and issue 'startx' command. It'll try to load your desktop. It will most likely crash, but you'll be able (eventually) to see some error messages when it drops you back to text mode.

If none of this helps - let me know so I can give this issue a bit of thinking ;)

---

### Post by shavenlunatic on 2007-04-10
i usually do:

```
 sudo apt-get install --reinstall nvidia-glx 
```

or if you have installed envy

```
 envy 
```

and select option 1 :)

usually gets me back to my desktop after a "kernel / x / anything else that screws it up" update

---

### Post by darkzom on 2007-04-10
Thanks all! I will try some of those things as soon as I get home this night.

I have been looking around the forums and seems some people had problems with their start on gnome which are similar to mines... I wonder if adding another user would get me to the desktop.

Just for you to know, it might help, i have the latest nvidia propietary drivers from their webpage and beryl... I will try with reinstalling the driver (which I suppose it's the same as option 1 of envy), and then, if not, I wonder if removing beryl might help... 

btw, thanks for letting me know where to find for installed packages!!

Anymore ideas will be welcomed

---

### Post by shavenlunatic on 2007-04-10
> **darkzom said:**
>  if not, I wonder if removing beryl might help... 


unlikely, but once you get back to your desktop you will have to add the changes to xorg.conf to get beryl up and running again :)

---

### Post by AkiraXXX on 2007-04-10
I had the same issue.  I ended up removing Beryl.  I don't know if Beryl is the cause or if it is the symptom.  Boot up into a recovery mode and from the terminal go to your home directory.  Change to your .config directory and look in the autostart folder and remove any Beryl files.  After a reboot, you should be set.  

Again, I don't know if this is a Beryl issue or if it is a driver issue that is picking on Beryl.  Are you running an nVidia card?  If so, it may be a driver issue caused by a recent update.

Good luck.

---

### Post by bulldog on 2007-04-10
Don't think it's Beryl which make your ubuntu crash.
If Beryl crashes it should go back to metacity by default.

Recovery shouldn't even use Beryl.
But I have no idea what it is.

---

### Post by shavenlunatic on 2007-04-10
i stand by my original decision and a driver re-install is the way forward.. (but what do I know, im just a nub :D )

---

### Post by bulldog on 2007-04-10
Did you get a kernel update among the others?
If yes try to boot an older kernel.

---

### Post by darkzom on 2007-04-12
I am going to try right now, I will let you know what happens, gonna try this in order:

1) Reinstall latest nvidia drivers
2) If not, I will try creating another user, so to make sure it is not any config fault (beryl, etc)
3) Dunno, but VESA mode in xorg.conf together with booting another kernel (as the nvidia driver is compiled for the specific kernel)

Will let you know ;)

Thx ^.^

---

### Post by darkzom on 2007-04-12
K, perfect !!!!!!
Thanks a lot!!! This is what I did:

Sought for var/log/ file on dpgk to actually see that x was updated, so I thought that somehow it conflicted with beryl, gnome, or whatever, then decided to reinstall the nvidia driver and everything worked perfectly !!!

Thanks, really, now I know where to find logs for all sort of programs and know some little things that didn't yesterday.

That is why I just love linux, you can't stop learning!!

Thx again, greatly appreciated ;)

---

### Post by briangig on 2007-04-16
reinstalling glx fixed this for me...

this is what I hate about linux (windows suffers from the same problem).  Don't push updates that break systems...

---

