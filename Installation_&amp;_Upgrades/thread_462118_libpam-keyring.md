---
title: "libpam-keyring"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by NicholasWMR on 2007-06-02
I've [installed the libpam-keyring package]("http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html") on a couple of systems to simplify logging on to a wireless network.  This most recent time something went very wrong (on a 64-bit install).  After installing the package and rebooting my username/password no longer work.   I know I didn't forget my password or username.  I know I didn't inadvertently modify the password.   I did *rm $HOME/.gnome2/keyrings/default.keyring* and *sudo gedit /etc/pam.d/gdm* as required 

I've tried to reset the password by booting into a [full root shell]("http://ubuntuforums.org/showthread.php?t=3609").  I get a command line, I enter *passwd username*.  I'm asked to provide a password but when I type a single letter it immediately asks me to reenter the password.  I type the same single letter again and I immediately exit back to the command prompt.  This strikes me as strange behavior for the passwd utility.

When I reboot the new password does not work.

I wonder if the package libpam-keyring has been corrupted.  The behavior of the *passwd* application suggests there is something seriously wrong.  The inability to log in suggests further trouble.

---

### Post by kayvortex on 2007-06-25
I think passwd doesn't accept a weak password: I seem to remember reading that in the man pages. Try entering a half-decent password.

---

