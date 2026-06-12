---
title: "Slows When Browsing"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by trevh on 2008-07-10
I have only just installed Ubuntu 8.04 and I have installed a number of additional packages.
Yesterday the PC locked up, so I shut it down by turning off at the mains. When it restarted it found some kind of errors that I answered Y to and it seemed to perform some kind of recovery and then started OK.
Since then it seems to slow down or lock when web browsing until the page is loaded.
Is there some kind of system check I can do? Maybe some way to tell it to scan all files/packages to look for corruptions or something?
My first thought was that there might be a health check in the Synaptic Package Manager, but I can't see anything there.
Other than that, I'm over the moon with Ubuntu.

---

### Post by Rallg on 2008-07-10
There are various possibilities. Without knowing more, I would guess that the sites you visit are deliving media that, for one reason or another, confuses your browser setup.

Does the browser go slow when you visit media-free web sites (no Java, no Flash, no Windows Media or Quicktime, etc.) ?

Another possibility, if you are using wireless, is that the connection is flickering on and off. I have noticed that under certain circumstances, Ubuntu takes a long time attempting to connect to a marginal signal, instead of giving up immediately.

---

### Post by trevh on 2008-07-11
It runs slow regardless of the website content.
I'm using RJ45 cabling. Other computers on my network are fine.
It's only this computer and only when browsing the internet, I can't switch between applications until the page is loaded.

---

### Post by trevh on 2008-07-11
Just remembered, it was an fsck that ran and found error that I replied "Y" to fix. I don't know if that helps.
From what I can see, fsck is a system file check, should I think about running that again?
Is there some way of checking the files associated with packages I installed to ensure there are no corrupt files?

---

### Post by trevh on 2008-07-13
OK,
I've reinstalled loads of packages including networking and browser in the hope it will improve things, and it has to an extent.
Mozilla was taking ages to load, it's now quicker.
Basic network content is fast, for example google. Bigger sites are slower.
The real hassle is that when it slows right down for a more complicated site, the whole PC locks up while waiting for it.
A particularly bad site is facebook, but strangely once it's completed the load then ALL browsing is back to normal without any freezing.
It's as if the system is doing something to allow the content, but once it's done that bit for that content (whatever it is) all seems normal.

---

