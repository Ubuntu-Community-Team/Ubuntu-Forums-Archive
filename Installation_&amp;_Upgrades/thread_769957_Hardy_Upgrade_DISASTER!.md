---
title: "Hardy Upgrade DISASTER!"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Rob916 on 2008-04-27
I need major help.  I ran the update manager last night and it started downloading all the packages without a hitch.  I went to bed and woke up early to start the install.  I went to work, came home and found it sitting at the login screen (with a low screen resolution) I log in with my user and pass and it logs into Enlightenment, looks like crap, theres no icons anywhere, I log out, change the session to "Gnome" and it looks like my desktop but smaller resolution.  Nothing works, there is no networking so no internet, firefox won't even load.  I try running Nvidia setup from the menu and it can't find it. Many of the programs it can't find or says it can't find.  HELP!  Is there a way I can restore with the CD without losing all my documents?

---

### Post by Peter09 on 2008-04-27
OK - lets just break down your problems into a few smaller bits.

1. Is your home directory ok. Can you see your documents as they were before the upgrade.
2. Are you running wireless or wired, if possible run wired as its easier to get a connection.
3. Installing the Nvidia drivers is different in hardy, try typing
```
xfix
```

PC

---

### Post by chek2fire on 2008-04-27
Try to install driver with the programme envyng. You can find it from synaptic.

---

### Post by Rob916 on 2008-04-27
> **Peter09 said:**
> OK - lets just break down your problems into a few smaller bits.

1. Is your home directory ok. Can you see your documents as they were before the upgrade.
2. Are you running wireless or wired, if possible run wired as its easier to get a connection.
3. Installing the Nvidia drivers is different in hardy, try typing
```
xfix
```

PC

1. My home directory is fine, all my files are still there.
2. My PC is wired to the router
3. Typing "xfix" in a terminal yields "bash: xfix: command not found"

Also, when I first log in a window advising "Failed to initialize HAL!" pops up.

I figured I could copy all my files to my usb hard drive however my USB drive will not pop up anymore.  I suppose I could try to burn all my documents to DVD and do a fresh install.

---

### Post by superprotta on 2008-04-27
Hi, I'm not an expert with ubuntu but I had some problems too upgrading to hardy. I couldn't find my programs, my configurations and so on. Turned out that the problem was that the new kernel renamed my partition devices so my fstab configuration wasn't good anymore. Try loading the old kernel: if it loads correctly this is the problem and you just need to adjust your fstab. At least this solved all my problems

---

### Post by Peter09 on 2008-04-27
Yes,
superprotta may have an answer, worth a try.

If this fails then the first step is to recover you internet connection, without that it will be difficult to proceed.

PC

---

### Post by Rob916 on 2008-04-27
the fstab thing sounds somewhat feasible however some programs are available and some are not.  I'm backing up my home directory to DVD right now and I think I'm just going to wipe and fresh install.  Somehow I think the upgrade didn't go as it was supposed to, my GRUB menu still shows 7.10

---

### Post by loell on 2008-04-27
this is the second report i've read where enlightenment became the Desktop environment after uprading to hardy.

---

### Post by ssam on 2008-04-27
if fstab was wrong you would lickly not have go to where you are.

it may still be recoverable, but a clean install is probably quicker and easier.

---

### Post by Rob916 on 2008-04-27
First of all I would like to thank everyone who tried to help.  This is a great community right here!

I did a fresh install and everything works.  One question however, When I copy files from my backup DVD to my home folder it placed a padlock icon over the file/folder I copied from the DVD.  What is this?

---

### Post by Plath on 2008-04-27
Me, I can't run 8.04 at all. I can install it but when i try to run it i have this : [http://paste.ubuntu-nl.org/64669/](http://paste.ubuntu-nl.org/64669/) 

  I installed with upgrade, with alternate CD , Desktop CD and in all case i have the same error when running 8.04. I would like some help please.

---

### Post by ssam on 2008-04-27
padlock means that files are read only. you get this if you copy a file from a readonly disk (like a dvd).

select all the padlocked files. right click and choose properties. then set the permissions for owner to 'read and write' then click the apply permisions to enclosed folders button.

---

### Post by ssam on 2008-04-27
> **Plath said:**
> Me, I can't run 8.04 at all. I can install it but when i try to run it i have this : [http://paste.ubuntu-nl.org/64669/](http://paste.ubuntu-nl.org/64669/) 

  I installed with upgrade, with alternate CD , Desktop CD and in all case i have the same error when running 8.04. I would like some help please.

hi plath.

you are suffering from a different issue. please can you start a new thread. thanks

---

### Post by Rob916 on 2008-04-27
Thanks for the help guys.  I figured the lock thing out, I have just never seen it before.  The only other issue I had was I had no sound with the Audigy card and I discovered Ubuntu sets it to use the digital output by default.  Switched that off and I had sound.  Everything works beautiful now!

---

