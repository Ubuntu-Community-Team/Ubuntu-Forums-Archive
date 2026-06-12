---
title: "Failed to start X server, thereby can't start Live session."
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by penge on 2006-07-07
[FONT="Arial"][SIZE="2"]Hi,
Since yesterday I've got my Ubuntu 3CD pack :). For 32bit pc, 64bit pc and Mac.

There is a problem I need to deal with to start my Ubuntu, because of my hardware :(

So let's start. 
I put my **Ubuntu 64bit CD** into cd-drive. Choose the 1st menu choise, just **Start or Install Ubuntu**. After a while, almost 9min omg, (I really don't know, why it took so long to boot) it shows up the red window with error message:  ***[COLOR="Red"]Unable to start X server[/COLOR]***... And it promptly scatter all the text on the screen. Problem with graphics I think so. 
I get the same result, when I try my **Ubuntu 32bit CD**. 
To amaze, all is working fine in VMware (just because of VMware graphics compatibility).

Anyone got any ideas to help me? 
Is there something I can solve with the console after the error message (Failed to start X server) shows up?[/SIZE][/FONT]
--------------------------------
*P4 3GHz, 1GB DDR2, Ati Radeon X800GT, Asus P5ND2 SLI (sound on board).*

---

### Post by Herman on 2006-07-07
Hello, penge, you might find useful information in the following thread:[Dealing with problems with the Xserver]("http://www.ubuntuforums.org/showthread.php?t=187177")
 &#8206;
To give some comfort to people who want to try the command:  sudo dpkg-reconfigure xserver-xorg , I have made a new web-page with some illustrations of the whole process so you can see ahead of time what it will be like and be prepared. For mine all I really needed to know was the brand of my video card, the rest was all auto-detected, so it was really easier than it looks. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p7.html") to see sudo dpkg-reconfigure xserver-xorg illustrated.

Do you mean you have this problem running the 'Desktop' Live/InstallCD from the CD-ROM drive before you even perform the install to hard-disk?
Most people use sudo dpkg-reconfigure xserver-xorg for as soon as they install to hard disk, I am not sure if that will work doing that just for running the live cd. I don't really know what will happen if that's what you mean.

I hope this information will be useful to you, and good luck, Regards, Herman :D

---

### Post by sYs^ on 2006-07-08
I have the same problem when I try to install Dapper on my new PC(details in my sig.). It writes "device not found" or something like this.
I tried the 64bit and the 32bit version too.

[penge]("http://ubuntuforums.org/member.php?u=133857"): seems like we have the same kind of vga :p (There must be the problem)

---

### Post by sYs^ on 2006-07-08
Here's the answer:

[http://ubuntuforums.org/showthread.php?t=190133&highlight=x800gt](http://ubuntuforums.org/showthread.php?t=190133&highlight=x800gt)

---

### Post by Kyuuketsuki on 2006-07-10
> Here's the answer:

[http://ubuntuforums.org/showthread.p...ghlight=x800gt](http://ubuntuforums.org/showthread.p...ghlight=x800gt)

... with a regylar install but how would you make it work with a LiveCD (CD's being non writable)? 

I have a similar system to the guy that started this thread i.e. ASUS P5ND2, Intel Socket 775 3.4GHz CPU, X800GTO PCI-E video etc. 

Kyu

---

### Post by shuflie on 2006-07-10
> **Kyuuketsuki said:**
> ... with a regylar install but how would you make it work with a LiveCD (CD's being non writable)? 

I have a similar system to the guy that started this thread i.e. ASUS P5ND2, Intel Socket 775 3.4GHz CPU, X800GTO PCI-E video etc. 

Kyu

If you read the link you'll see that this is for the live CD. the only problems are that unless you decide to do a proper harddrive installation you will need to go through this process every time you reoot the system and you won't be able to install the fglrx drivers, VESA mode isn't much fun.

---

### Post by sYs^ on 2006-07-11
Hmm, I tried this method and it's still not working when, I try to start X my screen goes black and nothing happens. :\

---

### Post by foots2015 on 2006-07-11
I have the same problem. it was suggested to me to use the alternate install. it worked... to a point. It started the install process but i couldnt get past the drive partitioning part. Appearently Ubuntu doesnt read SATA II drives. So im screwed in that aspect. I guess my next thing is to try Mepis or Suse untill the next ubuntu 6.10 comes out!

---

### Post by sYs^ on 2006-07-12
> **foots2015 said:**
> I have the same problem. it was suggested to me to use the alternate install. it worked... to a point. It started the install process but i couldnt get past the drive partitioning part. Appearently Ubuntu doesnt read SATA II drives. So im screwed in that aspect. I guess my next thing is to try Mepis or Suse untill the next ubuntu 6.10 comes out!

Try this:

> **/thomas said:**
> update: i did get the x800gt to work with ubuntu: i'm not 100% sure what it was any more, since i stayed up all night until i fixed it. 

after x server crashes, *sudo nano /etc/X11/xorg.conf* and then change the *driver ati* to *driver radeon* as well as delete all resolutions (for 24 bit) except 640x480. that way you can continue with ubuntu. 

the screen is unbearably small, but it is possible to go through with the installer from the desktop. at some point i went to synaptic and installed the *fglrx* drivers. after having installed ubuntu, i changed the driver from *radeon* to *fglrx* and added my display's native resolution to the list.

sorry about the confusing explanation, but i was extremely tired when i did this.

now my dilemma is: how do i get my dual displays to work as an extended desktop? at the moment they are in clone mode/mirroring mode. i read about some xinerama but it seems **so** complicated...

This worked for me.

---

