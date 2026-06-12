---
title: "[SOLVED] reinstall from live cd w/dual boot vista"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2008-08-17
messing around with my (fully functioning)Nvidia driver settings in synaptic i somehow lost x server access.Yeah i should have left well enough alone,but i didnt,i had to play.Ive had knowledgeable help in forums giving me terminal codes to try to restart x server with no success.I have the live cd i used for my original install that i let auto partition my Vista for dual boot.Can i reinstall Hardy in same partition and overwrite all my troubles?Will the auto install know where to overwrite or will i have learn to manually partition? 'cause i screwed up my old XP desktop trying to manually . partition a dual boot with Gutsy and im really uhh uncomfortable,it took quite a few beers to get the nerve to let Hardy auto install on my new Vista machine.I must admit ive learned alot of linux by mistakes/ubuntu forums but i relly want to get off Vista again ASAP.Thanks for listening JESSE C

---

### Post by jualin on 2008-08-17
What command did you try to restore the Xserver? Maybe we can suggest a new one.

---

### Post by jesse c on 2008-08-17
JUALIN the holy helpful penguin,you are assisting me on my other xserver crash post but alas no luck so far thats why im thinking the reinstall route.The ubuntu community is amazing.Thanks JESSE C

---

### Post by jualin on 2008-08-18
I hate to admit it but sometimes that's the best option when you don't want to spend too much time troubleshooting a problem. However without reinstalling is how you learn more, Tough decision though: To reinstall or not to reinstall, that's the question:lol:

---

### Post by jesse c on 2008-08-18
JAULIN im willing to learn and check my other thread often.In this post i want to learn to reinstall.I have put in my live cd and gone to 'install' option and get to partition (auto)and it shows 2 ubuntu partitions the first is highlited in orange and no Windows partition.I kind of assume the highlited Ubuntu is setting up to overwrite my VISTA os.Panic-cancel-backspace hit manual partition options,get a list of /dev but dont have a clue as to what to do.By the way i have googled dual boot and watched and read many,many tutorials on the process but im still confused as to which partition im trying to change.Now i decide to restart the cd into live (not install) mode, go to gparted,and see a visual graph of my disk.Great!I assume dev-3 is ubuntu cause the first one on graph is labeled HP,and VISTA came loaded on my HP computer.I see there is a 'delete' key and i can highlight the dev-3 part of the graph,but i  panic and quit cause i dont know what to do next anyway if it does delete that part of the partition.Sorry for long post but i want to give reader an idea of what i am/am not familiar/comfortable with . JESSE C

---

### Post by Sef on 2008-08-18
Applications > Accessories > Terminal

Paste or type in this code:

```
sudo fdisk -l
``` Small L  That will show you your partitions.  Then copy and paste it here.

---

### Post by jesse c on 2008-08-18
sorry SEF but my ubuntu is so corrupted the pages are so huge they dont fit on my monitor and i cant access the buttons to even get to forums page let alone copy/paste.Im doing all this forum work from a borrowed  XP laptop.My VISTA works but since its dual boot i cant be on both os at same session.I can type the jist of it though
400 GB hard drive
                                        start                end
/dev/sdai    hpfs/ntfs                  1                  33610
/dev/sda2    hpfs/ntfs                  47825              48642
/dev/sda3    linux                      33611              47241
/dev/sda4    extended                   47242              47824
/dev/sda5    linux swap/solaris          47242              47824
 
then it adds"partition table entries are not in disk order"

---

### Post by jualin on 2008-08-18
> **jesse c said:**
> JAULIN im willing to learn and check my other thread often.In this post i want to learn to reinstall.I have put in my live cd and gone to 'install' option and get to partition (auto)and it shows 2 ubuntu partitions the first is highlited in orange and no Windows partition.I kind of assume the highlited Ubuntu is setting up to overwrite my VISTA os.Panic-cancel-backspace hit manual partition options,get a list of /dev but dont have a clue as to what to do.By the way i have googled dual boot and watched and read many,many tutorials on the process but im still confused as to which partition im trying to change.Now i decide to restart the cd into live (not install) mode, go to gparted,and see a visual graph of my disk.Great!I assume dev-3 is ubuntu cause the first one on graph is labeled HP,and VISTA came loaded on my HP computer.I see there is a 'delete' key and i can highlight the dev-3 part of the graph,but i  panic and quit cause i dont know what to do next anyway if it does delete that part of the partition.Sorry for long post but i want to give reader an idea of what i am/am not familiar/comfortable with . JESSE C

I have a tutorial in my signature that may be able to help you with the partitioning And [here there is another one with screenshots]("http://www.herman.linuxmaniac.net/p24.html"). Pretty much you should [LIST=1]
[*]Backup your data on the Vista partition first
[*]Defragment your Vista partition (using Windows defrag tool) (make sure you write down how much space Vista is using so you don't resize the partition too much)
[*]Restart your computer and Boot using the Live CD
[*]Continue to follow the instructions on the tutorial guides.
[/LIST]
Feel free to ask anything else. The Windows partition are usually the first partitions on the graph (most of the time) and you can recognize it because of their size and because of their Filesytem (NTFS). Good luck!

---

### Post by jesse c on 2008-08-18
JUALIN ive done the dual boot thing before,what i dont know is how to remove or put the new install in the same space as the old one.Right now im looking at my other computer(that im trying to fix)screen where i have put in the live cd and gone up to the partition part where i have selected manual option which brought up a page with my 4 /dev/sda "partitions".Now i know my /sda3 (ext3) is my ubuntu os and my /sda5 (swap) is the swap file.Now i can mouse over these lines and the lines highlite as do three options   
EDIT PARTITION--DELETE PARTITION--UNDO CHANGES TO PARTITION.  This where im lost.I presume im supposed to do something with the ext3 and the swap lines but what?and what do i do after that?or will the next screen be more understandable cause i stop on this page and cancel/quit install?AT this point im thinking of digging out a brand new hard drive that i bought on sale a year ago and never opened and installing it and putting the fresh ubuntu into that drive (but since i dont know how to do that either i wont torture you with that can of worms) thanks again JESSE C

---

### Post by jualin on 2008-08-18
> **jesse c said:**
> JUALIN ive done the dual boot thing before,what i dont know is how to remove or put the new install in the same space as the old one.Right now im looking at my other computer(that im trying to fix)screen where i have put in the live cd and gone up to the partition part where i have selected manual option which brought up a page with my 4 /dev/sda "partitions".Now i know my /sda3 (ext3) is my ubuntu os and my /sda5 (swap) is the swap file.Now i can mouse over these lines and the lines highlite as do three options   
EDIT PARTITION--DELETE PARTITION--UNDO CHANGES TO PARTITION.  This where im lost.I presume im supposed to do something with the ext3 and the swap lines but what?and what do i do after that?or will the next screen be more understandable cause i stop on this page and cancel/quit install?AT this point im thinking of digging out a brand new hard drive that i bought on sale a year ago and never opened and installing it and putting the fresh ubuntu into that drive (but since i dont know how to do that either i wont torture you with that can of worms) thanks again JESSE C

You need to edit the EXT3 partition and set the "mount Point" to "/" and then click on next (Apply changes) to format it.

---

### Post by jesse c on 2008-08-19
J and P22 thanks for encouragement/help (see other thread,im mixing up my posts)  JESSE C

---

