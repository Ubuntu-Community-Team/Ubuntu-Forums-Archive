---
title: "Installing Ubuntu desktop on Kubuntu base, weird issues..."
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by Robert A. Morin on 2007-02-24
I was wondering why this happens, I have Kubuntu Dapper as my primary Linux OS on my external hard drive.  However, I'd like to install the GNOME/Ubuntu desktop on top of it.  For some strange reason, it doesn't even seem to want to download for me...  Does this type of dual-screen even exist on this base?  I mean, I know that you can install Kubuntu on the Ubuntu base, and that was successful when I was using Edgy Eft.  However, I'm looking to install the other way around, this time with Dapper (I seem to prefer Dapper over Edgy for some strange reason).  I did the sudo apt-get install ubuntu-desktop bit, but it just doesn't seem to like me doing that, for some strange reason...

---

### Post by aysiu on 2007-02-24
Can you be more specific than this? > it doesn't even seem to want to download for me...  > but it just doesn't seem to like me doing that Post (copy and paste the text) the output of these terminal commands? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by linux_kid on 2007-02-24
What type of error are you recieving?

---

### Post by Robert A. Morin on 2007-02-24
Okay, I'll try doing that, I mean, I did the apt-get, but aptitude seems to work better, eh?  You may be on to something here, and thank you for that.  I'll do that later on...

As for the error I'm receiving, I'll have to try running it again, I'm in, :cough: Vista :cough: at this point, I'll have to go into my Kubuntu boot to post it.

---

### Post by aysiu on 2007-02-24
It's not about *aptitude* versus *apt-get* (though that *may* make a difference possibly). It's about posting here whatever errors you're getting.

It's not enough to say it doesn't like you or doesn't seem to work. Unless we see errors, we can't help you solve your problem.

---

### Post by linux_kid on 2007-02-24
Please copy, paste & post the whole terminal session in which you type the following command,
```
sudo apt-get install ubuntu-desktop
```

This will tell us what is wrong.

---

### Post by Robert A. Morin on 2007-02-24
Okay, without further ado, here's what happened:

```
morinro@morinro-laptop:~$ sudo apt-get install ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: language-selector but it is not going to be installed
                  Depends: libglib2.0-data but it is not going to be installed
E: Broken packages

```

Seems like it's a broken packages issue.  I thought that it would install right out of the box at first...

Does this mean that I would have to create an Ubuntu Live CD and then install this manually on top of Kubuntu?

---

### Post by aysiu on 2007-02-25
Dependency errors usually stem from conflicting repositories. Can you **[get a fresh sources.list](http://www.psychocats.net/ubuntu/sources)** and then try ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` again?

---

### Post by Robert A. Morin on 2007-02-25
Right, because Dapper Drake is probably a bit more tricky to work with, so that seems like a go to me.  Thanks.  The same thing should be done to install Xubuntu as well, I'm guessing.  Well, for right now, the best that I did was reformat the external HDD and install Ubuntu as the base desktop, then install Kubuntu and Xubuntu on top of that.  At least this seems like a bit more of a stable installation than the other way around.  Let's see if THIS works now...

---

### Post by linux_kid on 2007-02-25
Wait, all you should have to do is type the following commands,
```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install language-selector && libglib2.0-data

sudo apt-get install ubuntu-desktop
```

That should do the trick ;)

---

### Post by stocker on 2007-03-15
When i do ```
sudo apt-get install ubuntu-desktop
```

This is the error that I receive

```
matt@matt-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop
matt@matt-desktop:~$

```

Any advice?

Thanks

---

### Post by aysiu on 2007-03-15
> **stocker said:**
> When i do ```
sudo apt-get install ubuntu-desktop
```

This is the error that I receive

```
matt@matt-desktop:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop
matt@matt-desktop:~$

```

Any advice?

Thanks
Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by stocker on 2007-03-18
Sorry guys but I removed Kubuntu and installed Ubuntu Dapper.  But now Im stuck with hideous resolution until I manage to get my ATi Radeon Express 200 Graphics to work.

---

