---
title: "Old users can't login after upgrade to 12.04"
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by AlexBooton on 2013-07-30
Boy am I glad this forum is back!

While it was down I upgraded to 12.04 and now my existing users can't login.

I can add new users and they can login w/o problem.

How do I get my old uses to show up on the login screen?

---

### Post by Bhawani007 on 2013-07-30
Can you login via command line(tty) using existing user.

Press ALT+CTRL+F1 and try to login as old user.

---

### Post by Frogs Hair on 2013-07-31
[COLOR=#000000]ALT+CTRL+F1  will take you to TTY and to get back use [/COLOR][COLOR=#000000]ALT+CTRL+F7. [/COLOR]

---

### Post by AlexBooton on 2013-07-31
> **Frogs Hair said:**
> [COLOR=#000000]ALT+CTRL+F1  will take you to TTY and to get back use [/COLOR][COLOR=#000000]ALT+CTRL+F7. [/COLOR]

Thank you both Bhawani007 and Frogs Hair,

That's what I've done and used the terminal to create a new user.  Old users can also login this way (via the terminal).

But the old users still don't show up on the graphical login screen (the new user does).

How do I get them back?

---

### Post by steeldriver on 2013-07-31
What are the UIDs of the old users? what version did you upgrade from? The default lightdm configuration in 12.04 only displays users whose UID is >= 1000 (and creates new users starting from UID = 1000) - you can change the displayed UID cutoff via /etc/lightdm/users.conf

```

$ cat /etc/lightdm/users.conf
#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
**minimum-uid=1000**
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

The actual UID_MIN used for account creation is in /etc/login.defs, should you need to modify that as well

---

### Post by AlexBooton on 2013-07-31
I think I'm getting somewhere.

First off this is a private system with just one user (me) plus root.  I've now added a second user who is able to login.

My UID is 1000 and does not show on the login screen.  The new user does.

But the login screen shows a user named "Comment" who has my UID (1000).

I've changed the real name of user 1000 to me and that part is now fixed.

But the login screen won't accept my password.  It does NOT say the p/w is invalid; the screen just goes black and comes back just as it was b4.  If I enter an invalid p/w then it does tell me it's invalid.

So why won't it take my p/w?

My p/w is simple with only 6 alpha characters.  Does 12.04 require a stronger one?

Thanks

---

### Post by steeldriver on 2013-07-31
Most likely it *is* accepting the password, but is unable to start your X session - either because your home directory is not writable or your ~/.Xauthority file is not writable - check ownership and permissions

```

ls -ld /home/*username*

ls -l /home/*username*/.Xauthority

```

---

### Post by AlexBooton on 2013-07-31
> **steeldriver said:**
> Most likely it *is* accepting the password, but is unable to start your X session - either because your home directory is not writable or your ~/.Xauthority file is not writable - check ownership and permissions

```

ls -ld /home/*username*

ls -l /home/*username*/.Xauthority

```

THANK YOU steeldriver!

You called it exactly right.

The owner/group for /home/me/.Xauthority was root/root.

That was a bit of a surprise since I was able to login as me b4 the upgrade to 12.04. 

I'm just overjoyed that it's now working.

---

