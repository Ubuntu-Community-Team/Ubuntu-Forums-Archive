---
title: "Can't login to GNOME after upgrading"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by WalkerPL on 2010-05-04
Yesterday I did a successful upgrade to 10.04. Today, after a few hours of using and a few reboots, when I provide my password in GDM, the screen turns black and gets me back to the GDM. The same with recovery mode.

When I turn onto the terminal I can't see any letters but a bunch of blurred lines on the top of the screen. In recovery mode the terminal works properly.

GDM also works properly. Neither graphics, nor the resolution has changed.


What can cause this problem and how to find a solution?

---

### Post by WalkerPL on 2010-05-05
I still haven't found any solution and don't know what causes the problem. Would you please point me what should I check or where to look?

Is this a matter of drivers or GNOME?

---

### Post by japsai on 2010-05-05
There's some other people with similar problems, such as me:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641")

I don't know what to do yet either, sorry.

---

### Post by WalkerPL on 2010-05-05
> **japsai said:**
> There's some other people with similar problems, such as me:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641)

I don't know what to do yet either, sorry.

I've tried everything that I've found here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/574641)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/555263](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/555263)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/494394](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/494394)

But none of the methods has worked. Startx from tty gives the same  result. I don't have to change permissions from 500 because it is  already done. I've even created a new user, but still cannot login.

---

### Post by WalkerPL on 2010-05-06
I'm still fighting with the problem. It seems like it's not a driver issue, nor graphics or GDM (I've browsed through logs and haven't found anything suspicious). But if not, so what it is?

What surprises me is that I can't see any info that should be displayed after GRUB and before GDM. There are only blurred, horizontal lines at the top of the screen.

I really would like to come back to my Ubuntu because I cannot stand Vista anymore. :) If I can't fix it, what to do? I don't want to lose all my settings, installed apps, etc . by reintalling the system.

---

### Post by bitter_mike on 2010-05-06
I had a very similar similar problem that I've managed to fix on my laptop. When I got to the logon screen and logged it, the screen would flash black, then bring the logon screen back up and it would be stuck this way. I did not see anything like the blurred text you're talking about, but the login loop thing is right on the nose. Check and see if at your logon screen there is still a menu for selecting the session in addition to the language and keyboard menus on the bottom. On  my computer, that menu had disappeared. 

Here's how I fixed it:

First, I booted into recovery mode and from the terminal, I used apt-get to remove GDM completely, then I re-installed it with apt-get (you'll have to connect to a network via ethernet cable and use dhclient from the command line to get an internet connection). Just doing this changes things so that when I logged in, I just got a little xterm window.

Next, I used apt-get to install the gnome-session package, which was evidently not installed. This restored my normal desktop at logon except there was an error with loading one of the applets which I fixed by installing the package indicator-applet-session. At this point, everything was back to normal. 

There's a possibility that at the same stage as when I re-installed GDM I also re-installed AppArmor, but I can't remember, so if reinstalling GDM doesn't do it, reinstall that as well.

Good luck.

---

### Post by WalkerPL on 2010-05-06
Hey, you saved me! :)

I just had to install gnome-session which was removed when I purged evolution before the last working reboot. :) Everything works! :)

---

### Post by benplanet on 2010-05-30
unbelievable!!! waas unable to login to my desktop for hours.... i executed this simple command from tty:


```
sudo apt-get install gnome-session
```

I don't know how that got uninstalled... i thought the whole problem was due to .Xauthority error.


anyway thanks to the people above me :p

---

### Post by adarsh_iitg on 2010-05-31
I have a problem, solution to which I could not find anywhere. 

here it goes:

My ubuntu 10.04 64-bit was running extremely well. I tried to install a few packages for google-gadgets from the offical website. it was unsuccessful.
adding to it, my login screen has disappeared. After booting, only the background screen(theme) comes without any login window. absolutely nothing is written ...

please help me. I tried recovery option from the grub menu, but could not find anything relevant (like system restore to factory settings or similar) 

however I can reach command line login by pressing ctrl+alt+f2 and hence login into command line environment ....

Can anything be done from the terminal ???please suggest ....

---

### Post by Sp4 on 2010-05-31
Thanks for this

```
sudo apt-get install gnome-session
```

worked perfect for me but loads of errors so i will now backup and reinstall

---

