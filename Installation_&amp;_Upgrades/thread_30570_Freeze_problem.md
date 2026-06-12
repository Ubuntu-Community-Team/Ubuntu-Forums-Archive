---
title: "Freeze problem"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by elyask87 on 2005-04-29
I have just installed the latest version of ubuntu and this is the first time i use linux. I have completed the installation successfully and get the login screen, after entering my login data ubuntu loads.

Once it is done loading, I am able to move the mouse, however if I am to right click, open one of the application, simply try to do something else the screen freezes and I am unable to do anything except performing a restart by pushing the button on pc.

My PC spec is:

P4 1.7GHz
80GB Maxtor HD
128MB RAM
nVidia TNT2 32MB
D-Link Network Card

I read somewhere in this forum that it may be a problem with my drivers (something wrong with Nvidia and ubuntu), I have the update file (a .run file) on my desktop however I am unable to install them since I'm a newbie and have no idea how to use the shell etc...

Can someone help me?

Thanks  O:)

---

### Post by nocturn on 2005-04-29
Hmm, you can use the NV (free) driver for Nvidia.

Try pressing CTRL-ALT-F1 on the login screen
This gets you a text-base login.

Login as your user, then enter
```
sudo su -
cd /etc/X11
edit xorg.conf
```

Now search for Driver "Nvidia" and change "Nvidia" to "nv"
Save & exit

```

/etc/init.d/gdm restart

```

Note that this driver does not support 3D.

---

### Post by elyask87 on 2005-04-29
I tried the above and I got:

Warning: unknown mime-type for "xorg.conf" -- using "application/*"
Error: no "edit" mailcap rules found for "application/*"


The above appears after I enter the edit xorg.conf command

---

### Post by elyask87 on 2005-04-29
I was able to open the editor in xorg.conf and the driver is set to "nv" already.

---

### Post by nocturn on 2005-04-29
[QUOTE=elyask87]I was able to open the editor in xorg.conf and the driver is set to "nv" already.[/QUOTE]

Strange, so this cannot be the cause of the freeze.
Is there anything in your log files ?

/var/log/Xorg.log.0
/var/log/messages

---

### Post by elyask87 on 2005-04-29
When I try to open the messages log the same problem happens, it opens then it freezes, however i did notice that in the log one of the lines mentioned 127mbLOWMEM something like that... Could low memory be the problem?

When I was browsing a few sites using the firefox in ubuntu one of the sites gave me a sort of mixup with the colors it was like tv static but with the colors of the web page, which makes me still think it is sometihng with the drivers of my vid card unless im wrong  :neutral: 

On my desktop I have a .run file with the drivers I have to update, however the instructions tell me I have to run it when X is not operating (have no idea what that means) and i am unable to get it to open successfully in root commands outside of the graphical system.

---

