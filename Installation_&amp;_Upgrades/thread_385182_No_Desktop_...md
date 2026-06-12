---
title: "No Desktop .."
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by fantomet on 2007-03-15
Yesterday i installed ubuntu with the live cd... i made a partition on my second HD, on my first i have Win XP... everything worked as it should... i could boot into both OS's.. but first time i went in to windows after installing... the second hard drive was gone ..? then i booted back to ubuntu and tried it (since its my first run on linux).. then i booted to windows again, and my hardrive was back (except 25GB wich I installed ubuntu on)... then i went to bed and thought everything was just fine.... but when i started my computer today and choose Ubuntu, all i get is the commandline, no desktop :-s   Anyone have any idea what the problem is here... i tried to boot in recovery mode to, but still no desktop :confused:

---

### Post by Kaphix on 2007-03-15
Sounds like my problem. Look here
[http://ubuntuforums.org/showthread.php?t=385117](http://ubuntuforums.org/showthread.php?t=385117)

---

### Post by fantomet on 2007-03-15
I've done the mounting thing, the prolem is that i never get to the desktop when i boot into ubuntu... all i get is a black screen saying starting up, and then i get the command line..

---

### Post by FruitieX on 2007-03-15
Well, tell us more about your system and it will be a lot easier to help you out! Like what graphics card do you have? Recovery mode is meant to boot into the command line just in case the desktop crashes your whole pc :). Did the desktop (The X server) work when you first booted it up yesterday? Did you change anything since that?

Edit: You shouldn't try this without an nvidia graphics card. Well, atleast you could try the "vesa" thing to get to the X server, but with poor performance.


Anyway you could try to log in into the command line and run "sudo dpkg-reconfigure xserver-xorg" if you have an nvidia graphics card, change "nv" into vesa. (Temporarily) The nv driver seems to have problems... And do you have a dual graphics card setup?  
If you get to the "desktop" like this, you can go to the nvidia website (once again with an nvidia graphics processor, I assume you have one now) [www.nvidia.com](www.nvidia.com) . Download drivers, Linux drivers, If you have an AMD64 CPU, chose this one, if you don't, chose an other one. Save it to your home folder (/home/*username*/) where *username* is your name. When it has finished downloading, log out from the desktop, press Ctrl+Alt+F1 to get to the command line again, run "sudo /etc/init.d/gdm stop" and then (to ensure that you get all the needed packages) run: sudo aptitude install nvidia-glx . The sudo command is there so that you run it as superuser (like an administrator in windows) After all this, write: sh /home/*username*/NVIDIA and press Tab. (Again *username* is the same as your log in) Then press enter. Accept the license agreement and continue. As it asks to download something, answer no. Then just enter should do it :). After the installation (IF it succeeded :D) run "sudo dpkg-reconfigure xserver-xorg" again, but now there should be an nvidia driver also. Set up the rest of the settings like you want them, if you don't understand something, you should be able to just press enter (or use tab to get to the OK button) In the resolution screen, set the best resolution that your screen can take and down. And the refresh rates... (they should be something like this (Horizonal): 80-75, (Vertical) 75-70. Well these are mine... After this it SHOULD work... You can try running "gdm" to test. No rebooting needed like in windows ;P.

You'll figure it out I guess.

Good luck!

FruitieX

---

### Post by fantomet on 2007-03-15
My system is:
 Mainboard: MSI k8mm-v
 CPU: AMD Athlon 64 2.0GHz (No i dont use x64 ubuntu)
 Graphic: OnBoard graphics (VIA S3G UniChrome Pro IGP)
 Memory: 2x Crucial PC3200 DDR-DIMM 1024MB
 HDD: 1x Western Digital Caviar SE 250GB SATA2 (Win XP) + 1x Samsung SpinPoint P80SD 80GB SATA2 (Ubuntu)

The Desktop worked fine yesterday, now i only get the command line...

---

### Post by FruitieX on 2007-03-15
Darn! No nvidia card... Have you got the vesa option done? An alternative approach is: "sudo nano /etc/X11/xorg.conf" Search for the Device section and from there Driver. Replace the driver with vesa. Press CTRL+X to exit, it will prompt for saving. Press Y and then enter it to save and exit. Try startx again and see if something else than a command line with lots of code comes up. If the error codes show, Could you then please write the messages down/take a photo of them and attatch them here? Don't give up just yet! :)

Edit: Why don't you use x64 ubuntu? :)

Edit2: What are you going to use this computer for? Gaming? (Probably not), Apps? Server?

FruitieX

---

### Post by fantomet on 2007-03-15
When i type 'startx' i get two errors:

- failed to load module "openchrome" (module doesnt exist, 0)
- No Devices detected

I did have another graphic card, but it doesnt work (i have sent it back on the guarantee).. so i mainly use it for gaming.. i installed linux just to try acctually.. get to know what all the fuzz it about

I dont use x64 because i've heard its more trouble with that version ..??

---

### Post by zvacet on 2007-03-15
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by FruitieX on 2007-03-15
No it's not more trouble with that version? I use it with no problems... openchrome??? What's that? :P. And have you entered a correct value for the Device BusID? If you don't know it you should leave it empty. Absolutely no idea why some openchrome module ain't suddenly detected after a reboot O.o. What brand/model is the other graphics card? You could always try to do "sudo aptitude update" and then "sudo aptitude dist-upgrade" IF that would help... Otherwise "sudo aptitude purge xserver-xorg" then "sudo aptitude clean" then "sudo aptitude install xserver-xorg", couldn't that help? Upgrade to feisty? :D.

And lastly, doesn't x64 versions speed things up? As I have heard...

---

### Post by fantomet on 2007-03-16
I got it working now... thanks to everyone :D

---

### Post by ryckmonster on 2007-04-04
how'd u get it working??


if anyone can help me, i am having a great deal of difficulty installing 64 bit linux distros, on my amd64 3400+...

I am currently using ONBOARD graphics, and I'm guessing it is my main problem... I can never boot the live cd, or install, it always hangs up... somehow I did get kubuntu to install, however, the graphics was terrible as I never found a driver....

any tips??? I am sooo frustrated...

---

