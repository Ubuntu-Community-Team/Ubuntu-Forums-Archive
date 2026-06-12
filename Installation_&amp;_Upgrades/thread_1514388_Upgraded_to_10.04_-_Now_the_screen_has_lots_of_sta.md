---
title: "Upgraded to 10.04 - Now the screen has lots of static lines"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by jmaridon on 2010-06-20
I have been using Ubuntu on and off for the past couple of years. I just upgraded to 10.04 from 9.1. Everything related to the screen and graphic worked perfectly in 9.1. I am now getting tons of what looks like static lines on the screen. Several things effect the static, including mouse clicks and moving the mouse around. Sometimes I can clear the static by clicking the header or resizing the window, but that does not fix the static at the top and bottom of the screen, outside an active window. (screenshot1) When I type in a text field, the field usually goes to static. I looked at some videos on youtube, they were choppy and blinky. I tried to open FlightGear, but just got a screen full of garbage. (screenshot2) I tried to change the screen resolution, but I got the same thing. I switched from the DVI port to the HDMI port, with the same result. I don't know what else to change.

I have a feeling that the issue is related to video drivers. I am running an MSI 785GM-E51 MB with onboard ATI Radeon HD4200 graphic subsystem. I have always used whatever video drivers that came with the install with no problem in the past.

I am at a loss. Any ideas?

---

### Post by PSyMastR on 2010-06-20
Looks to me like you need to reinstall your graphics driver. Were you using amd/ati's binary driver?

---

### Post by jmaridon on 2010-06-24
> **PSyMastR said:**
> Looks to me like you need to reinstall your graphics driver. Were you using amd/ati's binary driver?

Yes, I WAS using the ATI/AMD proprietary FGLRX graphics driver. I believe that the graphics driver is definitely in the middle of the problem. Reinstalling the driver helped at first, but only for a short time, then the problem started again. Another thing that fixed it was reconfiguring the graphics mode to disable that driver, but that was only a short term fix as well. The only thing that seems to be working somewhat consistently is "low graphics mode," which is not very cool to look at, nor does it do video very well. And through everything that I have tried so far, Flightgear doesn't work at all.

In the meantime, my wife has expressed a lack of patience for my complaining and insists that the fix lies at Costco in the form of Windows 7.

---

### Post by sudeepkghosh on 2010-06-25
I am having the same problem. I am using AMD(Dell). I am getting static line screen. Is there a solution? Please help.

---

### Post by Naggobot on 2010-06-25
Hmmm

I have a suspicion that proprietary driver does not work with lucid. It might be worth Googling. If this is the case then changing to open source driver might help. (Whit quick Googling it seems that there is a lot of models that are not supported [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4))

Also I have had problems with hibernate and those problems are caused by kernel graphics mode setting. This is something that has changed since Karmic. Modesetting can be moved away from kernel adding a command line option "nomodeset" to grub. Check grub2 community help if you want to try it. It's a long shot but it might be the cause.

Edit
Also check: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543045)
which might be related and there is a possible fix available, see post #18.

---

### Post by sudeepkghosh on 2010-06-25
So, what step should I take ? Cannot load GNOME, but can get into shell.

What's the best thing to do to make the computer up and running quickly ?

---

### Post by Naggobot on 2010-06-25
Sorry I am not a command line wizard :p. I know that from command line you can use synaptic package manager to remove and install packages. Also I know that the application that manages (to at least some extent) the proprietary drivers is called jockey. 

man pages for apt which is used to add / remove packages.

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

about removing proprietary display drivers and installing the open source driver

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

about editing grub to set nomodeset parameter

[http://bennybeta.blogspot.com/2009/12/ubuntu-910-on-dell-studio-1555.html](http://bennybeta.blogspot.com/2009/12/ubuntu-910-on-dell-studio-1555.html)

Unfortunatelly this does not list what application you can use from command line to edit. [This]("http://fixunix.com/ubuntu/509025-easy-terminal-text-editor.html") seems to refer to vi and nano as command line editors.

About using experimental kernel: You need to download architecture dependent files from 
[http://people.canonical.com/~sconklin/radeon_flicker/]("http://people.canonical.com/%7Esconklin/radeon_flicker/") and then you need to use [dpkg]("http://unixhelp.ed.ac.uk/CGI/man-cgi?dpkg") to install the packages. 

Now I must emphasize that there is no guarantee that none of these offer any remedy for your particular hardware / problem. I can only guess that some of them might be of use. Unfortunately I am not so adept with Ubuntu my self that I could walk you through these step by step. 

If I were in your position I would first try adding the nomodeset parameter to grub to see if it corrects the problem. This is very easy to try and even I am able to do it with gedit.In your case it would go as follows

1. Select your text editor to see how you can save the file
2. Login to Ubuntu command line
3. run command

```
sudo vi /etc/default/grub
```or 

```
sudo nano /etc/default/grub
```depending your preference of vi or nano editor. I do not know how to save with those editors, you need to find out. 

then edit line where it says

```
 GRUB_CMDLINE_LINUX = ""
```to say

```
 GRUB_CMDLINE_LINUX = "nomodeset"
```save file

type

```
sudo update-grub
```boot to see if the problem was corrected. If not then remove the "nomodeset" from commandline. Nomodeset tells the linux kernel not to set display resolution etc while booting, instead it is done by X11. Visually you see the difference when the resolution of the splash screen is lower when booting and some flickerin occures while the X11 sets the resolution. 

If nomodeset does not work then I would try removing the proprietary driver (if you are using one) 

If that does not help then I would try downloading and installing the experimental kernel since of the three trying this would present the most problems for me. Installing the kernel using dpkg is breeze once you figure out how to get it to your computer using commandline. I probably would try using USB stick but I have no idea how to mount the stick from commandline and I do not know if it is required. 

Also you can try to boot to the "rescue mode" to get graphical low resolution X it might help you some extent while working out the problem. If you do not have menu visible during boot up I think you can bring the menu up by pressing shift while booting the computer. (seem so, see [this)]("https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202"). 

Sorry I can not help you more in detail, hopefully this is of some use to help you while working out the problem. Good luck. Also if you have some specific questions I recommend 
asking from the forum since someone else might be able to answer.

also as last note I recommend reading a bit in to the [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543045") report. If you suffer from this particular bug then it it might be worth finding out about adding the pll_quirk what ever that is. Post number #2 explains on how to try that fix. It seems straight forward.

---

