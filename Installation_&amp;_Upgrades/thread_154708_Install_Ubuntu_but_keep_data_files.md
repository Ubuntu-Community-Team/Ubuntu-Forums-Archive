---
title: "Install Ubuntu but keep data files"
date: 2006-04-03
forum: Installation &amp; Upgrades
---

### Post by dfiant on 2006-04-03
Ok... here's my situation.  I am a current windows user who has used ubuntu dual boot in the past and now I want to switch my entire system over to ubuntu.  I have two hard drives.  One of them (a 120GB) is used completely for storage, while the other (a 160GB) holds the operating system and is also used for storage.  I was wondering if there is any way to keep the files (mostly video files) I have on my 120GB drive and part of my 160GB drive and still replace windows with ubuntu WITHOUT partioning the 160GB (because I don't have much space left on it.)  I would really appreciate any help with this.

---

### Post by AdotB on 2006-04-03
If I understand correctly, then right now you only have Windows installed and each disk has only one partition (the whole disk). 

I don't think its possible because Windows usually uses the ntfs file system which Ubuntu cannot write to.

---

### Post by ubuntu27 on 2006-04-03
This is what I understand from "dfiant" post.

General:
1) He has two OS, Ubuntu and Windows
2) He wants to **delete** Windows and **keep** Ubuntu

3) He has two HD, I will name it "A" and "B"
4) HD "A" is only used to store his personal files... (I guess it uses FAT fylesystem in order to share it between Ubuntu and Windows.)
5) HD "B" has like 4 partition if I'm correct:
   a) B have Windows and Ubuntu OS [Two partitions]
   b) swap [one partition]
   c) Another partition for his "Home" folder...  or maybe not.
   d) so... maybe he has 3 or 4 partition in HD B


To be sure of his situation, we need more info.


**@dfiant,** can you open "gparted" and post a screenshot of it here? That will help a lot.

sudo apt-get install gparted

if you don't have it installed.


or just run the Live CD, and open gparted. [Applications/System Tools/gParted]  ;)


EDIT: I've re-red it, and now I'm lost >< I'm not even sure if he has ubuntu currently instaled or not :D

dfiant. :) We need your imput :D

---

### Post by dfiant on 2006-04-03
sorry... I should have explained myself better... I ONLY have windows installed currently... It used to be a double boot.

1.  Windows is on Drive A
2.  Storage is Drive B
3.  I want to save some of the data from Drive A and all of it from Drive B, However, I do not have the space to partition drive A in order to keep the files I still want seperate from Windows.
4.  Is it possible to keep the files I want from Drives A and B, and still COMPLETELY get rid of Windows in favor of Ubuntu?

P.S. Let me know if this still doesn't make any sense... lol.

---

### Post by dfiant on 2006-04-03
and if it's not possible to do that... then would it be possible to keep my files on the computer if i converted the filesystem to fat?... i have partition magic... which aparently allows you to switch filesystems without damaging the files.

---

### Post by ubuntu27 on 2006-04-03
ok.

First, move your files that are in HD&#12288;A to HD B.

And then, isntall Ubuntu over HD A (thus erasing Windwos :) )

You have partition magick? Then, can you please take a screnshot of it? 
[_ Alt + Print Scrn_ and then paste to some image program like Paint and save it] 

:)

---

### Post by dfiant on 2006-04-03
ok... i'm currently burning what i want from HD A to dvds because i don't have space on HD B to put it all on... after that I'll install Ubuntu Over HD A... should I change the filesystem of HD B to FAT with partion magic?... and If I install Ubuntu over HD A are you sure it will recognize HD B without damaging the data on it?... (just want to make sure.)

Drive A is actually in 2 partitions (1 very small for Windows recovery which will also be overwriten when i install ubuntu)

The screen cap of partition magic can be found here:  [http://photos1.blogger.com/blogger/2324/2624/1600/partitionmagic.jpg]("http://photos1.blogger.com/blogger/2324/2624/1600/partitionmagic.jpg")

---

### Post by rplantz on 2006-04-04
The usual rules apply here. Namely, the value of a backup equals everything you've done since your last backup. (Only you can determine what that is.)

This might be a good time to buy an external disk and start using it for backups. Then you could back up at least your important data before beginning this adventure.

I've been doing this stuff since the early 60s, and I still make dumb mistakes. A few weeks ago I read a warning about deleting my home directory in my chroot environment. Within a few hours I did precisely what I had just read that I should not do. Glad I had a backup! Okay, there's probably a point where aging overrides experience. I don't *think* that I've quite reached that -- yet.  :)

---

### Post by ubuntu27 on 2006-04-04
[QUOTE=dfiant]ok... i'm currently burning what i want from HD A to dvds because i don't have space on HD B to put it all on... after that I'll install Ubuntu Over HD A... should I change the filesystem of HD B to FAT with partion magic?... and If I install Ubuntu over HD A are you sure it will recognize HD B without damaging the data on it?... (just want to make sure.)

Drive A is actually in 2 partitions (1 very small for Windows recovery which will also be overwriten when i install ubuntu)

The screen cap of partition magic can be found here:  [http://photos1.blogger.com/blogger/2324/2624/1600/partitionmagic.jpg]("http://photos1.blogger.com/blogger/2324/2624/1600/partitionmagic.jpg")[/QUOTE]


Perfect. Burn everythign that's on HD A you wanna save on a CD or DVD :)
Then, install Ubuntu over your HD A. ;)

I don't have two hard drives, but, I'm sure that Ubuntu will recognize your second hard drive [haha, too much faith? :P]
But, I am PRETTY SURE that Ubuntu won't touch your second HD unless you tell it so.

Good Luck!!

Tell us if everything went well. :)

---

### Post by dfiant on 2006-04-04
Ok... everything worked... but now i have a new problem... i can't edit anything on HD B... it says that the access path is /root and I can't change anything because I'm not the owner... what can i do to fix this?... i can read everything on the disk... i just can't change anything.

---

### Post by AdotB on 2006-04-04
I had the same problem with my windows partition. i used this guide by aysiu: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I hope that helps.

---

### Post by ubuntu27 on 2006-04-05
[QUOTE=dfiant]Ok... everything worked... but now i have a new problem... i can't edit anything on HD B... it says that the access path is /root and I can't change anything because I'm not the owner... what can i do to fix this?... i can read everything on the disk... i just can't change anything.[/QUOTE]

The problem is that your HD B is using NTFS, and Ubuntu can't write onto it [just read it]

So, you should format your HD&#12288;B as Fat32, no, you don't have Windows anymore..   format it as ext3.

NOw, I think it is better to **Backup your files that are on HD B** on a DVD or CDs BEFORE you format the disk (HD B) just in case. One never knows what could happen.

---

### Post by dfiant on 2006-04-05
I actually figured out the problem with some help from some people from IRC.  The problem was not that it was ntfs... it's fat32... the problem was that the drive was not mounted... may sound like a very simple problem... but i managed to complicate things... thanks for all your help!... everything's good now.

---

### Post by ubuntu27 on 2006-04-05
[QUOTE=dfiant]I actually figured out the problem with some help from some people from IRC.  The problem was not that it was ntfs... it's fat32... the problem was that the drive was not mounted... may sound like a very simple problem... but i managed to complicate things... thanks for all your help!... everything's good now.[/QUOTE]


Yey! Good Job dfiant. :D

And thank you at the peple of the #ubuntu channel :)

---

