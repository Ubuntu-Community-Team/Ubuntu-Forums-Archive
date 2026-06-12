---
title: "upgrade went wrong"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2012-08-16
Hi, I ran update manager this morning. It somehow went wrong, and got stuck before it had finished. I rebooted, hoping that would fix it. Now I can't update. I went to the command line , but I get this:

pedro@pedro-bedro:~$ sudo apt-get update
[sudo] password for pedro: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
pedro@pedro-bedro:~$ apt-get purge
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pedro@pedro-bedro:~$ sudo apt-get purge
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
pedro@pedro-bedro:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
pedro@pedro-bedro:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
pedro@pedro-bedro:~$ 

Any tips out there??

---

### Post by Bucky Ball on 2012-08-16
Hmm. You attempted an update, *not *an upgrade. They are very different. Advise you change the thread title by editing the first post and hitting 'Go Advanced'. ;)

You are issuing purge and clean commands also. Update is not working so not sure if you are trying to achieve anything apart from fixing the update problem. Are you just attempting a regular update? 

Do you have Synaptics or SWCentre open while attempting this? If so, close and try again.

---

### Post by Pedroski55 on 2012-08-16
Sorry, did I write upgrade?? I was only doing an  everyday update.
Nothing else is open. I thought the command line would do it.

Anyway, after using Fedora for the afternoon, on rebooting Ubuntu, the problem had vanished.

But I'd like to know how, say, apt-get locks the process so that another instance cannot take over or alter anything. 
How does it do that??

---

### Post by cortman on 2012-08-16
> **Pedroski55 said:**
> Sorry, did I write upgrade?? I was only doing an  everyday update.
Nothing else is open. I thought the command line would do it.

Anyway, after using Fedora for the afternoon, on rebooting Ubuntu, the problem had vanished.

But I'd like to know how, say, apt-get locks the process so that another instance cannot take over or alter anything. 
How does it do that??

Info on the apt lock [here]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/").

---

### Post by Bucky Ball on 2012-08-16
> **Pedroski55 said:**
> 

Anyway, after using Fedora for the afternoon, on rebooting Ubuntu, the problem had vanished.

But I'd like to know how, say, apt-get locks the process so that another instance cannot take over or alter anything. 
How does it do that??

Perhaps only one instance of apt can be open at a time.

Glad to hear problem's gone away even if the original problem is still unknown.

---

