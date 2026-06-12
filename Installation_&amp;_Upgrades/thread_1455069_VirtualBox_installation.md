---
title: "VirtualBox installation"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by bolenjx1 on 2010-04-15
I just installed VirtualBox using a i386 deb package from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

And I'm not sure if it installed correctly as I can't find it anywhere in order to run it. Did I do this right? I'm using Karmic btw.

---

### Post by rtilson on 2010-04-15
In a terminal type the command vbox or virtualbox these start it or display error messages that will help in determining the problem.

Or in synaptic see if virtualbox is installed. If it is uninstall it then install it through synaptic. Virtualbox is offered in the repos to you don't need to download it from Virtualbox.org.

---

### Post by bolenjx1 on 2010-04-15
> The program 'vbox' is currently not installed.  You can install it by typing:
sudo apt-get install isdnvboxclient
vbox: command not found

The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose-qt
virtualbox: command not found

I typed virtualbox in synaptic and there's a green shade in the box beside "virtualbox-3.1"

Should I remove it then do something like sudo apt-get install virtualbox?

---

### Post by ajgreeny on 2010-04-15
Use ```
which virtualbox
``` but keep changing the case of the initial letters of virtualbox, to see what the executable in /usr/bin is called.  Or just search in /usr/bin for the executable.   I seem to remember that it is */usr/bin/VirtualBox* so that, or just *VirtualBox* will be the command to run it.  My memory may be wrong, of course.

You can also look at the properties of the package in synaptic and see the files installed, and in there you should find the /usr/bin file

You may also need to look for **Oracle VirtualBox** as the entry in your menu, rather than Virtualbox, as again I think the old menu entry was Sun VirtualBox.  I am absolutely certain that a menu entry was added by the system.

---

### Post by bolenjx1 on 2010-04-15
Ok, it's VirtualBox. lol

Thanks for your help. I looked at the menu again but it's just not there. It's not a problem though.

---

### Post by isbiyanto on 2010-04-15
> **rtilson said:**
> In a terminal type the command vbox or virtualbox these start it or display error messages that will help in determining the problem.

Or in synaptic see if virtualbox is installed. If it is uninstall it then install it through synaptic. Virtualbox is offered in the repos to you don't need to download it from Virtualbox.org.

i am sorry for my english.
i agree with you rtilson.
i use ubuntu software center or synaptic package manager to install. no need to download :KS.

---

### Post by ajgreeny on 2010-04-15
> **isbiyanto said:**
> i am sorry for my english.
i agree with you rtilson.
i use ubuntu software center or synaptic package manager to install. no need to download :KS.
Yes, but it is a different version, and lacks some of the useful properties and facilities of the one direct from Oracle.

---

### Post by mkvnmtr on 2010-04-15
If you are using gnome look for it in applications under system tools. The deb from Sun is called Sun Virtual Box on the menu.

---

### Post by _0R10N on 2010-04-15
You should download the virtualbox-3.1 package from the repositories, adding previously the finger-print given at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

I recommend this, because versions who don't require finger-print, lack of several features like USB support.

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-15
One more thing I almost forgot, you have to edit your user privileges in order to have access to USB devices. That can be done by entering System -> Administration -> Users & Groups / User Privileges. Then scroll the privilege list down and select the last option, "Use Virtual Box".

_0R10N >>

---

