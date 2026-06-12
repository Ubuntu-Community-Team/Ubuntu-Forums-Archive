---
title: "ubuntu 12.04 does not boot (after reinstalling nautilus ?)"
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by lalorca on 2013-04-15
Hello all,

Very sadly, ubuntu (64 bits) does not boot correctly on my (dell latitude) laptop. I can get to the screen where I can generally enter my login, but all I get is a (quasi-subliminal) black screen, and then I am back to the login screen. This is identical if I try to login as a guest. Here is what I could read from the black screen (which vanishes quasi-instantly, so I am not sure about everything):


Error: no running sessions found
Bye
NX server-Version 3.2.2-74-SVN 08 (GPL, using backend 3.5.0)
Bye
speech-dispatcher disabled: edit/etc/default/speech-dispatcher
[LIST]
[*]starting Virtualbox kernel modules
[/LIST]
sared disabled: edit/etc/default/sared
[LIST]
[*]starting anacCh)ronistic cron
[*]stopping anacCh)ronistic cron
[*]Checking battery state...
[*]Stopping system V runlevel
[*]starting CUPS printing spooler/server
[/LIST]


Before I shut down Ubuntu for the last time, two unusual things that may or may not be related to this occurred:
a) I could not use sftp with nautilus to connect on a server (but ssh and scp from terminal, were fine)
b) I tried to fix this by uninstalling and reinstalling Nautilus from the Update manager


Two questions:
1) is there any hope to not have to reinstall everything, and if yes, is it possible to recover the data (to prevent angry comments: I have backups, but I would still like to know i have more than one copy right now)
2) are the ' Bye' statements in the black screen ironical (-_-) ? (Sorry, I am trying to be a bit positive)

Thanks for any help,

Laureline

---

### Post by darkod on 2013-04-16
I'm not sure how to fix this, and I don't see how reinstalling nautilus could affect the login itself.

But for data recovery, you should be able to easily read all data from live mode, and you can copy it to any external hdd. Just be careful when copying if you want to keep ownership and permissions intact. it will also depend on the filesystem of the destination disk, since ntfs for example can't keep linux permissions.

---

### Post by lalorca on 2013-04-16
Thanks for your answer.

I am indeed going to reinstall ubuntu after backing up my home directory.

---

