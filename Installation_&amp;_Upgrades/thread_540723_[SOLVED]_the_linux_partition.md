---
title: "[SOLVED] the linux partition"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by shortybookit on 2007-09-01
I am not sure if i can post this here but i want to learn linux so i downloaded ubuntu
to install it i made 4 partitions
partition 1 is for windows XP NTSF Boot
partition 2 is for ubuntu EXT3
partiition 3 is a linux swap
partition 4 is for data and i used NTSF format which i think was my mistake should this be FAT32


when i am in my linux partition and go to my computer or whatever i see the folders and files from partition 1 the windows stuff and that is it

when i click my computer on the linux partition i want to see the linux and data partitions is this possible 
i mean why does my windows partition come up??

when i am in my windows partition when i click my computer it works i see all my windows files and then another drive or partition for the data files

i see nothing that has to do with linux which i like

---

### Post by Pumalite on 2007-09-01
You usually cannot see Ubuntu from Windows.

---

### Post by merlinus on 2007-09-01
Not to seem presumptuous, but... did you actually install ubuntu?  Or are you running from the live cd?

-merlin

---

### Post by shortybookit on 2007-09-01
to the first reply i know i like this and thats ho wi want my ubuntu to be

and to the 2nd guy yes i installed it i currently have a microsoft office cd in the cd rom:)

i am also typing this reply from the ubuntu firefox

---

### Post by merlinus on 2007-09-01
You can see your ubuntu files in Places/Home Folder and Places/Computer/File System.

-merlin

---

### Post by merlinus on 2007-09-01
If you want to be able to write to your NTFS partition from ubuntu, do this:

Open a terminal and enter:

```

sudo apt-get install ntfs-config

```then:

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

-merlin

---

### Post by shortybookit on 2007-09-01
my home folder shows examples and desktop
my places home brings up HDA1 which is my windows system files
i want to be able to see partition 4 from both linux and windows is this possible or should i reformat with only 3 partitions

windos,linux,and the swap?

---

### Post by merlinus on 2007-09-01
If you want to be able to see and write to your linux partition from windows, then install this driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

After you install ntfs-config (instructions in my previous post), then run these commands in a terminal and post the results:

```

sudo fdisk -l
mount
cat /etc/fstab

```-merlin

---

### Post by shortybookit on 2007-09-02
when i open the terminal this is there on default
eric@eric-desktop:~$
after i put the first part in and hit enter this is shown

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-confi


E drive works fine on the XP partition if it is not found by linux did i format it the wrong way?  I used NTSF for the E drive should i be using something else?

---

### Post by shortybookit on 2007-09-02
i want to see and be able to write to my E drive from linux 

now windows

---

### Post by merlinus on 2007-09-02
Looks like you mistyped the command.  Copy-and-paste from my earlier post.  Use Shift-Insert to paste into terminal window.

-merlin

---

### Post by shortybookit on 2007-09-03
the first comand works fine the second comand
sudo ntfs-config
it says couldnt find package ntfs-config

---

### Post by merlinus on 2007-09-03
Try restarting and then entering sudo ntfs-config

If the first command worked, then it installed the program.

You might also look in Applications/System Tools/NTFS Configuration Tool.

-merlin

---

