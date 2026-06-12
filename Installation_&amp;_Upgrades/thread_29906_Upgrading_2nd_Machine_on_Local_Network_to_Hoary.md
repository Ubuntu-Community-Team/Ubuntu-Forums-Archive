---
title: "Upgrading 2nd Machine on Local Network to Hoary"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by wulf on 2005-04-26
I've done a bit of searching round but not found the answer to a question thats been on my mind for a few days.

At home, I've got a small LAN, including two machines running Ubuntu. The main one is my laptop currently on Warty and the other is my old desktop system, which I successfully upgrade to Hoary over the weekend. Both are fully up to date for their respective releases.

I'm finding Hoary works smoothly (and the upgrade was also easy on the machine I use at work) and now I want to upgrade my laptop as well. I could just follow exactly the same steps as I did on the desktop machine - update the sources list, replacing *warty* with *hoary*, etc (as per the [release notes](http://www.ubuntulinux.org/support/ReleaseNotes504)).

However, I know that will take a couple of hours to pull down the updates, as well as being another chunk of bandwidth used up. From what I've been able to see and pick up, the downloaded packages are in */var/cache/apt/archives* - can I use the desktop machine on the local network as a primary source, so that only packages not installed there (I use the laptop a lot more so it's got a few extra things added to it) need to be pulled across my Internet connection?

As a related question, can I delete some or all of the contents of the apt archive on the laptop once I'm done? That machine is relatively low on space, as it's installed in a partition created by copying off the Windows rescue CDs that came with the machine and the extra 300MB or so would be a valuable saving. I'm not quite ready to  trash Windows, as I've still got one or two programs I need to run on it.

I'm happy to RTFM but would be grateful if someone could tell me where to find it!

Thanks,

Wulf

---

### Post by wulf on 2005-04-27
Any ideas?

Wulf

---

### Post by stardotstar on 2005-04-27
I wonder if it is possible to copy the archives to a directory served by apache and then add that machine as a repository for the local network.

I am dealing with this very issue right now - and have a slower connection at one site than the other and would prefer to do this only once.

I really don't know how it all works though.

---

### Post by arcilite on 2005-04-27
Maybe burn a cd or put the packages on an external usb hard drive?

---

### Post by wulf on 2005-04-28
[QUOTE=arcilite]Maybe burn a cd or put the packages on an external usb hard drive?[/QUOTE]
If I'm going to do that, couldn't I just mount the package archive on the older machine in the same way as mounting a CD rom?

Wulf

---

