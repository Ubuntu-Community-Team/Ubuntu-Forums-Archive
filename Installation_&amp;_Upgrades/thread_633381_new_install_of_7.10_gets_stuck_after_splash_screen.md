---
title: "new install of 7.10 gets stuck after splash screen"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by nathandean on 2007-12-06
I just installed 7.10 on a dell inspiron 1200

after POST,

GRUB 1.5

Starting up...

Loading...
Please Wait

The splash screen runs then I get:

*Starting anac(h)ronistic cron anacron             (ok)
*Starting deferred execution scheduler atd     (ok)
*Starting periodic command scheduler crond    (ok) 
*Checking battery state                                   (ok)
*Running local boot scripts  (/etc/rc.local)        (ok)

These lines appear together and flash on and off three times then stay on the screen. After this the machine will just sit there displaying the above info. I have tried Alt+F4 and was able to log in and got to the terminal but I don't know what to change to move past this point. Any help?

---

### Post by odysseusjak on 2007-12-09
I have the same problem.  However, an added feature with mine is that my video output is through an nVidia 6200 DVI.  This system also has an integrated video and that works just fine.  However, I would prefer to use the nVidia card since this is a customers computer.

Thanks.

---

### Post by nathandean on 2007-12-09
Still no luck I have tried the install 4 times. I even burned the install CD at a different speed thinking that this might be due to a hardware issue with the laptops CD-ROM. No luck.

Going to take out the hard drive and try this on a different MOBO. maybe I can get it going that way. Will keep you posted.

---

### Post by PmDematagoda on 2007-12-09
The problem is with the VGA driver not being set-up properly.

Go to a terminal after Ubuntu gets stuck at ```
*Running local boot scripts (/etc/rc.local) (ok)
``` by pressing Ctrl+Alt+F1.

Once there, do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After that is done, try doing:-

```
sudo startx
```

To see if the GUI works properly then.

---

### Post by nathandean on 2007-12-14
ok, sorry it took so long to get back to everyone. I have used the above instructions and can now boot into the GUI under the root user. once "inside" I tried to switch back to my normal user and got this message:

-/.Xauthority file badly configured or missing.
100 Not authenticated


I will be checking other forums to see if this has already been posted.

---

### Post by nathandean on 2007-12-14
I went ahead and updated the system while in the root user mode. I got thru most of the 145 updates fine but towards the end (I think it was working thru some gnome updates) it started going to a 16-bit screen with a grey window telling me something to the affect of the console was busy and the server needed to be moved to another console and to press Ctrl + Alt + funtion key to swith to another console. I kept telling it no and it would go back to the GUI and complete one update but as soon as it started the next it would go back to htis screen. at the end of the updates it restarted without asking my permission and came up at the normal GUI logon screen. I tried to log in with the usrname and password that I set up during install and got this error:

Your session only lasted less than 10 seconds. If you have not logged out yourself , this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Details:

Refusing to initialize GTK+

(Process: 5229) GTK-WARNING **: this process is currently running setuid or setgid. THis is not a supported use of GTK+. you must create a helper program instead. For further details, see:

[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+
/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Could not create gnome accelerators directory ' /home/rick/.gnome2/accels  " : Permission denied


I am guessing that the OS is denying itself access to the file system to initialize the user's session but why or how to fix it is beyond me. PLease help!

---

### Post by PmDematagoda on 2007-12-14
I think you may have goofed the permissions or ownerships for your Home partition while being Root.

Do(Replace username with your username and usergroup with the group you belong to):-
```

sudo chown username:usergroup /home/username
```

And see if that may solve the problem.

---

### Post by nathandean on 2007-12-14
I understand your instructions but I didn't designate a usergroup when I did the setup on this laptop. Would be the same as the username then?

username: rick
name of Laptop: rick-laptop

those are the only two things that I changed at setup.

---

### Post by PmDematagoda on 2007-12-14
If you did not change your username or usergroup then the command should look like this:-
```

sudo chown rick:rick /home/rick
```

---

### Post by finaryman on 2008-02-11
i have seen this problem, but not sure if this works.

at terminal run command : sudo apt-get remove powernowd
make sure the packet is uninstalled.
then boot just normaly.

could be something else too but...

---

### Post by finaryman on 2008-02-12
```
sudo dpkg-reconfigure xserver-xorg
```
and if this doesn't work im out of options right now.

---

