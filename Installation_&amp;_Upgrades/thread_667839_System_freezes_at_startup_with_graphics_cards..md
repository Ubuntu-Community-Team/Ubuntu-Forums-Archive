---
title: "System freezes at startup with graphics cards."
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by rolobio on 2008-01-14
Hello! Take this as a pre-thank you for reading this.

I've tried two different nVidia graphics card and my system freezes at startup on the third line of "the worm" on the Ubuntu startup screen. The two cards are: nVidia GeForce FX5200 PCI, and nVidia GeForce 6200 OC PCI. I recently bought the 6200 thinking maybe my 5200 was broken. Does anyone know of any tutorials on how to set up these cards? I've looked and lots of tutorials and websites but can't seem to find an answer to this problem.

Heres what I've been trying to do:
Install and enable the restricted driver for nVidia graphics cards with the Restricted Drivers manager. But a popup comes up telling me: "Your hardware does not need any restricted drivers." but if I put my card in the system freezes... if I can't enable the driver without the card in how can I install and enable the driver??

I've tried everything I can think of in root and my own username (doubt that does much, but I'm willing to try anything).

I've seen a few people with a problem similar to mine.

---

### Post by Pumalite on 2008-01-14
If you want special effects, you have to start from 6600 GS up.

---

### Post by rolobio on 2008-01-14
ok... how does that help me with my system freezing?

---

### Post by Pumalite on 2008-01-14
Try the Alternate CD. (to avoid graphics problems)

---

### Post by rolobio on 2008-01-14
Alternate CD? what do you mean? can you give me a link?

---

### Post by PmDematagoda on 2008-01-14
Actually the Nvidia 6200 runs graphic effects perfectly. And it also runs very well with Linux in general(Including Live CDs). All of this is true because I use a Nvidia 6200 VGA card myself:).

Now for your problem rolobio, try installing the Nvidia driver manually.

1) Download the Nvidia driver from [here]("http://www.nvidia.com/object/linux_display_ia32_169.07.html"). 

2) Then kill the GUI by entering:-
```
sudo /etc/init.d/gdm stop
```

3) Navigate to where the installer is and execute the installer using:-
```
sudo sh nameofinstaller
```

4) After the install is complete execute:-
```
sudo dpkg-reconfigure xserver-xorg
```

5) After reconfiguration is complete, do:-
```
sudo /etc/init.d/gdm start
```

---

### Post by rolobio on 2008-01-14
Thank you so much! I'll try this out and tell you how it works...

---

### Post by rolobio on 2008-01-14
Ok i'm on my other computer now... I did the first commmand "sudo /etc/init.d/gdm stop" and my GUI did stop but when i type things and hit enter nothing happens... it shows a few commands above where i'm typing "Running local boot scripts (/etc/rc.local)" and a few things like that...

do i need to restart in terminal or something? if so how do i do that? thanks so much!

---

### Post by rolobio on 2008-01-14
Ok, never mind that! I got to the file but when i run "sudo sh NVIDIA-FreeBSD-x86-169.07.run" i get the error "sh: Can't open NVIDIA-FreeBSD-x86-169.07.run" what should I do?

---

### Post by PmDematagoda on 2008-01-14
Are you sure that the driver is located in the current folder? You can make sure that the file is present by executing:-
```
ls
```

---

### Post by rolobio on 2008-01-14
yes i'm sure i'm in the correct directory i used the "dir" command.

---

### Post by PmDematagoda on 2008-01-14
Could you please post the result of:-
```
ls
```

---

### Post by rolobio on 2008-01-14
ok (btw i'm doing this via root in recovery mode, i still can't seem to type using the first command):

NVIDIA-FreeBSD-x86-169.07                        NVIDIA-Linux-x86-169.07-pkg1.run
NVIDIA-FreeBSD-x86-169.07.tar.gz

---

### Post by PmDematagoda on 2008-01-14
Are you sure you got the driver from:-
[http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html)
?

Because you are supposed to be having the Linux driver not the FreeBSD driver.

---

### Post by rolobio on 2008-01-14
Yes i'm sure i just tried to download it again and it tried to replace the file. (i've gotten this far by myself before and run into these same problems, but this is about as far as I've gotten)

---

### Post by PmDematagoda on 2008-01-14
Execute this command:-
```
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run
```

---

### Post by rolobio on 2008-01-14
Hmm... this time (under root in recovery mode) it worked-ish, it says I don't have the GNU chipset (sorry i didn't memorize the words) i'll try putting the card in and doing the same thing.

---

### Post by rolobio on 2008-01-14
Hmmm... it seems to freeze on startup in recovery mode as well...

Well... this is as far as I've gotten! Any suggestions? Need any more information? Thank you so much!

---

### Post by PmDematagoda on 2008-01-14
The Ubuntu Recovery start-up freezes on your Nvidia 6200 VGA card?

---

### Post by rolobio on 2008-01-14
Yes, it works completely fine just before I put it in then it freezes when I do put it in (while its off of course). (Recovery doesn't seem like it should break to me :P )

---

### Post by PmDematagoda on 2008-01-14
Is your Nvidia card used on a PCI slot or a PCI-E slot?

---

### Post by rolobio on 2008-01-14
PCI slot i dont have any PCI-E (crappy I know but its what I've got XD )

---

### Post by rolobio on 2008-01-14
BUMP does anyone know whats going on here? I'd really like to get this working. If I can't i'm going to have to switch back to windows, which i REALLY dont want to do, but I need this card working properly. thanks so much!

---

### Post by scorp on 2008-01-15
I can't really help that much tho i do have an idea that may just work but it's a hell of a long shot,order the cd from ubuntu then try installing,or attempt an earlier version install preferably with an original cd then upgrade from that,the reason i say this is when i first decided to give ubuntu a try v7.04,the iso i burned even tho it's md5 was fine, after selecting safe install mode all i got was a blackscreen,the live session was there i just could'nt see it,the same thing has happened with 7.10,however i had ordered the original 7.04 cd from this site & it worked as it should,so there is a difference from the downloadable iso, compared to an ordered cd is my guess there's no other logical explanation that i can think of,i was able to upgrade to 7.10 by installing off the original ordered ubuntu 7.04 cd,like i said a long shot in your case but it may work or not
good luck

---

### Post by Pumalite on 2008-01-15
Install again; this time with the Alternate CD. Cofigure your xserver at the end of the installation. Once IN the system, start looking for appropriate driver (probably the one I gave you in the second post)
If you run into other hardware problems: here is a guide and a collection of boot parameters you might want to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)

---

### Post by rolobio on 2008-01-15
ok i'll try the text installation. my dvd came with a text based installer is that ok to use? (i bought a dvd because my internet is too slow to download such a big file)

---

