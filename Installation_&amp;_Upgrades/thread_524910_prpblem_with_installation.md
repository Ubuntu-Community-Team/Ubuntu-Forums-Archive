---
title: "prpblem with installation"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by swaroopg42 on 2007-08-13
i have just now downloaded ubuntu 7.04 i386... its an iso file so mounted it in my virtual drive using deamon tools... when i was done and clicked on my virtual drive it says launching browser, please wait.. and it suddenly disappears and nothing else happens... wats the problem.. please help me.. mine is core 2 duo 1.86 and 1 gb ram.. did i download the wrong iso file.. i downloaded th x86 one... :(

---

### Post by logos34 on 2007-08-13
you should have seen the Kmeleon browser windows open with all the OpenCD programs to choose from (GIMP, FF, GTK+, Abiword etc).  But to install you have to burn it to a CD and boot from it.  Or do you want to install from hard drive?

---

### Post by swaroopg42 on 2007-08-13
cant i just mount that iso to a virtual drive and install it

---

### Post by siralphred on 2007-08-13
yes i dont see why not, but to do a physical installation u might want burn the iso to cd first, will make things a lot easier(assuming u have a burner)

---

### Post by swaroopg42 on 2007-08-13
ya as u say i woul check tat out

---

### Post by logos34 on 2007-08-13
> **swaroopg42 said:**
> cant i just mount that iso to a virtual drive and install it

to install it to the hard drive you will have to resize windows, then  create a root and swap partition.  The easiest wayis to burn a cd and use that.

You can install it to hard drive without partitioning your drive by running it through Wubi.  Basically it just puts it in a folder inside windows and does loopback mounting.  (bit slower performance though)

---

### Post by swaroopg42 on 2007-08-13
again the same thing happened.. i just now burned it into my cd and ran it but same old thing happened.. it stops after that particular message at the beggining.. cant i run this thing in my pc... i am a newbie to linux so help.. is there any other way to install it in my pc...

---

### Post by swaroopg42 on 2007-08-13
help me out please.... :confused:

---

### Post by logos34 on 2007-08-13
you might not have burnt it as an **image**. If you just burn it to cd as data, won't work.

follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Are you booting from the cdrom drive?  If not, enter the Bios at startup (by pressing F2, Esc, delete, etc, whatever yours uses) and set the cdrom as first in the device boot order, ahead of the hard drive.  Now try it.

---

### Post by moose16285 on 2007-08-13
](*,)he's running a core 2 duo... two 32 bit cpus... he needs the ubuntu 64bit d/l then burn to cd...

---

### Post by logos34 on 2007-08-13
swaroopg42, 

you don't need the x86_64 version,  the i386 version will work just fine with your c2d...in fact, although 64-bit support is improving (i.e. w64codecs) and there are viable workarounds for various av formats (i.e. flash--but you have to run the 32-bit FF browser), I'd still go with 32-bit for ease of installation and compatibility.

---

### Post by swaroopg42 on 2007-08-14
thanks logos34.. but now some thing else is happening.. in the boot screen of ubuntu i selected start and install option.. then after some time it gives a list of never ending errors for ever.. i almost waited 3 hours but it is not getting stopped.. it is saying some i/o errors with different numbers.. do not know what to do....

---

### Post by swaroopg42 on 2007-08-14
help me out please.....

---

### Post by logos34 on 2007-08-14
> **swaroopg42 said:**
> help me out please.....

try the text-based alternate cd.  if you still get the buffer i/o errors post back with the specifics.

---

### Post by swaroopg42 on 2007-08-14
where can i find the text based alternate cd....

---

### Post by swaroopg42 on 2007-08-14
or probably how to install ubuntu by text based interface....

---

### Post by merlinus on 2007-08-14
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by swaroopg42 on 2007-08-14
ya i downloaded that alternate cd only.... now should i burn only alternate cd iso to a cd and reboot????

---

### Post by merlinus on 2007-08-14
Yes, and be sure to burn it at 4x and as a disk image, not a data disk.

-merlin

---

### Post by swaroopg42 on 2007-08-14
thanks merlin.. but again a prob...i completed the installation.. when i reboot and start the os it is stopping at main screen where logo comes.. so again rebooted the pc and started it in recovery mode... then there it is stopping at a point
37.388782] kernel panic- not syncing: Fatal exception in interrupt
37.388898] 

and the cursor blinks continously....

help me!!!!!

---

### Post by merlinus on 2007-08-14
Does pressing Ctrl-Alt-F1 get you to a command prompt?

-merlin

---

### Post by swaroopg42 on 2007-08-14
help me    :frown:

---

### Post by swaroopg42 on 2007-08-14
i will check that out...

---

### Post by swaroopg42 on 2007-08-14
no not getting into the command prompt...

---

### Post by merlinus on 2007-08-14
Post complete system specs.

-merlin

---

### Post by swaroopg42 on 2007-08-14
intel core 2 duo 1.86
1 gb ram
160 gb sata hd
20x lite on dvd writer
nvidia 7100 gs graphic card

---

### Post by merlinus on 2007-08-14
The only problem I can imagine is with the driver for your video card, but usually booting into recovery mode will get you to a prompt where you can configure the x-server to use vesa.

Do you get to the opening grub menu?

-merlin

---

### Post by swaroopg42 on 2007-08-14
and already have windows xp sp2 installed...

---

### Post by swaroopg42 on 2007-08-14
ya i do... 4 options ubuntu, ubuntu recovery mode, somr memtest and windows xp

---

### Post by merlinus on 2007-08-14
Shut off the machine and wait a few minutes.  Start again, boot into recovery mode, and if you get an error message, try pressing Ctrl-Alt-F1.

-merlin

---

### Post by swaroopg42 on 2007-08-14
no man nothing is happening.. can somehow reinstalling can help me?????

---

### Post by mrhirsh on 2007-08-14
I tried to install 7.04 from CD that I burned.  It went through a set up, but then gave me an error message re: my graphics driver.  After wasting a day trying to find a Linux graphics driver for my video card (It wouldn't install correctly), I went and downloaded version 6.06, which installed much better . . . but got hung up at step 5 or 6 where it is supposed to let me designate which drive to install on.

---

### Post by merlinus on 2007-08-14
Reinstalling may be a good idea, because if Recovery Mode will not get you to a console (command prompt), then most likely nothing will work.

-merlin

---

### Post by swaroopg42 on 2007-08-14
can re-installing help me out in anyway...

---

### Post by swaroopg42 on 2007-08-14
and how to re install... same procedure a..

---

### Post by merlinus on 2007-08-14
How did you install the first time?

-merlin

---

### Post by swaroopg42 on 2007-08-14
it was using the alternate cd... i partitioned my e drive which was of 40gb into 15 and 25gb... i installed it in 25 gb one....

---

### Post by swaroopg42 on 2007-08-14
or can u direct me to a detailed procedure for re installation where i cannot go wrong...

---

### Post by merlinus on 2007-08-14
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

-merlin

---

### Post by swaroopg42 on 2007-08-14
can system restore in xp fix the problem?????

---

### Post by merlinus on 2007-08-14
xp system restore will let you put its bootloader back in the mbr (master boot record) so you can start up windows, but will definitely not do anything to assist with ubuntu.

-merlin

---

