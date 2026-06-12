---
title: "difficulty to mount window part in fstab"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by francois.lavoie on 2005-04-09
I am a some kind of a newbie that tries to migrate progressivelly to linux. Ubuntu seems the best bet. I've tried to install hoary but had major problems. So I stick to warty that works better on my computer. 

My main issue now is that I do not achieve mounting win2k partition with the use of fstab.

I was able to install ubuntu warty on a fat32 disk with a win2k os and data already installed. With the win2k os two partition were already provided. I knew I would eventually install a linux os on the second partition. My computer is an old DELL inspiron 3200.

I have different problems amongst which not being able to connect via a wireless card, within a small windows network. My card is a linksys WPC54GS. To be able to work it out, maybe with ndiswrap, I would like to have access to my window partition on which some precious files gathered by the internet could be dumped.

For the fstab issue the message I get is:

mount: mount point /WIN2K does not exist

My fstab is written as follow:

/dev/hda2    /     ext   defaults, errors=remount -ro         0     1
...

... /dev/hda1   /WIN2K    Vfat   defaults                            0     1

I understand that the last line must be wrong (naturally there is no such code lines as '...' in my file. It is just a way to omit all the text of the file.

What is wrong


I've tried

---

### Post by taygan on 2005-04-09
have you created the /WIN2K directory on your hard drive first? (an empty directory)

```
mkdir /WIN2K
```

---

### Post by jordanau on 2005-04-09
[QUOTE=francois.lavoie]I am a some kind of a newbie that tries to migrate progressivelly to linux. Ubuntu seems the best bet. I've tried to install hoary but had major problems. So I stick to warty that works better on my computer. 

My main issue now is that I do not achieve mounting win2k partition with the use of fstab.

I was able to install ubuntu warty on a fat32 disk with a win2k os and data already installed. With the win2k os two partition were already provided. I knew I would eventually install a linux os on the second partition. My computer is an old DELL inspiron 3200.

I have different problems amongst which not being able to connect via a wireless card, within a small windows network. My card is a linksys WPC54GS. To be able to work it out, maybe with ndiswrap, I would like to have access to my window partition on which some precious files gathered by the internet could be dumped.

For the fstab issue the message I get is:

mount: mount point /WIN2K does not exist

My fstab is written as follow:

/dev/hda2    /     ext   defaults, errors=remount -ro         0     1
...

... /dev/hda1   /WIN2K    Vfat   defaults                            0     1

I understand that the last line must be wrong (naturally there is no such code lines as '...' in my file. It is just a way to omit all the text of the file.

What is wrong


I've tried[/QUOTE]
 Okay Ndiswrapper will work for you i have the same card I think. Little tip move your computer to your wireless router and plug and ethernet cord from router to computer. Then do the ndiswrapper install wiki (which i can't find right now because it looks like ubuntulinux.org is down)

Secondly for the hard drive...

if you want to refer to the windows partition as WIN2K, then type the following:

sudo mkdir /media/WIN2K

Then change the line in fstab to 
/dev/hda1       /media/WIN2K  vfat    umask=000       0       0

change the umask= value to 0222 if you just want read only, leave it as is for read/write.

Finally:
sudo mount -a

that will mount the partition for this session, it will automatically be mounted during boots.

this is all at [www.ubuntuguide.org](www.ubuntuguide.org), which i advise you read/skim through

---

### Post by francois.lavoie on 2005-04-09
Thank you very much for answering rapidly to my window directory and fstab problems.

Taygan's solution was enough to mount the win2k partition. However under Gnome I could not get the properties of the files and the subdirectories where not apparent.

However, Jordanau solution worked just fine. I'm able to find every files of my windows partition and edit it.

Concerning Jordanau's solution to solve with ndiswrap my wireless card driver issue, I cannot hook myself directly to the router. My only other non-wireless option on the Dell being a Linksys USB 100 network adapter for which I have no linux driver. The plug of the origninal ethernet adapter had been broken.

In addition I do not even know how to unpack and install new software from the ubuntu gnome environment. I am still trying to find a very explicit internet link on the subject.

That is why I wanted to work on a downloaded ndiswrap file and windows driver from my win2k partition. Is there any obstacle to do so?

---

