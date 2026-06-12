---
title: "Apt-get broken"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by mnml on 2009-12-26
Hi,
My apt get is not listing any software installed anymore, and when I want to install something I get:

> 
E: Internal Error, Could not perform immediate configuration (2) on libattr1


My /var/lib/dpkg/status file is empty, Is there anyway I can rebuild the index? :(

---

### Post by gradinaruvasile on 2009-12-26
Try:

In a terminal:

sudo apt-get update

---

### Post by gradinaruvasile on 2009-12-26
But i dont think it will help...

How did you get in this situation?

---

### Post by phillw on 2009-12-26
> **mnml said:**
> Hi,
My apt get is not listing any software installed anymore, and when I want to install something I get:



My /var/lib/dpkg/status file is empty, Is there anyway I can rebuild the index? :(


Hi, and ouch .....

when i had my apt-get hosed i did this ...

```

cd /var/lib/dpkg
sudo mv status status.bak
sudo mv status-old status
sudo apt-get update

```
It is from this thread --> [http://ubuntuforums.org/showthread.php?t=1352725](http://ubuntuforums.org/showthread.php?t=1352725)

It got me out of 'jail'  Hope it as successful for you.

Regards,

Phill.

---

### Post by gradinaruvasile on 2009-12-26
But read here:

[https://answers.launchpad.net/ubuntu/+source/synaptic/+question/12093](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/12093)

Its about rebuilding a blank status file. There are some scripts there that seemed to work for that guy.

---

### Post by gradinaruvasile on 2009-12-26
> **phillw said:**
> Hi, and ouch .....

when i had my apt-get hosed i did this ...

```

cd /var/lib/dpkg
sudo mv status status.bak
sudo mv status-old status
sudo apt-get update

```
It is from this thread --> [http://ubuntuforums.org/showthread.php?t=1352725](http://ubuntuforums.org/showthread.php?t=1352725)

It got me out of 'jail'  Hope it as successful for you.

Regards,

Phill.

IF he has status-old.

---

### Post by mnml on 2009-12-26
thanks for the help apparently status-old is empty too and I have no clue how it happened

---

### Post by phillw on 2009-12-26
> **gradinaruvasile said:**
> IF he has status-old.

Which he hasn't :-(

The other option in that thread is along the lines of how to recover a really messed up flash installation - Brute force.

But, I'd do a +1 for the method that you posted for trying to recover & will update my link that I use.

Thanks for the additional info,

Phill.

---

### Post by mnml on 2009-12-26
I found it in /var/backups , solved, I have no clue how It got there :confused:
thanks for the help guys

---

