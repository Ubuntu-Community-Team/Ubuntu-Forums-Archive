---
title: "Just installed windows, now installing Ubuntu 14.10, am i doing this right? (w/ pics)"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by dalvacoder on 2015-02-05
Hi guys! Okay so I just did a fresh install of Windows 10 and got rid of my old windows 7. I only plan on using windows to play League and maybe do some programming in visual studio. Anyways, I used to have an existing Ubuntu install before i installed windows 10 (its a long story i ****ed up plenty and managed to get windows back on my system). I just loaded from usb with Ubuntu, and wanted to start the Ubuntu install for a dual boot system but the installer says "no other operating system detected" and gives me an option to erase everything and install ubuntu or"other."  

So i went with other, and i attached pics of what I see.  I notice a 367 mb partition for windows recovery, then another 200gb ntfs partition which is where my windows OS is installed, so its definitely there. Then I see another partition that says "unknown" which is the one that I previously had Ubuntu installed. Finally i have the swap partition of my previous install (idk why i made it 17 gb, i have 8gb ram and i read somewhere to make it 2x your ram, so w.e, sorry guys im noob). 

What do I do now? I don't want to delete my windows again because i went through a mission and a half to put windows back, but i definitely want to use ubuntu as my main system (i tried it and now i'm definitely not going back to windows but league is ****** in linux). First picture is what I see, second picture shows what I assume is the next thing i should do: double click "free space" and select use as ext4 and mount point / . And the 3rd picture shows what i see after doing that and clicking swap and selecting to use as swap. "free space" becomes sda6 with / .

Is this okay? Or is there an issue because Ubuntu didnt recognize my windows system?? Will I be able to boot both through grub if i go through with this? Any would be much appreciated!! And sorry for the noobiness, gotta start somewhere though.

[IMG]http://i.imgur.com/W7YZAL7.jpg[/IMG]


[IMG]http://i.imgur.com/lRVo1Wo.jpg[/IMG]

[IMG]http://i.imgur.com/JoqdqDb.jpg[/IMG]

---

### Post by dalvacoder on 2015-02-06
ok managed to do it on my own u guys are slow and i was getting the ubuntu itch lol. anyways just went through with the installation, got stuck on reboot but after that its fine. when i start grub gives me option for windows recovery mode but apparently that is regular windows because it boots me to the OS not recovery.  also selected sda as / instead because it made more sense, all is well now.

---

### Post by sudodus on 2015-02-06
Welcome to the Ubuntu Forums :-)

Many of us were sleeping while you were solving your problem. I just woke up now. Other people were at work. You must remember that we have a world-wide forum with people in all time-zones.

So next time you may need to wait for one day and night to give a chance to all people who are able and willing to help you. If still no reply you can bump the thread (not exactly after 24 hours, but maybe after 16 hours and 32 hours to reach people in another time zones).

Write 'bump' in a reply (or if you have more information or questions, tell us).

And last but not least, thanks for sharing your solution :KS

---

### Post by dalvacoder on 2015-02-06
haha yes i was only joking, i knew by tomorrow i'd get some help but Ubuntu was calling my name. Anyways glad to be part of the community hopefully i can contribute more in the future :)

---

