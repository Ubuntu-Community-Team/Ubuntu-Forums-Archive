---
title: "rsync questions before a fresh reinstallation of ubuntu 9.10"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-03-26
Hi there:

I have been having problems with an upgrade from EXT3 to EXT4 and have been adviced to make a fresh reinstallation from the live cd. I have "backuped" all my relevant data to an external hard drive (EXT3 format), but then, I was adviced to use rsync.

First, I was told to create, via terminal, a new folder in the external hard drive. With the next code I accessed the external hard drive (Volume 1):

```
hihihi100@hihihi100-laptop:~$ cd /media/Volume\ 1
hihihi100@hihihi100-laptop:/media/Volume 1$ 

```With the next command, I created the folder "old":

```
hihihi100@hihihi100-laptop:/media/Volume 1$ sudo mkdir ./old

```Entered my password, and I was able to see the new folder

I would appreciate if somebody could explain why I cannot just go to the external hard drive folder, right click on "create folder" instead of doing it via terminal.

Then I, via terminal, accessed this new folder named old:

```
hihihi100@hihihi100-laptop:/media/Volume 1$ cd old
hihihi100@hihihi100-laptop:/media/Volume 1/old$ 

```And then, told to write:

```
hihihi100@hihihi100-laptop:/media/Volume 1/old$ sudo rsync -aS /home/../.

```And Ubuntu started to copy files to my old folder inside the external hard drive. Please confirm this is not dangerous for the data stored in the external hard drive. After some 10 minutes, it stored 102 MB in this "old" folder. Ill show you a sample of  this command, plus the last lines, that include a warning:

```
drwx------        4096 2010/03/22 11:04:50 var/tmp/kdecache-hihihi100/kpc
-rw-r--r--     5230592 2009/11/02 14:08:17 var/tmp/kdecache-hihihi100/kpc/kalzium.data
-rw-r--r--     1359872 2010/02/26 16:04:30 var/tmp/kdecache-hihihi100/kpc/kalzium.index
-rw-r--r--    16240640 2010/03/22 11:04:34 var/tmp/kdecache-hihihi100/kpc/kde-icon-cache.data
-rw-r--r--     4296704 2010/03/22 11:04:50 var/tmp/kdecache-hihihi100/kpc/kde-icon-cache.index
-rw-r--r--           0 2010/03/22 11:04:43 var/tmp/kdecache-hihihi100/kpc/kde-icon-cache.updated
drwx------        4096 2009/07/29 18:35:20 var/tmp/kdecache-hihihi100/libphonon
-rw-r--r--       14084 2009/07/29 18:35:20 var/tmp/kdecache-hihihi100/libphonon/hardwaredatabase
_rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]_
hihihi100@hihihi100-laptop:/media/Volume 1/old$ 

```Just how important is the underlined section? And what is error code 23?

Then I was told to execute ls /home:

```
hihihi100@hihihi100-laptop:/media/Volume 1/old$ ls /home
hihihi100
hihihi100@hihihi100-laptop:/media/Volume 1/old$ 

```hihihi100 appeared in cyan

then told to execute ls:

```
hihihi100@hihihi100-laptop:/media/Volume 1/old$ ls
hihihi100
hihihi100@hihihi100-laptop:/media/Volume 1/old$ 

```and again, hihihi100 appeared in cyan

Now, what do I have to do?

Im a noob, my computing skills are very limited, so, please, give me a clear answer and type the commands I must execute clearly. Thanks

---

### Post by Slim Odds on 2010-03-26
First, you don't need sudo with rsync to backup your own files.

Second, any time that you see "/home/../." you know someone does not know what they are talking about. That type of construct is never ever needed. It's the same as "/home"  (which makes it look like you were backing up everyone's files).

Also, why are you "upgrading" from ext3 to ext4? There is no real benefit for a desktop system and you are just asking for trouble.

---

### Post by hihihi100 on 2010-03-26
slim, thats why I posted the thread, cause I dont know, but, AFAIK, the instructions I have been executing will allow me to, once I fresh reinstall, dont lose any piece of software I currently use, so I think

Anyway, it wont hurt the OS to run the command with the "home" part in it, will it?

And, given all the problems I am experiencing, I may just use EXT3

---

### Post by Slim Odds on 2010-03-26
> **hihihi100 said:**
> slim, thats why I posted the thread, cause I dont know, but, AFAIK, the instructions I have been executing will allow me to, once I fresh reinstall, dont lose any piece of software I currently use, so I think

Anyway, it wont hurt the OS to run the command with the "home" part in it, will it?

And, given all the problems I am experiencing, I may just use EXT3

Your programs are not in /home, so backing that up won't help you. You need a program like clonezilla that will let you backup your partitions in their entirety.

Give it a look..... [http://www.clonezilla.org/](http://www.clonezilla.org/)

There is no compelling reason for you to switch to EXT4. I'd just leave it alone if I were you.

P.S. Why to want to use EXT4?

---

### Post by leclerc65 on 2010-03-26
Grsync is easier to use than Rsync (sudo apt-get install grsync).
Another vote against EXT4.

---

### Post by hihihi100 on 2010-03-26
hiyas:

I say it again: I wanted to upgrade to EXT4 for the theoretical speed increase, up to 3 times, I even created a thread asking for POV's regarding the issue, and its not like the system doesnt work, right now Im writting this reply from the laptop in question with Gparted showing EXT4, but on kernel 19, not 20

Ill look into that new piece of software u make reference to... grsync

And yes, after the total reinstallation Ill leave it on EXT3

cheers

---

### Post by hihihi100 on 2010-03-26
No, Im not gonna leave it on EXT3, cause it is already GRUB2 and EXT4

After the fresh reinstallation, I have confirmed that both GRUB2 and EXT4 are fully operative in my laptop, and im obviously not gonna revert back to EXT3

EXT4 stays

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
```Thus, mine is not a vote against EXT4

Plus, you may want to take a look at the .png attached to the message #42 in [http://ubuntuforums.org/showthread.php?t=1435270&page=5](http://ubuntuforums.org/showthread.php?t=1435270&page=5)

And yes, all the detailed process summarized in the first post has been a waste of time...

Regards

---

