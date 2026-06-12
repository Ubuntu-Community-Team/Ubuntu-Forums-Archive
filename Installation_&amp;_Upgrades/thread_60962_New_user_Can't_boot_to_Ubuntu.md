---
title: "New user: Can't boot to Ubuntu"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by Tux_army on 2005-08-29
Hello people the name is Dustin. I'm a new user to Ubuntu comming from SUSE. I've decided to give Ubuntu a shot mainly because i was getting sick of SUSE.

Anyways i installed Ubuntu 5.04 64bit (Hoary Hedgehog). During the installation everything went fine without any error message.

When it ask me to remove to the cd-rom so it can boot into my newly ubuntu system -so i did. Then Ubuntu starts loading again i get an error message saying

> Bootin 'Ubuntu, kernel 2.6.10-5-amd64-generic default'

root (hd0,0)
Filesystem type unknown, partition type Oxa5
kernel /boot/vmlinuz/ root=/dev/hda1 ro console=tty0 Quiet Splash

Error 17: Cannont mount selected partion

Press any key to continue....

So yeah i tried the press any key option and tried all the option it gave me and still to no vail.

Also is there a way so i can have Lilo as my boot loader instead of grub. I seem to always have problem when Grub is the bootloader. Ubuntu default bootloader seems to be Grub.

Thanks in advance.

---

### Post by John.Michael.Kane on 2005-08-29
Good luck getting software based help!!!! hardware help seems to be fine...

---

### Post by heimo on 2005-08-29
[QUOTE=Tux_army]
Also is there a way so i can have Lilo as my boot loader instead of grub. I seem to always have problem when Grub is the bootloader. Ubuntu default bootloader seems to be Grub.
[/QUOTE]

At the end of first stage of installation (before the first boot), installer gives option to "go back" or something like that. Go back - you'll get a menu with all the steps of installation process, and option to install LILO.

---

### Post by John.Michael.Kane on 2005-08-29
Thats good he got an answer to bad no one could give me one oh well!!!

---

### Post by heimo on 2005-08-29
[QUOTE=SD-Plissken]Good luck getting software based help!!!! hardware help seems to be fine...[/QUOTE]

 >      Thats good he got an answer to bad no one could give me one oh well!!! 

 > unless you need to run the os right now you may have to install something that works till you can get an answer.. answers seem slow on this part of the forum sorry i too have yet to get any answers to my question. so best bet install windows or some other os you like.. 

> 
I hope you dont expect an answer right away seems reponces are slow in this part of the forum... 

Posted today:
[http://ubuntuforums.org/showthread.php?t=60898]("http://ubuntuforums.org/showthread.php?t=60898")
> Post Removed Cause No Answers....... Everyone with hardware issues you will get help trying to get software based answer good luck.... Figure it out on your own then post how you fixed the software problem.... 

Posted today:
[http://ubuntuforums.org/showthread.php?t=60933]("http://ubuntuforums.org/showthread.php?t=60933")
> 
Removed no answers!!!!! 

Maybe if you gave us time to answer and used less time trolling around forums, experience would be more pleasant for all of us.

---

### Post by John.Michael.Kane on 2005-08-30
heimo sorry you having a bad time when and if anyone wants to know what my questions are im sure you will post just like you did here.. looking for help not a fight ...

---

### Post by heimo on 2005-08-30
[QUOTE=SD-Plissken]heimo sorry you having a bad time when and if anyone wants to know what my questions are im sure you will post just like you did here.. looking for help not a fight ...[/QUOTE]

What's the point of removing your posts if you don't get answers in couple hours? There's no point. That's not the way it works around here. Please try to make it _easier_ for all of us, not harder.

---

### Post by Tux_army on 2005-08-30
No i'm not in the hurry to get ubuntu working. 

For some reason it won't let me install lilo everytime i try to install lilo it says failed. It just says it failed, didn't say why just said it failed.

I tried to re-install lilo and Ubuntu about ten times alreayd but i keep getting the same message. When i try to to stick with Grub i get the error message on my first post and once i got a different error message saying "Error 15-file cannot be found"

I have my HD installed as a slave and i tried installing it on master just to see if it would work.

What do i do now?

---

### Post by Tux_army on 2005-08-30
Hey guys just comming in again to let you guys know that i got everything working now. As a matter of fact i'm on Ubuntu right now. 

While trying to install Ubuntu i got error message Error 17,15,25. Those were the three types of error message i got on my 12 attempt on installing Ubuntu.

On my 13 attempt i re-download Ubuntu from my step dad xp computer and burn it on  at 2x with determine maximum speed, stimulation, finalize and of course write check.

Now everything works.

---

### Post by heimo on 2005-08-30
This is a long shot... But I would try to change the access mode for that disk, it's a setting in BIOS - usually gets values LBA, normal, large, auto. I'd try different ones - LBA first. :-/ You could also try using boot floppy - to actually boot Ubuntu, and to experiment which boot loader configuration will work straight from hard disk (grub can be installed from grub-command line).

Some links:

[https://wiki.ubuntu.com/SmartBootManagerHowto]("https://wiki.ubuntu.com/SmartBootManagerHowto")
[https://wiki.ubuntu.com/HowToMakeAGRUBBootFloppy]("https://wiki.ubuntu.com/HowToMakeAGRUBBootFloppy")

[http://www.gnu.org/software/grub/]("http://www.gnu.org/software/grub/")
[http://www.gnu.org/software/grub/manual/html_node/]("http://www.gnu.org/software/grub/manual/html_node/")
[http://en.wikipedia.org/wiki/GRand_Unified_Bootloader]("http://en.wikipedia.org/wiki/GRand_Unified_Bootloader")

---

### Post by John.Michael.Kane on 2005-08-30
Help with installing the os no help with what you can remove from os what a joke

---

### Post by heimo on 2005-08-30
[QUOTE=Tux_army]
Now everything works.[/QUOTE]

:D I was writing my answer at same time. It's _great_ you got it working. Welcome to using Ubuntu and to Ubuntuforums, stick around ... and don't forget to check Breezy Badger (5.10), new release, coming in October.

---

### Post by John.Michael.Kane on 2005-08-31
great  still no answers to my questions  got to love this palce help with hardware problem  cool help with installing the os cool help with what you can remove from the os no help

---

