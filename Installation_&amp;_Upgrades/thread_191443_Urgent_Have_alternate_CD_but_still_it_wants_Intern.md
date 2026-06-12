---
title: "Urgent: Have alternate CD but still it wants Internet connection?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Zombithium on 2006-06-07
Hi,

I am having an Alternate CD for upgrade. I followed the instructions listed at Dapper upgrade link :
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
But when I do 
sudo apt-get update && sudo apt-get dist-upgrade
It begins downloading from the web.. now it is asking 

Need to get 75.9MB/522MB of archives.
After unpacking 262MB of additional disk space will be used
Do you want to continue [Y/n]?

what should I do? will it download this stuff from the web..? I am worried because my broadband connection is not very reliable? Also what does he mean by "Need to get 75.9MB/522MB of archives" ? does it need to download 75.9MB or 522MB ?

And i am still wondering why is it not using the CD that I have put in there? Or is he now going to use the CD to get those archives?

(I am still waiting at that [Y/n] prompt !! please help)

---

### Post by Hanj on 2006-06-07
You need to remove all internet sources from your /etc/apt/sources.list file.

---

### Post by Irony on 2006-06-07
The alternate cd has only the basic stuff on it, however things like nvu, blender and whatever will be updated via the internet.

You could of course comment out the repositories as suggested.

---

### Post by Zombithium on 2006-06-07
[QUOTE=Irony]The alternate cd has only the basic stuff on it, however things like nvu, blender and whatever will be updated via the internet.
[/QUOTE]

Yeah that's right. thanks.
I went ahead with Yes Option. It downloaded around 79.5MB of data (which is okay as compared to 522MB). Anyways the good news is that finally the upgrade was successful :-)
Although I am not feeling very Dappery right now .. it still feels like breezy.

---

