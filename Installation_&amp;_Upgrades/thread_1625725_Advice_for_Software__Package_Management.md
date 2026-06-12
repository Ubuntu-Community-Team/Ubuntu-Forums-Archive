---
title: "Advice for Software / Package Management"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by dcaunt on 2010-11-19
Hi all.

I'm new to Ubuntu Server (though I have some experience with SUSE and Solaris) and I'm setting up a new server environment.  I'd like some advice about the best way to manage software installation / configuration, given the setup I'm trying to achieve.

First a little background about the setup I'm planning:  I intend to install Ubuntu 10.10 Server on a Dell PowerEdge 2950 that  has hardware-based RAID 1 (2 physical disks).  Using KVM, I then would like to install two guest servers (also Ubuntu 10.10 Server) on that host.  One will be a LAMP server.  The other will be a streaming media server (using Wowza Media Server).  The media being served is on a fiber-attached SAN (EMC Clariion) if that matters.

My foremost question (as I already mentioned) is about software management.  The documentation covers APT (APT-GET and APTITUDE), but I know there are other ways to go about it (from source, for instance).  Can anyone with LAMP experience give me advice about the best way to manage software installation / upgrade?  Is APT-GET the best way?  By "best" I mean easiest to use for day-to-day upgrades, as well as robust enough to allow for further configuration.  For example, I'm somewhat of a beginner when it comes to PHP installation/configuration.  If I'm going to be installing extensions later (OCI8 and CURL for now, but probably more later) would I be better off installing AMP from source, or will APT-GET allow me all the flexibility I'll need to configure/tweak extensions and other add-ons for Apache, MySQL, and PHP?

Any other advice that may come to mind, given the setup, is certainly welcome.

Thanks.
Dan

---

### Post by Zookalicious on 2010-11-19
Hi there dcaunt, first of all welcome to the Ubuntu forums! 

In regards to your concerns, apt-get is an extremely versatile program. I would advise reading the man pages on it so that you can become acquainted with all of its features and flexibility. apt-get is certainly the most straightforward and simple way to manage new installations and upgrades on your servers. In terms of flexibility, you are always able to add additional repositories to your software sources with a simple one line command
```

sudo add-apt-repository ppa:<repository-name>

```
or by editing your [FONT=monospace]"[/FONT]/etc/apt/sources.list" file and adding the new repositories. 

Adding additional repositories allows you greater control over the software available to you through apt-get, which provides the benefits of being able to update and upgrade all the software on your system simply by typing in 
```

sudo apt-get update
sudo apt-get upgrade

```

If for any reason there is not a repository available for the software you need, you can install build-essential and your linux headers to build any additional programs you require from source. However since apt-get consolidates and simplifies your updates, it is highly recommended that you use that method when available. 

I manage my file-server / minecraft server through SSH and apt-get and find it to be extremely straightforward and easy. If you have any questions, or want clarification (I know I went on a bit of a rant here), just let me know!

---

### Post by dcaunt on 2010-11-19
Thanks, Zookalicious!  I have one follow-up question to your explanation - I don't know if this is a PHP specific question, or if it would apply to most packages that require extensions/add-ons/etc.  Let's say that I use APT-GET to install AMP, but somewhere down the road I need to install a PHP extension from source.  The next time I upgrade PHP with APT-GET, will that blow away the extensions that I installed from source since the previous APT-GET upgrade?

---

### Post by Zookalicious on 2010-11-19
Generally speaking apt-get is intelligent enough to recognise that an application has been modified. When it tries to upgrade that program (AMP for instance) if it notices that you have patched it, it will automatically ignore that update and inform you that the program could not be upgraded. It should then offer to do a partial upgrade, which will get all of your other software up to date, but ignore the one that you made changes to. 

The plus side to this is that you do not lose your patches, the downside is that once you have modified the application, you must manually update it, or reinstall it with apt-get, thus losing your patch. You obviously seem to have a firm grasp of the more manual side of things though, so I don't think that is a massive concern for you ;)

EDIT: Also often plugins and extentions are available through apt-get which will take care of them for you. To make your life easier, its always worth checking to see if you can install the extension you need this way first!

---

### Post by dcaunt on 2010-11-19
Thanks again.  I wouldn't have expected it to recognize changes, but that's a nice feature to have.  I should have so few packages that might need manual patching, that it will be easy to remember when it comes time to upgrade.  I'll just have to document the changes I make so that I can re-apply them after upgrading.

---

### Post by Zookalicious on 2010-11-19
Sounds great, glad I could help. :D

---

