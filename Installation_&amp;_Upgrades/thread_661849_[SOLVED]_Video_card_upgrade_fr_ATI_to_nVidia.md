---
title: "[SOLVED] Video card upgrade fr ATI to nVidia"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2008-01-08
Trying to upgrade a Gutsy 7.10 box from an old ATI card to a new(er) nVidia 5500.  I get the POST screen and the first Ubuntu splash screen with the notice that I need to change the refresh rate and/or resolution.  (It is a generic pivot enabled LCD. Want to be able to pivot the unit, hence the card change.) Then it goes blank and occasionally I will get a "flash" of some image or artifact on the screen, but it fails to get to the sign in screen.  I tried to run the repair boot (have the option on the boot us screen) but when it gets to the root command line, I get lost .. no password, of course.  So where do I go from there?  Will I have to do a dirty install of the system from the disk?  Or what?

---

### Post by rufius on 2008-01-08
Are you sure the card is working? Does it every drop to a console? 

If it doesn't drop to console, it sounds to me that the card is messed up.

What say you?

---

### Post by oldsoundguy on 2008-01-08
card is assuredly working ... (read)  .. I get the POST SCREEN and the initial splash screen .. also get the option screen of what do I want to do .. I SEE stuff on the screen, hence the card IS working.
I can get into a repair boot and launch it and watch it go through it's song and dance. (then I get to a root prompt and do NOT know where to go from there as I don't know what command line to enter.

---

### Post by forestpixie on 2008-01-08
try running inrecovery mode and doing this 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then reboot
you'll probably need to get the right driver, try restricted driver, or envy or getting the driver from nvidia

---

### Post by oldsoundguy on 2008-01-08
tells me that phigh is not installed and goes back to the prompt.

(have Envy already waiting on the machine ONCE I get booted.)

---

### Post by forestpixie on 2008-01-08
if you'd already used envy for the ati - from the envy site


> C) What happens if you are no longer able to access your Desktop Environment (because of a blank screen at boot)?

Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:

envy --uninstall-all

then simply type:

reboot

and boot as usual.

On next reboot the Xserver should work fine (but you will use the open source driver) 

if that doesn't work try 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by perixx on 2008-01-08
Hi...

if you can work on the console, you can get back to graphical VESA mode by doing
> sudo nano /etc/X11/xorg.conf
and editing the 'nv / nvidia' in the driver section to 'vesa'.
Save & Exit with CTRL-X and restart the X-server with 
> sudo /etc/init.d/gdm restart.
Before doing so, best make a backup of that file with
> cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old to have something you can go back to if things screw up.
You might be able to reconfigure your screen setup with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but if you don't act carefully, you might have less things working afterwards (keyboard problems, screen probs...).

If it turns out that your driver isn't working at all, consider re-installing it, after removing ATI's and Nvidia's drivers... here some links:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Regarding your Pivot-function, I think I've read that 'xrandr' function used in xorg.conf can provide it (or maybe a script using xrandr). Perhaps also your card's setup program provides such functionality...

**Off-Topic**: btw. Forestpixie, if you have some time, could you please have a look a my problem here too please? [http://ubuntuforums.org/showthread.php?p=4097202#post4097202]("http://ubuntuforums.org/showthread.php?p=4097202#post4097202")
greetz,
perixx

---

### Post by oldsoundguy on 2008-01-08
nope .. did  NOT use it for the ATI .. Just loaded it in anticipation of the nVida card.  But will try the un-install anyway.
(done)

On re boot .. goes to the initial sign in screen with NO DISPLAY (can hear the bongos)

So tried the second code line and got "command not found"

---

### Post by oldsoundguy on 2008-01-08
perixx: generic video and vesa are already there .. no mods done.

---

### Post by oldsoundguy on 2008-01-08
an FYI to those trying to help.
I am not a total noob to Linux, but AM to Ubuntu (love it thus far!)

I already have two 7.10 machines running nVidia cards and pivot enabled (and WIRELESS NETWORKED also).

Did NOT have this problem on those boxes.  But this one, for some reason, is giving me a ration .. solvable, but a ration none the less!

---

### Post by forestpixie on 2008-01-08
> Off-Topic: btw. Forestpixie, if you have some time, could you please have a look a my problem here too please? looks alright to me :)

oldsoundguy - have you tried reconfiguring without -phigh ? I know there's a -plow as well but to tell truth not been here long enough to have deciphered the difference

---

### Post by oldsoundguy on 2008-01-08
got into plow .. and then hit a wall when it asked for the descrete values for fixed-frequency display.
Using an older 15" Flexus (no longer made) LCD  ... 1024x768.

---

### Post by forestpixie on 2008-01-08
and I bet you've not the paperwork that came with it  - if indeed any did ;)

can you not get > sudo dpkg-reconfigure xserver-xorg to work

---

### Post by oldsoundguy on 2008-01-08
OK .. after multiple re-boots and experimenting with the plow entry .. got it!  PITA as there are just so many variables, but simplicity was the key (1025 x 768 and using the "simple" option, for instance)  did the deed.  Now to do the Envy d/l and set it up right!  THANKS A BUNCH for the help and the prods and the codes.

(BTW the reconfigure xserver-xorg command ... NO SUCH!)

---

### Post by forestpixie on 2008-01-08
odd it didn't work - sure the command is the right one

never mind glad I helped some

---

### Post by perixx on 2008-01-09
Thx, forestpixie, for looking it over... I managed to solve things with the > sudo dpkg-reconfigure -phigh xserver-xorg command ;)

perixx

---

### Post by oldsoundguy on 2008-01-09
Yep, no paper work with  that monitor as I bought it used!
BUT for ALL ... if you need a manual and are really not picky about the pretty pictures,  go to any search site for the FCC and plug in the FCC number .. first three are the manufacturer's code.  In MOST (not all) cases there will be a link to a PDF of the manual on the page containing the manufacturer's info and the description of the item.!

---

