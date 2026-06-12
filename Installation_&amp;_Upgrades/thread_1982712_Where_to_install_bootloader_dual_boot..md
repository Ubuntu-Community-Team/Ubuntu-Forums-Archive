---
title: "Where to install bootloader? dual boot."
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2012-05-19
Hi. I have decided to install Xubuntu 12.04 LTS. I am going to be dual booting and am at the end of the installation. I have a prompt asking where I wish to install the boot partition. 

Do I choose the partition with W7 bootloader on it? There is also an option for what appears to be the whole hard drive. IIRC I would install the linux bootloader over the W7 bootloader correct? I have included a screenshot of two locations I think the bootloader might go. Not sure so I hope someone can help me out :)

Thanks.

---

### Post by wilee-nilee on 2012-05-19
> **emeraldgirl08 said:**
> Hi. I have decided to install Xubuntu 12.04 LTS. I am going to be dual booting and am at the end of the installation. I have a prompt asking where I wish to install the boot partition. 
 
Do I choose the partition with W7 bootloader on it? There is also an option for what appears to be the whole hard drive. IIRC I would install the linux bootloader over the W7 bootloader correct? 
 
Thanks.
 
Grub would go in the mbr which is sda sounds like your calling that the whole drive. Yes it will overwrite the windows boot loader in the mbr, but grub will find the windows install and it will be in the boot menu.

---

### Post by emeraldgirl08 on 2012-05-19
Thanks for responding wilee. Bootloader in sda and not sda1 correct? You probably just noticed I have included a screenshot now.

---

### Post by Elfy on 2012-05-19
That's correct :)

---

### Post by emeraldgirl08 on 2012-05-19
Yay! Okay here goes!

Thanks :) :) :)

---

### Post by emeraldgirl08 on 2012-05-19
The installation gave me a grub-rescue prompt. I have included a screenshot of my partition setup. Is there any code I can run in terminal to fix my setup?

---

### Post by wilee-nilee on 2012-05-19
> **emeraldgirl08 said:**
> The installation gave me a grub-rescue prompt. I have included a screenshot of my partition setup. Is there any code I can run in terminal to fix my setup?

Check out this boot-repiar tool, it will probably fix this with the recommended repair, it will generate a script as well to read, post it if you still have problems

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by darkod on 2012-05-19
It would be best to run the boot info script from the link in my signature. That will show us many details.

In case you want to try installing grub2 to the MBR again, from live mode in terminal you can try:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

But the script results would also show if any grub2 files are missing.

Also, do you have more than one HDD? You might have broken grub on another hdd and if the system is trying to boot from that one, you will get the grub rescue message but your working grub2 can be on another hdd.

---

### Post by emeraldgirl08 on 2012-05-19
In desparation tried this 

[repair bootsector]("http://ubuntuforums.org/showthread.php?t=1926510")

I am going to reboot and see what happens. I will work on this some more when I wake later on this morning. It is 2am here in Arizona and sleep sounds very good. I will be able to work better on this when I get a couple of hours sleep in. 

@darkod. This dual boot is on my laptop. It has one hard drive. I divided up my root,/home, and swapfile for the Xubuntu install. If you take a look at my screenshot from gparted it shows the different partitions. Xubuntu is somewhat new to me as I have been using Ubuntu on-and-off the last three years. 

@wilee. Thanks for that link. I will look at it when I wake later. 

Good night guys.

---

### Post by black veils on 2012-05-19
not sure what you have done, but there is an app you can use to fix boot problems.


1.  boot into your Ubuntu live cd/usb, choose to load the desktop environment.

2.  open the terminal and copy-paste the following commands individually (press the Enter key after each and wait).

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
```
sudo apt-get update
```
```
sudo apt-get install boot-repair
```

3.  find and launch boot-repair, then choose recommended repair

---

### Post by darkod on 2012-05-19
> **emeraldgirl08 said:**
> In desparation tried this 

[repair bootsector]("http://ubuntuforums.org/showthread.php?t=1926510")

I am going to reboot and see what happens. I will work on this some more when I wake later on this morning. It is 2am here in Arizona and sleep sounds very good. I will be able to work better on this when I get a couple of hours sleep in. 

@darkod. This dual boot is on my laptop. It has one hard drive. I divided up my root,/home, and swapfile for the Xubuntu install. If you take a look at my screenshot from gparted it shows the different partitions. Xubuntu is somewhat new to me as I have been using Ubuntu on-and-off the last three years. 

@wilee. Thanks for that link. I will look at it when I wake later. 

Good night guys.

That is for repairing partition boot sectors if grub ends on it somehow. It wouldn't help you booting your computer in this case. It would only help if the problem was that grub was installed onto the windows partition.

---

### Post by emeraldgirl08 on 2012-05-19
Back after some much needed shut-eye :)

Okay. I turned on my laptop and the dos-text is an error that states:

```
error: the symbol 'grub_xputs' not found.
grub rescue>
```

@black veils. Thanks for the instructions. I will give it a try now. It's been SO long since I have had to repair a boot in linux! My 10.04 partition of Ubuntu LTS was totally trouble free since it first came out and I installed it.

@darkod. Hi there again. Thanks for the information on that fix I tried :)

---

### Post by emeraldgirl08 on 2012-05-19
SOLVED.

@all who helped. Thanks for the help! I got it working with the boot-repair tool :):):)

---

