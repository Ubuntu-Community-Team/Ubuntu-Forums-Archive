---
title: "GRUB questions"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by Trexx on 2005-08-12
Hello,

 I have a few questions to ask, but first let me explain my situation.

I want to install Ubunto on a external USB harddrive. 
I want to do this considering I share my computer, and I want to try out Ubunto, and seeing how reinstalling Windows XP isn't a good option for other users using computer, I want to install it on my backup USB harddrive.

I know how to partition it and everything, but after I install it, it says it wants to install GRUB bootloader on my master drive (drive in my computer).


So, here's my questions:

1. Can installing GRUB on my internal WinXP drive damage my WinXP files? 

2. Are there any risks installing GRUB on my internal harddrive? 

3. How would I install GRUB on a floppy disk to boot it with that?

Thanks for your help!

---

### Post by PeP on 2005-08-12
[QUOTE=Trexx]Hello,

 I have a few questions to ask, but first let me explain my situation.

I want to install Ubunto on a external USB harddrive. 
I want to do this considering I share my computer, and I want to try out Ubunto, and seeing how reinstalling Windows XP isn't a good option for other users using computer, I want to install it on my backup USB harddrive.

I know how to partition it and everything, but after I install it, it says it wants to install GRUB bootloader on my master drive (drive in my computer).


So, here's my questions:

1. Can installing GRUB on my internal WinXP drive damage my WinXP files? [/QUOTE]
grub will replace the master boot record that windows put there to allow you to dual boot.
it won 't touch your files bot if the install fails, the computer won' t boot.

just try not to unplug the computer when grub installs itself and everything should be ok...

[QUOTE=Trexx]
2. Are there any risks installing GRUB on my internal harddrive? [/QUOTE]
barely, but you have no warranty as well ...

[QUOTE=Trexx]
3. How would I install GRUB on a floppy disk to boot it with that?

Thanks for your help![/QUOTE]
lots of good and detailed answer on this page (!)
[http://www.google.com/search?q=grub+floppy+ubuntu&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=grub+floppy+ubuntu&ie=UTF-8&oe=UTF-8)

---

### Post by Trexx on 2005-08-12
[QUOTE=PeP]grub will replace the master boot record that windows put there to allow you to dual boot.
it won 't touch your files bot if the install fails, the computer won' t boot.

just try not to unplug the computer when grub installs itself and everything should be ok...


barely, but you have no warranty as well ...


lots of good and detailed answer on this page (!)
[http://www.google.com/search?q=grub+floppy+ubuntu&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=grub+floppy+ubuntu&ie=UTF-8&oe=UTF-8)[/QUOTE]

Thanks for the information, but I have another question.

Is there a way to backup the original master boot record incase something goes wrong? Just wondering, thanks!

---

### Post by PeP on 2005-08-12
if someting goes wrong, the easiest thing to do is to install grub again.

I never got any problem with it and I never really cared since I just don't use windows, but I ve seen peoples who have some issues with grub on the forum

Once again, google can help you:
[http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=restore+windows+mbr+from+grub&btnG=Rechercher&lr=](http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=restore+windows+mbr+from+grub&btnG=Rechercher&lr=)

---

### Post by Trexx on 2005-08-12
[QUOTE=PeP]if someting goes wrong, the easiest thing to do is to install grub again.

I never got any problem with it and I never really cared since I just don't use windows, but I ve seen peoples who have some issues with grub on the forum

Once again, google can help you:
[http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=restore+windows+mbr+from+grub&btnG=Rechercher&lr=](http://www.google.com/linux?hl=en&ie=UTF-8&oe=UTF-8&q=restore+windows+mbr+from+grub&btnG=Rechercher&lr=)[/QUOTE]
 Thanks for your help!
Going to try to install it tomorrow, and
I now feel safer now that I know more about it.

P.S. Sorry I didn't think about Google. :(

---

