---
title: "Reinstalling Ubuntu, Keeping Old Settings"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Uthalin on 2007-01-02
I ran into some issues installing new drivers when I was upgrading video cards.  As a result when I turn on my Ubuntu 6.10 install after the load screen I just get a blank screen, not even the OS without GNOME, just a blank screen, no cursor.  I however realized I could still ssh into the box and decided to immeditaly backup the entire filesystem onto a Mac on the network.   

In order to do this I just ran the following command.

sudo rysnc -a -v / username@192.168.1.101:/path/to/backups

What I am planning on doing is to reinstall Ubuntu using the exact same CD I used to originally install the computer.  What I'm trying to figure out is if I want to keep all my settings what files should I copy over to the original install.  I'm also planning on takeing this oppurtunity to replace my existing HD with a new one (my old one is starting to make some death sounds).  

So, what do I need to copy over?  What would be the best way to copy these files over?  I have new applications installed including stuff like new media codecs to play audio files and services (like the sshd server).  I'm OK with loosing all my X configuration files.  I'm just going to stat over with that.  Would it be possible to just copy everything over excpet the files that have to do with X, the graphics card, and the new HD?  What would be the best way to do that and what files do I need to ignore.  Basicaly I'm up for whatever you think the best way to solve this problem would be.

Also, if I was interested in trying out Kubuntu to get a feel for KDE would that just complicate things up way too much?

Thanks in advance for any help.

---

### Post by Uthalin on 2007-01-03
Any ideas?

---

