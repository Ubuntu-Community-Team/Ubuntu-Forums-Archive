---
title: "Please help Human15709"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by Human15709 on 2011-05-15
Hi.  Forgive me for daring to ask a total noob question... 

But with over 10^6 posts and replies, it appears more that a tad daunting... 
Hate to be opinionated, but that needs to be looked into...
To be freed from noob status and moved to Ubuntu demigod do you have to read all of beginner posts?  Sound sarcastic? I TRULY am sorry.  


I have an  i7 Windows 7 pro x64 raid.  Installed Natty TWICE and followed directions... Rebooting goes to Windows... reboot and boot menu has only WIN 7.    I did search several threads and some were related to video resolution...  But this just did not show the Ubuntu option on the boot menu.  Any ideas....   Should I read the 10^6 noob posts...?


Signed Human15709
Age and experience taught me ...  
Knowledge does not equal intelligence
Character and integrity seems to be more rare in people these days.
Arrogant baseless opinions, ignorance, and sloppiness abounds on the internet.
Time is equally valuable to all people...
t207

---

### Post by Quackers on 2011-05-16
Raid0 or raid1 or something else?
Hardware raid/bios raid/linux software raid?
How did you install Natty?
Where did you install grub? Did it fail?

---

### Post by conradin on 2011-05-16
For starters, try Lucid lynx 10.04 LTS, its alot less buggy than 10.10 or 11.04 versions. Thats my recommendation. 

Also, tell us abit more about this RAID config. What type of RAId is it?

---

### Post by Rubi1200 on 2011-05-16
Hi and welcome to the forums :-)

Could this be the problem?
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/752694](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/752694)

Please download and run the boot info script so we can see what is going on:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```
You need to do this on a LiveCD/USB with internet connection.
Download the script and move it to the Desktop.

Then run this command:

```
 sudo bash ~/Desktop/boot_info_script*.sh 

```
This will produce a RESULTS.txt on the desktop. Copy and paste the contents into a new post here. Once pasted, highlight all text and wrap with code tags by clicking on the # icon on the toolbar.

Once we have this information we can help you troubleshoot what is going on.

---

