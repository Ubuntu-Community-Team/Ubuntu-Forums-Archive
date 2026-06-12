---
title: "First time, I'm really LOST"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by PhoenixP3K on 2005-03-30
Hi, everyone. I know nothing about Linux, and I get to learn from experience, but right now I'm stuck. I have both a Live cd and install Cd of Version 4.10 (Intel x86).

Now, I've tried the live cd a few times and loved what I saw, so I decided to install it on my second harddrive.

I went trough the process, Grub is loading but I'm stuck, I have no idea on how to get the desktop running, it asks for login then password. But this is really the most I can do. And YES! I've been searching the forums and did not find something usefull.

Thanks if anyone can help me ASAP.

---

### Post by bored2k on 2005-03-30
Grub asking for password ? Grub the boot loader ? Or GDM the GNOME Display Manager ?

---

### Post by PhoenixP3K on 2005-03-30
Seems like I made a mistake while installing Ubuntu, so I tryed it back, and running it right now! That's great. I just have to figure out a few things but that should come naturally.

But I'd still have a question on how to make Windowx XP, default on start-up, I have other users in the house and they're not ready to switch to Linux, so I have to make windows run default first, if someone can hint me on how to do so easily I'd be grateful

---

### Post by bored2k on 2005-03-30
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

After reading/applying this, in a terminal do 
sudo apt-get install grubconf
OR in synaptic package manager search for grubconf

After installing it, in a terminal run
sudo grubconf and select windows for default ^_^ .

---

### Post by Buffalo Soldier on 2005-03-30
You can also refer to [How to change default Operating System boot-up for GRUB menu?](http://ubuntuguide.org/#changedefaultosgrub) at [UbuntuGuide.org](http://ubuntuguide.org).

---

### Post by bored2k on 2005-03-30
[QUOTE=Buffalo Soldier]You can also refer to [How to change default Operating System boot-up for GRUB menu?](http://ubuntuguide.org/#changedefaultosgrub) at [UbuntuGuide.org](http://ubuntuguide.org).[/QUOTE]
 grubconf is GUI and mostly harmless. I would not recommend messing with those things manually to any newcomer sir ;) .

---

### Post by ubuntu_demon on 2005-03-31
Why not install the hoary release candidate ? Not much will change as hoaryis quite stable and gets released next week. If you should run into trouble with your screen in hoary run sudo "dpkg-reconfigure-xserver.org"

---

### Post by PhoenixP3K on 2005-03-31
Well, I read the forums, search and found a load of stuff. Step by step instructions helped me put Windows default. I was following what was written and I'm starting to understand the way linux is build. I love it. Thanks for the support. As for update, I don't have full hi-speed access so downloading large updates is not in question right now, so I'll have to wait some more.

---

### Post by bored2k on 2005-03-31
You could get the new Hoary [RC] and just upgrade when it turns final . Its -really- stable right now .

---

### Post by ubuntu_demon on 2005-03-31
[QUOTE=bored2k]You could get the new Hoary [RC] and just upgrade when it turns final . Its -really- stable right now .[/QUOTE]
 or get someone else to download it for you :-D

---

