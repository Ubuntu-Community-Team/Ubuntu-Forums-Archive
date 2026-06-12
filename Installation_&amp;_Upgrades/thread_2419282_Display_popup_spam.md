---
title: "Display popup spam"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by bippsie on 2019-05-19
Hi everyone,

I found a laptop here at home to install Ubuntu studio on, since I do photography and my wife sings and makes music.

Problem is this message that keeps popping up like 30 times on startup, and then stops. I tried both 19.04 and 18.04 LTS without luck.

How do I fix this so I can actually start using the OS?

Thanks in advance

---

### Post by Rubi1200 on 2019-05-19
Hi and welcome to the forums :-)

From my limited knowledge of Scandinavian languages I see it has something to do with screen resolution?

When did this start happening? Did you first try or go directly to installing?

Please post the specifications, especially RAM, graphics, and screen resolution.

Thanks.

---

### Post by Rubi1200 on 2019-05-19
Do you by chance have a second monitor attached?

---

### Post by bippsie on 2019-05-20
Hi, correct. It has something to do with screen or resolution.

It started right away, both when testing and after install. They pop up as soon as I reach my desktop even if I don't touch anything.

It's a HP laptop with 4gb ram, AMD rs880 graphics and AMD athlon ii n350 dual core CPU.

I do not have any other screens connected to it.

---

### Post by Rubi1200 on 2019-05-21
What does the output of this command show?

CTRL+ALT+T to open a terminal:

```
xrandr
```

Post in code tags please for easier reading (Go Advanced >> look for # and paste between).

Thanks.

---

### Post by bippsie on 2019-05-21
> **Rubi1200 said:**
> What does the output of this command show?

CTRL+ALT+T to open a terminal:

```
xrandr
```


Post in code tags please for easier reading (Go Advanced >> look for # and paste between).

Thanks.

I just installed regular Ubuntu and it works, can I use this command in "try before installing" or do I need to install Ubuntu studio again?

---

### Post by Rubi1200 on 2019-05-21
Regular Ubuntu, you mean plain vanilla Ubuntu 18.04?

Yes, the command also works in Try before installing. Basically, what it shows is your current screen resolution and all options to change to (should you wish).

The other thing I was going to suggest on Studio would be to go to the Notification settings and if there is an entry for display to disable it (but that would only appear after installing not on the live session).

I forgot to ask before but if you had installed the latest version of Studio, 19.04 I think, and it was causing issues then try installing the 18.04 LTS version they have available on the site.
[http://ubuntustudio.org/download/](http://ubuntustudio.org/download/)

---

### Post by bippsie on 2019-05-21
> **Rubi1200 said:**
> Regular Ubuntu, you mean plain vanilla Ubuntu 18.04?

Yes, the command also works in Try before installing. Basically, what it shows is your current screen resolution and all options to change to (should you wish).

The other thing I was going to suggest on Studio would be to go to the Notification settings and if there is an entry for display to disable it (but that would only appear after installing not on the live session).

I forgot to ask before but if you had installed the latest version of Studio, 19.04 I think, and it was causing issues then try installing the 18.04 LTS version they have available on the site.
[http://ubuntustudio.org/download/](http://ubuntustudio.org/download/)

Hi, I just installed Ubuntu studio again to fix the problem. Xrandr gives me the same resolution as the display window suggests, 1366x768.

I can not find anywhere to turn off notifications for screen.

---

### Post by Frogs Hair on 2019-05-21
The window is your display settings though I don't know why it is opening unaided . You would normally have to open settings or right click the desktop open to activate the window. If you right click the desktop do you see a shortcut to display settings?

---

### Post by Rubi1200 on 2019-05-21
If it is still showing up as before that is quite odd.

As Frogs Hair points out you would not normally see that window unless you had opened settings to adjust something.

As a test, I ran a live session of Studio and was not affected by this.

---

### Post by bippsie on 2019-05-22
> **Frogs Hair said:**
> The window is your display settings though I don't know why it is opening unaided . You would normally have to open settings or right click the desktop open to activate the window. If you right click the desktop do you see a shortcut to display settings?

Yes I do, I just clicked it and closed it, and now I don't get the window again.

But after reboot it is back, and continues after opening and closing desktop settings

> **Rubi1200 said:**
> If it is still showing up as before that is quite odd.

As Frogs Hair points out you would not normally see that window unless you had opened settings to adjust something.

As a test, I ran a live session of Studio and was not affected by this.

Okey, I'm starting to think it might have something to do with my graphics drivers maybe? How do I uninstall/reinstall them?

I ticked the box for "proprietary" drivers during install

I just noticed that the computer kind of freezes for a second just before the window opens, if that's helping at all:D

---

### Post by Rubi1200 on 2019-05-22
I am doubtful as to whether it is a graphics card issue since you said it also happened during testing of the live medium.

Since this is a fresh install and you have probably not changed anything yet let's try this (to reset the desktop settings) but again I am not sure this is the issue:

Log out of the session and then at the login screen use CTRL+ALT+F1 to get to a TTY command line and type in your username and password (will not show on the screen but just type it and then Enter).

Rename the config file for display with this command:

```
mv .config/xfce4 .config/xfce4backup
```

When the command completes type this to restart a graphical session:

```
startx
```

Hopefully this will resolve the issue.

---

### Post by bippsie on 2019-05-22
> **Rubi1200 said:**
> I am doubtful as to whether it is a graphics card issue since you said it also happened during testing of the live medium.

Since this is a fresh install and you have probably not changed anything yet let's try this (to reset the desktop settings) but again I am not sure this is the issue:

Log out of the session and then at the login screen use CTRL+ALT+F1 to get to a TTY command line and type in your username and password (will not show on the screen but just type it and then Enter).

Rename the config file for display with this command:

```
mv .config/xfce4 .config/xfce4backup
```

When the command completes type this to restart a graphical session:

```
startx
```

Hopefully this will resolve the issue.

Unfortunately this didn't work either... But when I started X the icon for the menu was different, and I got a message about "light-locker" with some error.

Any other ideas? I really appreciate your help

---

### Post by Rubi1200 on 2019-05-22
Go back to the TTY terminal please and then do this:

```
mv .config/autostart/light-locker.desktop .config/autostart/light-locker.desktopbackup
```

```
startx
```

This is certainly an unusual problem, one I have not seen before.

---

### Post by bippsie on 2019-05-22
> **Rubi1200 said:**
> Go back to the TTY terminal please and then do this:

```
mv .config/autostart/light-locker.desktop .config/autostart/light-locker.desktopbackup
```

```
startx
```

This is certainly an unusual problem, one I have not seen before.

It says "can't get status of  '.config/autostart/light-locker.desktop': file or catalogue doesn't exist"

Maybe I should get the vanilla Ubuntu instead and just install all the software manually, since Ubuntu vanilla worked...

---

### Post by Rubi1200 on 2019-05-22
Well, here is the thing, I looked at some of the software on Studio and I believe it is all available in the repositories so...it might be the best bet.

I really do not understand why you had these problems with the display notification (perhaps some bug specific to your setup, who knows).

If you need more help please feel free to ask.

---

### Post by bippsie on 2019-05-22
> **Rubi1200 said:**
> Well, here is the thing, I looked at some of the software on Studio and I believe it is all available in the repositories so...it might be the best bet.

I really do not understand why you had these problems with the display notification (perhaps some bug specific to your setup, who knows).

If you need more help please feel free to ask.

Thanks again for all help. I tried the other night to install the studio on top of Ubuntu, but it didn't seem to work. I used some "sudo apt install ubuntu-studio-installer", but when I tried to install stuff it just froze... Will try again and return to you if it's ok

---

### Post by Rubi1200 on 2019-05-22
I believe you need to run this command:

```
sudo apt install ubuntustudio-controls ubuntustudio-installer
```

and also enable the Backports PPA:
[https://help.ubuntu.com/community/UbuntuStudio/BackportsPPA](https://help.ubuntu.com/community/UbuntuStudio/BackportsPPA)

---

### Post by bippsie on 2019-05-30
> **Rubi1200 said:**
> I believe you need to run this command:

```
sudo apt install ubuntustudio-controls ubuntustudio-installer
```

and also enable the Backports PPA:
[https://help.ubuntu.com/community/UbuntuStudio/BackportsPPA](https://help.ubuntu.com/community/UbuntuStudio/BackportsPPA)

Hi, I got it working! But when I tried to install xfce it all started happening again, so i guess it has to do with xfce and not the system itself... which is a shame since the computer would run a lot smoother with xfce, but oh well...

---

### Post by Rubi1200 on 2019-05-30
Hmm, that is very interesting indeed.

You might want to consider filing a bug report with the xfce developers about this.
[https://mail.xfce.org/mailman/listinfo/](https://mail.xfce.org/mailman/listinfo/)

There are also alternatives that might suit you:
[https://alternativeto.net/software/xfce/?platform=linux](https://alternativeto.net/software/xfce/?platform=linux)

Also look here:
[http://www.linuxandubuntu.com/home/5-lightweight-linux-desktop-environments](http://www.linuxandubuntu.com/home/5-lightweight-linux-desktop-environments)

Most are available in the repositories though for Studio I am not sure.

---

