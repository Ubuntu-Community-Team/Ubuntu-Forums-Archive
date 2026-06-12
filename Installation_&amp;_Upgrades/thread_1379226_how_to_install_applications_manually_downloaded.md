---
title: "how to install applications manually downloaded"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by Shubhank on 2010-01-12
i am a quite new to ubuntu actually any linux os and i donot have net suporting it 
so i downloaded an app " vlc " for linux in windows a tar.bz file 
but it is not an installation wizard

---

### Post by Puck7 on 2010-01-12
Downlloading manually applications is not recommended, always use the repositries.

You have to download the apropriate file, usually it's .deb

Why not install vlc from the repository?
sudo apt-get install vlc

---

### Post by audiomick on 2010-01-12
vlc is available through synaptic. Install it from there, it is a lot simpler.

system> administration> synaptic package manager
use the search function to search "vlc"
click on the box next to the vlc entry that shows up.
click on apply in the task bar.

---

### Post by chrisinspace on 2010-01-12
> **Puck7 said:**
> Why not install vlc from the repository?
sudo apt-get install vlc

The command above is the fastest way to add the application, but being new to Linux, you might be more comfortable with the graphical approach.  

Go to System -> Administration -> Synaptic Package Manager.  In Synaptic, search for VLC.  Click the check-box next to vlc and choose 'Mark for Installation'.  Click the 'Apply' button the the toolbar.  You can see why Puck7 recommend the CLI since this requires a few more clicks, but both methods will install vlc.  The added benefit to using the repository is that when an update becomes available the package, you will be notified automatically.

The repository is definitely the way to go.  I've been using Linux for a few years now and very rarely compile applications. 

Edit: Oops...took me a few minutes to type this, so it looks like audiomick beat me to it. Gotta love the responsiveness of the Ubuntu forums! :)

---

### Post by drpjkurian on 2010-01-12
Hi Subhank

Double click that tar ball, you will be able to open the folder. In that folder you will see an install file. Please attach that file here in the post. I hope I will be able to help you.

Though it sounds difficult to install by tarball, It is actually easy.

---

### Post by Puck7 on 2010-01-12
> **chrisinspace said:**
> The command above is the fastest way to add the application, but being new to Linux, you might be more comfortable with the graphical approach.  

Go to System -> Administration -> Synaptic Package Manager.  In Synaptic, search for VLC.  Click the check-box next to vlc and choose 'Mark for Installation'.  Click the 'Apply' button the the toolbar.  You can see why Puck7 recommend the CLI since this requires a few more clicks, but both methods will install vlc.  The added benefit to using the repository is that when an update becomes available the package, you will be notified automatically.

The repository is definitely the way to go.  I've been using Linux for a few years now and very rarely compile applications. 

Edit: Oops...took me a few minutes to type this, so it looks like audiomick beat me to it. Gotta love the responsiveness of the Ubuntu forums! :)

So true so true, sorry (:

Maybe Software Center or Add/Remove is even more easier? Just some extra thoughts. (:

---

### Post by chrisinspace on 2010-01-12
> **Puck7 said:**
> So true so true, sorry (:

Maybe Software Center or Add/Remove is even more easier? Just some extra thoughts. (:

I would use your method, for sure, but I was just thinking a new user might want to ease into Linux before opening a terminal.  Although, you don't get a much easier introduction than installing an app with apt-get.

Of all the graphical methods, I like Synaptic the best.  It's easy for the uninitiated, but you can still kind of see what's happening behind the scenes for a greater understanding of the process.  The end result with all of these suggestions is the same, though.  So, I encourage new users to experiment and find out what works best for them.

---

### Post by mlentink on 2010-01-12
The OP does not have an internet connection, so synaptic and Software Centre are not going to work.

You might want to download a .deb file from here:
[http://packages.ubuntu.com/karmic/i386/vlc/download](http://packages.ubuntu.com/karmic/i386/vlc/download)

This assumes you're running a 32 bit system, otherwise use this one:
[http://packages.ubuntu.com/karmic/amd64/vlc/download](http://packages.ubuntu.com/karmic/amd64/vlc/download)

Once you have to .deb on your ubuntu system, simply double click it

---

### Post by audiomick on 2010-01-12
> **mlentink said:**
> The OP does not have an internet connection, so synaptic and Software Centre are not going to work.

Oops, didn't notice that. Should read more carefully...:redface:

---

### Post by Shubhank on 2010-01-18
thanks , but now i got lan and i have creared all the dependencies , and its running successfully

---

