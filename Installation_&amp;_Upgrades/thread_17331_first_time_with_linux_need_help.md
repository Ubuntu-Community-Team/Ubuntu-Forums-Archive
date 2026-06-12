---
title: "first time with linux need help"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by linux-newbie1 on 2005-02-27
Hello all. I downloaded "warty release" and installed it ok. restarted then did some internet updates. i have an install of windows xp and ubuntu on the same drive and i used "Grub" to select which OS to load. 

when i load Ubuntu it says cannot load server x (i think it called this) so i have no graphical interface and i do not know how to get the graphical interface to load.

all i can do is enter my user and password on the black screen with white text.  can you please describe to me how i get the graphical display please. 

i am a windows user and i wish to learn linux.

thank you very much.

---

### Post by bored2k on 2005-02-27
:-& that's not too good... straight from redmond and having X problems...

Have you tried the ubuntu live disc? did it work ?

---

### Post by KLineD on 2005-02-27
Try to type 'startx' and post here the output that you get. Maybe then someone can help you. I hope you don't get dissapointed at linux because of that error.

---

### Post by linux-newbie1 on 2005-02-27
[QUOTE=KLineD]Try to type 'startx' and post here the output that you get. Maybe then someone can help you. I hope you don't get dissapointed at linux because of that error.[/QUOTE]

Hello.
Before i saw your post i found i had to do this:
 sudo apt-get install nvidia-glx

then

 sudo nvidia-glx-config enable

then it seemed to work.

I do not understand the code but it did the trick. I am in Ubuntu right now.

How do i make the resolution bigger i have a 19inch LCD monitor and everything is too huge!  :grin:

---

### Post by KLineD on 2005-02-27
Those commands are to install the nvidia graphic drivers from the ubuntu repositories using apt.

Apt is a tool to get and install new software or to update the software currently present in your system. It's very powerful and it can do very amazing stuff that if you stay in linux surely are to find about.

If you can now boot to a graphical environment, just go to the System menu, then preferences, then screen resolution. You can change the resolution there.

---

### Post by Gary Powers on 2005-02-27
Under the Applications/System menu, you will find preferences > screen resolution and should be able to set it from there.  Under Hoary, it's under the System drop down.

Gary

---

### Post by sandman55 on 2005-03-02
[QUOTE=linux-newbie1]Hello all. I downloaded "warty release" and installed it ok. restarted then did some internet updates. i have an install of windows xp and ubuntu on the same drive and i used "Grub" to select which OS to load. 

when i load Ubuntu it says cannot load server x (i think it called this) so i have no graphical interface and i do not know how to get the graphical interface to load.

all i can do is enter my user and password on the black screen with white text.  can you please describe to me how i get the graphical display please. 

i am a windows user and i wish to learn linux.

thank you very much.[/QUOTE]

I think I am in the same boat Ive installed the warty warthog release from the free disk (the live disk works perfectly) when I instal and let them instal the updates I have the DOS type screen, but when I reinstal and dont update I have GUI. 


Ive since reinstalled with updates and I'm stuck with the Dos type screen with a log on. (takes about 1 hour on ADSL for the updates)

The same as you I'm dual booting only I'm using Win98

Ive posted my problem [Here](http://ubuntuforums.org/showthread.php?p=82073#post82073) so if I get help it may help you and the same with you for me

Edit: I have tried startx and I get: "bash: startx: command not found"
This is on the place after I have logged in

---

### Post by az on 2005-03-02
[QUOTE=Gary Powers]Under the Applications/System menu, you will find preferences > screen resolution and should be able to set it from there.  Under Hoary, it's under the System drop down.

Gary[/QUOTE]


You may need to do
sudo dpkg-reconfigure xserver-xfree86
and configure your X server to be able to enable more resolution options.


Sandman:  Try 
sudo apt-get -f install

---

### Post by sandman55 on 2005-03-02
Thanks azz I tried that and it said:
Reading Package lists...  Done
Building Dependancy Tree...  Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

Im still at the DOS type screen do you have any other suggestions?

---

