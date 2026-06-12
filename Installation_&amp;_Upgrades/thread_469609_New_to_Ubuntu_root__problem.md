---
title: "New to Ubuntu root  problem"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by ElectricRanch on 2007-06-10
I am trying to install theh LAMP stack for development, but the system tells me I can't write to /opt. I am logged in as the user that installed Ubuntu, but no luck.

Can someone help a newbie?

---

### Post by Ardrias on 2007-06-10
Did you 'sudo' the command to install?

---

### Post by ElectricRanch on 2007-06-10
Thank you for the prompt reply.

I am using the graphical user interface. Do you mean I will have to work from the terminal to use Ubuntu?  I thought that the user that did the installiation was root. Am I wrong or am I missing something?

---

### Post by eentonig on 2007-06-10
And how are you trying to install the LAMP via the GUI?

Are you using Synaptic (Software Management) or installing by hand?

sudo is the CLI command to gain temporary root privileges.
gksudo is the equivalent for using GUI based apps.

IE. If you want to open a nautilus explorer window with root privileges. Enter
> <Alt><F2>
gksudo nautilus
A prompt will appear to enter your password. After that, the app will launch with the required user privileges.

Apps that always equire root access to use, do the prompt themself. For things like nautilus, you might want to create a launcher.

---

### Post by ElectricRanch on 2007-06-10
Thanks for the info.

To install Apachefriends LAMP stack, you install it iin /opt and configure the startup script to run XAMP start. Simple. Where i REALLY have the problem was accessing the website under /opt.

I will try to setup the launcher and ftp as you recomended. 

Much thanks.

---

