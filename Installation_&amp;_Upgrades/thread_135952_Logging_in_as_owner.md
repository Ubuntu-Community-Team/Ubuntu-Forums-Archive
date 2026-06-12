---
title: "Logging in as owner"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by bradhawk08 on 2006-02-24
How do I log in as the owner so I can change the permissions of the folders?
Please help.
Thanks
Brad

---

### Post by taurus on 2006-02-24
Not exactly sure what you want to do but you did create an account when you first installed Ubuntu, right!  Log in using that username and password and if you are not the owner of that folder (may I ask which folder/directory are you talking about here?) and would like to change, then you need to use the sudo command as

sudo chown -R <your userID> <directory>

---

### Post by andrewsawyer on 2006-02-24
you can use ```
sudo chmod
``` from the command line as a normal user, or ```
sudo su
``` to put you in super user mode to make a few alterations.

Although it is not the 'safest' way to do things, you could also try ```
sudo nautilus
``` which will give you a super user version of File Manager.  As I say though, this is a super user mode, so it is possible to delete critical components.  Remember to close it afterwards so you don't get it confused with the standard file manager.

---

### Post by bradhawk08 on 2006-02-24
Okay so here's the deal. I'm trying in essence to update the X Window System.  In the process, I'm also installing Perl.  In running the Perl installation steps, it gets to the end and says error: cannot write to /usr/local/bin  so i was trying to change the permissions so it can install correctly.  also i would like to move all the downloaded .tar.gz files off my desktop.  i can't write anything to the entire filesystem (where /usr/local/bin) because i'm not the "owner" and it won't let me change permissions.  hope that helps for you to give me more advice.  (is it best to go with either super user or the nautilus super user as described above? and if so how do i get back out of the super user mode?)
thanks
brad

---

### Post by andrewsawyer on 2006-02-24
If installing a program (or compiling one) you need to be in super user mode.  This is a saftey restriction (in part to stop nasty programs deleting core files).  So when you are installing a program, make sure you are in super user mode.

For example to compile a program you would write ```
sudo make install
``` rather than just ```
make install
```

As super user has access to everything, this will fix your problem.  Likewise with moving the tar files off your desktop, you can put them anywhere in your /home directory.  So just create a new subdirectory in your home directory called Downloads or something and stick them all in there.

To do what you want, you really don't need to worry about changing ownership of directories at all.

---

### Post by jpkotta on 2006-02-24
Don't change the permissions of /usr/.  They are set that way for a reason.  If you can (and I'm not sure why you couldn't), use the commandline with sudo, as suggested above.  sudo runs things as root (the superuser, or administrator).

---

### Post by aysiu on 2006-02-24
Check out the third link of my sig.

---

