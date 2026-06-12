---
title: "lost login manager - cannot revert auto login"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by washakie on 2009-07-07
Hello,

Just recently I activated auto login following this:
8. Enable Gnome Auto login
A lot of us are the sole users of our computers, and it makes little sense navigating through a login screen before getting to our desktops. You can enable auto-login for a default account on your Ubuntu machine by selecting ‘Login Window’ from the System> Administration window. Switch to the ‘Security’ page, enable ‘Automatic Login’ and select the user.

Now, I want to revert, but I no longer have the menu item System>Administration>Login Window

Is there a package I have to install to get it back? Or, better yet, is there a command line / config file method to change auto login?

Thanks!

EDIT: Here's the solution:

> [http://www.jirka.org/gdm-documentation/x241.html](http://www.jirka.org/gdm-documentation/x241.html)

Gave lots of good information.

Ultimately, I edit the file /etc/gdm/custom.conf:

AutomaticLoginEnable=false

And I now am again asked which session to log in to...

---

### Post by michy99 on 2009-07-07
See if this works:

```
gksu /usr/sbin/gdmsetup
```

---

### Post by washakie on 2009-07-07
Nope.

Any way to do this with a config file somewhere? perhaps .gconf?

---

### Post by ajgreeny on 2009-07-07
Are you doing this as the admin user?  If you are and it does not work, try reinstalling gdm, as this is where the gdmsetup executable is.  Michy99's solution certainly should work OK.

---

### Post by washakie on 2009-07-08
Maybe it is because I am running karmic? 

%sudo su -
root@nino:~# which gdmsetup
root@nino:~# /usr/sbin/gdmsetup
bash: /usr/sbin/gdmsetup: No such file or directory

---

### Post by washakie on 2009-07-12
Bump.

Anyone know how I can change back to having a menu selection of managers to log into? Right now GDM is not working so I have to hack around and use xfce, but I can't do it directly from reboot.

I have to first login to a tty, kill gdm , restart x, then launch xfce...

If there is a configuration file that I can edit that would help!

---

### Post by washakie on 2009-07-12
[http://www.jirka.org/gdm-documentation/x241.html](http://www.jirka.org/gdm-documentation/x241.html)

Gave lots of good information.

Ultimately, I edit the file /etc/gdm/custom.conf:

AutomaticLoginEnable=false

And I now am again asked which session to log in to...

---

### Post by mdurham on 2009-07-15
> **washakie said:**
> [http://www.jirka.org/gdm-documentation/x241.html](http://www.jirka.org/gdm-documentation/x241.html)

Gave lots of good information.

Ultimately, I edit the file /etc/gdm/custom.conf:

AutomaticLoginEnable=false

And I now am again asked which session to log in to...

Hi washakie, which section did you use?
I only have:
[xdmcp]

[chooser]

[security]

[debug]

All are empty. I want to enable auto login. So I guess I need
AutomaticLoginEnable=true
AutomaticLogin=mike
But where do I put these lines?
Cheers, Mike

---

### Post by balloons on 2009-07-15
Yes - new version of GDM for gnome in Karmic. See this bug:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)

---

