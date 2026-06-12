---
title: "Web server: upgrade from 9.04"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2011-08-05
Hi all

I have a client with a small dedicated server running 9.04, which I want to upgrade for obvious reasons. It's got the LAMP stack installed, as well as bind for DNS. Apart from that it's pretty vanilla.

Do you think I'll be alright to do a dist-upgrade? Will all configs for the above packages be held intact? It's quite important that there is no/minimal downtime on this server so I'm anxious to be sure about the upgrade before I do it.

Thanks for your help!

---

### Post by melat0nin on 2011-08-13
bump

Anyone have any thoughts on any obvious pitfalls I should avoid? Any help appreciated!

---

### Post by Old_Grey_Wolf on 2011-08-13
Take a look at this thread. It appears to work in the end. [http://ubuntuforums.org/showthread.php?t=1819834](http://ubuntuforums.org/showthread.php?t=1819834)

---

### Post by Old_Grey_Wolf on 2011-08-14
> **melat0nin said:**
> 
Do you think I'll be alright to do a dist-upgrade? Will all configs for the above packages be held intact? It's quite important that there is no/minimal downtime on this server so I'm anxious to be sure about the upgrade before I do it.


I haven't seen any activity on this thread for a while; therefore, I thought I would bump it.

As you can see from the thread I linked to, it is not straightforward to upgrade from an end-of-life release. You also have a LAMP stack that has Apache, MySQL, and php, I wouldn't call that vanilla. I have never tried to upgrade an Ubuntu install that was not a vanilla desktop install and even vanilla desktop upgrades have failed.

I would recommend planning for the worst outcome. If it is a server, I would assume it is being backed up, if not, back it up. Plan on reinstalling the LAMP stack and configuring bind. Basically have a written set of instructions ready for rebuilding the system from scratch.

I would consider imaging the client's system to removable media, upgrading or re-installing Ubuntu using that image on your own system, testing it, then re-imaging the client's server from the removable media, and transferring any data that has changed while you were doing this from a fresh backup. If you don't know how to do this; then, I think you may have taken on a "client" with requirements beyond your ability.

---

