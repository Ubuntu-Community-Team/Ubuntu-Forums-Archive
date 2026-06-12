---
title: "Best fit for Ubuntu version on server"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by fcoury on 2008-01-15
Hello everybody,

This is my very first post on this forum, so first of all a warm hello to everyone here.

I have used Ubuntu before on desktop and I really like this OS. My problem is that I have an old PC laying around for quite a while and I would like to use it as a network server and run common servers on it, like: 

- A SVN server for my network
- Tomcat web server for Java development
- Apache web server for Python development

And also, probably run a BitTorrent clone that fits nice to a server, so I can download my stuff on a dedicated server.

The hardware on that machine is pretty old: it is an AMD Athon (can't remember how many Mhz tho) with 256Mb ram and about 20Gb hard drive.

What would be the best fit for that hardware: any Ubuntu version or another distribution?

Thanks in advance.

Best reards,

Felipe Coury.

---

### Post by dgray_from_dc on 2008-01-15
Xubuntu is probably the best fit.  However, you'll find that normal Ubuntu/Kubuntu will run, if you don't mind a little lag.  I find that the heavier versions offer more in the way of GUI interfaces to the system settings.

I run a file server with a 733Mhz P3 and 128MB of RAM.  I use Xubuntu with the Kubuntu-Desktop package installed.  This way I get quick and functional with Xfce and full featured ease of use when I need it with KDE.

---

### Post by fcoury on 2008-01-15
dgray,

Great news. I will start downloading Xubuntu right away. Is it easy to install that additional package? Any references I can follow or is it straightforward?

Thanks again!

Cheers,
Felipe.

---

### Post by dgray_from_dc on 2008-01-15
Once you've installed Xubuntu, use the Synaptic package manager to install either ubuntu-desktop (Gnome) or kubuntu-desktop (KDE).

To install the ubuntu-desktop package manually from the command line

```
sudo apt-get install ubuntu-desktop
```

Keep in mind to build a server, you'll probably still need to roll up your sleeves and dig in as there aren't GUIs for everything.  

I'd also recommend webmin for a GUI-like web interface that can be accessed by remote.  For some reason, it's not part of the ubuntu repositories, but you can find it on google, download the .deb package and install from any ubuntu variant.

---

### Post by fcoury on 2008-01-15
Cool, very nice tips. I will definitely download the webmin package. Regarding the GUI, I have used Gnome before, but would like to try KDE. What is you opinion on both? What do you see as pros and cons of one over the other?

Again, thanks so much for helping me out on this matter. ISO image is at 70% downloading at superb (at least for my connection speed) 242KB/sec.

---

### Post by dgray_from_dc on 2008-01-15
I prefer KDE only because I've been using it more than Gnome for a few years.  In ubuntu, Gnome is well put-together and very very user friendly.  However, I use KDE because I already know where everything is and I find it easier to customize.  I really couldn't give you a good comparison because I don't use Gnome much at all.  I can tell you that it all boils down to personal preference because both are wildly popular and equally as developed and stable.

---

### Post by fcoury on 2008-01-15
Understand. I will think it through and make up my mind. Thanks a lot for all the information. I have already downloaded webmin and will install it after finishing the SO install.

Best regards,
Felipe.

---

