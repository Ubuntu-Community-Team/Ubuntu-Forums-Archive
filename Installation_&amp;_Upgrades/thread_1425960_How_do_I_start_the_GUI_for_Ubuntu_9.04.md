---
title: "How do I start the GUI for Ubuntu 9.04?"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Datamac on 2010-03-09
I have command line "$" prompt and need to know where I go from here to get a GUI and start learning the system?

---

### Post by Revolutionary101 on 2010-03-09
Enter this into terminal:

```
gnome&
```

That should start GNOME so you can see the GUI of Ubuntu. Although I have to ask, how did you get Ubuntu to the command line in the first place?

---

### Post by Datamac on 2010-03-09
Ubunto 9.04, after the initial install and reboot process stopped with the command prompt in display.  I had to enter a "passphrase" to get it to completely boot, then login using the user name I created during the install.  I tried the command you suggested but that isn't getting me a GUI

---

### Post by Revolutionary101 on 2010-03-09
Try this:

```
sudo gdm start
```

---

### Post by Datamac on 2010-03-09
Thanks but that didn't work either.  However it did perform a search for the command.  I know that it's a bit late for the following info but I failed to mention that I have the server version of 9.04 loaded and running.  And, this machine needs to be a server.  I have the tendency to get deep with project even in the beginning stages of life for me.

---

### Post by louieb on 2010-03-09
A server install does not come with a GUI. Its CLI only.

Easy way to get Gnome.  

```
sudo aptitude install ubuntu-desktop
```

Other desktops are available - Gnome is the easiest to use.

---

