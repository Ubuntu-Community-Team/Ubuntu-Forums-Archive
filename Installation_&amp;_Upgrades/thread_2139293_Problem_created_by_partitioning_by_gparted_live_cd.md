---
title: "Problem created by partitioning by gparted live cd"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by Ioannis1 on 2013-04-26
Hi 
I am a relatively new ubuntu user , I have an Acer laptop and I recently upgraded to 12.04 Ubuntu from 10.04 . I decided to make a partition for installing Windows 7 and I used gparted live cd . It had no allocated space available so I had to move the only large 476 GB partition available.  I started moving it and then after reaching 75GB it gave me an input/output error . I think ignored it but then it stopped. I could not do anything further so I pushed the power button. I started again and then I got : [SIZE=2][SIZE=2]''[/SIZE]Your system is running in low-graphics mode[/SIZE]''  and ''Your screen, graphics cards, and input device settings could not be   detected correctly. You will need to configure these yourself.'' I tried to search for the error and I got Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
I run the cd for ubuntu 10.04 , reinstalled it and while doing it I had the choice to install it in a different partition ( approximately 15GB) that was not available before.. I did it and then this worked just fine. I found all of my previous files and can run them ,from the previous large partition ( which is now shortened by the way ) but it only lets me read the files and not store anything. I tried to boot the 12.04 kernel with recovery mode and i did everything such as failsafe mode , clear data , grub update , flxc , but nothing fixes the problem.. If I reboot from the recovery mode it just appears black and does not move on. If I boot from the start the normal mode it gives me always the low-graphics mode .
I would appreciate your help. 

Yiannis

---

### Post by fantab on 2013-04-26
Instead of reinstalling 10.04 you could've downloaded and installed 12.04. or Did you?
Suggestion: Download and Install 12.04.

More info needed about your 'previous large partition':
Is this /home or just an ordinary partition?
What file system does it have?
Is it automounted with boot or do you manually mount it?

Try changing the permissions to 'read/write' with:

```
sudo chown -R Ioannis:Ioannis /media/xyz
```

assuming your partition is mounted as */media/xyz* and your username is *Ioannis*.

I don't understand what you mean by "I tried to boot the 12.04 kernel with recovery mode"?

---

### Post by dino99 on 2013-04-26
here is a standard install:  [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by Ioannis1 on 2013-04-26
My ''previous large partition'' I think is actually my filesystem so it contains everything like home , but also bin, boot , cdrom , dev etc . And the whole thing is '' locked '' . The other functionable small partition has its own filesystem( and home ) and I know that I can install 12.04 and anything else, but the partition is small ( around 14GB) .  My problem is that I have the major partition of my system locked( 434 GB and I can not save anything new- I can only either open the files or delete them) . I think that this partition is automounted and here is a pic that might help you: file:///home/ioannis2/Desktop/pic3.png

---

### Post by Ioannis1 on 2013-04-26
1

---

### Post by Bashing-om on 2013-04-26
Ioannis1' Hi !

Fabtab's advise still applies. 
If you have not done so, make a mount point - as a suggestion only:
```

sudo fdisk -l ##to determine the partition that 10.04 occupies
sudo mkdir /mnt/10.04 ##your new mount point
sudo mount /dev/sdXY  /mnt/10.04 ##where X=the drive designation (a?) and Y=the partition(2 ?)
ls -la /mnt/10.04 ## to see the contents of the mounted partition
sudo chown Ioannis1:Ioannis1 /mnt/10.04/<some_directories> ##to change the ownerships if needed to you(Ioannis1)

```
Copy via the terminal any data to an external medium.

VerY IMPORTANT remember to (un-)mount that partition prior to logging off, failure to do so will result in file system corruption at some level !!!
```
sudo umount /mnt/10.04
```

When you have your data recovered, by all means wipe the partitions with GParted and install 12.04 as 10.04 is close to it's end of life ![INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Ioannis1 on 2013-04-28
Sorry for my late reply .
  Maybe the problem is just that I have unistalled the graphics card or the Grub , using gparted. I tried the ''chown'' command and then I got: cannot access /media/xyz , no such file of directory .. As for what I said about the ''kernel''( I amaware of my lack of experience)  when I turn on the machine I get a GRUB menu ( not sure if that is what it is ) that allows me to choose between several choices of ''versions'' of ubuntu either choose normal or recovery mode for each of them, like 2.6 or 3.2  ( I think just these 2 - but the 2.6 appears several times as a choice) . I have only tried 2 of them : the 2.6 at the top and and the  only 3.2 available- which actually gives me the low graphic mode . When I choose the 3.2 under recovery mode I get another menu with choices like : reboot normal , repair damaged files , failsafe mode , enable networking etc.
    I thought  that maybe I should focus on the '' low graphic mode '' problem and try to fix that ,because maybe the locked disk problem is just because I boot an operating system from a different partition.  PLus right now I have 420GB full and 2 external hdds that are almost full and Ican't really find another way to save my data somewhere else. So I was hoping that I could find a solution to reinstall graphics card etc. ( if this is the only problem)
So regarding the ''Server is already active for display 0'' I have tried so far some things:  like reistalling GRUB( as this is what they recommend at the gparted website , because they say that this is usual when you move partitions) . At another thread here someone that had the same problem solved it by '' lspci'' command  to check how many cards are installed or sth and then he installed nvidia -current . I tried this and started getting some files ( around 144 MB) it gave an error in the end about not having enough space in my disk.

---

### Post by Bashing-om on 2013-04-28
Ioannis1; Hi again !

Ok... there are several problems, all with solutions, If indeed you are out of disk space, this must be addressed first ! We have to get some operating room.
All right ? Then the GUI at this time is of secondary importance.
Now I have to do things in baby steps as I am not setting in front of your console and a terminal is required;
Try this:
At the grub menu press the "e" key for edit mode, arrow down to the line similar to this:
> linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff
Arrow across to the terms "quiet splash" delete them and all after, insert the term "text" -without the quotes - ;
key combo ctl+x to continue the boot process to a text log in;
Type in your user name followed by your pass word ( no response to the screen, security reasons)
You are currently set for your present working directory (pwd) as your home, and I want to know that you have a functioning terminal and a look at disk usage;
terminal code:
```
du -h --max-depth=1 | sort -hr
```
See:
```
man du
``` for documentation.

If the above is a success, I will provide commands to get us some operating room on that disk.[INDENT=2]
baby steps will still get us there

[/INDENT]

---

### Post by Ioannis1 on 2013-04-28
Thank you for your help . 

I tried the ''e'' key but then it only has: linux /boot/vmlinuz-**2**.**6** .0-24-generic root....,  and not the 3.2
Above it there are these lines (sth like this) : recordfail
insmod ext2
set root= ' (hd0,6) '
search --no-floppy --fs ..

---

### Post by darkod on 2013-04-28
I think the issue is the interrupted resize. Not sure if the partition will be readable because of that. It definitely wouldn't be locked just because you are accessing it from another installation or live mode. You should always be able to read it except some files which have permissions blocking you to read them.

Do you have a backup of the data? If you do, it would be much easier to simply make a new clean 12.04 install and put your data back.
If you don't, you can try bringing the old partition back with testdisk, but in the best case some of the data might be corrupted because you already started writing on the disk (you installed new 10.04 on a small partition but that space physically belonged to the big partition earlier).

In any case, it doesn't look good.

I'm also confused why you said you had to move the partition in your first post. I guess you needed to resize it, to make unallocated space for a ntfs partition. Just moving a partition doesn't help creating space for a new one. In any case, partitioning options are very risky on big partitions because they take long time, and anything can happen during this time which will stop the process and leave the disk in chaos.

If you want to try testdisk stop using the new installation as soon as possible. Don't write anything on the disk any more. Make a live cd of 12.04 and use it in live mode, not booting from the hdd.

---

### Post by BBeckley on 2013-04-28
> **Bashing-om said:**
> Ioannis1; Hi again !

Ok... there are several problems, all with solutions, If indeed you are out of disk space, this must be addressed first ! We have to get some operating room.
All right ? Then the GUI at this time is of secondary importance.
Now I have to do things in baby steps as I am not setting in front of your console and a terminal is required;
Try this:
At the grub menu press the "e" key for edit mode, arrow down to the line similar to this:

Arrow across to the terms "quiet splash" delete them and all after, insert the term "text" -without the quotes - ;
key combo ctl+x to continue the boot process to a text log in;
Type in your user name followed by your pass word ( no response to the screen, security reasons)
You are currently set for your present working directory (pwd) as your home, and I want to know that you have a functioning terminal and a look at disk usage;
terminal code:
```
du -h --max-depth=1 | sort -hr
```
See:
```
man du
``` for documentation.

If the above is a success, I will provide commands to get us some operating room on that disk.[INDENT=2]
baby steps will still get us there

[/INDENT]                              Im having the same issue. Ive followed your steps and the command "man du" worked for me. Now on my screen I have description of disk usage. What next?

---

### Post by Bashing-om on 2013-04-28
@          Ioannis1;
Your predicament is now dire,  darkod's advise rules. Salvage what you can and (re-)install.

@ BBeckley; Hi ! Welcome indeed to the forum .

In oder to attend to your matter with the attention it deserves, please start your own thread. Post the out put of the "du" command sequence (between code (#) tags) and we will address it then.[INDENT=2]
try'n to help

[/INDENT]

---

