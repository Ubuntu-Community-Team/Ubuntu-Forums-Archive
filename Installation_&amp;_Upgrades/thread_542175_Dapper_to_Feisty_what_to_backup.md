---
title: "Dapper to Feisty: what to backup ?"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by key7 on 2007-09-03
Hi,

I know this may sound as a simple question, anyway, please, bear with me.
I am an user of Dapper 6.06 LTS and i want to upgrade to a newer version of ubuntu (the 7.04 or the next LTS...).

The thing is that i spent a lot of time customizing the distro the way it is now (for instance, the installed programs, the chat logs, all the usernames and passwords, bookmarks, the "open with" preferences, the skins....) and, if i do a clean install, i have to start everything from scratch again.

I thought to back up on my external hard drive all mine /home directory (all my personal data are there), but i am afraid that, acting like that, i will leave out something...

What do you think is the best way to retain all the customizations a user makes ?

Thanks in advance

---

### Post by Pumalite on 2007-09-03
I think you can only save /home. Might be wrong. I would go for a clean install personally. Upgrades are messy. Hard drives full of litter.

---

### Post by key7 on 2007-09-06
Thanks.
There is a thing I still don't get.

Once I have installed he latest Ubuntu, when the next release will come out, an apt-get dist upgrade (or using the upgrade manager) will be enough to be "updated" without a lot of hassles or is better to always start from scratch (like with Windows) ?
I am asking that because i want to know if to do the whole process every 6 months...

Thanks in advance

---

### Post by zvacet on 2007-09-06
First,you don´t have to do it every 6 months.If you are satisfied with version you are runing you can stick with it.As far I know from this forum there is people wich have problems with upgrading via net.I tryed both methods ,and never have problems.Maybe I was lucky.But you can try to upgrade from alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807]("http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807")

---

### Post by jis on 2007-09-07
key7, I suppose the only way to upgrade from Dapper to Feisty (or later) directly is clean install. Some people report that you can keep your /home, if it is on separate partition. See [here]("http://ubuntuforums.org/showthread.php?t=494139").

If your /home is not on separate partition, check [this]("http://www.psychocats.net/ubuntu/separatehome") out.

---

### Post by tgalati4 on 2007-09-07
Make a backup of /etc, but only use it for reference.  It contains a lot of configuration files for services that you will need in the new installation.  Don't simply copy /etc over to the new distro, since newer versions of these services will have newer configuration files.  You will need the backup copy to see what changes you need to make:  printers, file sharing, etc.

---

