---
title: "starting vmware"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by otis on 2007-06-02
I just installed vmware through the festy repository and when I go to the System Tools menu and select the VMWare icon I get the spinner, I see "Starting VMWare server" in the task bar for about 15 seconds then I just goes away and never starts.  I am able to start it from the command line though.  Any ideas what would be causing this?

Thanks, Otis

---

### Post by veloce on 2007-06-03
> **otis said:**
> I just installed vmware through the festy repository and when I go to the System Tools menu and select the VMWare icon I get the spinner, I see "Starting VMWare server" in the task bar for about 15 seconds then I just goes away and never starts.  I am able to start it from the command line though.  Any ideas what would be causing this?

Thanks, Otis

Do you just use the command "vmware" on the command line?

---

### Post by otis on 2007-06-03
yes I am able to start it with just running vmware without sudo

---

### Post by veloce on 2007-06-03
Very bizarre.

The only thing I can think of is that the menu item has some command line parameters that are causing a problem.

Try this:

Right click on the menu item and "add this launcher" to either the control panel or desktop.  
Right click on the new control panel or desktop launcher and see what command is being used.

Before deleting the new launcher, see if it works!

---

