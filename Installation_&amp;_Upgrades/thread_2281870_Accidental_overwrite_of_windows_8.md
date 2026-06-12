---
title: "Accidental overwrite of windows 8"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by nat7 on 2015-06-10
Hi everyone , first I'm new on the forum ! Altough I tried ubuntu and mint in the past I never thought about installing it until yesterday on my computer . 
The problem was , Windows 8 was pre-installed , and you probably at least heard of that , they don't make dual boot easy at all . 
Anyway , I managed to create the partition and to force the computer to boot on my usb , I did it 3 times (the first because I couldn't remember what was the number of the partition I created and the second because I forgot to create a partition for the VRAM) and the third time , when ubuntu ask me what to do to install , I was tired and instead of selectionning "something else" , I chose "erase everything" or something like that by accident .
 Then I panicked and I turned off my PC , leading to the oblivion of windows 8 ... Well that's not a big lose , but I had lots of precious things for me on my :C drive and I was wondering if I could save at least a part . I am currently , and desesperatly , downloading a Live USB version of BootMed , I'm going to put it on my computer and try to save some data with TestDisk . Is there any Hope ? I mean I'm kind of a noob , when I checked "erase everything" , did it actually erase everything or did it just gave the possibility to ubuntu to overwrite the hard drive ? Thanks for your help , I feel so dumb after that ...

EDIT : If anyone have a suggestion about how to make a bootable USB with bootmed that would be nice , I use Unetbootin to do it with ubuntu but they don't propose to do it with bootmed and I don't want to mess up anymore by choosing a wrong distribution .

---

### Post by westie457 on 2015-06-10
Hello nat7.

Instead of using bootmed why not use the installation usb you already have. Boot it into 'Try' mode, open software&updates to check the universe repository is enabled, close the window agreeing to the pop up. Open a terminal and run ```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by nat7 on 2015-06-10
Hi thanks for your answer ! I should have said that I actually tried to use again my installation but for reasons beyond my comprehension it just freeze now on the ubuntu loading screen (I must have really ****** up by shutting down my computer in a critical moment ) . That's why I wanted to give a try to a distribution made for recovery .

EDIT : ok so I couldn't find a way to make a bootable usb with bootmed so I'm back to ubuntu wich I have to download again since I erased the one on my usb *sigh* ...

---

### Post by oldfred on 2015-06-10
Data was not erased, but overwritten by Ubuntu. But with ext4 entire partition is used randomally where Windows has all data at beginning of drive. Ubuntu is also a lot smaller than Windows.
So you may be able to recover some, but not all or a working system.

Some vendors will ship you a replacement recovery drive image. That is not a full Windows installer, but the image of the drive as installed, that you should have made when you first started up system. They may charge a shipping charge, a few are free, and some just do not offer anything and then you have to buy a new copy of Windows if you really want it.

If testdisk's deeper search shows files that is best case as the part of drive where files names are was not overwritten. But if not testdisk also includes photorec. It scans entire drive and looks for anything that looks like each file type. You do not get file names, just extensions and have to manually rename files. Photos have internal data that you can use to rename them with, most other files do not. I now include file name in every text file I save as I had to use photorec once and it took weeks to sort, compare and update each file. It recovered all the changed versions each time I saved it, so there were many copies of the same file.

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Some here that are also Windows users suggest that Windows tools may work somewhat better.
      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by nat7 on 2015-06-14
Hi , thanks for the help of everyone . I did not try Recuva since it was not an easy task for me to have rapidly acces to window , but I tried to use photorec and Oldfred , I totally understand what you mean when you say it took weeks for you to sort everything , I was only interested in getting some particular files , but they were lost in the sea of windows 8 files , and I  quitted in front of the huge task . Photorec is still really nice , I recommend it !

---

