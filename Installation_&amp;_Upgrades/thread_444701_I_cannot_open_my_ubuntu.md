---
title: "I cannot open my ubuntu"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Usta_AsH on 2007-05-15
Hello, first of all i can open my ubuntu for live cd but when i install my ubuntu for my hdd, I cannot open my ubuntu. Ubuntu asking for me username and password and i enter my usrname and pass. and ubuntu ain't open my desktop. When i looked my monitor there is only background picture. Please don't say me wait, cuz i waited 15 hour.

Ps: I deleted ubuntu and reinstalled but this problem not solved.

---

### Post by ghostboy on 2007-05-15
> **Usta_AsH said:**
> Hello, first of all i can open my ubuntu for live cd but when i install my ubuntu for my hdd, I cannot open my ubuntu. Ubuntu asking for me username and password and i enter my usrname and pass. and ubuntu ain't open my desktop. When i looked my monitor there is only background picture. Please don't say me wait, cuz i waited 15 hour.
 
Ps: I deleted ubuntu and reinstalled but this problem not solved.
 
When you installed Ubuntu on your hard drive, you were asked to setup a username and password. 
 
For example, **Username: USERX** **Password: XXXXXX**. Use the username and password you supplied at the installation. 
 
I hope this helps. Let me know.

---

### Post by Usta_AsH on 2007-05-15
you don't understand me.
i enter my username and password and ubuntu accepting i know my detected password. Whatever
i am entering my username and password ubuntu accepted after there is a only background picture it looks like orange colour middle of monitor there is white line(not strait). And ubuntu waiting this background i cannot see anything in my monitor(except background)

---

### Post by StatVoid on 2007-05-15
::BUMP::

I have this same issue.  I just installed 7.04 today, but have been trying since two days ago, and had originally tried to use the LiveCD (btw, this was all done with both the 32- and 64-bit versions) to try it out but when I would go into the option to Try or Install it, it would load and then just go to the default background image, except it was clearly distrorted and nothing would work and I've have to hit the refresh button on my PC to reboot.  So instead of wasting CDs and finding no answers online like I was doing, I decided to just download the text-only alternate and go ahead with a full install.  Not a big problem. Sooooo...

Long story short, everything seems like it's working right and it has to reboot after installing GRUB (so clearly before it got to this point, I had already created a username and password for the system).  So now I'm excited to see this OS, and I proceed to enter in my created username and password.  As it begins to show the desktop... NOTHING.  All it shows is what should be the default desktop image, but the background is distorted and nothing loads up (just like it did when I booted from the LiveCD, to no avail). The only thing that works is the mouse, which I can only move around as clicking does nothing.  The keyboard can't even turn NUMLOCK on.  So I try again and again; nothing.  This time on the login screen, for the hell of it, I decide to see my Language options (I only know English, but what the hell...might as well try something) and the "Select Language" box pops up and...nothing.  The only thing that shows is an outline of what is clearly supposed to be the drop-down menu but inside the outline it is clear and I can still see the "Select Language" screen and the keyboard is frozen and the mouse will do nothing more than move.

If you want to, I'll take a picture with my camera to show you all what I mean.  Either way, this is extremely frustrating.  I'm relatively new with Linux though I am good and patient with computers, so I'll give suggestions a try, just keep in mind they may need to be a little more detailed than usual so I can coherently follow them.

Here are my hardware specs in case this may help (if there's anything else you might wanna know to help me solve this problem, please let me know)...

AMD Athlon 64 3700+
2GB DDR Ram
nVidia GeForce 7800 PCI-express
ASUS A8N-SLI mobo w/ nVidia nForce4 chipset
250GB WD IDE Hard Drive
60GB WD IDR Hard Drive (which I'm using, fresh, with only Ubuntu and the swap partition on it)
DVD RW
CD RW
Wired LAN (through mobo)
Creative SoundBlaster LIVE! 24-bit

Thank you for the help in advance.

---

### Post by Usta_AsH on 2007-05-15
has anyone use ubuntu 7.04 without live cd?

---

### Post by bveb on 2007-05-15
Hi,
On login screen hit CTRL+ALT+F2 you see text mode login prompt. Login and delete your .gnome directory on your home.  Hit CTRL+ALT+F7 and try login from X. If no success back to text mode and start top command. Look for CPU usage .If some process use %100 write here name of process. After that try to kill gdm.

---

### Post by rajausman on 2007-05-15
Which type of hard disk are you using? As most of the hard disk related problems are solved by typing:

linux all-generic-ide

Don't hit enter when you try to install at the first place, but you should press F6 and try this code as a parameter, at the end of the line. Should work now.

---

### Post by Usta_AsH on 2007-05-15
> **bveb said:**
> Hi,
On login screen hit CTRL+ALT+F2 you see text mode login prompt. Login and delete your .gnome directory on your home.  Hit CTRL+ALT+F7 and try login from X. If no success back to text mode and start top command. Look for CPU usage .If some process use %100 write here name of process. After that try to kill gdm.

i don't understand you i'm beginner
how can i delete .gnome directory can you tell me one by one.

---

### Post by StatVoid on 2007-05-15
> **rajausman said:**
> Which type of hard disk are you using? As most of the hard disk related problems are solved by typing:

linux all-generic-ide

Don't hit enter when you try to install at the first place, but you should press F6 and try this code as a parameter, at the end of the line. Should work now.

During which point in the boot process would I hit F6? Thanks.

---

### Post by rajausman on 2007-05-15
By the time you load the live cd. It gives you a 4 or five options, with a timer 30 sec timer on the left. At the bottom it gives you all the options.

Thanks

---

### Post by StatVoid on 2007-05-15
> **rajausman said:**
> By the time you load the live cd. It gives you a 4 or five options, with a timer 30 sec timer on the left. At the bottom it gives you all the options.

Thanks

I have already installed Ubuntu with the text-only installer. My question now is concerning the performance, or complete lack-there-of, of the OS not loading anything beyond a distorted desktop image.

---

### Post by Usta_AsH on 2007-05-15
i understand some part of them
this .gnome file
is it in the home directory?
if your answer is yes
i don't have .gnome file or folder.

---

### Post by Death_Sargent on 2007-05-15
> **bveb said:**
> Hi,
On login screen hit CTRL+ALT+F2 you see text mode login prompt. Login and delete your .gnome directory on your home.  Hit CTRL+ALT+F7 and try login from X. If no success back to text mode and start top command. Look for CPU usage .If some process use %100 write here name of process. After that try to kill gdm.

in order to delete your .gnome directory you must first locate it

while its probubly under /home/<your user name>/.gnome

you can make sure by typing

```
locate .gnome
```

once you asertain its location type 

```
rm /the/path/to/.gnome
```

being sure to make sure the path is correct

add sudo infornt of any code ie "sudo rm blablabla"so that you can use admin powers.

the password is your login pass word

---

### Post by Death_Sargent on 2007-05-15
if you cant find your .gnome folder then i recomend installing a new desktop environment 

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

be sure to have a wired internet connection that is working when you do this. 

then restart. 

when you see the login screen click either "options"or "sessions"or some combination of the two.

from there select xfce and you will have a lack luster desktop

i recomend fully uninstalling gnome or installing kde or whatever works. hell you may just want xfce.

---

### Post by Death_Sargent on 2007-05-15
`note when you log in it will prompt you 

READ THE PROMPT as hitting cancel will make this an excersie of futility

you may reinstall gnome infact im pretty sure you have too

---

### Post by StatVoid on 2007-05-16
I feel stupid... The one thing I didn't try was starting it up in Safe Graphics Mode. Turns out that that was my personal solution and probably the main solution that should be used when someone comes across an error similar to my own. After a million discs, turns out my answer was probably easier than expected. Oops. Oh well, you've got to mess up in order to learn, right? Heh. Thank you all who tried helping me. Now hopefully I'll really be able to get a grip on the OS and eventually only use that instead of depending on the machine that is Microsoft.

---

### Post by Usta_AsH on 2007-05-16
hello
rm: cannot remove ".gnome" : Is a directory.

---

### Post by bveb on 2007-05-17
rm .gnome -rf

---

### Post by Usta_AsH on 2007-05-17
i cannot successful on this
software packages volume detected program has lag.

---

### Post by Death_Sargent on 2007-05-17
> **Death_Sargent said:**
> if you cant find your .gnome folder then i recomend installing a new desktop environment 

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

be sure to have a wired internet connection that is working when you do this. 

then restart. 

when you see the login screen click either "options"or "sessions"or some combination of the two.

from there select xfce and you will have a lack luster desktop

i recomend fully uninstalling gnome or installing kde or whatever works. hell you may just want xfce.

did you give this a try
since you are seeing the software packages I assume you did. If so I have never heard of the lag error. 

You may want to try buying an install CD instead as it seems starting over from scratch may be the way to go.

---

### Post by Usta_AsH on 2007-05-20
i did i opened my ubuntu but that ubuntu was too bad. There is lots of bug. What can i do?

---

### Post by Death_Sargent on 2007-05-21
for support please list the bugs so we can help you

---

