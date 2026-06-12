---
title: "Install Gnome on 7.10 server"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by jahshuah on 2008-02-20
I have a somewhat unique predicament in that I have searched the forums and numerous posts point to firing up the command line and issuing the command:

```
sudo apt-get install ubuntu-desktop
```

and that would be great, however, I have a server in a lab that cannot be connected to the internet for security reasons.  I have both the 7.10 server cd as well as the 7.10 desktop cd.  I really don't care what gets installed if I were to issue the above command - I'm not hard-pressed about a minimal gnome installation. I just want the GUI on the server.  Really simple.

Now, is there a way with the two CD's that I can install gnome on the server and not have to resort to the internet (again, that's not really an option anyhow)?  If anyone knows how this can be done, they are worth their weight in gold.

Thanks in advance.

---

### Post by ajgreeny on 2008-02-20
If you had the alternate install CD you could use that, but not, I'm afraid the desktop CD.  Your only option is to download all the packages needed for ubuntu-desktop onto another internet capable machine and then use that CD as a repository when using apt-get.  Unfortunately I don't know the necessary syntax etc to add the CD to an apt-get session, but someone else will, I'm sure of that.

---

### Post by aysiu on 2008-02-20
The quickest way, in your situation, would be to install from the Desktop CD *over* (i.e., in place of) your current server installation.

You cannot simply *add* the Gnome desktop to your server installation without an internet connection or the Alternate CD.

---

### Post by jahshuah on 2008-02-20
Downloading the alternate cd isn't a problem.  I have an internet connection...just not in the lab.  I'll download the alternate cd tomorrow morning.  In the meantime, does anyone know where I can find instructions on using the alternate cd?  Thanks again to all who replied already.

---

### Post by aysiu on 2008-02-20
> **jahshuah said:**
> Downloading the alternate cd isn't a problem.  I have an internet connection...just not in the lab.  I'll download the alternate cd tomorrow morning.  In the meantime, does anyone know where I can find instructions on using the alternate cd?  Thanks again to all who replied already.
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by jahshuah on 2008-02-21
> **aysiu said:**
> ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

The alternate CD is downloading right now.  I'll give that a try once I have the .iso burned.  Thanks again!

---

