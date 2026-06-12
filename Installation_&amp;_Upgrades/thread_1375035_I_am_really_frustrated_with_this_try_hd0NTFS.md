---
title: "I am really frustrated with this try hd0:NTFS"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by salman4u on 2010-01-07
Hello,

Everything was working smooth and fine in Ubuntu until i went into Synaptic Package Manager and it give me few hundreds of updates for Ubuntu, and i clicked yes to install it (I curse myself for doing it). i am reading forums since hours but i am not getting anything i am total newbie to Ubuntu. Now whenever i boot into Ubuntu it takes me to silly command prompt grub> and gives some strange message of pressing tab will give you this and that etc and i am not getting anything in it. Please guide me how can i get my system back. I promise i will never update again in Ubuntu, not atleast till i pass my college. i made my java programs in Ubuntu and all of sudden it stopped working and gives me silly command prompt, i dont want to make my java programs again. Please tell me what can i possibly do to get back my system. i don't want any updates. Whatever was there was fine with me. Is there any way to revert back the changes? And ya i have installed using Wubi. Reinstalling Ubuntu will probably erase all my programs :(. Please help me in a way a newbie can understand. I will be really thankful to that person.

Further details :-

i have Windows Seven on my C:\ drive and i have Ubuntu (using Wubi) on my E:\ drive

---

### Post by Herman on 2010-01-07
Have you tried booting into recovery mode?
It's just one line down in your GRUB Menu.
If you don't see your GRUB Menu try tapping your 'Esc' key as Ubuntu is booting and try to get your GRUB menu to appear. I don't know if you see one in a wubi installation, I only know about dual booting, but I hope you can get your GRUB menu that way.

Once you get your GRUB Menu up, just scroll one line down and boot into recovery mode and you'll see some options in there that might help you.

---

### Post by salman4u on 2010-01-07
Hello,
Thanks for you reply but i am not getting any menu even after pressing Escape. the only thing i get when i select Ubuntu is try(hd0:NTFS) and then in 2 seconds a command prompt appears and i dont know???what does it expect me to type. This kind of command prompt :-

sh:grub>

and when i pressed tab it gave me few command list but yes when i typed boot it showed error message like no kernel loaded. Does this message help anybody to solve my problem? what should i do? i am very much confused.

Before my upgrades,it showed me menu from which i selected the 1st option of linux 14 generic but now no menu appears and it directly throws me to command prompt

---

### Post by Herman on 2010-01-07
My Recovery mode menu looks like this:
```
* Start init crypto disks ...
clean     Try to make free space
dpkg     Repair Broken Packages
grub     Update grub bootloader
netroot Drop to root shell prompt with networking
root     Drop to a shell prompt
```I think if I were you I would try the 'dpkg Repair broken packages'.

'Broken Packages' are software packages that have parts missing.
These can be parts of programs, and the program can't run because part of it didn't get downloaded maybe when you did your update for some reason or another.
A lot of times they don't matter much and you'll just get the missing pieces next time you get another update. In your case you seem to be missing something important and it's causing you not to be able to boot completely, (if I'm guessing right).
There's a very good chance "dpkg Repair Broken Packages" in Rescue mode can get the missing packges from the internet and install them for you.
Make sure your computer has a good internet connection while you're doing it.

Be patient, you may need to wait some time for the update to complete, that will depend partly on the speed of your internet, and also on the speed of your computer when the changes are being written to disk.

When it's finished it will say 'finished, press enter', and when you do press enter you'll be returned to the recovery menu.
From there you might try 'Resume Normal Boot', and see if the problem has been fixed, and hopefully it has and you'll boot back into your Ubuntu as normal again.

If you end up at a shell prompt instead of your GUI login screen, just type in your username and password and type: sudo reboot -i
Then you can reboot and then you should be able to log in as normal. (if all went well). :)

---

### Post by Herman on 2010-01-07
> Hello,
Thanks for you reply but i am not getting any menu even after pressing Escape. the only thing i get when i select Ubuntu is try(hd0:NTFS) and then in 2 seconds a command prompt appears and i dont know???what does it expect me to type. This kind of command prompt :-

sh:grub>

and when i pressed tab it gave me few command list but yes when i typed boot it showed error message like no kernel loaded. Does this message help anybody to solve my problem? what should i do? i am very much confused.

Before my upgrades,it showed me menu from which i selected the 1st option of linux 14 generic but now no menu appears and it directly throws me to command prompt
Oh, okay, then you should try some of the tricks in this page here to see if you can find a kernel and get it to boot, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System

---

### Post by salman4u on 2010-01-07
Thanks but i really don't understand what all is going on on that url. what does hda0 and sda refer to and which number should i enter? i have Windows 7 on C:\ and Ubuntu on E:\ and dvd drive on D:\ it's 1:30 in morning here and i am feeling so much guilt for updating ubuntu i will never ever update without thinking 1000 times next time

---

### Post by salman4u on 2010-01-07
ok! after breaking my head in that url for quiet some time i typed few command and got few results.

search -f /vmlinuz
loop0

search -f /sbin/init
loop0

then i typed :-

linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda3
initrd (loop0)/boot/initrd.img-2.6.31-14-generic
boot

After this i got results as :

Begin: Running /Scripts/init-bottom...
Begin: Starting AppArmor profiles
mount: mounting /sys on /root/sys
failed: no such file or directory

mouting /dev on /root/dev
failed :no such file or directory

target filesystem doesn't have /sbin/init. No init found. try passing init=bootarg

Then one shell came named busybox


I know i am troubling too much but i am newbie so please bear with me and it's important as i have my college assignment in there :( otherwise i wouldn't have troubled you i would have simply reinstalled ubuntu

---

### Post by Sef on 2010-01-07
> I know i am troubling too much but i am newbie so please bear with me and it's important as i have my college assignment in there :sad: otherwise i wouldn't have troubled you i would have simply reinstalled ubuntu

If you have a Live CD, you can use it to retrieve your assignment.  Just save it to a usb drive, a cd-rom, or other storage device.

---

### Post by greg563 on 2010-01-07
Hello, looks like you and I have the same problem. I think the live CD approach is your best bet if you just want to grab your files and be done with it.

However, there is a way to boot manually from the Grub2 prompt for us Wubi users. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1339203&highlight=wubi#5](http://ubuntuforums.org/showthread.php?t=1339203&highlight=wubi#5)

I followed the steps in reply #5 and was able to boot Ubuntu.

---

### Post by salman4u on 2010-01-07
No,
good news is that i am into ubuntu again :d i am so happy it's almost 3 now in morning but i am so happy that i am not feeling sleepy all i needed to type at sh:grub> was

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic 
boot


But the problem is that everytime now i boot i have to type this. Can anybody tell me where to put these two lines so that i don't need to type it again and again. In grub.cfg i saw menuentry but those menuentries are never displayed (they used to be displayed before i installed updates). This should be easy for you folks now :). Just need to know where to put those two lines so it takes by default?

Thanks in advance!!

---

### Post by kansasnoob on 2010-01-07
Since this is Wubi and I'm an idiot regarding such please see if this is helpful:

[http://ubuntuforums.org/showthread.php?t=1374248&page=3](http://ubuntuforums.org/showthread.php?t=1374248&page=3)

There is an old bug report:

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)

---

### Post by salman4u on 2010-01-07
> **kansasnoob said:**
> Since this is Wubi and I'm an idiot regarding such please see if this is helpful:

[http://ubuntuforums.org/showthread.php?t=1374248&page=3](http://ubuntuforums.org/showthread.php?t=1374248&page=3)

There is an old bug report:

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)


Hip Hip hurrey! now it's working smooth as before.

[http://ubuntuforums.org/showthread.php?t=1374248&page=3](http://ubuntuforums.org/showthread.php?t=1374248&page=3)

mentions to overwrite wubuildr file to c:\ and i did exactly the same and it did the job for me. Atlast after wasting so much time i can finally concentrate on Java!
Thanks to all who replied. I am really thankful without your help i would have simply reinstalled Ubuntu :d

---

### Post by presence1960 on 2010-01-08
Get rid of wubi for 2 reasons: 

1. There are a lot of problems with it especially in 9.10 & it is hard getting help for wubi because most do not use it.  

2. [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/) 

That link is an interview with a creator of wubi. Read the second question asked of him and note his response- wubi is not meant to be a permanent installation but rather a way for those who are unsure if they like Ubuntu to TRY it without committing to partitioning their hard disk(s)

I suggest you uninstall wubi and do a proper full installation of ubuntu to your hard disk.

---

