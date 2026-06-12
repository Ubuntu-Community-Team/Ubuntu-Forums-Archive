---
title: "Installed ubuntu, now what?"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by ~vjay~ on 2005-05-30
I just went and installed Ubuntu linux on my D drive, I finally figured out how to install it and it went well, once finished I had to reboot and grub is installed so i can dual boot, now the problem is when I choose ubuntu it seems to load fine but then I get to a dos like screen where I am told to enter my login and password, which i did, now I am still in a dos screen and it has things like this on it

[[IMG]http://img200.echo.cx/img200/8162/image0002if.th.jpg[/IMG]](http://img200.echo.cx/my.php?image=image0002if.jpg)

What do i need to do now??

Any idea, I can't get into the Ubuntu, 
I know it's there and now I am back in my xppro and the d drive is missing which I assume is normal because the ubuntu can't see it.

Thanks :)

---

### Post by Mez on 2005-05-30
hey, I'm assuming you did a default install not a "server" install (mininal/custom)

try this command

```
sudo killall gdm
sudo gdm
```

This should hopefully bring up an X session, or it'll bring up a nice error box oin a blue screen... that's if you've installed your default setupo, not a server one

if you've installed server, then try

```
apt-get install ubuntu-desktop
```

and hopefully this should isntlal a base system for you

---

### Post by ~vjay~ on 2005-05-30
[QUOTE=Mez]hey, I'm assuming you did a default install not a "server" install (mininal/custom)

try this command

```
sudo killall gdm
sudo gdm
```

This should hopefully bring up an X session, or it'll bring up a nice error box oin a blue screen... that's if you've installed your default setupo, not a server one

if you've installed server, then try

```
apt-get install ubuntu-desktop
```

and hopefully this should isntlal a base system for you[/QUOTE]
 I think I did the server install, not sure now, but have written this down and am off to try this now

thanks :)

---

### Post by Mez on 2005-05-30
yeah, the server instlal doesnt instlal any GUI packages,

```
sudo apt-get install ubuntu-dekstop
```

Will instlal gnome for you

or if you want to try kubuntu

```
sudo apt-get install kubuntu-desktop
```

---

### Post by ~vjay~ on 2005-05-30
i tried both, the first one gave me a "no processes killed message"

the 2nd one gave me an error message
E:Could not open lockfile /var/lib/dpkg/lock-open(13 permission denied)
E: unable to lock the administration directory( /var/lib/dpkg)
are you root?

Maybe I did something wrong at install and will have to redo it, 
are there any easy guides to set up a dual boot xppro/ubuntu somewhere?


I am going to bed now, is nearly midnight here, will retry some more things tomorrow.

---

### Post by BKonkle on 2005-05-30
VJay - in his first post Mez accidentally showed you the command to add the ubuntu desktop without adding the "sudo" command in front of it.  Ubuntu is much more secure than Windows is, and one of the ways that it protects your computer is by locking certain commands to the "root" user, or administrator.  To run those commands, you type "sudo" before them, it'll ask for your password, and away you go!

When you see an error similar to the one you saw, then you know you forgot to use "sudo".

To install the gnome desktop (which I personally prefer), type the following:

```
sudo apt-get install ubuntu-dekstop
```

---

### Post by dabear on 2005-05-30
[QUOTE=~vjay~]i tried both, the first one gave me a "no processes killed message"

the 2nd one gave me an error message
E:Could not open lockfile /var/lib/dpkg/lock-open(13 permission denied)
E: unable to lock the administration directory( /var/lib/dpkg)
are you root?

Maybe I did something wrong at install and will have to redo it, 
are there any easy guides to set up a dual boot xppro/ubuntu somewhere?


I am going to bed now, is nearly midnight here, will retry some more things tomorrow.[/QUOTE]
 hehe, linux isn't like windows. You don't have eprmission to install all the software you want unless you are a privileged user or the administrator ( that's `root`). type sudo -s -H and your password, and you'll be into the root account. Then try apt-get install ubuntu-desktop . Ubuntu should have set up a dualboot already for you if windows was installed when you installed ubuntu. I have this at the end of my /boot/grub/menuu.lst ( which you have to be root to edit)
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by BKonkle on 2005-05-30
One of my favorite places to go as an Ubuntu and Linux n00b is [http://www.ubuntuguide.org](http://www.ubuntuguide.org).  I would visit it often, because they are updating things on it all the time.

---

### Post by ~vjay~ on 2005-05-30
[QUOTE=BKonkle]One of my favorite places to go as an Ubuntu and Linux n00b is [http://www.ubuntuguide.org](http://www.ubuntuguide.org).  I would visit it often, because they are updating things on it all the time.[/QUOTE]
 Well it is morning now and figured I had messed up and should of installed the default setup instead of server (silly n00b I am), so I went in and redid it all, first step was to resize the settings, I think I left the system partition a bit small last time, and then I installed ubuntu and it worked like a charm, I am sitting here and am using ubuntu and I love it, hehehe

---

### Post by Battlestar on 2005-05-30
Got the same problem here dude,,Almost I installed Ubuntu about 15 times :(..Same error message what you got. Im newbie from Ubuntu, Somebody want to help us?

Btw this is the error that I encounter:

```

login: xxxxx
pasword:xxxxx

Last Login: Sun Blah Blah Blah
Linux Ubuntu 2.6.8.1-3-386xxx Blah Blah Blah

The Program Includewith the ubuntu system are the software Blah Blah Blah
Ubuntu Comes with the ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

You have mail
warty@ubuntu:~$

```
What this means for?
Here's another one error I encounter

```

I cannot start the X-Server (I Think this one is the Video Card right?)

```

PLease PLease help us here guys I want to switch in Ubuntu :(

---

