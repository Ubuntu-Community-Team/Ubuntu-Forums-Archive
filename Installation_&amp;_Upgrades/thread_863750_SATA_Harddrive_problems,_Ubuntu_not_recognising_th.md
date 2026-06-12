---
title: "SATA Harddrive problems, Ubuntu not recognising them"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Skyrail on 2008-07-18
I finally decided to install linux onto my second HDD of this computer. I chose Ubuntu however when I try and install it at the partition step none of the HDD's appear. fdisk doesn't show anything either :/

I tried booting with all_generic_ide and then fdisk recognised the drive but it seems like a funny hack that I don't understand. Is there a known problems about SATA drivers and such that means ubuntu won't recognise the dirves? It's a complete pain as I have Ubuntu on a slower PC and it works okay, but I want to try it out on a much faster PC.

As an aside the two times I booted I put the output into files and compared them: [http://earthtone.redpointnetwork.co.uk/changes.txt](http://earthtone.redpointnetwork.co.uk/changes.txt) that shows all the changes, big and a little over my head but if anyone can help me find the problem that would be brilliant, otherwise I'll just have to find another distro :( Thanks :)

---

### Post by Jordanwb on 2008-07-18
No Ubuntu has Sata support. After all my pc (which I'm on now running Kubuntu), has two Sata drives. Possibly the linux kernel doesn't have drivers for your particular SATA controller. Unfortunately I don't have a clue as to what to do.

---

### Post by Skyrail on 2008-07-18
Aww man, that's quite a pain mhmm, if only I knew how to compile Gentoo and grab everything I needed from scratch haha. Mhmm, I hope someone knows a solution, I'd like to enjoy messing with linux on a faster, less borked machine soon :/

---

