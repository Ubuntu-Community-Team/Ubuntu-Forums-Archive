---
title: "Video Card Drivers?"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by 122jdh on 2013-01-03
I installed Lubuntu and it boots fine. It gets to the Lubunto splash screen and then goes to a black screen with a mouse pointer. I used CTRL+ALT+F1 and it takes me to a prompt screen just fine. I think i need to install a video card driver for this card:
Mobility Radeon 7000. How do I download this driver using the prompt screen?
I've searched around and found that i need the fglrx driver, but i am only able to get to terminal, can someone tell me a command to download an updated driver?

---

### Post by Bashing-om on 2013-01-03
122jdh; Hi !

See if this will work for you.
Boot to the login screen and log in (username followed by password)
enter the terminal command:
```
jockey-gtk
``` to try and load the Additional Drivers utility.
(As we not know if X server has loaded at this time, may not load)
then install the recommended driver.
Reboot to see results:
```
sudo shutdown -r now
```"sudo" requires the use of your password -elevating privileges - will get no response to screen (security reasons).
[INDENT][INDENT]just try'n to help <== BDQ
 
[/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
using the first command you gave me told me it was not installed so I installed it.
and then when i try your command it tells me that package is not installed?
Im using Lubuntu 12.10

---

### Post by Bucky Ball on 2013-01-03
When you get to the menu at boot, choose the kernel you want to use and hit 'e' to edit the entry (if you are not getting the list to choose from at boot hit Shift after the BIOS screen).

Find the line that ends in 'quiet splash' or either quiet or splash.

After a space, add 'nomodset' at the end of that line.

Follow the instructions at the bottom of the screen to save and continue the boot.

What happened? If this gets you in, get online, do an update, then check 'Additional Drivers' and see if there's something in there for your video card. The process of the update may install appropriate open-source drivers anyway. Good luck.

---

### Post by 122jdh on 2013-01-03
im using an ibook there is no bios just open firmware. and i have no idea how to choose a kernel i just let it boot up.

---

### Post by Bashing-om on 2013-01-03
122jdh; Lemme scratch my head a bit on this, I have lubuntu 12.04 and the jockey-gtk (aka Additional Drivers) is installed by default.
Run this terminal command see where it is installed:
```
whereis jockey-gtk
```my output looks like this (ubuntu 12.04)
> jockey-gtk: /usr/bin/jockey-gtk /usr/bin/X11/jockey-gtkBe advised if we can not get Additional Driver utility via CLI, - which I thought to be the easiest method- will try via the grub menu at boot up -after bios loads--.

[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
when i try that command i get 
jockey-gtk:
and that is it.
And ibooks do not have a BIOS.

it boots to "first stage ubuntu bootstrap"
and gives me the option of I for GNU/Linux or C for CD
and then it goes to yaboot loader where it give the prompt boot:

---

### Post by Bashing-om on 2013-01-03
122jdh;

I am at a loss here.
 I have never seen an ibook, nor have I ever seen yaboot loader.
As you can not get to a grub boot screen, all I know to do is try and install the jockey-gtk application. Did you do like this to install ? (as the whereis command indicated the package is not installed)
```
sudo apt-get install jockey-gtk
```and enter your password.

[INDENT][INDENT][INDENT]still try'n to help <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
i used
dpgk -s jockey-gtk
to find out where it was installed
i get these locations
/usr/share/doc/jockey-gtk
/usr/share/doc/jockey-gtk/copyright
/usr/share/doc/jockey-gtk/changelog.Debian.gz

but that feature was merged into the OS its now called software-properties-gtk

---

### Post by Bashing-om on 2013-01-03
122jdh;
That again indicates that jockey-gtk is not installed. Installed package would have a long result inclusive of it's status as "install ok installed"; As well as lots of other info.
Might try this as the package failed to install:
```
sudo apt-get install --reinstall jockey-gtk
```[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
i get the same problem as before. 
Could my main problem be the resolution? How do you change that in terminal?

---

### Post by Bashing-om on 2013-01-03
122jdh;
imo the symptoms would be different for a resolution problem.
If you can not install a package, that points to even graver problems.
In answer to your question about changing the resolution from the command line; I am sure there is a way. But, I do not know how. That gets real deep into the system and complex.
At this point I really wish there were a way to get to the ubuntu grub menu to edit the boot parameters.
[INDENT][INDENT]not lookin' too good <== BDQ

[/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
I've made huge progress on my problem. When it went to the black screen adn i moved my mouse around I could tell there was a logon prompt. So by moving my mouse slowly till I got the insert icon as a pointer, i was able to login to the desktop. however its all fuzzy and off color so now i just need to update my driver. Where can i go for the driver update?

---

### Post by Bashing-om on 2013-01-03
122jdh; 
give me a bit of time to log out/log off and boot up my lubuntu12.04...be back with specific locations.

---

### Post by Bashing-om on 2013-01-03
122jdh; I am back
my 12.04 lubuntu Additional Drivers:
Bottom of screen is the task bar;
Far left "manta ray" looking icon->preferences->top item is Additional Drivers.

[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by 122jdh on 2013-01-03
The top item in mine is Bluetooth Manager

---

### Post by Bashing-om on 2013-01-03
122jdh;

The list is in alphabetical order-bluetooth is my second option.
All I can say is that Additional Drivers (aka jocky-gtk) is not installed on your system.

Try and install it from synaptic ??? system tools->synaptic->search term "jockey-gtk" ->mark for installation.

[INDENT][INDENT][/INDENT][/INDENT]hth <== BDQ

---

### Post by 122jdh on 2013-01-03
im installing jockey-kde right now but i dont know if it will work. Id be much more confortable with a link to the driver instead of going through all this.

---

### Post by Bucky Ball on 2013-01-04
If you can find Additional Drivers the correct driver could well be there already and ready to enable without you having to do much but click to enable ...

---

### Post by 122jdh on 2013-01-04
I have additional drivers its in a tab under software sources and it will not open, I click on the program a box comes up and i only see the bar with name of the program, i cant see anything and if i hit enter a couple times it brings up this authentication . this happens also in software updater (i think thats the name) so i cant even update but does not happen in other programs.

---

### Post by Bucky Ball on 2013-01-04
When that happens just put in your password ...

---

### Post by 122jdh on 2013-01-04
I do that and then the window becomes larger but i still have the same problem

---

### Post by gilgongo on 2013-01-04
Do you have an NVidia graphics card? If so, and you're trying to install Ubuntu 12.10, there is an amazingly huge bug right now that prevents you from being able to install the right video driver for your card.

If so, you might like to read this:

[http://askubuntu.com/questions/218629/driver-for-nvidia-graphics-card-on-12-10](http://askubuntu.com/questions/218629/driver-for-nvidia-graphics-card-on-12-10)

and/or this:

[http://ubuntuforums.org/showthread.php?t=2083868](http://ubuntuforums.org/showthread.php?t=2083868)

---

### Post by Bucky Ball on 2013-01-04
Or you might like to try 12.04 LTS.

---

### Post by 122jdh on 2013-01-05
No my video card is an embedded Radeon Mobility 7000 (RV100 CHIP)
i would love to try and install another version, but the problem i have (YAY another problem) is when i try and create a cd or usb. I created the USB i used for setup on MAC OS X 10.3.9. When i put it in the mac it shows up just fine when i boot holding ALT and in the OS, but I put it in my XP and it tells me the disk is not formatted. After making a usb or cd in XP, and putting it in the MAC, it shows up in the OS but not during the boot when holding ALT. I don't use a program that specifically puts the iso on the usb, i open the ISO in a program and then just extract the files to the USB. I'm pretty sure the USB made in the MAC OS is using a RAW format enabling it to boot, but Im not positive.

---

### Post by 122jdh on 2013-01-05
I just searched "linux drivers" on google and I got here:
[http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon) 
and then went here:
[http://cgit.freedesktop.org/xorg/driver/xf86-video-ati](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati)
I selected the newest one and downloaded it, i extracted it but now i have no idea how to install those files.

---

### Post by tlhIngan on 2013-01-05
Find out which driver you have installed.
There is the official ATI driver called fglrx, and there's the open source driver called radeon.
Some hardware works best with fglrx, other hardware works best with the open source driver.
Whichever one you have, try the other one.

---

### Post by 122jdh on 2013-01-05
that doesnt help me as i have no idea how to get those drivers

---

