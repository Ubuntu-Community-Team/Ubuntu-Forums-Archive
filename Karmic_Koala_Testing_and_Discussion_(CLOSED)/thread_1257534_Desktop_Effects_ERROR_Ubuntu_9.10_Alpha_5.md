---
title: "Desktop Effects ERROR Ubuntu 9.10 Alpha 5"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by littleangelscott on 2009-09-03
G'day, I just completed the installation of Ubuntu 9.10 Alpha 5

I'm having trouble enabling the Visual Effects "Extra"

Some information about the problem:
--------------------------------------------------------------------------------------------------------------------------
These error messages after trying to enable it: "SystemError: E:Unable to correct problems, you have held broken packages." "Desktop effects could not be enabled"
--------------------------------------------------------------------------------------------------------------------------
_____@_____-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
-------------------------------------------------------------------------------------------------------------------------
Oh and I can't find xorg.conf file for some reason :(

Can someone please tell me what's going on, also how to enable?

---

### Post by overdrank on 2009-09-03
Hi and welcome, moved to Karmic Koala Testing and Discussion :)

---

### Post by VMC on 2009-09-03
It's found at "/etc/X11/xorg.conf" If not there you can crate it using ```
Xorg -configure
```

What video chip do you have. What's output of this:   ```
lspci -nn | grep VGA
```

---

### Post by littleangelscott on 2009-09-03
NVIDIA GeForce Go 7300
256MB Video Ram
----------------------------------------------------------------------------------------------------------------
Xorg -configure didn't work...

_____@_____-laptop:~$ Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by Amaranth on 2009-09-04
You've got broken packages so the system can't install the nvidia driver for you. Open up a terminal and run `dpkg --configure -a` and if it still gives you errors paste the output here.

---

### Post by Bucky Ball on 2009-09-04
Hi. Just wondering, I notice you have two beans. Do you have quite a bit of experience with Ubuntu/Linux already? If not, Karmic is definitely NOT a good place to start as it is not stable and is still 'testing'. In the Ubuntu world, latest does not necessarily mean greatest and most stable. 

If this is your first Ubuntu install, you might like to try 8.04 or 9.04 to start (8.04 oldest and stablest and long term support). If you are confident and already know your way around, disregard my post.

Just a thought. ;-)

---

### Post by littleangelscott on 2009-09-04
I don't have terminal experience... but I have been using Ubuntu since version 6
----------------------------------------------------------------------------------------------------------------------
_____@_____-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

Im not sure what that means, but how do I get superuser privilege?

---

### Post by Bucky Ball on 2009-09-04
> **littleangelscott said:**
> I don't have terminal experience... 

You're sure as hell going to get some now!! 

Is there any reason you want to use Karmic? What is the main reason, because you have a lot of tweaking in front of you. Again, Karmic is 'testing' and not really intended for person's with no terminal experience. If learning is what you are after, then get ready for a roller coaster ride on the learning curve.

If you'd rather just switch on your computer and use it to do regular computing tasks, drop back to 8.04 or 9.04. Karmic is intended  to tweak and prod for now, not for stable, production computing. If you have a spare partition, install it there and play with it, practice fixing things. But if you want a reliable computer you will be spending a long time trying to fix things with Karmic.

If you are wondering how to become super-user in a terminal, Karmic is probably not for you unless you are in for the 'big learn'. If that is the case, good for you, go for it. The community is always happy to have testers.

The answer, btw, is:

```
sudo dpkg --configure -a
```su=superuser; do=do. **Su**peruser **do** ...

:)

---

### Post by littleangelscott on 2009-09-04
I tend to use the latest versions of whatever's available. For later versions of kernels and firefox ftw :D

I tried "sudo dpkg --configure -a" and the terminal just goes to a new line? Nothing opened or showed up?

---

### Post by Bucky Ball on 2009-09-04
Read my last post again. You are currently a Karmic 'tester'.

---

