---
title: "How to make a Kubuntu/Win98/WinXP multi boot work?"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by KuifjePDX on 2006-05-17
On a clean hard drive I created four partitions. In order: FAT32 (Win98), NTFS (WinXP), swap (Linux), ext3 (Linux). I then proceeded to install WinXP, Win98, and Kubuntu. I used PQBoot to select between the OS's during startup and for both Win98 and WinXP this worked just fine. Adding Linux to the PQBoot menu locks up the system when Linux is selected to boot to. WinXP and Win98 still work fine.

So I reinstalled Kubuntu from a Live/Install CD. It installed GRUB as part of the process and it gives me the option to boot into Linux, WinXP, and Win98.
- When I choose Linux it works just fine.
- When I select WinXP I see the boot screen for XP and at some point get a light blue screen saying it can't find AUTOCHECK after which it hangs on a Blue Screen Of Death (BSOD) with a Fatal Error.
- When I select Win98 I get a black screen with the A> prompt asking me to enter the command processor (C:\WINDOWS\COMMAND.COM), but nothing I enter can make it boot.

So, at this point I can either a) use PQBoot and get to both Microsoft OS's, or b) use GRUB and get to Kubuntu Linux.

Does anyone have any ideas on how to consolidate these two scenario's into one and use either PQBoot or GRUB to boot to one of three OS's. I'd would prefer the GRUB route as I will use Linux most of the time on this machine and  Win98 and WinXP only rarely.

I am a Linux newbie so a detailed (step-by-step) solution would be most welcome.

Doei!

---

### Post by deadgobby on 2006-05-17
For a good video on line
[http://video.google.com/videoplay?do...11311898236&q=](http://video.google.com/videoplay?do...11311898236&q=)

---

### Post by KuifjePDX on 2006-05-17
[QUOTE=deadgobby]For a good video on line
[http://video.google.com/videoplay?do...11311898236&q=](http://video.google.com/videoplay?do...11311898236&q=)[/QUOTE]


The link you posted was truncated but I searched for 'Ubuntu' and 'Windows' in the Google Video Search Bar and found the one you're (probably) refering to.

I watched the video and it pretty much details what I have done, but the video does not go into detail on how to edit the GRUB configuration. It's pretty much "This is how it is supposed to go, and if there are no errors it will work.', so it is not of much use to me as I am past the point where this video ends.

Doei!

---

### Post by Sef on 2006-05-19
Check this out:

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Herman on 2006-05-19
Hello KuifjePDX, 
Mr. Doei!, I have some information on the link that sef provided for you, but I do not know about booting more than one Windows, or anything about Partition Magic or PQBoot, so I am not sure whether or not your present installation can be repaired if PQBoot has altered your Windows systems in some way.
If your Windows Operating systems are intact, all you should need to do is forget about PQBoot, and focus on getting GRUB to temporarily 'hide' whichever Windows partion you do not want to boot at any instance.

My GRUB Page does not include that information, but here are some links that should help you. 
This link is about how to do a multi-boot install with a Linux and more than one Windows Operating system.
[Multiboot with **GRUB** Mini-HOWTO]("http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html")
Particulary notice the way the author has applied the 'hide' and 'unhide' commands in his /boot/grub/menu.lst in that how-to.

This link the GRUB Manual reference to the 'hide' command.
[**hide** - **GRUB** Manual]("http://www.gnu.org/software/grub/manual/html_node/hide.html")

This link gives another example of the 'hide' command in use. (How to apply it).
[Advanced **GRUB** commands]("http://www.bo.infn.it/alice/alice-doc/mll-doc/linux/advanced/node50.html")

Here is a link to a GRUB Command-Line How-to which is (I think) better than mine.
**[[B]Grub Grotto**]("http://www.troubleshooters.com/linux/grub/index.htm")
[/B]If you click on the top title on that page and click on this heading [B][B][Having Grub Do Your Research For You]("http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You")
[/B][/B]you should be able to combine that information with the information on my page (the one sef linked you to), and have Grub booting Windows from the command line.
Once you find out the right commands by trying them out on with the comamnd line of GRUB, then you can edit your /boot/grub/menu.lst with the same commands and you'll be all set! :D

If Partition Magic and PQBoot have not damaged your Windows installations then GRUB should be able to boot Windows this way.
I realize this is a lot of reading, but you won't have to read it all, just the bits that apply to you. Those are some pretty good links to save for future reference. 
Regards, Herman :D

---

### Post by Basu on 2006-05-20
Hmm... I've never really seen this sort of a problem happen. There is a certain possibility that the Windows installs themselves have been corrupted somehow, but I'm not enough of an expert to say for sure. I would recommend that you follow Herman's advice and read through the GRUB manual. If it's just a problem with GRUB, it shouldn't be too hard to fix it.
Good Luck.
BTW has anyone tried to boot Minix3 along with Ubuntu using GRUB?

---

### Post by bigken on 2006-05-20
personally i would have used qtparted to make the fat32 partion for win98 install it then use winxp to create its own partion and install  then install ubuntu using whats left on the hdd ;) 

both win98 and xp are repairable google the win98 you will find the answer easily and do repair install on xp then run ubuntu install when u get to partion bit click cancel and select install grub this might sort it (i think pqboot is the problem get rid of it)

---

### Post by KuifjePDX on 2006-05-23
[QUOTE=Herman]Hello KuifjePDX, 
Mr. Doei!, I have some information on the link that sef provided for you, but I do not know about booting more than one Windows, or anything about Partition Magic or PQBoot, so I am not sure whether or not your present installation can be repaired if PQBoot has altered your Windows systems in some way.
If your Windows Operating systems are intact, all you should need to do is forget about PQBoot, and focus on getting GRUB to temporarily 'hide' whichever Windows partion you do not want to boot at any instance.

My GRUB Page does not include that information, but here are some links that should help you. 
This link is about how to do a multi-boot install with a Linux and more than one Windows Operating system.
[Multiboot with **GRUB** Mini-HOWTO]("http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html")
Particulary notice the way the author has applied the 'hide' and 'unhide' commands in his /boot/grub/menu.lst in that how-to.

This link the GRUB Manual reference to the 'hide' command.
[**hide** - **GRUB** Manual]("http://www.gnu.org/software/grub/manual/html_node/hide.html")

This link gives another example of the 'hide' command in use. (How to apply it).
[Advanced **GRUB** commands]("http://www.bo.infn.it/alice/alice-doc/mll-doc/linux/advanced/node50.html")

Here is a link to a GRUB Command-Line How-to which is (I think) better than mine.
**[[B]Grub Grotto**]("http://www.troubleshooters.com/linux/grub/index.htm")
[/B]If you click on the top title on that page and click on this heading [B][B][Having Grub Do Your Research For You]("http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You")
[/B][/B]you should be able to combine that information with the information on my page (the one sef linked you to), and have Grub booting Windows from the command line.
Once you find out the right commands by trying them out on with the comamnd line of GRUB, then you can edit your /boot/grub/menu.lst with the same commands and you'll be all set! :D

If Partition Magic and PQBoot have not damaged your Windows installations then GRUB should be able to boot Windows this way.
I realize this is a lot of reading, but you won't have to read it all, just the bits that apply to you. Those are some pretty good links to save for future reference. 
Regards, Herman :D[/QUOTE]


Thank you for the pointers. I have been trying to modify the menu.lst file in the grub directory but when I tried to save the modified file I got some kind of error stating more or less that access was denied and the file could not be saved. I only configured one user during installation so I must assume this user is the administrator. I use that user's password to install updates and add programs. I haven't figured out yet how to change the authorization level so I can edit the grub/menu.lst

Doei!

---

### Post by Herman on 2006-05-23
I am not sure if this will be your problem or not, but many people when they are very new to Ubuntu, try to open files the same way as they are used to in Windows. That is by navigating to the file and simply opening it. I remember I tried that at first too. We all probably did. Maybe that's what you are doing wrong?
In Ubuntu, when you want to make important system changes you almost always need to open the file using your 'terminal', and usually the command to open your file will need to have the word 'sudo' placed before the command. That will make the terminal ask you for your password before it carries out your command of opening the file. When you enter your password that tells Ubuntu that you are the boss and you mean business! 
Here is a command to make a back-up copy of your /grub/menu.lst file in case you haven't done so already:
```
  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` Here is the right command for opening your /boot/grub/menu.lst so that it can be edited and have the changes saved:
```
sudo gedit /boot/grub/menu.lst
```You do not need to type these commands yourself unless you want to, just copy them right off this post and paste them in your terminal with your right-click on your mouse. That will make it easier for you.

This 'sudo' idea is important for security and it is one of the reasons we don't suffer from viruses and malware, or other threats like that. You will soon get used to it, it's far better then the alternative. When the file has been opened with 'sudo' you become authorised to do many things and save the changes, so always be a little more careful about what you are doing, that's all. 
My grub page has that information, but I admit it is getting to be rather a lot of reading for people to take it when they are just beginning. I hope this is what you needed to know, Regards, Herman.

---

### Post by KuifjePDX on 2006-05-30
With all the good help I was able to make it work.

First I used PartitionMagic 8.0 (boot from CD) to create four partitions on my hard drive (Linux swap, Win98, WinXP, Linux ext3) and installed Win98, then WinXP and finally Edubuntu LTS 6.06 RC (using the live CD and the included install routine).

I had to install Win98 a number of times as it had some issues with finding the install CD when it tried to install drivers for added hardware. In the process it removed the GRUB boot menu so I had to reinstall Linux to make GRUB work again. Maybe there was no real need for that but being a novice I didn't know of any other way.

In the end I found the best method to install Win98, so it could find the files needed, was to boot from CD, exit the install routine. Then from the DOS prompt make a bootable hard drive and copy the entire install CD to a dedicated subdirectory on the hard drive and run the setup program from there instead of CD. This way Win98 keeps track of the install paths and can find the files needed on its own.

But the biggest thing to keep an eye on when installing multiple installs of Windows is making sure that GRUB **_hides_** and **_unhides_** the partitions.

My setup looks like:

# Windows 98
unhide             (hd0,1) # Windows 98 partition
hide                (hd0,2) # Windows XP partition
rootnoverify     (hd0,1) # Windows 98 partition
makeactive
chainloader      +1

# Windows XP
unhide             (hd0,2) # Windows XP partition
hide                (hd0,1) # Windows 98 partition
rootnoverify     (hd0,2) # Windows XP partition
makeactive
chainloader      +1

So far, so good. Now if only I could make my Airlink101 wireless PCI card work without making Edubuntu hang during boot......

Doei!

---

