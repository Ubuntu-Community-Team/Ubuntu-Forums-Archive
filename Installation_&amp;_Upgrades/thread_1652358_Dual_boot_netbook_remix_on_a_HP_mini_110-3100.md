---
title: "Dual boot netbook remix on a HP mini 110-3100"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by scummie50 on 2010-12-24
I just bought a HP mini 110-3100. I want to install ubuntu netbook remix 10.10 and do a dual boot. I've got it installed on a usb drive already and started the installation. When I get to the screen where I am supposed to partition the drive I get confused. It seems there are already four partitions on my drive and I'm not sure what to do with them. I am pretty inexperienced with this stuff and don't want to mess up my new computer.

---

### Post by scummie50 on 2010-12-24
the four partitions are (C:), HP_TOOLS, RECOVERY (D:), and SYSTEM.  They take up all of the space on the hard drive.

---

### Post by Rubi1200 on 2010-12-24
Stop right now!

Firstly, welcome to the forums :)

Before you do anything else, go to Applications > Accessories > Terminal and post the output of this command:

```
sudo parted -l
```

(lowercase L not 1)

Do not continue with the installation until we see the output and can advise you on the best course of action.

Thanks.

---

### Post by scummie50 on 2010-12-24
The four drives are (C: ), HP_TOOLS, RECOVERY (D: ), and SYSTEM. These partitions take up all of the space on the hard drive.

---

### Post by scummie50 on 2010-12-24
Rubi1200, is there a way to do this in windows 7? Since I was unsure how to install ubuntu I haven't been using it.

---

### Post by Rubi1200 on 2010-12-24
Yes, I understand that.

The command I asked you to run will give us more information that will help us advise you how to deal with this.

You cannot have more than 4 primary partitions. Meaning, you will need to either delete or resize one of them.

The output will give us, and you, a better idea of how to achieve this.

Thanks.

EDIT: you can go to Disk Management in Windows and also post a screenshot if that is easier for you right now.

---

### Post by scummie50 on 2010-12-24
[IMG]http://i56.tinypic.com/148esyo.png[/IMG]

---

### Post by Rubi1200 on 2010-12-24
Thanks for the screenshot :)

Okay, scummie50 here is what I suggest.

Firstly, if you do not have a Windows installation/recovery disk you can make one from within Windows. I highly recommend this because you never know...

Second, if you want to install the latest version of Ubuntu, 10.10, you need to be aware of the fact that the installer has undergone some changes. 

These changes include options that may, and I stress may, cause you to lose your Windows install if you are not careful when it comes to partitioning and installing Ubuntu.

In any event, you would need to shrink the C drive to make room for Ubuntu. This can be done with the built-in tools in Disk Management.

Please read the following link to understand what I am talking about:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I know there is a lot of information there, but be patient and you will avoid mistakes.

If you are at all uncomfortable with any of this, I suggest you try Ubuntu using Wubi. This will create a virtual disk within Windows and requires no partitioning or other potentially damaging side-effects.

Once you are more comfortable, we can show you how to set up a proper dual-boot scenario.

I encourage you to read as much as you can first, ask questions here until you are happy with what you are about to do.

The last thing we would want is for you to lose your Windows installation.

I hope this helps you take your first steps towards using Ubuntu.

---

### Post by scummie50 on 2010-12-24
thanks so much, i will definitely be doing my homework with what you've provided.

---

### Post by Rubi1200 on 2010-12-24
You are more than welcome :)

I have to go now, but there are many users here who can also offer you great advice on what would be the best options for your particular scenario.

Good luck!

---

### Post by garvinrick4 on 2010-12-24
rubi1200:
#He would have to delete HP_Tools also, he needs another Primary.
#Wow HP has used all four Primarys from factory that is a pain in the rear.
#I have a HP laptop I am on now came with 3 used, boot,OS and Recovery
  at least left me one.

scummie50
# Hello I would use a linux partitioning tool called gparted in Ubuntu install cd under TRY UBUNTU.
# There you can remove HP_Tools and resize your C: drive: to give room for Linux
# Linux or UBuntu will give all your partitions sda numbers like sda1 sda2 sda3 and so on. Mean same thing
as C: or D: or H: in Windows.
# From now on in linux / means your C:drive or fllesystem and X means your Desktop and format is ext4 and windows format is NTFS
   Linux can read all formats Ntfs,fat,ext and Windows cannot read ext4
#Merry Christmas and welcome to Linux

P.S.  If I was you I would take a screenshot of gparted in Live CD and post it here with version of Ubuntu you want to install
        and let a user guide you thru first install.

---

### Post by scummie50 on 2010-12-25
Thanks for the info, I'm still reading through what Rubi1200 linked to.  I wonder though, is there not going to be stuff in HP_TOOLS that I need?  It wouldn't mess something up?  Some of the other stuff you wrote about really is like gibberish to me. I am definitely a newbie, I need to read through everything just to understand what the hell it all means.

---

### Post by Rubi1200 on 2010-12-25
That is a good question. I don't have the answer right now, but you could probably also find some information on the HP site.

You almost definitely don't want to delete the recovery and system partitions.

Keep reading and asking questions.

In the thread I linked to keep an eye out for posts by Herman linking to his site; these are some of the best instructions you will find anywhere for installing Ubuntu in a dual-boot configuration.

---

