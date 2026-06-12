---
title: "What's with Software Sources. Cannot tick security updates"
date: 2008-07-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-05
Security sources are listed under third party software, and under updates it is not possible to tick security. 

Anybody else noticed this.

---

### Post by plun on 2008-07-05
There are no "formal" security updates for development versions.

But... upstream updates comes faster to a development version.


For formal security updates there are also strange time-gaps for
a release.

I have seen it with several vulnerabilities at **Secunia**, Redhat/Novell
are much faster to correct versions.

[http://secunia.com/](http://secunia.com/)

---

### Post by philinux on 2008-07-05
How come the security repo's are listed under third party software, and  not possible to tick security.

---

### Post by plun on 2008-07-05
> **philinux said:**
> How come the security repo's are listed under third party software, and  not possible to tick security.

Well, its ticked for me....:)

But there are no reasons to have security updates for unstable development.

This is the normal procedure (for stable released versions)

[https://wiki.ubuntu.com/SecurityUpdateProcedures](https://wiki.ubuntu.com/SecurityUpdateProcedures)

Security updates are also trigged from Main to avoid time-gap because of
servers left behind.

But for development its just to roll out fixes.... if it brakes, it brakes...:)

---

### Post by uBeer on 2008-07-05
Well, I don't know if it's related, but I can't seem to select security updates at all in Hardy. Or is it related to the backports that I have selected?
In my sources the security repositories are checked, but not in the update field... kinda weird...

---

### Post by plun on 2008-07-05
> **uBeer said:**
> Well, I don't know if it's related, but I can't seem to select security updates at all in Hardy. Or is it related to the backports that I have selected?
In my sources the security repositories are checked, but not in the update field... kinda weird...

For Hardy you have several security updates.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)


A default Hardy sources.list should include this  

[http://de.pastebin.ca/868272](http://de.pastebin.ca/868272)

Check that you have these.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

```

sudo gedit /etc/apt/sources.list
```

---

### Post by ccw on 2008-07-05
> **plun said:**
> For Hardy you have several security updates.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

A default Hardy sources.list should include this  

[http://de.pastebin.ca/868272](http://de.pastebin.ca/868272)

Check that you have these.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

```

sudo gedit /etc/apt/sources.list
```


You can put those on one line. Here are my hardy sources...

```

#8.04 Hardy Heron LTS 
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

---

### Post by uBeer on 2008-07-05
Putting them on one line is really convenient!
I just looked at my sources.list and the security repos are enabled, but it's just that the box with security updates is not checked.
I'm gonna find out if there is a bug like this somewhere.

---

### Post by basblplayr on 2008-07-07
Has anyone gotten a good explanation for this?  I can't seem to figure it out either.

---

### Post by philinux on 2008-07-08
It's happened to the point release too, this must be a bug.

[http://ubuntuforums.org/showthread.php?t=852947](http://ubuntuforums.org/showthread.php?t=852947)

---

### Post by steeleyuk on 2008-07-08
I don't remember seeing this bug in 8.04 but its appeared here too in 8.04.1. The repositories are added fine but its just that the checkbox won't display a tick.

---

### Post by fluteflute on 2008-07-08
Bug Report: [https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093](https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093)

---

### Post by itsjustarumour on 2008-07-08
> **steeleyuk said:**
> I don't remember seeing this bug in 8.04 but its appeared here too in 8.04.1. The repositories are added fine but its just that the checkbox won't display a tick.

I can confirm this bug on 32-bit Hardy 8.04.1 since recent updates.  All three of my Ubuntu installs are demonstrating the same problem - I go to System>Administration>Software Sources>Updates tab, and I am unable to check the tick-box for "Important security updates (hardy-security)".

---

### Post by Rocket2DMn on 2008-07-08
> **fluteflute said:**
> Bug Report: [https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093](https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093)

I triaged and set the priority on that bug just a few hours ago, so work should begin soon on it.  It is a Hardy as well as Intrepid problem.

---

### Post by WolfWitch on 2008-07-23
FWIW- happening on 64-bit Hardy as-well.

I have the same problem on three machines. Two have been upgrades from Feisty through Gutsy to Hardy, so my sources.list was a mess on them anyway. Even after cleaning it up and verifying the Security repository is in the list, I can't tick the checkbox for it in the GUI.

---

### Post by smooth3006 on 2008-07-28
> **WolfWitch said:**
> FWIW- happening on 64-bit Hardy as-well.

I have the same problem on three machines. Two have been upgrades from Feisty through Gutsy to Hardy, so my sources.list was a mess on them anyway. Even after cleaning it up and verifying the Security repository is in the list, I can't tick the checkbox for it in the GUI.

so is this problem fixed yet ?

---

### Post by Rocket2DMn on 2008-07-28
A fix was released in the hardy-proposed repositories.  Please see the bug report:
[https://bugs.launchpad.net/ubuntu/hardy/+source/python-apt/+bug/244093](https://bugs.launchpad.net/ubuntu/hardy/+source/python-apt/+bug/244093)

---

### Post by philinux on 2008-07-29
Interestingly I did a reinstall of Hardy 2 weeks ago and the problem appears fixed. :)

---

### Post by smooth3006 on 2008-07-29
mines not fixed and i checked the hardy proposed updates in software sources. i still can't check the box so i don't know if it's enabled or not ?

---

### Post by philinux on 2008-07-29
Click the link in post 17.

The security updates are added and working, just not in the right place.

It's cosmetic to a degree but needs fixing quick for new users

---

### Post by smooth3006 on 2008-07-29
> **philinux said:**
> Click the link in post 17.

The security updates are added and working, just not in the right place.

It's cosmetic to a degree but needs fixing quick for new users

i don't want to sound like an idiot but where is the download to the fix ? i don't see it on that page ?

---

### Post by cariboo on 2008-07-29
Here it is:

> Temporary fix:
1) sudo sed -e 's/security\.ubuntu\.com/archive\.ubuntu\.com/g' /etc/apt/sources.list > /etc/apt/sources.list.tmp
sudo mv /etc/apt/sources.list.tmp /etc/apt/sources.list
sudo apt-get update

Jim

---

### Post by smooth3006 on 2008-07-29
> **cariboo907 said:**
> Here it is:



Jim

thanks worked perfectly and also cleaned up my source list a bit i see. :)

---

### Post by Kevbert on 2008-07-29
Here's the official response for not having security updates in Intrepid (after I raised a bug report):
> Thank you for using Ubuntu and taking the time to report a bug. Intrepid
is the current development release of Ubuntu and as such, developers
will commit security fixes directly to the archive.  It is only after
release that the other pockets like 'security' and 'updates' are
available.

** Visibility changed to: Public

** This bug is no longer flagged as a security issue

** Changed in: ubuntu
       Status: New => Invalid

-- 
Unable to activate Intrepid-security updates
[https://bugs.launchpad.net/bugs/251945](https://bugs.launchpad.net/bugs/251945)

Security updates work fine for me on Hardy 64 bit.

---

### Post by PC_load_letter on 2008-10-24
Had this same problem on Ubuntu 8.04.1 amd64, the code Jim supplied took care of this problem. Thanks.

---

