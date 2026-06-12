---
title: "Installing Ubuntu 7.10 next to raid array"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Merlin7777 on 2007-10-20
Hey guys, what I am trying to do is a little different than the usual "install on a raid array".

I already have a raid 0 array, with Windows XP on their. Which is fine for me. I don't want to install ubuntu on the array. I have a separate 500gb drive that I want to install it too. 

All I want to be able to do is access the raid array, AFTER I have installed ubuntu. I know this sounds simple, but I have already tried this already, and I almost nuked my xp install. It turns out Ubuntu was trying to install grub on the raid array, which is exactly not where I wanted it to be.

I am running an e6600 with 2gb of ram on an Asus p5b deluxe. The raid array is on the Intel ICH8R controller. What I discovered in the bios is that it seems impossible to add a new harddrive to another sata connector, without it showing up in the raid array.

Actually the intel controller knows that it the new drive is not apart of the raid array, but when i go to select the boot device, the only option is "Intel: Raid 0". Thus in order to be able to boot off of the new harddrive I have to change the IDE settings to "IDE" or "ACHI" instead of "RAID".

One workaround for this may be to use the Jmicron controller. It has 2 sata ports on the board that I could use.


So, to sum up. I have a Raid 0 Array with XP on it. I don't want to install ubuntu on the Array. I have another disk that I want to install ubuntu on to. What I want is for grub to recognize both Ubuntu and XP, and I want to be able to boot Ubuntu and access the raid 0 array, which has movies and music on it and such.

Can someone help me do this?

P.S. Sorry for the Essay.

---

### Post by eyeRmonkey on 2007-10-21
Simply do

```
sudo apt-get install dmraid
```

That will install the utility that will let you view RAID partitions from Ubuntu.

---

### Post by Merlin7777 on 2007-10-21
Did that. 

Even though I did that, I still almost nuked my system. I think that I will have to do a manual install. I tried to do it once, but when I set it to start installing it said that my two drives that are in the raid array are set to mount in the same place.

---

### Post by teebiss on 2007-12-09
I am having the same problem.  Did you you find a solution?

---

### Post by Merlin7777 on 2007-12-09
Sort of. What I did was remove the power plugs from my XP install drives, just so I knew that they would not be written on. Of course, I backed up all of my critical information/programs and so on before hand, just in case. Then on my third drive I did a manual install, following the prompts and so on.

So, all three drives are running on my Intel Sata controller, which is configured for Raid. However, it does the right thing and distinguishes by third drive from the Raid Array. It says, "Non-Member", which is good.  Now, in order to boot to XP, I just switch the order in my bios of which "drive" is booted first. 

If it is my first/second drive(s), then XP boots. If it is set to my third drive, then Grub boots, and automatically loads Ubuntu 7.10 unless I tell it to do something else. Like boot my Sabayon install.

Hope that helps you, post back if you need more help. I would be glad to help you.

---

