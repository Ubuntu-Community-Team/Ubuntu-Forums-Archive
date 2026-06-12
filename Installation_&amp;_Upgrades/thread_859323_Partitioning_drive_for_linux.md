---
title: "Partitioning drive for linux"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by lhatch951 on 2008-07-14
I'm new to Linux and here is my situation.

I installed Ubuntu, but it erased all the files on my hard disk including windows XP. I need XP to do the things i can't do with Linux.

I want to partition my drive in windows BEFORE I try to install Ubuntu again. 

I would prefer not to run another all night recovery process =(

PLEASE HELP!!!!!!!!!!!!

---

### Post by lhatch951 on 2008-07-14
Srry. I wasnt clear. HOW do I partition my drive??

---

### Post by Pettman on 2008-07-14
There are many ways. The easiest for you, since you probably already got a desktop install cd, would be to boot into a live cd session and use the partition editor found under system->administration->partition editor (a quicker way to start it would be to press alt+f2 and type 'gparted' and press enter). Once you have started the partition editor the following procedure should get you where you want.
[SIZE="5"]**_Make a backup of all important files you have got on your computer before proceeding._**[/SIZE]
[LIST=1]
[*]Depending on if you already have a windows partition or not, initial steps will vary a bit.
[list]
[*]**If you do:** Use the move resize button to shrink the partition to desired size (this will be space available to windows, the empty space after it will be used for your Ubuntu installation).
[*]**If you do not:** Make a ntfs partition of desired size at the start of the disk and then proceed as instructed below.
[/list]
[*]Split the space intended for your Ubuntu-install into 3 partitions. [list]
[*]One with a size around 5-10 GB for the system-files (usally refered to as root file-system or simply '/' )
[*]One for your own files and settings (usually called /home-partition, since it it mounted at /home)
[*]One swap partition if you feel you need it (either if you got less than 1 to 2 GB of RAM or you want to suspend your computer to disk). About the double size of your RAM was the rule of thumb back when ram was pretty expensive, now you can go with less.
[/list]
[*]Apply the changes if you haven't been forced to do so during earlier steps
[/LIST]

When you encounter problems in the future I'd recommend you try searching (with google and these forums built-in search feature) before making a new post, many problems new users encounter have been encountered and solved many times before. Searching first have several advantages:
[list][*]If you manage to find the answer on your own, you don't have to wait for someone to bother to write an answer to our question.
[*]People with knowledge of Ubuntu and general GNU/Linux operating systems don't have to waste their time answering the same question over and over again -> they can tackle new questions.
[*]You don't have to write a well-worded explanation of your problem.
[/list]
Things that usually can yield good results when trying to search for the answer are: the name of the piece of software (ex. ubuntu), some word about what you are trying to do (for instance partition) and if you got problem with a program, any error-message it outputs (running it in a terminal can be handy to get your hands on these).

Also, when you realise you've missed something in a post please use the [IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]-button unless the thing you think are missing is pretty substantial and don't fit with the earlier post (don't happen so often)

---

### Post by lhatch951 on 2008-07-15
Thanks a ton for this info. I still have more questions.

1.) What is a live cd session? and Where is the partition editor?
2.) Is there a way to partition the drive before i try to install Ubuntu?
3.) Why is it necessary to split the Ubuntu side into 3 partitions? and 
    Will it be split into 3 LOGICAL partitions?

thanks

P.S. what does this mean?

Windows belongs in /dev/null and not on /dev/hd*|/dev/sd* !

P.P.S. (lol)

Do you have to rename drives? I read somewhere and found out through some tinkering that Linux does not name the drives the same way as windows. I am not very familiar with this.

Once again help is appreciated.

---

### Post by Pettman on 2008-07-17
> **lhatch951 said:**
> Thanks a ton for this info. I still have more questions.

1.) What is a live cd session? and Where is the partition editor?
[QUOTE=lhatch951;5391457]A live-cd session is what you get when you put the ubuntu-cd called desktop into your cd-drive and boot. It will then run ubuntu from the cd instead of from the harddrive (the harddrive will be left untouched unless you decide to do something with it, such as partitioning or installing).
The partition editor should be found under System->administration->Partition editor, if not install the package gparted via synaptic or input **sudo apt-get install gparted** into a terminal (found under programs->accessories->terminal).

2.) Is there a way to partition the drive before i try to install Ubuntu?
> **lhatch951 said:**
> Yes, by using a live-cd with ubuntu (see above).

3.) Why is it necessary to split the Ubuntu side into 3 partitions? and 
    Will it be split into 3 LOGICAL partitions?

thanks[/QUOTE]It's not, but I would recommend it. Or at least making 2 partitions, One for / and one for /home and a swap if necessary. Keeping the content of your '/home' directory on another partition than your system ('/') will make it easier if you have to reinstall ubuntu (or some other linux) in the future.

> **lhatch951 said:**
> 
P.S. what does this mean?

Windows belongs in /dev/null and not on /dev/hd*|/dev/sd* !

P.P.S. (lol)It's a joke saying that you shouldn't keep windows on your harddrive but on the NULL device (i.e. don't have it on your computer at all).

> **lhatch951 said:**
> 
Do you have to rename drives? I read somewhere and found out through some tinkering that Linux does not name the drives the same way as windows. I am not very familiar with this.

Once again help is appreciated.Instead of having multiple directory trees (one for each drive, C:, d: ect.) GNU/Linux keeps all drives in the same directory tree mounting additional drives in directories in the tree. The drive you've got your operating-system on is called root-filesystem and is mounted at /, then you can add the rest anywhere you like in the tree as long as there is nothing in the directory you want to mount in. Automounted drives usually get mounted in the /media directory. You don't have to worry so much about mounting stuff during installation since the install program will be pretty helpful with that kind of stuff.

---

### Post by lhatch951 on 2008-07-23
How do I get the live CD? Is that the same as the CD Image? Because I know that after I booted from that, it went directly to installation.

Thanks

---

