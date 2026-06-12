---
title: "kubuntu and apt-get"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by wonk-o-matic on 2007-02-05
I've always used apt-get to update, but see some posts for gnome users that apt-get isn't the "official" update tool for the dist-upgrade.

Soooo, there's an "official" update tool, and it isn't the traditional Debian apt-get?

That just seems so wrong!  Have I misundertood something?  I thought the gui stuff just ran apt-get in the background.  I'm worried that my system could be all goofed up.

Thanks, 
wonk

---

### Post by bapoumba on 2007-02-05
Hello, what do you call "official update tool for the dist-upgrade" ?

---

### Post by wonk-o-matic on 2007-02-05
$ gksu "update-manager -c"

See: [http://www.ubuntuforums.org/showthread.php?t=286599](http://www.ubuntuforums.org/showthread.php?t=286599)

---

### Post by bapoumba on 2007-02-05
[http://www.ubuntuforums.org/showpost.php?p=1694467&postcount=50]("http://www.ubuntuforums.org/showpost.php?p=1694467&postcount=50") ;-)

---

### Post by Lil_Eagle on 2007-02-05
There is a common myth that most users believe is true in all Debian based distributions and that is that apt-get is the preferred way way to fetch and install packages from the command line.

That was true in the Debian Woody days.  Since the release of Sarge, aptitude has been the recommended tool, simply because it keeps track of dependancies so when you remove software, if no other software is using them, they will be removed as well.

There is a very good example [here]("http://www.psychocats.net/ubuntu/aptitude")

If you're using the GUI (KDE in your case) then Adept or Synaptic are the normal methods.  Personally I prefer Synaptic, even though I use KDE as my default desktop.

---

### Post by wonk-o-matic on 2007-02-05
Thanks for the good answers.  

I'm curious, can the update-manager be run in KDE?  I have heard that applications built for gnome should be able to run in KDE, but that doesn't sound right, to me.  (...and what about KDE to gnome?)  

I know that apt-get had a lot of problems with the Edgy upgrade.  Is there any data about how successful other methods were?

---

### Post by bapoumba on 2007-02-06
Synaptic is GNOME "specific", as a GUI to manage packages, and Adept runs on KDE. They are both GUI to apt-get.

Now, GNOME uses gtk+ graphiclal libraries when KDE uses gt. So you can install GNOME packages on KDE, and KDE packages on GNOME. But, in each case, you'll have a whole load of libraries installed, and it may look ugly in your current environment. Should work though.

[http://en.wikipedia.org/wiki/GTK%2B]("http://en.wikipedia.org/wiki/GTK%2B")
[http://en.wikipedia.org/wiki/Qt_%28toolkit%29]("http://en.wikipedia.org/wiki/Qt_%28toolkit%29")

As far as update-manager, I do not know how it is handled by KDE (never used KDE ;)). I'll check.

---

### Post by Lil_Eagle on 2007-02-06
You're right that Synaptic belongs with Gnome.  So does gedit.  I use both of them in my kubuntu installation mainly because I like them.  There's no reason you can't run gnome applications in a KDE environment, and vice versa.  Granted, you're system will have to load the libraries of the other DE to run them, but so what?  Unless of course you're running on a 600mz celeron with 64MB of ram.  Then you'd be better off not using KDE or Gnome.

---

### Post by Mark C on 2007-02-22
adept has an updater similar to GNOME's update-manager. It is the official updater tool for KDE.

In my opinion, adept just sucks. If ever you want to use Synaptic and the GNOME update-notifier instead, press f2 and run update-notifier. If you set your KDE settings to restore sessions which is the default, it will run automatically everytime you log in to your desktop.

---

