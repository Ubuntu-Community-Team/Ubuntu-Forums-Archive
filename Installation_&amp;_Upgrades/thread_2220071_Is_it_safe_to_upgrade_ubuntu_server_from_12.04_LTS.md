---
title: "Is it safe to upgrade ubuntu server from 12.04 LTS to 14.04 LTS without backup?"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by niren on 2014-04-26
[COLOR=#333333][FONT=UbuntuRegular]Right now we have ubuntu server 12.04 LTS in our office server. This server is important for our production, so I need to upgrade server to 14.04 LTS carefully. I did setup LXC containers and each container have their own process running(e.g gitlab, database,..). What I want to know is, should I take any backup before update, if yes how should I take backup since I told that I have installed containers and each have process running I have no idea how to take backup. It is first time for me to upgrade server OS and also I'm new to ubuntu. If some thing goes wrong our production will get effect badly.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]And also I want to know how long would it take to upgrade.[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-04-28
I think your biggest problem is your seeming lack of regular backups. You seem to be at high risk of data loss regardless of whether you migrate to 14.04 or not.

See the lxc-backup and lxc-restore (or lxc-snapshot) commands for simple backup and restore capability.

---

### Post by stozz2 on 2014-04-28
As a system Administrator it is imperative that you keep a diary consisting of any software installations that you have done including those done in a terminal,
no matter how small.

You are best of spending time making this list of those software installations that you have installed, including any Terminal Commands entered to install and update the software.

I would also recommend that you back up the files (only those files where work has been inputted into) Word type documents ; spreed sheets; extra
Its also best to have a file directory trees exclusively for those types of work files,( *that has been preformed by employees*) as it makes backing up your work so much simpler...
You should also keep a list of those who log onto the system as well.

Once you have those lists go a head and do an upgrade.
Also **beware** that some software does not upgrade well..

If you don't have those lists, when system faliure occures getting the system up and running again can be a nightmare

When you have your list of software and terminal type installation commands, proceed with your update confidently

---

