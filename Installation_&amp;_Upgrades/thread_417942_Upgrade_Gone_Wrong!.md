---
title: "Upgrade Gone Wrong!"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Neondog82 on 2007-04-22
So there I was, trying to upgrade from 6.10 to 7.04 (Edgy to Fiesty?). It took my nearly two days to download all the required stuff through the update manager (crappy hotel signal). I started to install and it kicked out an error for something on the back end (i dont have any idea what it was talking about). I restarted my computer and I noticed that the update manager said I had some broken stuff. So i tried to upgrade/reinstall the broken stuff. That didnt work so I removed them. Then I tried to go back and upgrade again, it game me the option to do a partial upgrade (assuming because i had all ready started before)? It ended up that now the computer comes up to the splash screen and sits there with a little piece of progress bar showing. I just switched to Ubuntu 6 days ago because I got tired of Windows being a pain in the but. I would appreciate it if some one could help me recover from my current situation and then make progress into installing Fiesty. I am totally clueless as what to do. So if you help please talk to me like I am 2. I can still get to my files with the live CD i used to install it the first time so I can post up what ever configuration files or error logs you need as long as i know where to get them. Any help would be much appreciated, I am looking forward to your insight.

---

### Post by ecionci on 2007-04-22
Sir, If you can return to Edgy, you may be better off to order the Feisty dvd from shipit.
I say this only cause you were experiencing faulty internet downloads. Or, you may have a friend
download it for you.
Also try to bring up a console and type: sudo apt-get install --fix-broken
to see if that helps your situation.

---

### Post by Spr0k3t on 2007-04-22
Using your LiveCD, you can find your files in the /home/{userid}/ directory.  Considering you have a horrible connection, it may be easier to download the 7.04 release and use that as the upgrade path.  There have only been two package updates since the release of feisty.  You might be able to load into recovery mode (from the grub menu, press the escape key if you don't see it) and perform the sudo apt-get update/upgrade.  Not 100% sure on that though.

As a side note, I've noticed some hotels require you to keep thier proxy wall open so they can detect you are still using the network connectivity.  With the live disc, try opening up their proxywall (if they have one) and leaving it open while your download takes place.

Just some thoughts that may help you get to where you need.

---

### Post by Neondog82 on 2007-04-22
Thank you for the help, I will try to get into recovery mode. Last time I tried it brought up like 6 options, 3 with the words recovery after the ubuntu xx.xx.xx. Except when i got to the command prompt it just sat there, i tried to type in a command and it did nothing. I will probably use my wifes laptop to download Fiesty via a torrent. I only have one important file i need to retrieve from my computer. It is a Firefox bookmark that tells me how to fix my widescreen resolution very simply. Can you tell me how to retrive this book mark?

---

