---
title: "plz help error on startup"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by dutch_boi1 on 2005-06-30
hey i have done the installationg and it has all worked but wen i start up it cumz up with this error saying GUI(graphical user interface) unable to load, plz help me i want this 2 work.

---

### Post by kamstrup on 2005-06-30
So you end up in console right? If so, log in and type the following:
```
grep "Driver" /etc/X11/xorg.conf
```
This will tell you what drivers are being loaded. - It's almost 100% sure the graphics driver that's the problem. Please post the output of the command here and I'll maybe be able to help you get it working. If you're lucky it's an easy fix :-)

PS: And could you post the make/type of your graphics card as well?

---

### Post by dutch_boi1 on 2005-07-01
ok yes i start up after that error msg in the consol. i logged and tried typing in the code (grep "Driver" /etc/x11/xorg.conf) and it came up with an error saying " no such file or directory" and then it goes straight back to b4 i typed in that code.

my graphics card details , it is an ATI Radeon 9200 pro with 128mb of vram, it works fine with windows 98 in which i have tried. Does ubuntu suppport this graphic card? i have tried typing in and the consol after i have logged in " sudo dpkg-reconfigure xserver-xfree86 "to type in my settings for the graphics card and the monitor but that doesnt change anything. :mad: 

thankx

---

### Post by michael_salcher on 2005-07-01
/etc/X11/xorg.conf does not exist on warty. warty is using xfree86, hoary is using xorg. kamstrup wanted to know what driver the xserver uses. you can supply the same information by dumping the output of:

```
cat /etc/X11/XFree86.conf
```

here in the forum.

---

### Post by dutch_boi1 on 2005-07-01
ok thankx so if i type in that code , then wat do i do 2 get the x-server starting up with the login thing with out the console showing? cauz it starts up with the consol and it has the error saying cant load the x-server which has the GUI on it. so basicly im left with the gay console

---

### Post by dutch_boi1 on 2005-07-01
hey look i have tried that code and it did the same thing, so i dont know wat 2 do, could u plz help me cauz i wanna get this thing goin ](*,)

---

### Post by michael_salcher on 2005-07-01
it seems like what's happening is that when ubuntu starts, the xserver tries to start up but fails. therefore it's is likely that some of your XFree86.conf settings are incorrect. if you post the content of XFree86.conf here in the forum, someone (possibley me) might be able to figure out what's wrong.

---

### Post by michael_salcher on 2005-07-01
```
cat file
```

just prints the content of file to standard output. it won't fix your xserver.

---

### Post by dutch_boi1 on 2005-07-01
hey look how do i get the out put or info of that file if it duznt find it in the first place , wen i type in cat /etc/X11/XFree86.conf it says the directory duznt exist, what is happening?

---

### Post by dutch_boi1 on 2005-07-01
hey typing in cat file in the console still doesnt work it says that file cant b found or that directory duznt exist

---

### Post by michael_salcher on 2005-07-01
what does not exist?

/etc/X11/XFree86.conf

or 

/etc/X11

or

/etc ?

---

### Post by michael_salcher on 2005-07-01
if you type

```
cat file
```

you are supposed to replace 'file' with the file you want to print to stdout.

to get info on how to use any program on linux type:

```
man program
```

where 'program' is the name of the program you want help for. eg.

```
man cat
```

---

### Post by dutch_boi1 on 2005-07-01
i know it isnt going 2 fiz my x-server wat i need is sumtin that will fix it,lol wen the error msg appears it says exactly this :" I cannot start the X server ( your graphical interface ). It is likely that it is not set up  correctly. Would you like to view the X server output to diagnose the problem? " ans that is all it says, when i click yes it has nothing 2 do with fixing the problem, pplz help? also i cant open that cat file

---

### Post by michael_salcher on 2005-07-01
maybe you should read the messages that i posted, before you post something like this.

---

### Post by michael_salcher on 2005-07-01
it's not like i can give you one command to type in and it will fix your problems. we first need to figure out what the problems is.

---

### Post by dutch_boi1 on 2005-07-01
ok /etc/X11 exist     XFree86.conf does not, so wat duz that mea exaxctly?

wen i type in man cat it shows this information on all about that cat file , but i cant show the information for Xfree86.conf what can i do?

---

### Post by michael_salcher on 2005-07-01
probably that xfree is not installed. run

apt-get remove xserver-xfree86

(just to make sure)

and then

apt-get install xserver-xfree86

---

### Post by michael_salcher on 2005-07-01
actually, thinking about it again: xfree has to be installed, otherwise it wouldn't try to start  :smile: 

so i guess XFree86.conf is not the name of the config file. maybe it's called XFree86.config or similar. to find out, check what's in /etc/X11 and then post the content of the config file here. the important sections are the monitor and the graphics card section.

---

### Post by dutch_boi1 on 2005-07-01
hey could i like type in " man XFree86.conf " or sumtin to view the output cauz i dont know how to view the output? plz help. ](*,)

---

### Post by kamstrup on 2005-07-02
A few clarifications:

Sorry I didn't realize you where running Warty (as opposed to Hoary), this means that the file /etc/X11/xorg.conf is not supposed to exist, so that is all fine.

If I remember correct, it is the file /etc/X11/XF86Config which is the configuration for for the graphical system (XFree86 or just X)...

Try doing ```
grep "Driver" /etc/X11/XF86Config
``` instead. If the output doesn't say anything about "vesa" or "fbdev" it might be a good idea to change your driver to the vesa one.

**Changing drivers:**
Edit the X configuration file manually: ```
sudo nano -w /etc/X11/XF86Config
```

Find the _Device_ section and change the line ```
Driver       "something"
```
to ```
Driver       "vesa"
``` Save and exit the editor (Ctrl-X).

Now reboot ```
sudo reboot
``` -- and cross you fingers ```
cross fingers
``` :-D

Good luck

---

### Post by dutch_boi1 on 2005-07-02
hey  i tried typing in " grep "driver" /etc/X11/XF86Config " and it says " No Such File or Device "

then later i tried typing in " Sudo nano -w /etc/X11/XF86Config " and it came up with the editor but the whole and every page was blank, just black no words. wat duz this mean? do i have 2 run another setup program?

when i startup in the beggining it also has an error saying " ror : FATAL error in name resolution " in red, duz that  have nething to do with my graphics card?

i also tried setting up my graphics card and monitor by typing " dpkg-reconfigure xserver-xfree86 " and it says sumtimes " xserver-xfree86 not installed " but then when i type in " apt-get install xserver-xfree86" it says it is installed and updated .
Other times it loads the setup program and asks me all these questions like things to do with where my graphcs card is loacted in which pci slot with all these wacky numbers, even though it is an agp card. Does that mean nething? this installer is very buggy, i have had numerous errors and faults in the installer.

the 1st error i get is this " modprobe : FATAL : Error insterting hw_random (lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random.ko) : no such device " is that ok or is that a bad thing.

i have also tried typing in " startx " and it comes up with this error saying the x-server has crashed. how many errors can this os have. i wanted sumthing betta den windows and i already have errors, not a good start,lol

plz help

---

### Post by dutch_boi1 on 2005-07-02
ok on the consol i typed in

> dpkg-reconfigure xserver-xfree86 

then it came up in the setup screen where it says select ur driver, so i scrolled down and what was there but Vesa, so i selected that and clicked continue, and followed the onscreen instructions.

then to make sure it had all worked i typed in at the consol

> nano -w /etc/X11/XF86Config 

and it says that the file doesnt exist, what is going on?

thankx 4 the help

---

### Post by dutch_boi1 on 2005-07-02
ok i got it goin with the nano thing and i changed it to vesa. the onli thing i was waondering is , my video card is an ATI radeon, and it had a ATI thingy in there, wouldnt i b more apropriate to use that 1 then this vesa 1 which duznt belong to my graphics card?

would u know how to find out the bus id of my agp graphics card? becauz i dont know it?

thankx

---

### Post by dutch_boi1 on 2005-07-02
hey thankx it got it goin after a while, pretty good 4 a 13 yr old hey,lol yeh i am 13. i am aso happy i go it goin so in the end it was just that vesa thingy,pretty kool u know ur linux,great 1, O:) i am so happy, thankx again.

---

### Post by kamstrup on 2005-07-04
Now that you have become a l337 H4><0|2 you can try changing the "vesa" to "ati" and see if it works better. You can always change back if it doesn't.

If you're even more adventurous you might try installing the original drivers from ATI. This is prolly a bit harder but will give you 3d acceleration :D You should find *plenty* of threads about this in these forums. - The search function is your friend.

Cheers!

---

### Post by dutch_boi1 on 2005-07-04
ok where would i find the proper drivers for my graphics card for linux and how would i install them properly?

would u know how to make ubuntu more compatible with windows applications and b able 2 play games on it?

also ubuntu doesnt find my modem, it is a motorola sm56 internal pci modem, is there a way to install these drivers for it and all of the things i have asked?

---

### Post by kamstrup on 2005-07-05
[QUOTE=dutch_boi1]ok where would i find the proper drivers for my graphics card for linux and how would i install them properly?

would u know how to make ubuntu more compatible with windows applications and b able 2 play games on it?

also ubuntu doesnt find my modem, it is a motorola sm56 internal pci modem, is there a way to install these drivers for it and all of the things i have asked?[/QUOTE]
 As for games check this thread:
[http://www.ubuntuforums.org/showthread.php?t=5153](http://www.ubuntuforums.org/showthread.php?t=5153)

About installing the ATI drivers:
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

*NOTE: You find your kernel version by running "uname -r".*

also this thread:
[http://www.ubuntuforums.org/showthread.php?t=40494&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=40494&page=1&pp=10)

-- ATI's own site:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

*NOTE: If you end up compiling your own driver, note that you will need kernel sources installed. The package you want is linux-headers-<YOUR KERNEL VERSION>*


I'm sorry, but I don't know anything abou the modem...

---

### Post by BenGDoG38651 on 2005-07-05
i have the EXACT same problem with my TNT2 but whenever i try to type any of that code it says that it needs to be run as root. so i type su (thats what i used to do in mandrake) and and it asks for a password but i havent set a root password..... i tried the password from my account but it says authentication failure.

ps im also runing 4.10 warty warthog

O and on startup i get an two errors about "pciehp" and "shpchp"

any ideas??

thanks in advance.

---

### Post by dutch_boi1 on 2005-07-06
alright so the problem you have been getting is that it wont boot up the xserver?

if so type in ur account ( not root )

> sudo passwd root 

then it will ask for your password, not root just normal

then type in your password and then follow what it says on the screen. it will ask u for the new unix password ( the new root password ) and then it will ask u to repeat the password to make sure u havent miss spelt it.

ok after you have done that it should say password set or similar.

once u have done that logout of ur account and log into root by typing:

> logout 

then just type root into username and ur password u chose into the password thingy.

ok now that u are in root u wont have to do " sudo " behind every command, now to setup your xserver type in the following code into the consol:

> dpkg-reconfigure xserver-xfree86 

then follow on screen instructions, wen it asks u 4 the graphics driver, it will have a scroll or list, scroll down until u see " vesa " then select that and choose any other configurations u want.

sorri but i have no idea bout the errors on startup, hope this information helps

ps. it isnt "su" for warty warthog it is "sudo", that means superuser do.

---

### Post by kamstrup on 2005-07-07
[QUOTE=BenGDoG38651]i have the EXACT same problem with my TNT2 but whenever i try to type any of that code it says that it needs to be run as root. so i type su (thats what i used to do in mandrake) and and it asks for a password but i havent set a root password..... i tried the password from my account but it says authentication failure.

ps im also runing 4.10 warty warthog

O and on startup i get an two errors about "pciehp" and "shpchp"

any ideas??

thanks in advance.[/QUOTE]
 Ubuntu has no root user. Instead you type ```
sudo my_root_command
``` and use your normal user password, to do stuff as root. If you want to "become" root I suggest doing ```
sudo bash
``` - or as dutch_boi suggests, to create re real root account.

Good luck!

---

### Post by kamstrup on 2005-07-07
By the way... Both of you. Is there any specific reason for running Warty instead of Hoary? Hoary brings along a lot of niceness and improvements over Warty...

There are plenty of instructions for automated Warty->Hoary upgrades around...

Cheers!

---

### Post by dutch_boi1 on 2005-07-11
well i aint usin hoary cauz i havent got the cd yet and i havent downloaded hoary cauz i have dialup and i will take 2 long, by the way what type of improvements does it have? is it more compatible with windows?

another question i have is , do u know how to install wine? because with the warty i have it doesnt have internet so i downloaded the packages manually on this machine and put it onto cd's and i dont know how 2 install them manually, there r 5 packages all 2 getha. how would i do this?

---

