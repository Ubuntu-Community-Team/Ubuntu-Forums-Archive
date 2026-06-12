---
title: "how to solve this trouble???"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by cookiez on 2011-04-09
It is impossible to install or remove any software. Please use the  package manager "Synaptic" or run "sudo apt-get install -f" in a  terminal to fix this issue at first.


// i'm typing "sudo apt-get install -f" but is useless 

Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Unable to lock the administration directory (/var/lib/dpkg/), is another process using it

Software index is broken

how to solve it??

---

### Post by prshah on 2011-04-09
> **cookiez said:**
> 
// i'm typing "sudo apt-get install -f" but is useless 
Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You cannot have two package managers running simultaneously (Eg, Synaptic and apt-get). Close Synaptic, and then try the apt-get command in a terminal; or use Edit-> Fix broken packages option in Synaptic.

---

### Post by Rubi1200 on 2011-04-09
Hi and welcome to the forums cookiez :)

As suggested by prshah.

Also, what version of Ubuntu are you using?

---

### Post by jeliocranch on 2011-04-10
Hi, I'm having the same trouble.  I'm just getting into working with the terminal, and used apt-get for the first time a week ago.  Since then, Update manager says apt-get has changed package indexes and it fails to download packages.
So I tried 

sudo apt-get update

and got this:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Reading this post, I thought perhaps Update manager was still open, so I closed it and tried again... same result.

ran top, but no other package managers show except apt-get.

Help?  My wife uses this machine and needs the GUI-based stuff to work.

---

### Post by Enigmapond on 2011-04-10
> **jeliocranch said:**
> Hi, I'm having the same trouble.  I'm just getting into working with the terminal, and used apt-get for the first time a week ago.  Since then, Update manager says apt-get has changed package indexes and it fails to download packages.
So I tried 

sudo apt-get update

and got this:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Reading this post, I thought perhaps Update manager was still open, so I closed it and tried again... same result.

ran top, but no other package managers show except apt-get.

Help?  My wife uses this machine and needs the GUI-based stuff to work.

Try re-booting and see if that releases it.

---

### Post by jeliocranch on 2011-04-10
Its been booted 6 times since update manager first failed.  Unfortunately, it hasn't helped.

---

### Post by plucky on 2011-04-11
> **jeliocranch said:**
> Its been booted 6 times since update manager first failed.  Unfortunately, it hasn't helped.

Try removing the lock file

From a terminal ```
cd /var/lib/apt/lists/
sudo rm lock
```

Then run ```
sudo apt-get update && sudo apt-get upgrade
```


Good Luck

---

### Post by jeliocranch on 2011-04-12
Thanks Plucky.

A friend just suggested that, I tried it and voila!  everything works wonderfully again!

I was told its likely a result of an abruptly terminated apt-get.  I'm trying to recall when that may have happened, but who knows.  I have a 5 year old who knows how to shut my stuff down so she can go play "Disney Princess" on the Disney site.

Either way, thanks!

---

