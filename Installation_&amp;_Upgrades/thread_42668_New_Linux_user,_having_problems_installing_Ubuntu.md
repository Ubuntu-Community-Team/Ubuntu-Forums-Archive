---
title: "New Linux user, having problems installing Ubuntu"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Subversive on 2005-06-18
Hi there, I'm new to Linux. I'm a long time computer user,  but I'm having some problems installing Ubuntu (which I read was a very 'beginner friendly' distro of Linux). I downloaded the ISO from the Ubuntu site (running windows xp still), the title of the file is ubuntu-5.04-install-i386. It downloaded it as a WinRAR archive type file, which I don't know if that's part of the problem or not. I created a linux ext2 partition & a swap partition on my hard drive using partition magic. I then attempted to burn the image to a CD, I assumed it would be bootable as is. Turns out it isn't. So, I tried using my Nero to make a bootable disc, using the same image, but using the built in functionalilty of Nero to make it bootable. This time it booted, it took me to a prompt which basically looked like a dos prompt except it said DR-DOS (or something like that, I forgot to write it down). I did a dir and saw the only executable file there. Can't remember the title of it, but when I run it, I get what looks like it "could" be an installation screen, except everything is in German. I managed to exit without reformatting my hard drive or something (lucky me), but I don't know what I'm doing quite clearly. Can someone give me some basic instructions to get this install going? Thanks.

---

### Post by mohaham on 2005-06-18
did u download the iso file..
if yes then probably u didnt burn  the iso image on the CD using "burn image" option..
[http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)

---

### Post by Subversive on 2005-06-18
No, I didn't do that. It should be bootable if I burn it as an image? I'll try it right now, thanks.

---

### Post by byen on 2005-06-18
Yes! ubuntu has one of the easiest install procedures....and i think there are a couple of places where you might have gone wrong......so see if the following procedure is what yu followed.
ok... here is the way it is supposed to be done:
step1: download the ISO from the ubuntu website
step2: burn the ISO into a disc. Now note that burining an ISO is not the same as burning a data cd. when you burn an iso it makes the cd in a bootable/install format. I do not know about nero..but i have used "deep burner" software. it is free and available at download.com (remember to burn it as an iso project ;-). trust me.. this software is good and easy.
step3: once it is burned...pop it in your cd-rom and re-boot. by default it should boot through the cd...if not press f2 during boot sequence and make it cd bootable in the list of options.
step4: Now the cd should boot into Ubuntu. you can format your partition here. Partition magic sometimes screws up this procedure... ubuntu patitions it well and tells you a suggested swap space too. remember though ext2 is good..ext3 partition is recomended!! Also if you want to have a common drive to share files between windoze and Ubuntu... you can also have a fat32 drive as a common storage point!!
step5:{in expert mode} if you have 2 operating systems...Select- Install Grub in MBR option during install..this way you will be able to select the OS you want during boot. remember to select the  Ubuntu partition and make it root "/" in the options.
step6:just follow through the procedure which ubuntu cake-walks you and enjoy nirvana.
step6:let us know if you need anything else.

[COLOR=Red]*** here is a link to screenshots of the installation procedure ..  from a while but if you make it .... it will be worth it!! visit this page be4 you install.
[http://mrbass.org/linux/ubuntu/install/](http://mrbass.org/linux/ubuntu/install/)[/COLOR]
and here is a thread which might help too [http://www.ubuntuforums.org/showthread.php?t=42622](http://www.ubuntuforums.org/showthread.php?t=42622)
hope this helps. If not let us know! and remember,....dont get frustated.once its all set-up you'll love it. It took me getting help from more than 20 people from over 20 countries to get this far in linux...(not that yu'll be as bad as me :wink:  )lol. Good luck!

---

### Post by Subversive on 2005-06-18
Okay, that worked. I got Nero to burn it as an image for me. The install went very smoothly, and the installer was able to use the space I had previously partitioned via partition magic. I think next time I will just free up some space using partition magic and not actually partition it, as opposed to what I did this time. It did work, however, so that is good. The grub boot loader works great too. It gives me all sorts of options, including Ubuntu, Red Hat (which I had previously installed, but didn't like too much), and then the Windows loader where I can choose between my Windows XP installation and Windows 2003 server. Everything's going so well! Anyway, now I just need to play around with this system, start using it as my main system and hopefully get more comfortable. Thanks for the help and the quick responses.

---

