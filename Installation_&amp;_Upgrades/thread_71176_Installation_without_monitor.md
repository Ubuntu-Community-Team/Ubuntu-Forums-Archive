---
title: "Installation without monitor"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by louiscyphre on 2005-10-02
Hi everybody,
I have a computer with cd drive and network card but without a monitor. Is it possible to install and control Ubuntu using a laptop via LAN?

Thanks in advance.

---

### Post by Chrissss on 2005-10-02
Well to control a Linux System via Linux is not a problem at all, but to installl it withou a monitor? Hm, can't you connect your system to a monitor while making the first steps of the installation?

CU
 Christoph

---

### Post by louiscyphre on 2005-10-02
Ok... I think I will use a monitor for the installation... but, what kind of interfaces to control the system? Only shell?

---

### Post by TristanMike on 2005-10-02
If you do the standard install, you get a whole desktop, that is very comparable to any other OS out there now, and not just the shell, though you do get that as well. If you do the more advanced setup, you can choose what gets installed, but that's as the title suggests, for more advanced users.
I hope this is what you were curious about.

---

### Post by louiscyphre on 2005-10-02
Thank you very much... 
Now... I install Ubuntu (standard) and... how to connect the laptop to the other machine?

---

### Post by Chrissss on 2005-10-02
Depends on what OS you're using on your notebook. If you want a fast and simple way to do stuff on your server. Use a ssh connection to your server. You've got to install the openssh server on your server

# sudo apt-get install openssh

and some ssh client software on your client. If your using linux on your notebook, you don't need to install something, ssh is most likely installed. If you're using windows, go get [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/).

Another possibility is configuring most stuff via a webbrowser. Yes, this is possible ;) You can install webmin (and many modules for it) via apt-get. Now you can access your server via the webbrowser of your notebook.

Last but not least you could use vnc. I quote the vnc homepage:
VNC (Virtual Network Computing) software makes it possible to view and fully-interact with one computer from any other computer or mobile device anywhere on the Internet. VNC software is cross-platform, allowing remote control between different types of computer. For ultimate simplicity, there is even a Java viewer, so that any desktop can be controlled remotely from within a browser without having to install software.

There are clients for windows and linux.
CU
Christoph

---

### Post by louiscyphre on 2005-10-02
Thank you Christoph!
I'm running Ubuntu on my notebook ;)
I think VNC is what I was searching for.

---

