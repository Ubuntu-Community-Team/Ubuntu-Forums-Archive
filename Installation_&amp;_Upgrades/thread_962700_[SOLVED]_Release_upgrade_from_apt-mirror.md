---
title: "[SOLVED] Release upgrade from apt-mirror"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by lykwydchykyn on 2008-10-29
I have a local mirror of the Intrepid and hardy repos that I set up using apt-mirror.  I'd like to use it to do my release upgrades to intrepid.

For some reason, I've never been able to convince Ubuntu in the past to use my repos when I use the do-release-upgrade script.  It treats my local server as a third-party server rather than as the actual main repository servers (in other words, if you look in synaptic, my local repos are all listed under "third party software" and the "ubuntu software" server are all unchecked).

Is there a way to tell ubuntu to treat my local server like the actual repositories?  I don't really want to drag all those packages across the internet each time I upgrade, particularly on release day when the servers are likely to be slammed.

EDIT:  I'm starting to think from a launchpad search that this isn't possible.  Say it ain't so.  Surely the list of official mirrors is somewhere on the system and I can put my own server in there.  Anyone?

---

### Post by lykwydchykyn on 2008-10-30
Alright, well, I have gotten a little help from the General forum and now I've got a solution hacked together.  

I added my repository to /usr/share/python-apt/templates/Ubuntu.mirrors.  Then I went into synaptic and chose my mirror as the one to use.

Now do-release-upgrade is using my server!  Rock on! :guitar:

This will save Canonical a bit of bandwidth.

---

