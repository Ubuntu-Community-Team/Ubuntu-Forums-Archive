---
title: "Ubuntu 14.04 installation failure and unreadable content"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by robertcarlson1000000 on 2014-04-18
I came home starting the upgrade process to Ubuntu 14.10. about 1 hour later, I check my computer and I saw that Xorg crashed and I was given an option to restart, so I did. when I rebooted. lightdm started ok and I was able to log in, but My GUI didn't start up and I was left with just staring at my wallpaper. So, i obtained a copy of ubuntu 14.10 on CD, get my files off, and I was going to upgrade manually. but, as I was copying files over, I got some errors saying that some contents were "unreadable" and wouldn't copy over to my SD card. Did my disk drive get corrupted because Ubuntu failed to upgrade or is there a way to still get the data off???

---

### Post by carl4926 on 2014-04-18
Was your /home a separate partition? Ubuntu doesn't default to it.

If I were you I'd probably clone what you have right now. I'd use ddrescue from a Parted Magic CD
You need a backup target big enough though?!

**It's advised to have a backup before you do upgrades*

---

### Post by carl4926 on 2014-04-18
> **robertcarlson1000000 said:**
> I came home starting the upgrade process to Ubuntu 14.10. about 1 hour later, I check my computer and I saw that Xorg crashed and I was given an option to restart, so I did. when I rebooted. lightdm started ok and I was able to log in, but My GUI didn't start up and I was left with just staring at my wallpaper. So, i obtained a copy of ubuntu 14.10 on CD, get my files off, and I was going to upgrade manually. but, as I was copying files over, I got some errors saying that some contents were "unreadable" and wouldn't copy over to my SD card. Did my disk drive get corrupted because Ubuntu failed to upgrade or is there a way to still get the data off???

I assumed 14.10 was a typo FYI

---

### Post by robertcarlson1000000 on 2014-04-18
no /home was not a separate partition. I set the mounting point to / if that's what you're asking. I just noticed that when I press Ctrl+Alt+F1 and launch the console while booted on my disk drive, It can read all of my content just fine. but it can't while on a live CD. I'm going to try to copy everything on my /home folder to an SD Card. But, I don't know the command. Can you tell me??

BTW 14.10 was a typo. I was typing fast and didn't check for errors.

---

### Post by carl4926 on 2014-04-18
> **robertcarlson1000000 said:**
> no /home was not a separate partition. I set the mounting point to / if that's what you're asking. I just noticed that when I press Ctrl+Alt+F1 and launch the console while booted on my disk drive, It can read all of my content just fine. but it can't while on a live CD. I'm going to try to copy everything on my /home folder to an SD Card. But, I don't know the command. Can you tell me??

BTW 14.10 was a typo. I was typing fast and didn't check for errors.
Can I assume you are working from a Live session

I'd suggest using Parted Magic from the RAM

Here is a link to a recent edition of PM
[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

You may be able to use the file manager there to copy the files.

---

### Post by robertcarlson1000000 on 2014-04-18
Also, I just noticed that when Gparted Displayed information about my partition it said that about 90GB of space is currently being used. I remember that when I did a check on my used space last week, about 90GB was used. I think that there is still a chance of getting the data off.

Also, I have enough space on my SD card if I needed to do ddrescue (about 110GB!) I have a 128GB card.

---

### Post by robertcarlson1000000 on 2014-04-18
ok. I will give PM a try tomorrow.

---

### Post by carl4926 on 2014-04-18
FYI:

It would go something like this

```
ionice -c3 ddrescue /dev/sda /media/sdc1/laptop.iso
```

where sda is your hdd
/media/sdc1 is the target partition and laptop.iso is the image name

You can open .iso image files in acetoneISO or similar apps to access your files

*This makes an image of your entire HDD, the .iso will be the same size as your HDD

Try just copy the files you want with the file manager first. But it's generally considered best not to mess too much with possibly corrupted data.

---

### Post by robertcarlson1000000 on 2014-04-19
PM is working! It's copying files from my home folder to my SD card (still keeping my fingers crossed though)

---

### Post by robertcarlson1000000 on 2014-04-19
Yes! It worked! You are a lifesaver! PM got all of my valuables (Photos, Videos, Music, Documents) off with only a few errors (it couldn't copy over some screenshots, but i don't care about those files). If somebody can close the post and mark this as solved that would be great. I hope you have a very happy Easter. Next time, I will make sure to copy all of my stuff to an SD card before upgrading.

---

### Post by carl4926 on 2014-04-20
> **robertcarlson1000000 said:**
> Yes! It worked! You are a lifesaver! PM got all of my valuables (Photos, Videos, Music, Documents) off with only a few errors (it couldn't copy over some screenshots, but i don't care about those files). If somebody can close the post and mark this as solved that would be great. I hope you have a very happy Easter. Next time, I will make sure to copy all of my stuff to an SD card before upgrading.
Happy to help

---

