---
title: "Internet terribly flaky in Jaunty"
date: 2008-12-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-12-31
I don't remember seeing anything like this before on my system.

Somehow, with Jaunty, the internet has become incredibly flaky.  Frankly, I'm half-surprised it still lets me update the system.  About 2/3 of the time, it can't find Google, and presents me with the "page not available" screen.

Usually, if I'm upgrading or deleting packages, I'm fine, but if I ask aptitude (or similar tools) to update the package lists, half the time it can't even find the US Ubuntu archives.

What do I need to investigate to determine why Jaunty keeps losing connectivity?  (or whatever happens to be the problem here)

---

### Post by Triggerhapp on 2008-12-31
Knowing which wireless card/driver you're using would be a nice idea. 

```
sudo iwconfig
```
Tells me its "RT2860 Wireless" :) I suppose it should work that way around.

---

### Post by gnomeuser on 2008-12-31
Sounds like dns issues. It could also be related to the decision to finally build in ipv6 (I am unsure if it got loaded everywhere regardless before but if it didn't then this might cause it)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002290.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/002290.html)

There may be lots of little issues like this with ipv6 we need to solve, you should file a bug. We will need ipv6 support to be solid and it just might throw little fits like this at first.

---

### Post by dawynn on 2008-12-31
I'm off on another little vacation in a bit, but will file a bug within the next week or so.

BTW, it has nothing whatsoever to do with wireless.  I'm fully wired.

---

### Post by dawynn on 2009-01-08
I'm back from vacation and ready to put a bug together, but the fact is, I have no idea where to really start.  Basically, at this point, I'm seeing things sometimes working (retrieving packages usually works), and sometimes not (hitting Google usually doesn't).  I was just on Jaunty and things were clicking both in Synaptic and Firefox for a while, but about 5 minute later, neither was working.

What can I research on my system to file an intelligent bug? (or even research to find whether one has been filed)

Any help is appreciated.

---

### Post by LordVeovis on 2009-01-08
It is like Gnomeuser said.  It is the IPv6 bug with routers.  2 possible "fixes"  1 manually change your DNS servers to different ones (as they are likely set to your router)
 other option is to get updated networking equipment.

The problem is that alot of routers drop the IPv6 DNS queries since they are not a know format.  When dropped this makes the PC have to wait for timeout.  There are 2 or 3 types of IPv6 DNS queries before it tries IPv4.

You can verify this by pinging google.com then pinging the ip for google.com

EDIT: 2 more things.  The reason this only recently started is because IPv6 is now in the kernel instead of as a module.  Also the reason this happens again and again even for the same site is that your PC recieves no response from the router and will ask every time it needs to load anything.  That adds up to alot of timeouts.

---

### Post by ronacc on 2009-01-08
I've already got this bugged  #313218

---

### Post by ShirishAg75 on 2009-01-09
That's [lpbug]313218[/lpbug]

---

### Post by marmuta on 2009-01-09
This could also be a MTU issue.
Default is 1500. Try to lower it and find the highest working MTU with this (replace eth0 with your interface):
```
sudo /sbin/ifconfig eth0 mtu 1492

```
Once found, make it permanent in networkmanager.
[This old thread ]("http://ubuntuforums.org/showthread.php?t=944600")knows how.

---

### Post by mariuz on 2009-01-09
> **marmuta said:**
> This could also be a MTU issue.
Default is 1500. Try to lower it and find the highest working MTU with this (replace eth0 with your interface):
```
sudo /sbin/ifconfig eth0 mtu 1492

```
Once found, make it permanent in networkmanager.
[This old thread ]("http://ubuntuforums.org/showthread.php?t=944600")knows how.
Thanks :KS

that is the same issue i have with pidgin when connecting to yahoo trough 
an wireless router (msi brand)

[http://www.google.com/search?hl=en&q=scs.+yahoo.com+pidgin&btnG=Search](http://www.google.com/search?hl=en&q=scs.+yahoo.com+pidgin&btnG=Search)

---

