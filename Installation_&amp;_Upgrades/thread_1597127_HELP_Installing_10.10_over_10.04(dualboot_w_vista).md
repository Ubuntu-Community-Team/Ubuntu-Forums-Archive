---
title: "HELP: Installing 10.10 over 10.04(dualboot w/ vista)"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by User of Names on 2010-10-14
So, I am dual-booting Vista and Ubuntu 10.04 on my laptop. Earlier today, I hard shutdown Ubuntu while it was doing an automatic update... a very bad move as it turned out, but circumstances demanded it. Now, when I to boot Ubuntu, I only get an odd-looking login screen (icon of computer in center of login panel and blue login button instead of tan) that is totally unresponsive. Mouse movement doesn't seem to do anything, and neither does the keyboard; all I can do is a hard shutdown. 

I have tried safe mode, I have tried leaving it alone and waiting for a response. I have now made a Live CD of Ubuntu 10.10, and I am ready to reinstall, but here's the problem: I'm not sure if I can safely install a new version of Ubuntu over a corrupted old version, especially since I already have a partition set up. 

I've heard about the GRUB location being important, and I've heard about the Ubuntu partition needing to be formatted, but I don't know how to do those things and I don't know what is necessary in my situation. 

I really need advice and help! What should I do?

---

### Post by oldfred on 2010-10-15
Do you have a separate /home or have backed up /home so you just want to install the new version into the same / (root) partition as your current install?

If you just want to install to the same partition, use manual install and choose your current root partition as the new root and reformat. If you have /home choose it but DO NOT format. It will find your current swap without any help.

On the manual install screen at the bottom is a combo box on where to install grub2. Just install to the same drive sda if you only have one drive. Do not install to partitions sda1, sda2 etc as that will not let you boot.

New version looks slightly different but it is the same process.
You have partitions so you do not have to create as shown but it shows Maverick screens.
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Full Disk install Lucid Graphical
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by User of Names on 2010-10-15
Thank you for replying! I have backups (on the vista partition) of the important files from /Home, But I don't have an actual backup of the entire directory. I'm ok with losing all of my data from the Ubuntu partition as long as the vista partition remains unharmed. ...I'm not sure if that is what you're asking.

What do you mean by a "seperate /Home"?

---

### Post by ronparent on 2010-10-15
The only problem in making a clean install is that it will wipe any data files you have. You could maybe however use the live cd to create a separate partition to copy your /home filesystem to. Then you could relatively safely install over your corrupted install. By selecting a manual partitioning option the partition designated as / could be formatted and overwritten while the separate partition with home would be designated as /home and not formatted. It should then retain your data and  much of your configurations. You are best advised to backup your data beforehand especially if you are unfamiliar with manual partitioning during an install. Good luck. 

edit: I see oldfred has already responded with excellent advice.

---

### Post by User of Names on 2010-10-15
When you say that I am advised to backup my data beforehand, do you mean my data on the vista partition (which I am keeping) as well, or just on the ubuntu partition?

Basically what I need to know is what I have to do differently from the default install: Do I need to do manual partition stuff? Do I need to change the location of grub2? I'm pretty lost...

---

### Post by oldfred on 2010-10-15
Any partition editing or installs require good backups. Generally the software works ok, but we see many users who accidentally install to the entire drive by mistake or install to the wrong partition by mistake. 

If you just want to reinstall Ubuntu you need to use manual install and choose your existing / (root) partition, choose / and choose format (ext3 or ext4). It will find swap automatically. Some have created separate /home partitions, but standard installs put /home (all your user settings and files) inside the root partition. When you overwrite / you will then lose any settings and files you had in Ubuntu unless you have them backed up.

If you choose to overwrite your current root partition it should not modify your Vista install. Just do not choose entire drive nor entire partition (which is confusing). Use the manual install and besure to choose your existing root partition.

---

