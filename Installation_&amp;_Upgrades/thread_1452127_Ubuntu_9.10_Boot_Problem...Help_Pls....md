---
title: "Ubuntu 9.10 Boot Problem...Help Pls..."
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Naruto_Luffy on 2010-04-11
Well to begin with i guess the problem is related to boot, and not something else.
But i am not too sure abt it( well i m pretty much new to ubuntu).
Here are all the details to the problem---
1)I have Ubuntu 9.10 an inside windows dual boot (other OS Windows 7)
2)Network acces is through proxy authentication
3)Dell XPS M1530 laptop, with 3gb ram and 256md NVIDIA graphic card
4)My Ubuntu installation is in another drive (D:/), than my Windows installation (C:/).
5)Lastly, My DVD Drive is not working. SO if any suggestion involves using
some CD/DVD to boot, will be hard for me to comply. Hence anyother way
like USB or .iso file in windows would be appreciated.

Installed many new packages today and updated most all softwares.Was playing a game
when suddenly laptop switched off. Afterwards when i tried to restart and selected 
'Ubuntu' option on the boot screen i got the following screen---

[IMG]http://i39.tinypic.com/2dklhrt.jpg[/IMG]

I don't know what to call this screen (i guess grub loader?).From here onwards i am
unable to go anywhere. The same screen is encountered everytime i try to boot in Ubuntu.

Well i hope someone can help me with the problem
or else
direct me so some forum or webpage where i can get the solution to it
or else
tell me what exactly is the problem, so that i can atleast google it(well i have
been googling all possible phrases with no success)

Thanks in advance

Naruto Luffy

---

### Post by janmyszkier on 2010-04-11
I would advise taking live cd and reinstalling grub from it, then letting us know what's up.

---

### Post by oldfred on 2010-04-11
If this is wubi installed inside windows, then this bug may have bitten you. Do not install grub to the MBR as wubi boots thru windows boot loader. This is the fix:

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Naruto_Luffy on 2010-04-12
@[janmyszkier]("http://ubuntuforums.org/member.php?u=786191") srry i forgot to mention that my DVD drive is not working. SO if something is 
possible through USB drive or else frm windows then that would be great.

@[oldfred]("http://ubuntuforums.org/member.php?u=852711") hey the webpage u mentioned, i read it and followed the instruction. I dwnloaded the new 'wubuildr' file (78.5KB) and pasted it over the previous version (78.2KB) in my C:/ drive. But there was also similar file(to the old version) in my Ubuntu drive (D:/ubuntu/winboot/), so i pasted the new version over there too and the rebooted. But no improvement. Still getiing the same "grub:sh>" prompt.

Well is there any other suggestion...:(:confused:

---

### Post by Naruto_Luffy on 2010-04-12
@[oldfred]("http://ubuntuforums.org/member.php?u=852711") Hey also is there supposed to be (D:\ubuntu\disks\root.disk) file
in the ubuntu drive.. Because in mine there is no such file, instead
(D:\ubuntu\disks\swap.disk).

---

### Post by oldfred on 2010-04-12
I do not have wubi so I do not know all the details. root.disk is the Ubuntu install, it is equivalent to the root (/) partition in a full install. I guess you installed the swap (which with full installs is a separate partition) in a different windows partition. Did you have 2 wubi installs, it only supports one. 

If that fix did not work I do not know what else for wubi installs.

edit:
Try this:
Type this at "grub sh>" prompt:

set path=/ubuntu/disks/root.disk
linux /vmlinuz root=/dev/sda1 loop=$path ro
initrd /initrd.img
boot

---

### Post by Naruto_Luffy on 2010-04-15
@[oldfred]("http://ubuntuforums.org/member.php?u=852711") sorry for the late reply, my endsems are on right now...
Anyways about the manual boot info u shared, thanks for it, but i guess its missing some parts. Because when i tried to enter it second line onwards it was showing invalid command. Maybe some more command lines are involved in between, so if possible can u repost the boot info or else send me the link to the original page...

---

### Post by oldfred on 2010-04-15
IF your wubi is not in sda1 then the manual boot will require changing to the correct sdaX where X is your partition.

To see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Naruto_Luffy on 2010-04-16
@[oldfred]("http://ubuntuforums.org/member.php?u=852711")  Firstly, thanks for the page link, though i am still to try it  myself...
Secondly, yesterday i checked on my frnds PC(he also has installed  Ubuntu 9.10 inside windows on OS WIndows 7), and there i saw one extra  file in the C:/ubuntu/disks/ location::: "root.disk" in additon to  "swap.disk"
this file is currently absent in my ubuntu folder and the size of the  file is nearly equal to the size of the hard drive space allocated by my  friend for ubuntu at the time of installation (10 GB in his case).
Upon checking further on my laptop i noticed thatthe 16gb space allocated for my own ubuntu installation had also freed up mysteriously.:confused:
Now adding 2+2 i guess my root.disk file got deleted during one of my ubuntu system software upgrades and on rebbot hence it being non-existent resulted in boot failure.

Also i had read somewhere that if the root.disk file is preserved then upon fresh installation, previous files and setting can be restored, but i guess in this case i will be a little unfortunate and will have to redo all my modifications on a new clean ubuntu installation  :((which i am actually planning to go forward with on this coming weekend)

But i guess its just one of the disadvantages of such a highly customizable and fun OS UBUNTU  :KS

Well still thanks for all your help till now [oldfred]("http://ubuntuforums.org/member.php?u=852711") and also to anyone else who took some time out to give my problem a thought.

I guess the problem stands solved now.

Regards 

Naruto_Luffy

---

