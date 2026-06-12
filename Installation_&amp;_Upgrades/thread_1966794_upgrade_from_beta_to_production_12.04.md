---
title: "upgrade from beta to production 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by findlj on 2012-04-27
I am currently running the beta 12.04 and would like to upgrade to the current 12.04 LTS .   My update manager is not prompting for this upgrade yet.  I want to upgrade, not re-install.  

Is the production release not yet available?  I understood it was to be released today.

Thanks for the help, in advance.

---

### Post by wojox on 2012-04-27
If you have been running beta open a terminal and run:
```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by jadtech on 2012-04-27
change your servers in update manager click check for up dates,

go to a terminal window type in sudo apt-get update

all you have to do from beta is run the updates nothing more first update should start with kernel 3.0.2.24 there is sofar justover 2 dozzwn more updates I have had how efver that first batch with the kernal brings you to 12.04 release .. 

if you are not getting these updates like I said try to change the server in update manager I also have found after that rebooting spawns updates ..

---

### Post by jadtech on 2012-04-27
> **wojox said:**
> If you have been running beta open a terminal and run:
```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

this works well picked up all the packages I was still missing  and finished my update to the full release with no glitches on reboot less then 20 mins ..

---

### Post by Curtis6767 on 2012-04-27
if you've been updating all along, then you may have the latest release already installed.

Try this:

```
uname -r
```

If you get 3.2.0-24, then you should be up to date.

---

### Post by techsupport on 2012-04-27
> **Curtis6767 said:**
> if you've been updating all along, then you may have the latest release already installed.

Try this:

```
uname -r
```If you get 3.2.0-24, then you should be up to date.

Updates should be on 12.04 LTS this morning for anyone that was a Beta 2.

---

### Post by jadtech on 2012-04-27
> **techsupport said:**
> Updates should be on 12.04 LTS this morning for anyone that was a Beta 2.

I thought I had beta 2 I definatly had the 3.2.0.24 kernel but there was another 30 packages  just upgraded and installed here for me ..

---

### Post by techsupport on 2012-04-27
> **jadtech said:**
> I thought I had beta 2 I definatly had the 3.2.0.24 kernel but there was another 30 packages  just upgraded and installed here for me ..

yeah the linux kernel and headers came through this morning. My Ubuntu 3D is working for me now.

---

### Post by jadtech on 2012-04-27
i havent tried that guess  I will venture there soon .

I am still running the wubi install I guess over the next few day I will get the recovery disks and live cd made up and work on migrating to it own partition though I would love to keep this wubi install for testing and playing it has been a ride for sure over the last month and a half ..

---

### Post by findlj on 2012-04-28
Thanks for the help everyone.  I had done an update from the update manager on the 27th.  After running "uname -r" I saw I was already at 3.2.0.24...:)

---

### Post by jadtech on 2012-04-28
glad it all worked out for you :)

---

