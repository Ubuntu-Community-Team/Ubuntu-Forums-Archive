---
title: "apt-get dist-upgrade continuous loop?"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tommynz1975 on 2010-04-01
I have just installed lucid beta1 on an Nec system with 512mb ram
install seemed to go well and the reboot was extremely fast.

I went to terminal 
couldn't get 
sudo apt-get update to work
so used sudo dpkg --configure -a
then was able to get sudo apg-get update to work 
followed by sudo apt-get dist-upgrade.

366mb of files came down in 6mins and 4 seconds
so you can imagine I was impressed.

I said yes to update but wondered if it was stuck in a loop repeating its self?
due to the fact grub has been updated 2 or 3 times with the same changes made.

Or is this normal and I have never noticed this before?
The updates have been running for about one hour.

After typing this it now appears that the system is stuck on 
setting up evince

Is it safe to reboot the system? as I am thinking it now has crashed? 
The clock has not been updated in 23 minutes.

---

### Post by tommynz1975 on 2010-04-01
scratch the crash

the clock finaly updated and 

setting up evolution-common
setting up file roller and such
have finaly appeared on screen
but my original part I still wonder?
does grub get updated many times durring this process?  its seeming like the system is doing the same things over and over again..


Much Thanks

Tom

---

### Post by ranch hand on 2010-04-01
There are a number of things that require grub to be updated.  As apt does not "know" about packages not yet installed it upgrades grub after each one.

One way around this is to remove any grub updates from the upgrade and do them after the others are finished.  This would be a pain.

---

### Post by tommynz1975 on 2010-04-01
Ranch Hand Thank you for adding another piece of knowledge to my slowly growing ball.

I seriously thought maybe the upgrade had finished and was restarting, heck well stranger things have happened :)

As I said in the other post I had never noticed grub being updated many times.

Panic now over and I await the upgrade to finish

---

### Post by tommynz1975 on 2010-04-02
Hi People, just thought I'd post back.

After my last post, the update was stuck for quite a while. So I disconnected the lan cable, this promptley crashed the system.

On Reboot I couldn't access the system

so had to go into the original recovery mode. I got into Command line with Network access and preformed the following commands

```
sudo apt-get update
```

The response was to preform

```
sudo dpkg --configure -a
```

This did its thing, so I preformed update again, this worked :D then preformed

```
sudo apt-get upgrade
```

The system completed its task in a few minutes

So all is good and I am happy :popcorn:

Running Linux 2.6.32-18-generic #27-Ubuntu SMP Fri Mar 26 19:51:10 UTC 2010 i686 GNU/Linux

---

