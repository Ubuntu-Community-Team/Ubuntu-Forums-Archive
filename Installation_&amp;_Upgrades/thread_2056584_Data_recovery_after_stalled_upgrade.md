---
title: "Data recovery after stalled upgrade"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by silentlight on 2012-09-11
Here is the story of my self-made disaster:
Although I have been using Ubuntu for years I am by no means to be considered above Amateur-level user. I have never gotten much practice manipulating linux or using the system without the GUI. That being said, I can still follow directions on how to use terminal and so on to fix or enhance Ubuntu. Generally I have found that a quick google search and a bit of reading reveals one or more effective fixes to any problems that arise, so I think I had my account on ubuntuforums removed for lack of activity. However today I had to recreate it as I am NOT finding an effective fix or maybe am confused on what to do. .
I have been holding off on installing Ubuntu 12.04 as I was not pleased about the switch to the Unity interface and wasn't looking forward to whatever work was necccessary to switch back to GNOME. However 10.04 has not been good about operating with my Android phone and in fact eventually became completely useless in that regard. In my impatience I brazenly opted for an upgrade through GNOME without any backups, reckoning that even if the upgrade went wrong it would be a simple matter to run a live USB and recover my important fles... and in theory (according to a number of pages I have seen) that should be a relatively simple operation. Unfortunately I did enrypt my home directory. I know the mount password and somewhere, in some notebook, I have the encryption key or whatever written down. ( you know, the one it gives you when you first encrypt). this key is not easily accessible and may take weeks to find.
However- allthough both 10.04 and 12.04 live USBs have ecryptfs installed, when I try to run them it tells me that the command is unreckognized. Attempting to install ecryptfs through apt-get install results in a message that I already have them installed. Furthermore The recovery modes are not working properly and the GUI mode will not load at allI am not sure what to do and could use some simple step-by-step instructions. 
System information:
Modified Acer Aspire 7535-5415, 2.3GHz dual core Turionx2 Ultra ZM-84 chip. 8GB DDR2 RAM, 500GB sd-hybrid hard drive with a functioning window 7 partition. 
Here are my assets:
several USB drives
stacks of DVD-ROM and CD-ROM
a working windows 7 partition
So I am sure I must be doing something wrong, but I bet I am not the only person with this kind of problem. Can anyone help?

---

### Post by oldfred on 2012-09-11
I do not use encryption, but believe with encryption regular backup is more important as with a system failure then encryption prevents, as it should, any recovery.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

---

