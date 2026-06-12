---
title: "Nvidia driver installation problem - Lucid 10.04"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by TotalLinux on 2011-10-05
Hello all,
First post from me on the forum. Excuse the following 'War and Peace' style epic but I want to get as much relevant info across as possible in one go.

Came to Ubuntu at the start of last year, installation was fine as all hardware was a few years old and so drivers were not an issue.
Now the old PC is no more and all hardware for the new box (64 bit) was straight out of the box last week. I am still running Lucid 10.04 on the new system (primarily due to the LTS)
However, despite reading numerous threads I am still unable to get the Nvidia drivers installed for graphics card GeForce GTX550 Ti. Below is a (non-exhaustive) list of tasks I have attempted so far:

Installed all of the Nvidia packages via Synaptic Package Manager (the closest I got to getting this working was 'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file')
sudo nvidia-xconfig does not seem to have done anything to assist with the issue.
Various commands have been added / removed from the xorf.conf file without success. Now reverted back to the basic settings in the failsafe version of the file.

I have followed a number of instructions (to the letter) on various threads but the oddest issue I have encountered is when I type either
sudo /etc/init.d/gdm stop
or the shorter command sudo gdm-stop
I am left looking at a completely blank screen. I was under the impression that it should take me to a CLI (or have I completely misunderstood the commands in a noobish way?)

The above has also stymied any attempt at installing the driver package which I downloaded direct from the Nvidia site (NVIDIA-Linux-x86_64-280.13.run) as I've been unable to kill the X server to be able to type in the instructions.

I originally started on this task on Saturday evening (no sniggering at the back please). By Monday I had installed and uninstalled so many things that the system was showing signs of instability so I reformatted the drive and reinstalled from scratch. This is something I would happily do again if it means a clean install of the graphics drivers.

At present the display is stuck at 800x600 and reporting a refresh rate of only 51 Hz. Needless to say I'm unable to look at it for more than 30 mins without getting a blinding headache.

Many thanks to all in advance for any assistance.

Yours (while I go and get another couple of paracetamol)
TotalLinux

---

### Post by MAFoElffen on 2011-10-05
> **TotalLinux said:**
> Hello all,
First post from me on the forum. Excuse the following 'War and Peace' style epic but I want to get as much relevant info across as possible in one go.

Came to Ubuntu at the start of last year, installation was fine as all hardware was a few years old and so drivers were not an issue.
Now the old PC is no more and all hardware for the new box (64 bit) was straight out of the box last week. I am still running Lucid 10.04 on the new system (primarily due to the LTS)
However, despite reading numerous threads I am still unable to get the Nvidia drivers installed for graphics card GeForce GTX550 Ti. Below is a (non-exhaustive) list of tasks I have attempted so far:

Installed all of the Nvidia packages via Synaptic Package Manager (the closest I got to getting this working was 'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file')
sudo nvidia-xconfig does not seem to have done anything to assist with the issue.
Various commands have been added / removed from the xorf.conf file without success. Now reverted back to the basic settings in the failsafe version of the file.

I have followed a number of instructions (to the letter) on various threads but the oddest issue I have encountered is when I type either
sudo /etc/init.d/gdm stop
or the shorter command sudo gdm-stop
I am left looking at a completely blank screen. I was under the impression that it should take me to a CLI (or have I completely misunderstood the commands in a noobish way?)

The above has also stymied any attempt at installing the driver package which I downloaded direct from the Nvidia site (NVIDIA-Linux-x86_64-280.13.run) as I've been unable to kill the X server to be able to type in the instructions.

I originally started on this task on Saturday evening (no sniggering at the back please). By Monday I had installed and uninstalled so many things that the system was showing signs of instability so I reformatted the drive and reinstalled from scratch. This is something I would happily do again if it means a clean install of the graphics drivers.

At present the display is stuck at 800x600 and reporting a refresh rate of only 51 Hz. Needless to say I'm unable to look at it for more than 30 mins without getting a blinding headache.

Many thanks to all in advance for any assistance.

Yours (while I go and get another couple of paracetamol)
TotalLinux
Welcome to Ubuntu Forums!

Is Ubuntu the only OS on your system?  

Please download the nVidia Driver from NVida again...  Version 280.13 had problems with Ubunti and Unity.  Their devs say that v285.0509  is supposed to fix those problems (we'll see).

Boot and after the BIOS boots, press the shift key repeatedly. The Grub Menu should come up.  Press the "e" key > that should put it into an edit mode.  Arrow down to the lkerenl boo line - starts with "linux."  Arrow right to where it says "quiet splash".  Replace that text with "--verbode text" > Press <cntrl><x> to boot with those options.  That will boot into a TTY Text Console.  Log ing.

Install your driver using these instructions: Post  			#[**280**]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")

---

### Post by jawilljr on 2011-10-05
For a newbie x-swat PPA is the only way to install nVidia drivers.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current libvdapu1

```

Then reboot.

It can't get any easier than that...unless of-course you have an optimus system.

Jerry

---

### Post by MAFoElffen on 2011-10-05
> **jawilljr said:**
> For a newbie x-swat PPA is the only way to install nVidia drivers.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current libvdapu1

```Then reboot.

It can't get any easier than that...unless of-course you have an optimus system.

Jerry
Jerry, 

Xswat does have this newest driver yet.  Not sure it's even in Edgers yet...) Only out 2 days now.  The new before that, 280.13, has confirmed bugs at both ubuntu and nVvidia that is confirmmed with Unity, Comoiz and NVidia driver..  NVidia "says" this "now" newest is supposed to fix those.

That's the why for that.

MAFoElffen.

---

### Post by jawilljr on 2011-10-05
> **MAFoElffen said:**
> Jerry, 

Xswat does have this newest driver yet.  Not sure it's even in Edgers yet...) Only out 2 days now.  The new before that, 280.13, has confirmed bugs at both ubuntu and nVvidia that is confirmmed with Unity, Compoiz and NVidia.  NVidia "says" this "now" newest is supposed to fix those.

That's the why for that.

MAFoElffen.

Geez.. the main bugs is with the latest xorg...1.11.  The OP is on 10.04, which does not use unity. So x-swat will work. If it didn't then why am I posting it using 10.04 and x-swat?

Jerry

P.S.  Compiz works just fine with 10.04 and 280.13.

---

### Post by MAFoElffen on 2011-10-06
> **jawilljr said:**
> Geez.. the main bugs is with the latest xorg...1.11.  The OP is on 10.04, which does not use unity. So x-swat will work. If it didn't then why am I posting it using 10.04 and x-swat?

Jerry

P.S.  Compiz works just fine with 10.04 and 280.13.
Yes and the OP "has" 10.04 and 280.13. installed now.  Was just a suggestion,,, I can think of 5 other ways the OP could go and that would all work.  

There "are" other ways- I test edgers drivers, but I wouldn't recommend that to the average user. I recommend based on what they have experience on and what will cause less problems down the road.  If the OP installs the Xswat PPA (which I use on 2 of my boxes here), that PPA will have to be removed and purged (suggested by the Xswat team) if he wants to do a distribution upgrade right?

He already installed the 280.13 nVidia binaries.  He has experience with that already.  The correct thing, which would burn up more of his time, would be for me to ask him to post his nvidia-installer log and xorg log, to confirm that it failed to compile, build or load, because the previous older driver files are still present. That is what I suspect from what he said he did and what he is gtting as a problem.  

He will need to remove the present driver and the other instances of driver files, ensure he has all the basic build file resources present and reinstall the driver. (Some problems with even the .deb driver install packages is those resource files being missing.) 

The easiest way "would be" just to install nvidia-current, but he would still have to unistall and remove the previous driver files before that.  Even if ihe did nstall the Xswat PPA and used the drivers from there... He would have to ensure he removed those other driver files first... As those conflicting files "are" what the suspect OP's problem is.

Sidenote- I have Xorg.xserver 1.11 (running successfully) on 7 Boxes here for testing... Ubuntu (Stable) is still xorg-xserver v1.10, so that is not a consideration in this.  A segfault problem with compiz and nvidia driver 280.13 is... which 10.04 uses compiz.  NVidia and Launchpad agree that it doesn't affect a "majority" of user's, but If this OP is going to have to reinstall the driver anyway, he may as well ensure he's not in that minority, right?

I try not to take offense-  I have a twisted sense of humor:
> ***[SIZE=4][COLOR=Teal]Don't worry, You'll Be Fine;  I Saw It Work In A Cartoon Once...[/COLOR][/SIZE]***

---

### Post by TotalLinux on 2011-10-07
MAFoElffen & jawilljr - many many thanks for your help. Much appreciated. Now have a startlingly good display and no more headaches.

Just to answer a couple of things, yes Ubuntu 10.04 is the only OS on my system (same as with now discarded box). I resisted for quite some time but had to install WINE eventually (will do the same again on this box once I've got the rest of the config just how I want it).
Downloaded the 285.05.09 driver and the rest was relatively simple. The one, crucial, piece of information I was missing from all other pages I had looked at prior to seeking assistance was 'Boot and after the BIOS boots, press the shift key repeatedly'. Without your prompt I'd have been stuck on 800x600 until ...

Cheers chaps. Multiple thumbs up until I start to suffer from RSI :D

Regards,
TotalLinux

---

