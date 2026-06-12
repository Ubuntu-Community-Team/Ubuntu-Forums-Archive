---
title: "After update to 11.04 won't boot"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by bogie5464 on 2011-05-01
I updated to 11.04, looked down after about an hour and a half, and my laptop was off. Now when I turn it on, it acts like it's checking my desk, but it says something like "/ is not available or doesn't exist press s to skip, or m to manually recover" then when you skip it's like "/mnt is not available" It could be possible I accidentally turned it off during the upgrade. Is there anyway i can fix this?

---

### Post by psychgypsy on 2011-05-01
Do you still have your live cd / flash drive? It sounds like your computer is trying to boot into your hard-drive. Boot into your cd and do a fresh install.

---

### Post by bogie5464 on 2011-05-01
> **psychgypsy said:**
> Do you still have your live cd / flash drive? It sounds like your computer is trying to boot into your hard-drive. Boot into your cd and do a fresh install.
I am looking for an alternative. I want it to boot to my harddrive, that's how I updated it, and that's where all of my personal files are. I have virtual machines, iso images, documents, powerpoints, and programs that I need.

---

### Post by garvinrick4 on 2011-05-01
Use a live cd with internet connection and chroot into the install and try to repair from there. Need your ubuntu sda# to mount the ubuntu partition in live cd.
I am using sda5 here use your own sda#.  sudo fdisk -l  (lower case L) in terminal to get sda# of linux install:
```
 
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

``````
apt-get -f install 
```
```
dpkg --configure -a
```
```
apt-get update && apt-get upgrade
```
```
exit
```
 
```
 
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt

```
```
 
sudo shutdown -r now

```
Hopefully this will start the process again and get your / in shape.

---

### Post by bogie5464 on 2011-05-02
> **garvinrick4 said:**
> Use a live cd with internet connection and chroot into the install and try to repair from there. Need your ubuntu sda# to mount the ubuntu partition in live cd.
I am using sda5 here use your own sda#.  sudo fdisk -l  (lower case L) in terminal to get sda# of linux install:
```
 
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

``````
apt-get -f install 
``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
exit
``````
 
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt

``````
 
sudo shutdown -r now

```Hopefully this will start the process again and get your / in shape.
You sir, are a god! My dpkg command has been running for a while, but I have a good feeling about this! Thank you very much!

---

### Post by garvinrick4 on 2011-05-02
Thanks for the complement but I am a long way from a Deity, a long, long way. If it all works out fine under thread tools in upper right mark as Solved please. Stick around this Forum and read them and participate there are some users here that are real sharp. And also use google and google and google some more when stumped also, sometimes even often will have Solved
issues you are looking for in some of these threads. I believe Google has little things called Spiders running around here looking for info to put in Google as answers. On one Christmas I think there were more Spiders than users in the Forum and I was one of them. New that day
I needed to get a more constructive life style. Enjoy your Ubuntu.

---

### Post by Corniger on 2011-05-05
Mine won't boot anymore PERIOD. After the update, I get the Logo with the orange dots and that's it.
Through lots of trial and error experiments I found out that if I shut the omputer down, switch off the PSU, press the On button, switch the PSU back on and then the computer, it takes me to sort of a boot menu (but ONLY if Ubuntu shuts down getting a signal from the power switch and the PSU on /off procedure).
There I can choose all sorts of thing, repair this and that, nothing works EXCEPT "previous Linux versions". Then it boots into the new Ubuntu interface.
Can i tell Ubuntu somehow to boot from that "previous" version?
One more thing: pressing all sorts of keys during the stuck bootup I found the underlying system messages and it says it can't connect to system bus or so.
Any ideas?

Thanks!

---

### Post by Corniger on 2011-05-07
Anyone?

---

