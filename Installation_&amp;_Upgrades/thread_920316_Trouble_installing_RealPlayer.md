---
title: "Trouble installing RealPlayer"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by jeremytas on 2008-09-15
Hi. I'm having trouble installing RealPlayer on Ubuntu 8.04.
I have downloaded the file "RealPlayer11GOLD.bin" and saved it to the desktop.

I have already viewed these two threads in detail:
[http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player]("http://www.ubuntux.org/how-to-install-the-realplayer-multimedia-player")
[http://ubuntuforums.org/archive/index.php/t-405359.html]("http://ubuntuforums.org/archive/index.php/t-405359.html")

As those threads point out, the file did not have the correct permissions, so I fixed these by doing:

[COLOR="Navy"] cd Desktop
 chmod 777 RealPlayer11GOLD.bin
[/COLOR]
*The file permissions are now "-rwxrwxrwx".*

My problem is however that when I type the following, I get an error saying "No such File or Directory". I have also tried it with "sudo" in front, but this made no difference. I am aware that it is case sensitive.

[COLOR="Navy"] ./RealPlayer11GOLD.bin[/COLOR]

So why would it say "No such File or Directory" when clearly the file is there? The chmod command had no problem finding the file. Please help!

---

### Post by Partyboi2 on 2008-09-15
Are you in the correct directory before you run that command? (./RealPlayer11GOLD.bin)
So
```
 cd ~/Desktop
```
```
chmod a+x RealPlayer11GOLD.bin
```
then
```
sudo ./RealPlayer11GOLD.bin
```

---

### Post by jeremytas on 2008-09-15
Yes. Definitely in the right directory (Desktop). If I do "ls -lasi", the file is listed.

---

### Post by Partyboi2 on 2008-09-15
The only other thing I can think of  is to check your spelling of the excute command, that it is typed correct into the terminal (incorrect typing of a command has caught me out once or twice) and maybe follow [[COLOR=Blue]this[/COLOR]]("http://crunchbang.org/wiki/realplayer-on-ubuntu/") guide and copy and paste all commands to install realplayer.

---

### Post by jeremytas on 2008-09-15
Spelling definitely OK and no typo's either. Actually as well as typing it in manually (heaps of times), I even tried copying/pasting the file name from the output of the [COLOR="Navy"]ls[/COLOR] command (also heaps of times) but it made no difference. And as I said previously, the [COLOR="Navy"]chmod[/COLOR] command has no trouble finding the file. I have also tried entering the file name with quotes and without the [COLOR="Navy"]./[/COLOR] prefix, but still no luck.

I can't believe what should be quite simple is turning out to be so hard. Maybe there is something wrong with the version 11 file? If the file was corrupt would it display this error or a different error? I think I might download version 10 and give that a go.

---

### Post by jeremytas on 2008-09-16
Still no luck unfortunately!

I re-downloaded version 11 and also downloaded version 10. Tried installing both of them, but I still get the error saying "No Such File or Directory". This time I saved them directly in the "/home" folder (rather than on the desktop) but that made no difference *(as if it would anyway)*.

Attached is an image of the terminal window. You can that I am doing everything correctly! File permissions are correct and there are no typo's in the file names. I think I might have to try installing a different Linux distribution on to another computer, then try to install RealPlayer on that. This will allow me to rule out Ubuntu 8.04 as the cause of this problem.

---

### Post by SunnyRabbiera on 2008-09-16
well you could try to install the .deb file, I always found the default realplayer installer a pain to use:
[try this]("http://debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.2_i386.deb")

That will install realplayer 10, but meh there isnt anything different between Realplayer 10 and 11

---

### Post by oldos2er on 2008-09-16
Try "sudo ./RealPlayer11GOLD.bin"

---

### Post by carolinason on 2008-11-07
I received the same error, probably a bug. Loading Debian on another machine to test.

---

### Post by Bablefish on 2008-11-07
Have I got an easy install for you. How about a native .deb file check out the link  [http://packages.medibuntu.org/intrepid/realplayer.html](http://packages.medibuntu.org/intrepid/realplayer.html)

---

### Post by carolinason on 2008-11-07
In Debian, Real Player 11 does install. 

This appears to be an Ubuntu problem.

I did install the deb file in Ubuntu that is provded by the previous posters and it works fine.

---

