---
title: "Open Office 2.0 HELP!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by efranco0311 on 2007-04-21
Hey,

I am a NEW Ubuntu user (dapper) and did something stupid, and need some help.Here's the BIG PICTURE: I broke Open Office 2.0 and cannot get it reinstalled.

Here's what I did: I attempted to install Open Office 2.2 -- not really familiar with Terminal commands, I tried to do it via a couple of different commandline instructions that I found off of various web forums. 

PROBLEM: While I "mark for reinstallation" in Synaptic Package Manager, go through the motions to reinstall, my Open Office Writer program will not appear in the Applications --> Office menu. In additon, I cannot open an OO word processor document.

HELP: How can I either install Open Office 2.0 or 2.2 to include all of the applications?

I NEED: a clear step-through 

Thanks!

Eric

---

### Post by bwhite82 on 2007-04-21
Hi, do this, one command after the other:

> sudo apt-get install -f
sudo apt-get remove openoffice.org
sudo apt-get update
sudo apt-get install openoffice.org

---

