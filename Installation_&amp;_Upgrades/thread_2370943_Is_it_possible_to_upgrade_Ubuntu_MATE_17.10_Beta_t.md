---
title: "Is it possible to upgrade Ubuntu MATE 17.10 Beta to Ubuntu MATE Stable w/o reinstall?"
date: 2017-09-08
forum: Installation &amp; Upgrades
---

### Post by epicdragon44 on 2017-09-08
Is it possible to upgrade Ubuntu MATE 17.10 Beta to Ubuntu MATE 17.10 Stable (when it comes out later) without reinstalling?

If so, how?

Thank you!

---

### Post by oldfred on 2017-09-08
You do not have to do anything. Normal updates will update it to current version.

But as the development version, it has installed many apps perhaps multiple times, many kernels and changed many settings. So log files may already be larger than normal. 
If you are good at housecleaning then you should be ok, but I prefer to just reinstall so everything starts fresh. 

I do have data in separate data partition and scripts to reset most of my settings. If you made a lot of settings changes be sure to have good backups particularly /home. But that should be your normal practice anyway.

---

### Post by epicdragon44 on 2017-09-09
I currently have the Ubuntu MATE Beta Installation split across three partitions which occupy my whole hard disk collectively: being Root, Home, and Swap

By normal updates, do you mean apt-get dist-upgrade, or apt-get update && apt-get upgrade?

Also, would you recommend me personally upgrade from within the distro (using stuff like the commands above) or would you recommend me reinstall?

I know this may sound repetitive, but I want to know the best/clearest path before me.

Thank you! :D

---

### Post by deadflowr on 2017-09-09
> By normal updates, do you mean apt-get dist-upgrade, or apt-get update && apt-get upgrade?
apt-get update and/or either apt-get upgrade or apt-get dist-upgrade.
The difference between the two (apt-get upgrade and apt-get dist-upgrade) aren't what you may think they are, as they both only update the software for the current version of Ubuntu.

(Or use the update manager/software updater/whatever it's called in mate.)

As stated already, you're on 17.10 now so that's what you'll be on when it's released, officially.
Only difference is you'll get all the cruft (kernels, etc) that come along during the development cycle.
 
One thing I could say about reinstalling is the developers are always looking for users to help test the installer images
[https://wiki.ubuntu.com/Testing/ISO]("https://wiki.ubuntu.com/Testing/ISO")
[http://iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/")

So something like that is something to think about.
But you're fine either way.
Your choice, now.

---

### Post by epicdragon44 on 2017-09-10
Alright. I'll just upgrade packages from command line then, unless i break something between now and October,

Thank you to all!

---

