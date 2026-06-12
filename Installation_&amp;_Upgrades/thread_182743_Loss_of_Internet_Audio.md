---
title: "Loss of Internet Audio"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by cornishr on 2006-05-26
Last week Firefox was playing audio great with Flash and the Mplayer Plugin.  Three or four days ago the Destktop alerted me to several upgrades which I invoked without observing what was being upgraded.  (my mistake)!!   Since that upgrade, I have lost most audio from the internet.  On some Flash streams, if I turn the sound to max, I can barely hear the sound.   How do I recover the sound on Firefox?  The sound works great for Multimedia (Totem) and system changes.  I have searched the Forum for everything I can find on how to fix the audio, but I cannot find the solution.   Please help!!!  I forgot to add that I am using Breezy and have installed Automatix.   The device manager shows the Audio Card to be a CM8738 with ALSA Drivers.

---

### Post by Sef on 2006-05-26
Have you installed alsa-oss?

From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install alsa-oss

---

### Post by cornishr on 2006-05-30
I have been sick for last three days so I have not seen your reply until today.  I checked in Synaptic and ALSA-OSS is installed, but I followed your instructions anyway and the terminal reports that the latest version is installed.  Is there a next step in troubleshooting?
Thanks, for your help.

---

### Post by eindgebruiker on 2006-06-01
Hi,

I experienced exactly the same problem (I'm on Dapper though).
Please have a look at this bug report:

[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/45803](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/45803)

"aoss firefox" fixed the problem for me. To automate this I guess you could change "firefox" to "aoss firefox" in the menu. Or maybe use this (I haven't tried it yet):

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by cornishr on 2006-06-01
In a terminal I entered "aoss firefox" and firefox loaded, but I still get no audio???  Audio was working in Firefox until I performed one of the upgrades that was included in a notification by the desktop that there were upgrades available.  I looked at my history in Synaptic but it just list the programs changed, it doesn't list the changes made to individual files that could have created this problem.   If I just had a functional flow diagram of the programs that are executed to produce the sound for Firefox, maybe I troubleshoot the problem.  I grew up in Electronics; therefore, I do not mind solving problems if I just had the tools to understand.  At the moment, I am grabbing a straws.  Thanks for your help and if you have any other suggestions for a solution, I will be very grateful.

---

