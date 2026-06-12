---
title: "How to make a clean install of Xubuntu from Ubuntu 16.04 LTS"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by ubu112 on 2017-05-03
I have an Acer Aspire One AOA150/ZG5 with Ubuntu 16.04 LTS installed.

Now I'm tring Xubuntu from a live USB and it seems to be faster.Before the install,can I install Chromium?because Firefox is making something strange.And,can I update now or

 have I to wait after the install?

Please,I'd need help for how to make a clean install of Xubuntu 16.04 LTS (deleting Ubuntu)and how to change XFCE to LXDE.

I'm not an expert at all,please,guide me.

Thank you

---

### Post by ajgreeny on 2017-05-03
You install Xubuntu the same way you installed Ubuntu using the live USB that you have already tried.

Do you have a separate /home partition?
Show us the output from Ubuntu of command **df -h** in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by ubu112 on 2017-05-03
Unfortunately,i didn't make the Ubuntu install .

```
user@user-AOA150:~$ df -h
File system     Dim. Usati Dispon. Uso% Montato su
udev            477M     0    477M   0% /dev
tmpfs            99M  4,9M     94M   5% /run
/dev/sda1       146G   11G    128G   8% /
tmpfs           495M  6,3M    488M   2% /dev/shm
tmpfs           5,0M  4,0K    5,0M   1% /run/lock
tmpfs           495M     0    495M   0% /sys/fs/cgroup
tmpfs            99M   72K     99M   1% /run/user/1000
user@user-AOA150:~$ 



```

Thank you

---

### Post by ajgreeny on 2017-05-03
No you do not have a separate /home partition so if you have a lot of personal files (docs, music videos, etc etc) in your home you will need to backup all of them before reinstalling.

Having done that, install from the USB and allow the system to use all the disk which will then automatically set the partition sizes for the root or OS partition and another smaller one for swap.

There is a good thread at [https://ubuntuforums.org/showthread.php?t=2230389](https://ubuntuforums.org/showthread.php?t=2230389) about running live and installing the various *ubuntu family OSs.

---

### Post by ubu112 on 2017-05-03
Thank you for your answer.I'll read the thread you send to me.

I have few question:

 1)I'll copy and paste my files on an other USB 

2)I made the live USB using "disk creator" in Ubuntu,is it correct?I won't have problems when I'll start my system

3) Is really needed to check the .iso I downloaded? because I didn't understand md5sum

4)when I'll say to install Xubuntu,Ubuntu will be deleted completely?

Have you other suggestions to give me?I hope to be able to make all correctly,because this is my first time.

Thank you,ajgreeny

---

### Post by apmcd47 on 2017-05-04
This is the first time I've posted in a while.
> **ubu112 said:**
> Thank you for your answer.I'll read the thread you send to me.

I have few question:

 1)I'll copy and paste my files on an other USB 
Sounds good to me.> 
2)I made the live USB using "disk creator" in Ubuntu,is it correct?I won't have problems when I'll start my system
Assuming this is how you have been running your test live system, no.> 
3) Is really needed to check the .iso I downloaded? because I didn't understand md5sum
It's probably worth it to ensure you aren't using a hacked version with back doors for the "men in black hats".
It should be as easy as downloading an md5sum file (prefereably from a different download site, if you're really paranoid) and typing
```
md5sum --ignore-missing --check md5sums
``` (where *md5sums* is the name of your md5sums file.)
> 
4)when I'll say to install Xubuntu,Ubuntu will be deleted completely?
Very likely it will at best delete all the system directories and create new ones; at worst it will reformat the root partition, which in your case is the whole disk.> 
Have you other suggestions to give me?I hope to be able to make all correctly,because this is my first time.

Thank you,ajgreeny

You **could** just install the xubuntu desktop over your current system. I did this with my 14.04LTS when KDE kept crashing.
```
sudo apt install xubuntu-desktop
``` (Not a typo: that is meant to say apt, not apt-get).

It should work just as well; allow you to come back to Ubuntu if necessary; and keep your home directory intact.

If you go for the clean install, when it comes to how it should use the disk, choose the advanced option which should bring up a partition manager. Then set up separate root and home partitions (30-40Gb should be adequate for the root partition). Also add a swap partition (it should be the same size as the RAM).

I can't think of anything else.

Andrew

---

### Post by vasa1 on 2017-05-04
> **ubu112 said:**
> ...
Please,I'd need help for how to make a clean install of Xubuntu 16.04 LTS (deleting Ubuntu)and how to change XFCE to LXDE.
...

If you have backed up any personal data, you can do a clean install of any official flavor using its live USB. The installation process will overwrite your existing Ubuntu. You will be offered the option to retain your home folder but if you've backed up already, and are "new" to Ubuntu, just let the process make you a clean home folder as well.

I don't quite get why you *first* want to install Xubuntu and *then* change XFCE to LXDE :???:

---

### Post by ubu112 on 2017-05-04
First of all,thank you Vasa1 for your answer.

I'm not an expert at all,so I'd need some help because this is my first time and I don't want to make mistakes.

> [COLOR=#000000]I don't quite get why you [/COLOR]*first want to install Xubuntu and [I]then change XFCE to LXDE*[/I]

I received an advice in the previous thread,that LXDE is lighter than XFCE,honestly I don't know how much the difference is.

As you said,I'll let the process make a new home folder.Can you,please,explain to me the difference between keep the old folder or let make a new one?

Is it very important to check the .iso I downloaded?because, as not expert,I don't really know how to do correctly.

The process will create right partitions on my disk?

If you have some more advices,please,are really needed.

Thank you

---

