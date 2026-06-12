---
title: "No X?"
date: 2004-11-09
forum: Installation &amp; Upgrades
---

### Post by Lemvigh on 2004-11-09
After installing Ubuntu 4.10 I can't find out, how to start x. When I try to 'startx' I'm told that theres no such command. Shouldn't it be installed automatically??? Whatching the installationprocess I noticed the installation of all sorts of x-applications. Using apt it seems that gnome is installed as well.

Any suggestions as to what my problem could be???

Thanks
Morten

---

### Post by im_ka on 2004-11-09
if you boot into your freshly installed ubuntu system, it should start x and gdm should come up...

what happens?
any error messages?

---

### Post by Lemvigh on 2004-11-09
No errormsgs while booting. I get a standard textbased loginprompt. When I log in I'm presented with an X-less shell.  I tried to be attentive while installing, and I didn't notice any errors, but some of the messages went by to fast. Is there a log somewhere, where I can check if something went wrong?

Morten

---

### Post by HungSquirrel on 2004-11-09
Did you answer "No" to the question about downloading packages from the internet?

---

### Post by Tommy on 2004-11-09
[QUOTE=Lemvigh]No errormsgs while booting. I get a standard textbased loginprompt. When I log in I'm presented with an X-less shell.  I tried to be attentive while installing, and I didn't notice any errors, but some of the messages went by to fast. Is there a log somewhere, where I can check if something went wrong?
[/QUOTE]

I bet the xserver settings don't quite match your hardware, so the xserver fails. You may even see the screen flicker three or four times after the boot messages (you'll see a line that says "starting gdm").

There is an error log you can look in... /var/log/XFree86.0.log I believe.

But since you get to the command prompt, why don't you review your xserver settings --

once you log in, run 

sudo dpkg-reconfigure xserver-xfree86

and see whether the settings match your hardware (as best you know). You can try a few different things, just be careful with the monitor frequency settings because they can damage a CRT if you let them sit too long on the wrong settings.

---

### Post by Lemvigh on 2004-11-10
[QUOTE=HungSquirrel]Did you answer "No" to the question about downloading packages from the internet?[/QUOTE]

No, I answered "Yes". It all seems to be installed. When I "apt-get install" (after updating and dist-upgrading) either xfree86 og gnome I'm told that everything is installed in the newest version.

---

### Post by Lemvigh on 2004-11-10
[QUOTE=Tommy]I bet the xserver settings don't quite match your hardware, so the xserver fails. You may even see the screen flicker three or four times after the boot messages (you'll see a line that says "starting gdm").
[/QUOTE]

I didn't see "starting gdm". Would xserver settings explain why the command startx is missing?

[QUOTE=Tommy]
There is an error log you can look in... /var/log/XFree86.0.log I believe.
[/QUOTE]
I couldn't find any log which had an X-like name.

[QUOTE=Tommy]
But since you get to the command prompt, why don't you review your xserver settings --
once you log in, run 
sudo dpkg-reconfigure xserver-xfree86
and see whether the settings match your hardware (as best you know). 
[/QUOTE]
It looked fine. The only place where I didn't know what to select was the x-driver for my graphics card (Riva TNT 2).

---

### Post by ashley_v on 2004-11-10
[QUOTE=][/QUOTE]
 type 'whereis startx' and it may tell you.  Usually it's in  /usr/X11R6/bin/startx or /usr/bin/X11/startx.  And you might want to run 'xf86config' to select the right driver for your card.

---

### Post by Lemvigh on 2004-11-10
[QUOTE=ashley_v]type 'whereis startx' and it may tell you.[/QUOTE]
It just tells me:
startx:

[QUOTE=ashley_v]
And you might want to run 'xf86config' to select the right driver for your card.
[/QUOTE]
Doesn't exist either...

I've tried to reinstall a couple of times, but it was all the same... :-(

---

### Post by Tommy on 2004-11-10
From all you've written it sounds like you did a "custom" installation -- typed "custom" when you booted the CD the first time. In that case the system would be configured with a very basic installation but none of the X packages. If you didn't type "custom," some of the packages may have failed during installation -- though if that was true, apt would tell you some were unconfigured and you haven't mentioned that.

If you want the standard packages, it might be worth your while to start the installation again from scratch because it will take less time.

BUT before you do that, make sure you have lots of disk space -- try typing df at a prompt and see that none of your partitions are nearly full. I believe you need maybe 4 or 5 Gigabytes of free space during the installation -- because the installer copies a lot of packages from the CD before it reboots that will get removed after it finishes the install.

---

### Post by kenw on 2004-11-10
Hi
I have just downloaded and installed Ubuntu.
I was unable to obtain a desktop, I ended up with a graphical login and was told X would not start as it was probably incorrectly configured.
I read some of the post's here and followed the 'sudo dpkg-reconfigure xserver-xfree86' post and this allowed me to configure X by entering monitor type, graphics card etc.
During install I was not given any oportunity to configure the monitor, graphics card etc. in  X the only thing it asked me to set was the  screen resolution.
Is this perhaps a problem ?
Other than this Ubuntu appears to be an excellent system.
Kenw

---

### Post by FLeiXiuS on 2004-11-10
Before my later suggestion of reconfiguring, i may suggest this...

```
sudo /etc/init.d/gdm restart
```

Try re-configuring the X server.

```
sudo dpkg-reconfigure xfree86-server
```

Perhaps something had happened during the install that didn't like the modprobe.

---

