---
title: "instaling ubuntu"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by nepaliman on 2007-05-11
i am having a much problem in installlation of this ubuntu. recently i have installed 2 times somtimes it has sound problem somtime somthing else like there is no synaptic installer , it just vanished  , i dont know what to do ,pls instruct me step by step procedure to install ubuntu , with disk partation done manually , there is no other operating system,, hope to hear soon
thank u

---

### Post by mvaniersel on 2007-05-11
Well, usually it is very easy. 

You have to

1. Download the ubuntu desktop edition and burn it to a CD
2. insert the CD and reboot the computer
3. Let the system boot from CD. Click on the "install" icon that appears in the top-left when it's ready.

If you're having problems with manual partitioning, why don't you let the installer do it for you? If there is no other operating system on your computer, there is no reason not to.

Could you be more specific to which part of the installation is giving you problems?

---

### Post by nepaliman on 2007-05-11
thank u dude , somhow i solved my problem , i did it ! but actually my laptop is acer travel mate , with 40 gb hard disc , i parted4 drives with 10 gb 1gb 15 gb and 13gb...
now when ubuntu is installed when i check the properties it says the operating drive is just 7 gb .. so on ,, there is alot of hard disc space is missin , i dont know where is prob  , i mean i am loosing some 10 gb there ,,, 
hope u understood what i mean .
take care
nepaliman !:)

---

### Post by mikewhatever on 2007-05-12
In Ubuntu, can you go to Applications>Accessories>Terminal, type in the following commands and post the output here
> sudo fdisk -l
> df -h

---

### Post by dobelden on 2007-05-12
do what mike says...

hope your problem solve :)

---

### Post by mvaniersel on 2007-05-13
Yeah, to explain a bit more what mike said;

```
sudo fdisk -l
```
This will give you a list of partitions on your hard diks, and which filesystem they are (e.g. NTFS for windows partitions or ext3 for linux partitions)

```
df -h
```
This will give you the amount of free / used space on each partition. The -h switch makes the output more readable.

---

