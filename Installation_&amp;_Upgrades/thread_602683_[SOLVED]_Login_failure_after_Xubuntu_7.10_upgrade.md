---
title: "[SOLVED] Login failure after Xubuntu 7.10 upgrade"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by HalSF on 2007-11-04
I just upgraded from Feisty to Gutsy on a Dell laptop, and my attempts to login to the Xubuntu desktop produced a blank orange screen and cycled back to the login screen. I successfully changed my password in terminal mode but it didn't help, and I suspect it may be some display configuration problem. Incidentally, I found the upgrade process very disappointing in terms of user-friendliness; during the upgrade installation I was asked to make a number of y/n and accept/cancel decisions that were incomprehensible to me, and I guess as a result of answering "no" in each case the upgrade somehow failed to retain my 7.04 settings on some crucial level.  A solid bummer after I had had such an easy time installing Xubuntu 7.04 from CD and configuring everything earlier this year. But now I'm completely lost. Any advice on how to proceed would be very much appreciated!

---

### Post by taurus on 2007-11-04
Press <Ctrl><Alt>F2 to get to a console.  Log in and post the output of this command from a prompt.

```
df -h
```

---

### Post by kstella on 2007-11-06
> **HalSF said:**
> I just upgraded from Feisty to Gutsy ... and my attempts to login to the Xubuntu desktop produced a blank orange screen and cycled back to the login screen.

This sounds like the problem I'm having, except it doesn't cycle back to the login screen. Or maybe I'm not waiting long enough. Anyway, I'm going to watch this thread (because people haven't responded yet to mine. :p). If there's no fix, would clean install be a good idea?

---

### Post by kstella on 2007-11-07
> **taurus said:**
> Press <Ctrl><Alt>F2 to get to a console.  Log in and post the output of this command from a prompt.

```
df -h
```

Okay, this is what I got:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             9.2G  3.7G  5.1G  43% /
varrun                236M   88K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M   72K  236M   1% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   34M  203M  15% /lib/modules/2.6.22-14-generic/volatile
/dev/hda4              18G   13G  4.9G  73% /media/hda4
/dev/hda1             9.8G  9.1G  739M  93% /windows
```

---

### Post by HalSF on 2007-11-20
I'm still not sure what went wrong but I did a reinstall from the Live CD and now everything's working fine. Thanks for the replies!

---

### Post by Iren007 on 2008-02-03
I am also having a similar problem. I get to the login screen, log in, and get the orange screen. The odd thing is that I know xfce is working because I can shut down the computer by clicking where the exit icon would be. When I press the power button on my computer, I can see my xfce desktop for a second and then the computer shuts down. By returning to the login screen, I can enter failsafe mode and I can get a terminal, but I am completely new to Linux and I have no idea what to do with it. I guess I'll go try the df -h thing...

---

