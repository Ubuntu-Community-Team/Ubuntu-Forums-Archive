---
title: "A disk read error occured"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by meyersmp on 2008-01-30
I've got a problem. I've played around with ubuntu in the past on my laptop and have liked it alot. My wife wanted me to keep it off the main desktop we have because she runs her photography business on it and doesn't want "linux messing up my windows stuff." 

So after several installs and upgrades of ubuntu on my laptop I felt confident enough to dual boot the desktop. I installed it on a separate hard drive from my main XP OS. After a "sucessful installation" I rebooted and encountered an error when grub tried to load. It gave error 22. I did a search on the forums and followed the advice I found [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). I tried the quickstart option and it didn't fix it, so I tried the overwrite the windows bootloader section, without success, and then I tried the Super Grub Disk. 

Nothing worked. Thinking the problem might be the fact that ubuntu was installed on a separate hard drive, I deleted the partitions I created on the separate drive and resized and created partitions for a new install of ubuntu on the same drive as Win XP. After another "successful install" the grub loader gave me the same error 22. I tried the steps from the above link without success again. 

After searching for a way to simply boot back into windows, I found [this]("http://www.neowin.net/forum/index.php?showtopic=405091") link which recommended using the fixmbr and fixboot in windows recovery with the win xp install disk. 

After running those commands I get the error 

A disk read error occurred
Press ctrl+Alt+delete to restart

I can't even boot into a cd anymore because of this error. I had a perfectly working system this morning before I tried installing ubuntu. Where did I go wrong and how do I fix it?

I tried unplugging the power to the second drive. After doing that the drive with winxp and linux install was the only one left plugged in. That is when I couldn't even boot to the cd drive. I plugged the one with just ubuntu back in so that all drives have power and I can boot off of a cd again. Still no idea how I screwed up windows or how to fix it. ...help.

---

