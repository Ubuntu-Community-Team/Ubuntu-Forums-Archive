---
title: "Help windows ubuntu 11.10 and windows 7"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by Allurian on 2012-01-29
Okay so I had windows 7 and Ubuntu 11.04 when I first installed Ubuntu with Grub. Though I had issues and my windows partition had major issues and stopped working so I was forced to reinstall windows but now I can't get to ubuntu I've tried the Boot repair stuff with the live CD and stuff which didn't work and I've been looking through threads saying when you do the command 
sudo fdisk -l
It shows you all your partitions and drives and you should find the one that says linux, I've seen screenshots where they just say just "Linux" but I have the swap and an "Extended" which is where I'm stuck trying to get it working
Help would be appreciated 
Thanks! :)

---

### Post by oscarivera9 on 2012-01-30
Do yourself a favor and run:
sudo fdisk -l
Then, if possible get a screenshot of what you get, or at least copy and paste the results here.
After we see what you have we'll be able to help you.
Basically, we have to find out in which partition your Ubuntu is installed and then mount that partition with:
sudo mount /dev/sd?? /mnt
then:
sudo grub-install --boot-directory=mnt/boot /dev/sd?
then you reboot & then you run:
sudo update-grub

After that you should be back to normal.  The question ? marks is your Ubuntu partition.

---

### Post by darkod on 2012-01-30
It's better to copy the results of fdisk here, but if you really saw only Linux Swap partition when you run it, it means your root system partition (type Linux) is not there. You might have installed windows over it, or it got deleted or something.

Post the results of fdisk anyway.

---

