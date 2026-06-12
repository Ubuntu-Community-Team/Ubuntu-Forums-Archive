---
title: "MySQL broken after latest updates ..."
date: 2008-08-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David Tomic on 2008-08-24
Hi all,

I just installed some updates for MySQL [among other things] a few hours ago through the update-manager, and now MySQL is just refusing to start/run.

When the system boots up MySQL isn't running, and if I try and start it manually via 'sudo /etc/init.d/mysql start' then it just says [[COLOR="Red"]fail[/COLOR]], but doesn't provide any more information than that.

Is there some other log file which should provide more information about what's actually going wrong?

Synaptic says that the installed version of mysql-server is 5.0.67-0ubuntu1, which launchpad shows was just released earlier this morning.

Apologies if I've left out anything ... but this isn't really my area of expertise! ;)

---

### Post by David Tomic on 2008-08-25
Bump ... anyone?

---

### Post by sosriqwe on 2008-08-27
Updates broke mysql on my amd64 system too.  

mysql-common 5.0.67-0ubuntu2 is missing. mysql-server and mysql-client are not installable...

Does anybody have a fix|workaround?

---

### Post by forger on 2008-08-27
edit:
oops, my mistake!
didn't see it was the intrepid testing.. sorry

---

### Post by sosriqwe on 2008-08-27
..~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by sosriqwe on 2008-08-27
/etc/apt/sources.list.d/ is empty...

~$ cat /etc/apt/sources.list.d/*
cat: /etc/apt/sources.list.d/*: No such file or directory

---

### Post by sosriqwe on 2008-08-27
Oh, and I use Intrepid Ibex 64 bit with latest updates...

---

### Post by dinxter on 2008-08-27
certainly the amd64 versions will not install since some  5.0.67-0ubuntu2 packages are missing, the source is 5.0.67-0ubuntu3 as of yesterday so i'm guessing that build is in progress as we speak, hopefully a short wait for the full set of 5.0.67-0ubuntu3 packages

---

### Post by David Tomic on 2008-08-27
Hooray ... I was beginning to get awfully lonely in here all by myself!

Yes ... I'm AMD64 as well.  So it looks like we'll just have to sit tight and wait it out for a little bit longer.

---

### Post by sosriqwe on 2008-08-27
> **David Tomic said:**
> 
Yes ... I'm AMD64 as well.  So it looks like we'll just have to sit tight and wait it out for a little bit longer.

That's right. The question is "how long" now. But I also guess it will not last long...

---

### Post by dinxter on 2008-08-27
if someone is in dire need of a running mysql for some reason then you can downgrade any packages [here]("http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/") then 'pin' them and leave upgrading them until the full set of packages is available. be warned though, you may enter a dependency hell manually downgrading so on your own head be it! i'm running the 5.0.51a-3ubuntu5.2 versions myself, there were other dependencies to be manually resolved so i wouldnt recommend it unless its essential

---

### Post by erkiha on 2008-08-27
There was no need to resolv any dependencies manually for me just:

dpkg -i mysql-common_5.0.51a-3ubuntu5_all.deb 

and mysql is happy again.

---

### Post by dinxter on 2008-08-27
is this on amd64? the state of the broken dependencies is diferent compared to i386. just want to check i've not made too much work for myself :)

---

### Post by David Tomic on 2008-08-28
And we're back up and running again ... HOORAY!

---

