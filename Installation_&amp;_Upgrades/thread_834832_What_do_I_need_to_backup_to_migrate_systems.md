---
title: "What do I need to backup to migrate systems?"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by SnowPunk98 on 2008-06-19
I currently have my home directory on a seperate partition and need to migrate to a new system. I would like to retain everything including settings, programs, data, etc. The systems will be different hardware but I would like to basically be able to install Hardy on another system, copy everything over from my old system and be back up and running without having to start fresh.

Beyond moving my home directory over, including all the .application directories what else do I need to move?

---

### Post by SnowPunk98 on 2008-06-23
bump

---

### Post by adept_king on 2008-08-19
i was going to ask the exact same question.

other than the /home directory, is there anything else i need to move my install to another partition?

i already know about the 

```
dpkg --get-selections >mypackages

```
command to create the reinstall list for a fresh install of same packages.

i went through alot to get asio and vst working and i dont really want to go through all of that again.

---

### Post by Junkieman on 2008-09-07
Thanks king for the dpkg tip :) I'm trying to do the same, after realizing my setup is waaay too customized for my photo editing. 

This is going on to a new pc, so i will image the new install and have room to experiment with moving my settings over. 

i want to try and do a fresh install of all applications but see how stable the system will be after moving the settings over. My caveat, I'm moving from a Gutsy install to a clean Hardy. And i have a feeling there might be a few hairy issues.

I'm following this thread anyway and will post if i find anything useful.

---

