---
title: "[SOLVED] How to prepare partitions ?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by qwe99 on 2008-11-01
I want to install Ubuntu 8.1 on the free space which I have it expect Windows. But I don't know how to prepare the parts :( Now I want to make the partition as swap part+system files part+a storage part. But I don't know what means the options which are asking when I am going to click "new partition" on the free space ? "type for new partition" , "Location for the new partition" , "use as" and "mount point" ? How must I choise those options for every part ?:confused:

---

### Post by dru3692 on 2008-11-01
I assume you are letting the ubuntu CD do the partitioning and not another piece of software like Partition Magic. 

You should be able to adjust the amount of space the CD will allocate to each partition during the Ubuntu partitioning process by dragging the cursor left or right on the bar graph shown. Then just let the CD create all the necessary partitions for you. Thats what I did. It was very easy.

---

### Post by qwe99 on 2008-11-01
I use the Ubuntu cd to install not something different. I know that I can do it by dragging the cursor but I want to learn what it is going to do? Maybe it will be better for me if I want to delete Ubuntu from my computer. Because I read that sometimes it will be difficult do delete the parts from hdd. And if I am going to make the part as you sad, will it create a part for storage?
So can someone write me what should I do the options for every new part which I will create ? I only want that ?

---

### Post by Ryan450 on 2008-11-01
Alright I'll give you a quick rundown on Linux Partitioning.

The main operating system gets stored in a directory called /

/ is your top level that is referred to as root. All files get listed here.

if you want to seperate your data from the rest of the operating system, you can create another partition to do so. Most people accomplish this by creating a seperate /home partition. 

The /home is where all user files are stored. Think of this as the My Documents folder in Windows. All your saved documents, pictures, videos, etc etc usually reside in here. 

The swap partition doesnt get mounted into the operating system, instead it is reserved for additional memory should you run out of RAM. Usually you want to create a swap partition that is at least as big as your RAM. The reason behind this is that if the operating system were to crash or something really bad happened, the contents in your ram get dumped to your swap partition on the hard disk for recovery later. 

In linux you can break up the directory tree into as many partitions as you want. myself I usually create three partitions for my Linux system.

/
/home
swap

I usually keep 50% of my disk space for / as application files get installed into that partition, and depending on what your using it can grow pretty rapidly. The core operating system itself only takes about 4-5 gigs give or take. 

Hope this helps you out some more, if you want to get further in depth your best bet is to research the linux file structure via google.

---

### Post by m_l17 on 2008-11-01
My Ubuntu partitions are setup as follows:

/boot 100mb

swap 2gb just to be safe, I have 2gb of ram

/ <---- OS 10gb

/tmp <--- for temp files 2gb

/home <--- users files, the rest of the hardrive
 
/data <--- on a separate hard drive for backups and or anything else I want to keep separate from main hard drive  

These are just my preferences. You should at least have a separate /home partition. So if you have to reinstall all your settings and files will still be there. But you should back up your /home

---

### Post by qwe99 on 2008-11-02
Ryan450 Thank you but I did not understand something .. You told me that I can use the /home part to backup my files. But if Ubuntu would crash, I will have to format this part too :( . I want to have a part completely seperate from filesystem part which I'm going to format it at least every new version of Ubuntu. I had installed Ubuntu 3 month ago. I had install just / part (Because it was very simple :) no swap, no other part to save my files). But even I had not created a /home part on install, I can write my files on /home/username folder...


> **m_l17 said:**
> 
/data <--- on a separate hard drive for backups and or anything else I want to keep separate from main hard drive  



So I'm going to prepare the partitions like this :
/      (I will format this part if Ubuntu will crash)
/swap  (I never gonna touch this place:) )
/data  (for my documents)

But My document are deleting after I format the "/" part :(
 I have to a new part with Windows xp (ntfs) and I will use it for my documents:( But I don't want that.

---

### Post by kansasnoob on 2008-11-02
Best illustrated guide on planet Earth:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Especially look at the section:

> NEW: Choose one of three different Ubuntu 'Desktop CD' graphical installations,

Another great guide:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by bulldog on 2008-11-02
Just make three partitions and you are safe.

10GB for the /  [OS] format ext3
2GB for swap         format as swap    
As much as you want for /home format ext3 only once when it is empty!
You can make an additional 10GB partition if you want to try a next ubuntu,and use the same swap and /home
The only thing's you have to keep in mind:
When mounting the /home folder when it is loaded with your data,DON'T SET IT TO FORMAT,just mount it at the /home mount point!
The next thing is,when you do a reinstal or install a second ubuntu,CHOOSE A DIFFERENT USERNAME AND PASSWORD,don't use the same as the one you are replacing.
In your /home will be a new folder created for your new install,and you can copy all what you want to have out of the 'old 'one.
So if you want to try safely  a next ubuntu,and not destroying the old one,make two partitions of about 10GB,and use the same swap and /home for both.

---

### Post by qwe99 on 2008-11-02
kansasnoob your links which you gave me, doesn't explain about /home or /data to save your datas.

This is my partition now:
[http://img249.imageshack.us/my.php?image=beforekr6.jpg](http://img249.imageshack.us/my.php?image=beforekr6.jpg)

My system is very simple. I want the partition to be like this:
[http://img255.imageshack.us/my.php?image=afterye0.jpg](http://img255.imageshack.us/my.php?image=afterye0.jpg)

But I can't understand . If my Ubuntu will crashed, and if I format sda7(/), will sda8(/data) format automatically.So it is impossible to save my files with Linux... :( Please explain me how you save your datas! There is an another way to save it?I wont to be like the picture which I give.

(sorry for my english :( )

---

### Post by bulldog on 2008-11-02
Just make three or even four partitions and you are safe.

10GB for the /  [OS] format ext3
2GB for swap         format as swap    
As much as you want for /home format ext3 only once when it is empty!

You can make an additional 10GB partition if you want to try a next ubuntu,and use the same swap and /home

The only thing's you have to keep in mind:
When mounting the /home folder when it is loaded with your data,DON'T SET IT TO FORMAT,just mount it at the /home mount point!
The next thing is,when you do a reinstal or install a second ubuntu,CHOOSE A DIFFERENT USERNAME AND PASSWORD,don't use the same as the one you are replacing.

In your /home will be a new folder created for your new install,and you can copy all what you want to have out of the 'old 'one.
So if you want to try safely  a next ubuntu,and not destroying the old one,make two partitions of about 10GB,and use the same swap and /home for both.

---

### Post by m_l17 on 2008-11-02
> **qwe99 said:**
> Ryan450 Thank you but I did not understand something .. You told me that I can use the /home part to backup my files. But if Ubuntu would crash, I will have to format this part too :( . I want to have a part completely seperate from filesystem part which I'm going to format it at least every new version of Ubuntu. I had installed Ubuntu 3 month ago. I had install just / part (Because it was very simple :) no swap, no other part to save my files). But even I had not created a /home part on install, I can write my files on /home/username folder...[QUOTE/]





So I'm going to prepare the partitions like this :
/      (I will format this part if Ubuntu will crash)
/swap  (I never gonna touch this place:) )
/data  (for my documents)

But My document are deleting after I format the "/" part :(
I have to a new part with Windows xp (ntfs) and I will use it for my documents:( But I don't want that.

No will not have to format /home if it's own partition. But let's say you have to reinstall for some reason. All you have to do to fresh install of Ubuntu is.

Use manual partition from the install. You will have list of all partitions sda1 sda2 etc.. and a list of hard drives from the top right pull down menu. What I do is write down for future reference what each partition is for and hard drive. This is how mine are setup

/dev/sda
sda1 = /boot
sda2 = swap
sda3 = /
sda5 = /tmp 
sda6 = /home

/dev/sdc

sdc1 =/data

I recreate the mount points as above ONLY FORMAT /boot /tmp and /
/home will not be touched and if you use the same username you will have all your settings. But it is good practice to make a backup of /home before do a reinstall. Also anything in /data will not be touched either, since the only thing you will do is creat a mount point.

> But even I had not created a /home part on install, I can write my files on /home/username folder...

Yes, you are correct the difference is you have more control over your data by creating a /home partition. It's up to you how you go about it and if it's worth the extra steps.

---

### Post by fewjr on 2008-11-02
kansasnoob said > Best illustrated guide on planet Earth:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

 I second that motion!

So QUE99,
     Herman's site is very informative, and he has been very gracious and helpful to boot. I have read most of his site, and reread alot of it. I highly recommend this howto if you want to duelboot WinXp and Ubuntu:

[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

Do a little reading, it will do you alot of good in the long run.

Best Regards and good luck
fewjr

---

### Post by zuheyr on 2008-11-02
Hi,

I just installed the 8.10. I think it is a very good idea to burn the image of gparted and do the partitions *before* you run the live cd. Just reboot from the gparted cd. 

It is a *wonderful* tool that allows you to play with the partitions as you can do, and undo many times until you really know what you are doing.

Once you are happy, you finalize it and create the partitions. 

Just make sure you note the device names of the partitions. Then you run the live CD and it is a child play.

Good luck,

Zuheyr

---

### Post by qwe99 on 2008-11-02
m_l17 thank you. I will prepare the partition like this :
/dev/sda
sda1 = ntfs
sda5 = ntfs
sda6 = swap
sda7 = /

/dev/sdc
sdc1 =/data (my document)

It would be better like this .. Do I have to open the other parts (boot,tmp,home)? Because if I format the Ubuntu, I will format all of "/" part.
And if my solution is true, After I format the WindowsXP (sda1 = ntfs) how can I install the grub again from terminal of Ubuntu (with live cd)? 

Before I had just 3 parts sda1(ntfs)+sda2(ntfs)+ext(ubuntu filesystem /) I use these commands :
xterm
sudo grup
find /boot/grub/stage1
root(hd0,2)
setup(hd0)
... Or can you explain how the command using for every case ?

---

### Post by qwe99 on 2008-11-02
I try to prepare the part as I said, but it wants a format for all harddisk if I open a new /dev/sdc :( .  So I could not install. :(

---

### Post by m_l17 on 2008-11-02
> **qwe99 said:**
> I try to prepare the part as I said, but it wants a format for all harddisk if I open a new /dev/sdc :( .  So I could not install. :(

Sorry I forgot to mention, that the first time you will have to erase all current partitions and then create them as you like. You only have to this once unless you decide you change. 

You can also just erase the partitions you want and leave the ones you want. Create new partitions from free space.

I would back everything you need and or want and then proceed with the install.


> **qwe99 said:**
> /dev/sda
sda1 = ntfs
sda5 = ntfs
sda6 = swap
sda7 = /

Don't forget after you create the partitions, to create the mounts points.

sda1 = ntfs should be sda1 = /ntfs and so on

What are you using sda1 and sda5 for? 

And what are the current partitions, for sda and sdc?

Hope this helps.

---

### Post by qwe99 on 2008-11-02
m_l17 you tell me I should do the sda1 (C-ntfs part of windows xp) "/" (mount point) ?! Why ? I use the ntfs part for my windows. I don't want to use the ntfs part with Linux. I want a part which is not ntfs or fat32. I don't want to write from windows at this part. Think a part for just for Linux. If I don't use windows, how can I have got a part which is not formatting never when you re-install or delete the Ubuntu. (example on widows xp: I have the C drive for my program files and windows files. And second D part which I had never format it)
Please just teel me the answer like this and the reason :
sda1 = ntfs
sda5 = ntfs
sda3= swap
sda7=  ?????
sda2=  ????  the answers and why ? please !!!! :(

---

### Post by m_l17 on 2008-11-02
List all your hard drives and current partitions. Please explain what are you trying to do? You lost me.

---

### Post by qwe99 on 2008-11-03
List of my current partitions:
[http://img249.imageshack.us/my.php?image=beforekr6.jpg](http://img249.imageshack.us/my.php?image=beforekr6.jpg)

If you look the partititons you can see 2 ntfs parts.Thoose are for windows. The first is C which has progmram and windows system files. The second is D which has my speciall documents which are never deleting when I formöat windows xp. I want a part to copy my document like on Windows. But for Linux ofcourse)

---

### Post by m_l17 on 2008-11-03
> **qwe99 said:**
> List of my current partitions:
[http://img249.imageshack.us/my.php?image=beforekr6.jpg](http://img249.imageshack.us/my.php?image=beforekr6.jpg)

If you look the partititons you can see 2 ntfs parts.Thoose are for windows. The first is C which has progmram and windows system files. The second is D which has my speciall documents which are never deleting when I formöat windows xp. I want a part to copy my document like on Windows. But for Linux ofcourse)

/home = D in windows

You need at least these partitions:

/ <--- for Ubuntu OS [write down the device info [example /dev/sda4]
/home <---- this functions like your D:/ in windows
swap <---- size depends on how much ram you have, I suggest at least 1gb to be safe

It's up to you how much space to give both  partitions I would give at least 10gb for your / and the rest to /home or you split them evenly.
And format them as ext3.

When you get right before installing Ubuntu you will need to tell the installer where the boot loader needs to go so it doesn't mess with your current windows install. 

So look at the bottom right and you see advance click on it. It will ask you where you want the boot loader to go. Select the partition you used for / that you wrote down before [example /dev/sda4].

Hope this helps.

---

