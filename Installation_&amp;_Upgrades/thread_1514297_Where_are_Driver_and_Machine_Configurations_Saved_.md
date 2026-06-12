---
title: "Where are Driver and Machine Configurations Saved on My Computer?"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by u2rcrazy on 2010-06-20
**Where are Driver & Machine Confirgurations Saved Ccomputer?**
 
I just started using Ubuntu over the last several months and almost have it setup the way I need and want.  I understand that a new version comes out every 6months or so and plan on upgrading when it comes out.  I would like to be able to reformat and install the latest version, but retain all of my preferences, programs, device drivers, etc. so that it's all ready for the new version of Ubuntu.  Up to date, I have spent so much time changing setting, finding drivers that fit and installing them that I don't want to start over with this.  
 
How can I do this?  I have made a seperate partition for **/home. ** Will this help or is this folder only for to save my personal files?  If this doesn't help, what would you suggest.  Thanks in advance for your assistance.
 
Sincerely,
Bob:guitar:

---

### Post by oldfred on 2010-06-21
Your user settings are all in /home and if you do not overwrite it you will have all those settings preserved. 

System settings are in /etc but you cannot necessarily just copy those as a new version may use totally different configurations or settings. 

My work around is just to use another 20GB partition to install to and if I have to I can go back and find a setting. With Jaunty to Karmic I only had one or two things that I missed and I could have recreated from scratch in about the same amount of time it took to find and copy. I do try to keep track of any system related settings that I have manually changed and copy those into /home so I have backups and preserved copies.

---

### Post by u2rcrazy on 2010-06-21
> **oldfred said:**
> Your user settings are all in /home and if you do not overwrite it you will have all those settings preserved. 

System settings are in /etc but you cannot necessarily just copy those as a new version may use totally different configurations or settings. 

My work around is just to use another 20GB partition to install to and if I have to I can go back and find a setting. With Jaunty to Karmic I only had one or two things that I missed and I could have recreated from scratch in about the same amount of time it took to find and copy. I do try to keep track of any system related settings that I have manually changed and copy those into /home so I have backups and preserved copies.


Old Fred,
 
Your said:
> **oldfred said:**
> I do try to keep track of any system related settings that I have  manually changed and copy those into /home so I have backups and  preserved copies.


[COLOR=Red]Aren't these settings already saved there as you stated here:[/COLOR]
> **oldfred said:**
> Your user settings are all in /home and if you do  not overwrite it you will have all those settings preserved. 

System settings are in /etc but you cannot necessarily just copy those  as a new version may use totally different configurations or settings. 


You also stated:
> ** oldfred said:**
>  My work around is just to use another 20GB partition to install to and  if I have to I can go back and find a setting.

I have **/home** partition currently.  [COLOR=Red]Should I have a partition for **/etc**?[/COLOR]  I understand that these settings may not work with an upgrade, but I would like to try it.  [COLOR=Red]What is your experience with transitioning these system and user settings?  [/COLOR]

Here is a screen shot of my current system partition view:

[CENTER][ATTACH]161126[/ATTACH]

[/CENTER]
As you can see, my objective is to make it easier for the next upgrade the next time around.  Thanks for your help again :p

---

### Post by oldfred on 2010-06-21
User settings are not a problem and are in /home. The system settings I manually make in /etc to files like xorg.conf (now obsolete) or /etc/interfaces that I had edited, I also copy to /home. Those settings are not in /home. And I only copy the one's I know I have special settings in.

User settings on an upgrade have not been a problem. We do regularly get users who upgrade and a popup says use maintainers(new) or current settings, then use current settings and then are here because system does not work. Old settings potentially break system and if you kept all of /etc it would be impossible to fix as no one would know what to correct. You would be also missing all the new settings.

---

