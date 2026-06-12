---
title: "Update manager dist upgrade from local repo"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by XinefNarg on 2007-04-29
I have a local ubuntu repository in my office internal server, to speed updates in every workstation. Is it possible to make update-manager perform the dist update from the local repo? it disabled the local repo in sources.list and started downloading the update from official repo.

Thanks to all!!

Leo

---

### Post by spd106 on 2007-04-30
The only officially supported method is to use the upgrade manager, which as you've found will automatically alter the sources.list to the nearest official mirror.

You can use other sources such as your own repo, but you will have to do a normal dist-upgrade via synaptic or apt-get/aptitude. This method is not supported so there is no guarantee that it will work. You will increase your chance of success by removing third party repos and making sure that the ubuntu-desktop is installed first before upgrading. I would also suggest testing one machine first.

---

### Post by NeoTaoistTechnoPagan on 2007-05-01
Got this to work - just a moment ago.

I have Edubuntu 6.10 on my kids' PCs and wanted to upgrade it today. I have local mirrors of Dapper, Edgy, working on getting Feisty - but I do have the DVD image on the server.

I mounted the DVD image and have it shared using apache (the steps for this are beyond the scope of this topic IMHO - ask me for detail if needed.)

Here's what I have ...

server: 192.168.1.26

/ubuntu <-- repos for Dapper and Edgy.
/pub/ubuntu <--repos for feisty

The reason they are at different trees is well, apt-miirror kinda goofed when I tried to mirror another mirror close to me and it put the files under /pub/ubuntu. In hindsight now that I am thinking about it I could have just symlinked to /ubuntu/feisty - but then the /pool would be messed up - right?

Oh well - Will re-sync the mirror later so here goes:

edit your /etc/apt/sources.list and comment out all lines that have edgy in them.
Add the line for the server you want with the feisty repo.

do a ```
gksudo "update-manager -c -d" &
``` and then click on cancel if/when it complains about something broken.
Next, click on the dist-upgrade button. When it gets to the point where it asks to re-write the sources.list - say OK.

Upgrade should go fine - here it downloaded between 2000 and 4000K! I love having a 100M net with a switch! Can't wait to upgrade to Gigabit!

---

### Post by bryanl on 2007-05-01
take a look at apt-cache and apt-proxy

---

### Post by NeoTaoistTechnoPagan on 2007-05-03
> **bryanl said:**
> take a look at apt-cache and apt-proxy

And how do you use either of these when upgrading from Edgy to Feisty?

---

