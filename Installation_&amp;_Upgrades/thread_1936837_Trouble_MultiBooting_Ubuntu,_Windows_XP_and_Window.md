---
title: "Trouble MultiBooting Ubuntu, Windows XP and Windows 7"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by zealouszee on 2012-03-06
Hello,
  First of all, sorry for any stupid stuff I may talk about in here, because I am a complete beginner in this world of Linux and Ubuntu. Somehow, I successfully installed Ubuntu 11.10 and so far, I am loving this new experience. However, my problem is that in the boot menu option, I can see options to select Ubuntu and Windows 7, but there is no boot entry for windows XP. The boot menu also seems different than the old windows boot menu. So, I believe Grub2 or something has replaced that old boot menu. Anyways, can anyone help me recovering the boot entry for windows XP as well? I am hoping, someone would help me out. Please remember, I am an absolute beginner. So, I won't know much when you suggest me any solutions, but I will try.
Thanks.

---

### Post by darkod on 2012-03-06
You have done nothing wrong.

If you select win7 from the grub2 boot menu, does it show you the windows bootloader next with options for win7 and xp?

This is because of how windows works. When you install more than one version of windows, it combines the boot files. Ubuntu discovers boot files and makes entries for the boot menu. Since there is only one set of boot files to discover, it creates only one entry and calls it win7.

If you wanted win7 and xp to show separately, there were things to do before the windows installations. It can be sorted out now too, but it involves making changes that are not very simple (but not too difficult either) and you better leave it as it is.

Just make sure when you select win7 it shows the windows bootloader with options for 7 and xp and that you can boot both of them successfully.

---

### Post by zealouszee on 2012-03-06
Hello,
  Thank you so much for a quick response. Actually, I am loving Ubuntu that is why I haven't even tried selecting windows yet lol! But, I have most of my games installed in windows so, I will do that now and report back soon.
Thanks.

---

### Post by zealouszee on 2012-03-06
Also, I believe renaming the entry "Windows 7" should be easier? Can you tell me how to do it? because it just seems annoying to have two multiple options under the term "Windows 7" I would prefer having a more general term like "Windows" > and then inside that term the other two OS "Windows XP" and "Windows 7"
Thanks.

---

### Post by darkod on 2012-03-06
The boot files are detected as win7, so it calls it that.

You should be able to use Grub Customizer (install it first) to change the name. I have never actually tried that but it should work fine.

---

### Post by zealouszee on 2012-03-07
I tried and it worked. You were right, Thank you so much. I have one more question though. Before the installation, I came to know that we have to create various partitions for using linux. What I learnt is that I created /boot of about 550mb, /(root) 21 GB (To my understanding it is the partition where the installation file goes), **swap** (Some thing like virtual memory right? I set it to double of my RAM) Now, when I created these partitions, I could not use the left space of my harddrive. i don't know why. According to my understanding, I needed to create a /home partition as well. But, it said space is not available or unusable or something like that after creating these partitions.
My question is that, I could not really understand the use of a /home partition? Is it where our files are saved? if it is true than what about / (root) partition? I left 21 GB for root partition after thinking that it is where my installation and person files will be saved, but what about the /home partition. Can anyone explain?
Thanks.

---

### Post by darkod on 2012-03-07
As you probably noticed, in ubuntu every user has its own Home folder when personal files are saved (and program settings too).
If you have a separate /home partition, these Home folders are on it.
If you don't have a separate /home partition, the Home folders are included in the root partition.

The root partition is the main system partition.

People (myself included) prefer to have separate /home partition because it allows you to do a new clean install onto the root partition in the future, but keep /home without formatting it and your personal data will be there in the new install.

So, in your case, without separate /home partition, the root partition will have both the system files and the personal files of all users. You have 21GB to use for that so you will need to be careful with any huge videos, photos, etc in the Home folder of any user.

The separate /boot you created is not really needed and these days you would rarely create it for a home desktop system. But it will work the way it is right now, no problem with your setup.

---

### Post by zealouszee on 2012-03-07
> **darkod said:**
> As you probably noticed, in ubuntu every user has its own Home folder when personal files are saved (and program settings too).
If you have a separate /home partition, these Home folders are on it.
If you don't have a separate /home partition, the Home folders are included in the root partition.

The root partition is the main system partition.

People (myself included) prefer to have separate /home partition because it allows you to do a new clean install onto the root partition in the future, but keep /home without formatting it and your personal data will be there in the new install.

So, in your case, without separate /home partition, the root partition will have both the system files and the personal files of all users. You have 21GB to use for that so you will need to be careful with any huge videos, photos, etc in the Home folder of any user.

The separate /boot you created is not really needed and these days you would rarely create it for a home desktop system. But it will work the way it is right now, no problem with your setup.

Okay. Thank you that was very helpful. Right now, I am exploring Gnome and Unity...I dunno what they actually do....any recommendations?

---

