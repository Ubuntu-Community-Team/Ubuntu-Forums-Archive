---
title: "Failed to change ubuntu to Biolinux"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by stefan13 on 2013-11-25
Hi guys,

I have spend the past 3 hours completely failing to get my computer running back as normal. A little background of what I've done:

I had Ubuntu and Windows 7 dual boot on 1 hard disk installed. Things worked perfectly and smoothly.

 However, I wanted to change the ubuntu to biolinux, so I downloaded the biolinux iso, mounted it onto a USB, made a Biolinux Live Usb, and tried installing that on my computer. Now, as I was runing through the instal process one of the options given to me was to replace ubuntu with biolinux - perfect for what I wanted.

I clicked on the option, guided through the installation process, but within 3 minutes CRASH! error - some files could not be copied, possibly due to a faulty CD / USB or Hard drive.

I got slightly confused, and after a computer reset, I got greeted by the very common 

Error: unknown filesystem
grub rescue > 


I also, perhaps foolishly, tried to instal Biolinux alongisde the current partitions, so now my HDD looks like this, and nothing is bootable:

[IMG]http://i.imgur.com/kp73JiN.png[/IMG] 



Now I googled around, tried a little bit, and  figured I'd use boot repair:

**2nd option : install Boot-Repair in Ubuntu**

 - [boot your computer on a Ubuntu live-CD or live-USB.]("https://help.ubuntu.com/community/BootFromCD") 
- choose "Try Ubuntu" 
- connect internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type: 
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update- Press Enter. 
- Then type: 

sudo apt-get install -y boot-repair && (boot-repair &)- Press Enter




Which leads me to a horrible loop error:

[IMG]http://i.imgur.com/YC0bVDO.png[/IMG]a


At this point, no matter what I do, Boot repair seems stuck in a loop and can't do anything useful. I recieved

paste.ubuntu.com/6474752 as an error earlier.




Perhaps I have to have a CD? I'm not sure, all I know is I'm stuck and I've lost the use of my laptop.

If anyone can assist me and guide me in the correct way to sort this horrible problem out! All I want is to delete the old ubuntu and have Biolinux installed, not both at the same time!

Many thanks!

---

