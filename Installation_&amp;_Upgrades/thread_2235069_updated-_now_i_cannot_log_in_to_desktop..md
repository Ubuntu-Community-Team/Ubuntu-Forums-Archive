---
title: "updated- now i cannot log in to desktop."
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by steve_andrews on 2014-07-18
hello 

I clicked on an ubuntu update from update manager, but now i cannot boot to my desktop. 
(i am at present on a live cd to talk to you guys) 

when i boot, i am taken to a command line. 

i tried to reinstall nvidia drivers, but no luck, i may not have done it right though i did try to remove them and reinstall but i do nto know if i chose the right ones : ?

with ' startx '

i get messages like this:

"fatal server error
no screens found

unable to connect to  xserver no such file directory.
server error"

when i try this
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bckup
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

It says no such file or directory. there does not seem to be an xorg.conf or .failsafe file availible either

I have tried boot with failsafe graphics from the grub menu, but no joy. 

and i have tried previous ubuntu versions from the grub menu too but they all take me to the command line also. so maybe its not ubuntu , i think it is a display driver issue.

the live cd works fine, so my computer is o.k

i have files on my desktop and in my home folder that i really  need to keep.

please can someone help me, i have no idea what has happened.


 Thank you : )

i beleive it is now ubuntu 12.04.4, I was using gnome desktop (not unity)

quad p4 q6600
1066mhz 2 gig
asus p5q delux 
7200 gs geforce graphics ( comand line 'lspci'  this card is displayed as a vga compatible controller )

---

### Post by yancek on 2014-07-18
What did you update?  Was this a general 'updates available' thing which installed numerous updates?

> 
when i boot, i am taken to a command line. 

Is that a login prompt?  not a grub prompt (grub>).  Have you tried logging in if a login prompt?

> and i have tried previous ubuntu versions from the grub menu too but  they all take me to the command line also. so maybe its not ubuntu 

Do you mean you have earlier releases of Ubuntu or just older kernels?  Have you tried mounting whichevery partition you had your system and user files on?

---

### Post by steve_andrews on 2014-07-18
> **yancek said:**
> What did you update?  Was this a general 'updates available' thing which installed numerous updates?



Is that a login prompt?  not a grub prompt (grub>).  Have you tried logging in if a login prompt?



Do you mean you have earlier releases of Ubuntu or just older kernels?  Have you tried mounting whichevery partition you had your system and user files on?

hello

it was an offical update.from the update manager. 

when i log in now, instead of a login to desktop option like before, i am taken to a black screen login prompt instead , i login but then i am left with a comand line with black backgorund, with my user name and a $ at the end. i can type stuff in like 'lspci' and it shows my graphics card model.

i have the option of earlier versions at the grub2 menu, i think they are just older kernels, but i have had no luck getting to my desktop with any of them i am sent to the black screen with command prompt .

so am unsure what to do, i am not wise on all this ubuntu command stuff. but i think my graphics drivers need cleaning out and reinstalling, maybe : /

---

### Post by Bashing-om on 2014-07-18
steve_andrews; Hi !

Graphics driver possible & most likely if your were running a proprietary graphics driver and the kernel was updated.

Might try and boot from a recovery kernel.
Grub boot menu -> any kernel marked (recovery) -> resume normal boot.

From the recovery console can you get to your desk top ? Yes, then we can advise on methods to (re-)install a graphics driver.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by steve_andrews on 2014-07-18
> **Bashing-om said:**
> steve_andrews; Hi !

Graphics driver possible & most likely if your were running a proprietary graphics driver and the kernel was updated.

Might try and boot from a recovery kernel.
Grub boot menu -> any kernel marked (recovery) -> resume normal boot.

From the recovery console can you get to your desk top ? Yes, then we can advise on methods to (re-)install a graphics driver.[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


hello thanks for your reply.  if i choose a recovery mode option > resume normal boot , on any of the kernels, i am taken again to the black screen username-system-product-name login , when i log in, it again becomes a command line. ; /

---

### Post by Bashing-om on 2014-07-18
steve_andrews; Well;

So much for that thought of a graphics driver .

OK, as you are running Gnome-desktop, what results from terminal command:
```

sudo service gdm start

```

Maybe then get a hint of what is going on.

[INDENT][INDENT][INDENT]a poke in the dark
[/INDENT][/INDENT][/INDENT]

---

### Post by steve_andrews on 2014-07-18
> **Bashing-om said:**
> steve_andrews; Well;

So much for that thought of a graphics driver .

OK, as you are running Gnome-desktop, what results from terminal command:
```

sudo service gdm start

```

Maybe then get a hint of what is going on.
[INDENT][INDENT][INDENT]a poke in the dark
[/INDENT]
[/INDENT]
[/INDENT]



hello

it says "start: Job is already running: gdm"


thanks

---

### Post by Bashing-om on 2014-07-18
steve_andrews; Not OK, but;

I have another thought along the same lines;

Boot to the grub boot menu, 'e' key for edit mode; in the resulting boot parameters screen arrow down and across to the terms "quiet splash" and replace those terms with the term "text" - without the quotes. key combo ctl+x to continue the boot process to a text terminal (TTY1).
Log in here ( username and password - no response to screen when password is entered).

Now from this terminal try and start the GUI: Again with terminal command:
```

sudo service gdm start

```

Again we are looking for errors generated to give a hint of where the problem lies.

Right now we do not know 
[INDENT][INDENT][INDENT]could be this, could be that
[/INDENT][/INDENT][/INDENT]

---

### Post by steve_andrews on 2014-07-18
> **Bashing-om said:**
> steve_andrews; Not OK, but;

I have another thought along the same lines;

Boot to the grub boot menu, 'e' key for edit mode; in the resulting boot parameters screen arrow down and across to the terms "quiet splash" and replace those terms with the term "text" - without the quotes. key combo ctl+x to continue the boot process to a text terminal (TTY1).
Log in here ( username and password - no response to screen when password is entered).

Now from this terminal try and start the GUI: Again with terminal command:
```

sudo service gdm start

```

Again we are looking for errors generated to give a hint of where the problem lies.

Right now we do not know [INDENT][INDENT][INDENT]could be this, could be that
[/INDENT]
[/INDENT]
[/INDENT]


hello, i beleive i did everything you said; but again it says:
start: job is already running: gdm

thanks

---

### Post by steve_andrews on 2014-07-18
hi, also to add

when i type startx from here , i get the messages FATAL: Errror inserting nvidia_304 (lib/modules/3.12.0-32-generic/updates/kdms/nvidia_304.ko) : unknown symbol in module, or unknown parameter (see dmesg)

fatal server error
no screens found 


check thte log file /var/log/Xorg.0.log for additiional info

unable to connect to x server no such file or directory

---

### Post by Bashing-om on 2014-07-18
steve_andrews; Well !

I am surprised that GDM is running when no GUI has been yet started .. but, I do not run Gnome and can not test.

Think at this point one might take a look at the log files and see if there are any clues. Don't forget about .xsession-errors in your /home directory.

When I get the opportunity to re-boot my system I will check on another thought.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by steve_andrews on 2014-07-18
> **Bashing-om said:**
> steve_andrews; Well !

I am surprised that GDM is running when no GUI has been yet started .. but, I do not run Gnome and can not test.

Think at this point one might take a look at the log files and see if there are any clues. Don't forget about .xsession-errors in your /home directory.

When I get the opportunity to re-boot my system I will check on another thought.[INDENT][INDENT]cause and effect
[/INDENT]
[/INDENT]



Hi Bashing-om.

my ubuntu is working  again , pheeew.  : ) 

 i typed in teh command line:

sudo apt-get install --reinstall dkms nvidia-current-updates 
 
startx 

i am sure i tried that before , but second time lucky.

after which it booted into my desktop , with unity, so i logged back in with gnome no effects and all is back as it was, i believe.

thank you for your support, without your help i would have likely have had to use the live cd so to access and copy all my files out my home folder onto a back up and reinstalled everything, but i have other OS's in a triple boot so that would not have been fun to reset at all. 

so thank you again for keeping my hopes up and your advice too. 

have a nice summer : )

---

### Post by Bashing-om on 2014-07-18
steve_andrews; Great !

You do good work.

again, just goes to show
[INDENT][INDENT][INDENT]try'n pays off
[/INDENT][/INDENT][/INDENT]

---

