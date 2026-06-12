---
title: "3ddesktop"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Soldier174 on 2007-01-06
I am having this problem installing or making the 3ddesktop work...I don't know what to do after the installation..I read a few things on the forums and some people said to do the command..3ddesk --acquire...But all I get is this error...

```
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.

Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

```

I also tried 3ddeskd...I get this other error...
```
Daemon started.  Run 3ddesk to activate.
soldier@soldier-desktop:~$ 3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
```

What am I doing wrong?

By the way...I have Ubuntu 6.06 LTS with a ATI RADEON 9250 256MB...I installed all the drivers I need for that card before doing any acceleration...I already have the 3d acceleration...I just want to install the 3ddesktop...Please help...Thank you.

---

### Post by bulldog on 2007-01-06
I have not experience with the ATI graphics,but it appears to me your card isn't properly configured.

---

### Post by kvonb on 2007-01-06
Hello,

The ATI can be a real pain to get working properly, it can also be the asiest card!

Your card **will** run Beryl which is the better desktop, 3dDesktop is an older fake 3d thing.  It has it's charm, but is really deprecated by Beryl.

Have a go at my tutorial here:

[http://ubuntuforums.org/showthread.php?t=301364](http://ubuntuforums.org/showthread.php?t=301364)

If you have the 6.10 CD, it is very easy, if you are using 6.06 (Dapper) then you are in for a lot of problems.

You don't have to do this on the CD, you can do it on your running copy, but this will allow you to try it before making any changes to your system.

If you don't want Beryl just install 3dDesktop from Synaptic once the CD has booted to the desktop, it should work straight away.

Regards, KEv :)

---

### Post by Soldier174 on 2007-01-06
I have the Ubuntu 6.06 LTS....So I think it might be a problem...Soo....Are there any other 3ddesktop software or anything our there for 6.06?I need the 3d desktop....I already installed the 3d acceleration/ ATI Drivers for my card...Just need the desktop..Thanks again for replying.](*,) 

Just to add something....I don't get direct rendering...Everytime I see that command..Or error w/e...I see no.

---

### Post by kvonb on 2007-01-06
OK, here is a script that I wrote for downloading and installing the official 8.27.10 driver from ATI.  Just download it, unpack it, and run it from a terminal like so:

```
./ati-installv3-1.sh
```

It will download and install everything it needs and also does a few little tricks to get direct rendering and 3d screensavers working :).

This worked well on my computer when I had Dapper, hopefully it will work on yours too.

Also note that the last driver version to support the 92xx series of cards is 8.28.10 (from memory), and the one I install was the most compatible (8.27.10), as the 8.28 series had issues with google earth and a few other things.

Please also note that I take no responsibility if this script messes up your system!  There is nothing malicious in it, and it works well for me but there is always a chance that something MAY go amiss!  So please read through it first to get an idea of what it will do.

The script makes a backup copy of all the files it messes with in the folder ~/ATI-8-27-10-install, so all you have to do is rename the files and copy them back to their original locations IF you have any problems.  However your old ATI driver will need to be re-installed.

You can download my script from here:
[http://wamrfixit.homeip.net:8000/dapper/dapper-modifications/dapper-ati-installv3-1.sh.tar.gz](http://wamrfixit.homeip.net:8000/dapper/dapper-modifications/dapper-ati-installv3-1.sh.tar.gz)

Also all the files you will need for the script can be found on my server if they are not available for download, all you have to do is copy them into the ~/ATI-8-27-10-install folder and re-run the script, it will find them and use them instead of trying to download them. There might also be other useful stuff on my server here:

[http://wamrfixit.homeip.net:8000/dapper/dapper-modifications/](http://wamrfixit.homeip.net:8000/dapper/dapper-modifications/)


Good luck, Kev :)

---

### Post by Soldier174 on 2007-01-07
Not to mention....I want to install Looking Glass on my Ubuntu Dapper Drake...which is 6.06 LTS...I'm trying to look for good tutorials....but it seems like i can't find a good one....Good help will be nice...Thanks again for responding.:D

---

### Post by Zyphrexi on 2007-01-07
hey I never used 3dDesktop, you still trying to use that?

use beryl instead. more support, just search around.

---

### Post by kvonb on 2007-01-07
> **Soldier174 said:**
> Not to mention....I want to install Looking Glass on my Ubuntu Dapper Drake...which is 6.06 LTS...I'm trying to look for good tutorials....but it seems like i can't find a good one....Good help will be nice...Thanks again for responding.:D

Never heard of "Looking Glass", sorry :(

Let us know how the driver script goes please :).

Oh, I suggest re-installing the driver because you don't have direct rendering working, just to clarify :).

---

### Post by Soldier174 on 2007-01-07
My direct rendering says yes now....Now..is there a good tutorial out there for ubuntu dapper installing Beryl 3d desktop?Because i really want the desktop..Also...the drivers worked perfectly(i mean your script worked perfectly with my graphics card).

---

### Post by DarkN00b on 2007-01-07
For a good set of instructions on how to install Beryl, check out the [Beryl Wiki]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu"). Choose the install you want to do and get started.

Also, Beryl is easier to install on Edgy Eft (6.10) because it comes with AIGLX already installed. With Dapper you have to install AIGLX OR XGL seperately.

---

### Post by Soldier174 on 2007-01-07
I installed ubuntu 6.10 edgy and i can't seem to install the right drivers....I can't go in the x server with fglrx driver...i have to use ati driver to be able to go onto the desktop...Please help.

---

### Post by Soldier174 on 2007-01-07
Just to add something...I can't seem to use or know how to install the aiglx drivers...i tried everything...but it doesnt work...at the moment i have to use the vesa drivers since i cant use the fglrx drivers nor the aiglx(which is not in one of the choices)...Please help..Thanks.

---

### Post by DarkN00b on 2007-01-07
Yikes, dude. I wasn't asking you to install Edgy just to get eye candy. :) 

I have no idea how to install the drivers for your ATI card. I found a Howto [HERE]("http://www.ubuntuforums.org/showthread.php?t=290841&highlight=ati+beryl+edgy+how+to"). I don't know how much that'll help you but it should give you a place to start and you can always ask for help if you need it.

---

### Post by Zyphrexi on 2007-01-07
open up synaptic

System -> Administration -> Synaptic package manager

or just type in terminal

sudo synaptic
then type in your root pass.

in the window menu, click settings then repositories

make it look like these pictures included

hit close, click reload, and install your drivers =)

now you'll want the linux-restricted-modules for whatever your kernel version is. You can check this out by typing uname -r in a terminal.

I got a AMD Athlon XP processor, so I use linux-restricted-modules generic.
installing linux-restricted-modules-386 is probably your best bet since it applies to everything afaik.

---

### Post by kvonb on 2007-01-08
DO NOT TRY TO INSTALL ATI DRIVER OR YOU WILL END UP WITH LOTS OF PROBLEMS!

If you installed Edgy, then you don't have to do **anything** apart from installing Beryl from the repositories, the best driver is installed by default.

Have another look at my guide and follow it to the letter and Beryl will be installed and working.

Regards, Kev :)

---

### Post by Zyphrexi on 2007-01-08
eh? so I'm wrong?

---

### Post by kvonb on 2007-01-08
> **Zyphrexi said:**
> eh? so I'm wrong?

No, you're not wrong, it's just that installing the ATI driver unnecessarily complicates things, the open source driver (from my experience) is the simplest and easiest method.  The problem comes with "direct rendering", if he loses that (which happens frequently with the ATI driver), then he's going to be in a whole lot of trouble.  To get it working he will have to mess about with GLX and other nasty stuff.

Sorry if I sounded pushy, I didn't mean to :)

---

### Post by Zyphrexi on 2007-01-08
eh no prob, I don't use ATI so I'm not familiar with the specifics, but I know the linux-restricted-modules pacakge has a lot of useful drivers. In fact I wish it was installed by default, unfortunately there's a reason it's 'restricted'.

heh I wonder what kind of bind I'd be in if I did have an ATI card, since my wifi card has an atheros chipset I need that package. 

Besides if he did run into trouble he'd have us oldbies to guide him along right? 

OP do what kvonb suggests, and if later you decide to do other stuff, we can jump that hurdle when we get to it.

---

