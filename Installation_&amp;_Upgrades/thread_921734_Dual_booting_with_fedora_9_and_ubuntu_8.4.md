---
title: "Dual booting with fedora 9 and ubuntu 8.4"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by neba on 2008-09-16
Hello. 
I have a really big problem. It is that I'm a total noob at Linux. I don't even know if I'm posting this in the right place. I want to dual boot Ubuntu 8.4 with Fedora 9. I have been trying for several days now. It don't really matter what os should be installed first.  I have nothing saved on my computer. I looked in google. Ever thing they talked about is in a hole new language. lol Right now I'm trying to install Ubuntu twice, then i will install Fedora over one of the ubuntu. I don't know if it will work. It is worth the shot. I would appreciate any help.

---

### Post by manishtech on 2008-09-16
> I want to dual boot Ubuntu 8.4 with Fedora 9. I have been trying for several days now. It don't really matter what os should be installed first
You are not installing Window and Linux, both are Linux distributions. I suggest you to install Fedora first and then Ubuntu.
Why? Just as it, Linux distros are quite intelligent, they wont screw up the other distributions.
Just take care that they are installed in different partitions  but they can share swap.

If you have any problems, revert back soon.

---

### Post by Pumalite on 2008-09-16
If you are not using Windows; clean and reformat your drive. Make an extended partition of the whole drive. Within that, make 2 logical partitions. Install Fedora in one first. Then install Ubuntu in the other last.

---

### Post by neba on 2008-09-16
When I try to partitions my hd using the Ubuntu live cd, already having Fedora on. My partition editer wont allow me to partition it. Should I go into Fedora and try to partition my hard drive that way? One of the biggest probles I have is just getting both on to my hd. Ever time when I put one on it takes off the other. lol. Even when I partition it, something happens and takes off both partition. How do you make it into the same swap? What does swop do? Thanks for replying to me so fast. I really appriciate it.

---

### Post by manishtech on 2008-09-17
Lets start slowly neba,

**1)** There are three types of partitions -primary, extended and logical. Extended partition is one which encapsules the logical partitions. Extended partition doesnt hold data, instead hold logical partitions. 

**2)** On each disk you can have only 4 primary partitions or 3 primary and 1 extended partition. More than one extended partition per disk is not allowed. An extended partition can therotically have infinite number of logical partitions, but in real sense, they dont.

**3)** If you have all 4 partitions as primary, then you have to create the partition layout, everytime I create partitions, I create 1 primary for windows (if its reqd) and rest all space with extened. Inside extended , I create as many partitions as I like.

**4)** **Swap Space**: Its needed since you have a finited amount of RAM. Swap space allows you to run many applications whose total can increase your physical RAM. When an open application is not used for a long time, its swapped to swap space.

**5)** **How to make it to same swap**: When you select partitions for installing, there should be one swap partition in the whole layout. If its there the installer detects it and decided to use it, you dont need to select it, its automatically selected if its present.

**6)** **How does it detect that the partition is swap**: Linux needs swap partition to be formatted with filesystem **linux-swap** which is a unique filesysystem.

**7)** **Find partition Layout**: You can find out the partition layout using the command
```
sudo fdisk -l
```
Please run this command in Applications>Accessories>Terminal and post back the output you get from this command. When the password is asked, enter the password you use to login to ubuntu.

---

