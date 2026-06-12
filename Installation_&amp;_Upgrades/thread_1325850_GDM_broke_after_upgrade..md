---
title: "GDM broke after upgrade."
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by dawynn on 2009-11-13
Tried searching for this issue, and wasn't finding any posts quite like the issue I have.

I just switched a computer from a Linux Mint Gloria (9.04) XFCE version over to, what I intended would be a pure Gnome Ubuntu Karmic Koala by purging all the xfce and mint packages, installing ubuntu-desktop, and upgrading all the packages to Karmic.

Everything boots up.  I can sign in via the alternate console screen (ctrl-alt-f1, etc), but the graphical bootup (gdm) ain't workin'.

I like the funky graphics with the spotlight over the spinning disk effect.  And the colors look really nice on the gdm startup screen.  Problem is, unlike other upgrades that I've done to 9.10, there is no user list to choose from.

There's a selection for accessibility changes, and I can shutdown or reboot.  I can even type and a little text box will come up.  But there is no user selection list, and the text box isn't acting like a login text entry box.

Any ideas what I can do here?

---

### Post by Iced on 2009-11-14
I have the same problem.  I upgraded from 9.04 to 9.10 and have no userlist and cannot login without using console.  Mine was strictly a 'gnome' upgrade and I have a ton of GDM errors in /var/log/messages to sift through.

---

### Post by Iced on 2009-11-14
I disabled the userlist and restarted GDM and now can enter username and password.


[Disable Userlist]("http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/")

---

### Post by dawynn on 2009-11-19
My "solution" was a little more devious.  I reasoned that it was gdm causing the problem.  So, I installed wdm.  xdm or kdm probably would have worked just as well.

(Since I could get to a command line, aptitude was able to install any packages I needed.)

This at least got me into Gnome.  I haven't played much with that side of the system.  So, for now its still set with wdm booting into Gnome.

---

