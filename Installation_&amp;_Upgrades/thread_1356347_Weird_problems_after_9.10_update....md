---
title: "Weird problems after 9.10 update..."
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by animix on 2009-12-16
I just updated from ubuntu 9.04 to 9.10. I updated it using the update manager. Anyway, here are some problems I have experience so far.

1. I don't have "ubuntu software center" install. It's supposed to be under the applications, but it isn't listed. I also check under the main menu app, but it isn't listed under there. I tried to open it using the terminal command, but it says the program isn't found. I don't know if there are any programs that are missing.

2. Administrative programs don't open. I tried to open Synaptic, update manager, or any program that requires a password. However, none of these open. It shows the starting administrative program in the task bar, but it never loads. 

However, I can open synaptic & update manager using terminal commands. I think it's a "gksu" issue. I tried to open update manager a few times, and killed the process after several unsuccessful attempts. I noticed that there were several gksu processes running on the system monitor. I assume that gksu is preventing the password dialog box from appearing on the screen.

---

### Post by egravede on 2009-12-16
If it doesn't compromise your data try to download and install a fresh copy of 9.10 or wget/apt-get what you need (if you haven't tried already).

Sounds like some lib files are missing or corrupt.  Really weird problem haha.

---

### Post by slakkie on 2009-12-16
To install the software center, just 

aptitude install software-center

I believe it is only present in the meta-package ubuntu-desktop, so if you don't run the Gnome desktop it is not automaticly installed.

You could try this method to see if you have any packages which have issues: [http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/](http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/)

---

### Post by animix on 2009-12-16
Thanks I just installed ubuntu software center. I am running the GNOME Ubuntu distro. I changed the kernal to the server edition a while ago, so I could use 4 gigs of memory. I think that's one of the reasons I didn't get the software center.

Someone said that the gksu thing could be the problem. I tried to reinstall it, but I still have the admin problem. I get this error when I type in "gksu"  

"/home/dennis/.themes/xqua/gtk-2.0/gtkrc:2083: error: invalid string constant "gradient", expected valid string constant"

Do you think this has anything to do with the problem?

Edit: ignore the xqua gtk thing. I changed my theme, and I don't get the error when i type gksu. I still can't access the administration programs using the menu.

---

### Post by animix on 2009-12-19
Bump...

I think I found the solution - [http://ubuntuforums.org/showthread.php?t=816708](http://ubuntuforums.org/showthread.php?t=816708)

I edited, and saved the hostfile. I rebooted, and I still can't access the administrative application. Here is what I currently have for the file. Tell me if I messed something up.

> 127.0.0.1 localhost.localdomain
127.0.1.1 Dell Inspirion

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Edit: I fixed the problem. I changed the "localhost.localdomain" to "localhost", and the password prompt comes up again.

---

