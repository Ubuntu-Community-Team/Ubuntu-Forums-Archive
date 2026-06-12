---
title: "Need Grub (dell 2400 booting from External HD)"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by DanielCarey93 on 2010-10-25
Hello,
 
First time user of Ubuntu and first post on this forum. So i installed Ubuntu on an external hard drive, it took me a couple days. I followed the web sights direction and when i saw the option for windows or Ubuntu, clicked Ubuntu and that brought me to this:
 
 
[COLOR=darkgreen]GNU GRUB Version 1.98+2010...[/COLOR]
[COLOR=darkgreen] [/COLOR]
[COLOR=darkgreen]Minimal BASH-like line editing is suported. For the first word, TAB list possible command completion. Anywhere else TAB list possible device or file completions. [/COLOR]
[COLOR=darkgreen] [/COLOR]
[COLOR=darkgreen]GRUB>[/COLOR]
 
 
If anyone could Give me the grub for this Id greatly appreciat it. Also if you have anything i could read or educate myself with id also appreciat it but just the grub would be exelent either way.
 
No tricksters Im having a profetional check this stuff before i use any of it, if your wondering why they cant help me, they are buisy.
 
-Thanks For Your Time.

---

### Post by oldfred on 2010-10-25
Welcome to the forum.

Do you know the drive & partition you have installed to?

Can you manually boot:
 X is drive 0,1 etc
Y is partition 1, 2 etc
Grub uses hd0,1 for first drive, first partition but Ubuntu is sda1 or  drive 0 = a, partition 1 = 1
Adjust drive, partition to your install Example is sda5 or hd0,5:
sh:grub>ls
#If on (hd0,5) or sda5
sh:grub>ls (hd0,5)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd0,5)/vmlinuz root=/dev/sda5
sh:grub>initrd (hd0,5)/initrd.img
sh:grub>boot

Display the drives/partitions known to GRUB 2.

ls (hdX,Y)/    
Display the contents of the / folder of the designated drive/partition.

If you need detailed help:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

More info:
General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

