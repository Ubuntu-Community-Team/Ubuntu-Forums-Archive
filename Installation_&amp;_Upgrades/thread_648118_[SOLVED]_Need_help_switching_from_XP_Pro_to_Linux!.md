---
title: "[SOLVED] Need help switching from XP Pro to Linux!!"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by SoftWhip on 2007-12-23
I have recently downloaded and installed Ubuntu (current version) on my IBM ThinkPad T20 laptop. I was very impressed by the results, and would like to use the Ubuntu Studio version full time, as I will mainly be using it for artwork production.

My question is this, how do I completely remove XP Pro from the laptop and install Ubuntu Studio instead? I don't want to partition my hard drive as I fear it hasn't enough space to have both on at the same time, plus I'm fed up with Microsoft!! 

Any help at all would be much appreciated. Thanking you in advance, David Struve (frustrated XP Pro user!).

---

### Post by njparton on 2007-12-23
Backup any data you want to migrate to a CD or DVD, and then when installing, at the partitioning stage you'll be able to delete your windows partitions and create linux partitions.  It shouldn't be more difficult than that.

---

### Post by SoftWhip on 2007-12-23
Sorry to be a complete noob on this, but which data files should I need to backup? I've already deleted all my personal files and any programs installed. Also, will the downloadable disk come with everything I need, such as hardware drivers? I want to completely wipe XP from the laptop, and am worried about it failing on me!

Thanks and sorry again!  Dave.

---

### Post by SoftWhip on 2007-12-23
Okay, I just read the thread 'Missing Auto Partition Option in Install ' and followed the links provided for installing Ubuntu. I now understand what to do! Load the CD, click the 'Install' icon and choose the second option. This will delete windows and use the whole Hard Drive for Ubuntu....this is correct, yes?

Thank you for your valuable information **njparton**!!

I will be switching to Linux today!! Yay!!

---

### Post by Sabar on 2007-12-23
Yep that should install just Ubuntu on your laptop.

---

### Post by SoftWhip on 2007-12-23
Cheers **Sabar**. I am currently downloading the boot CD for Ubuntu Studio, and will be using it exclusively from now on! 
Can't believe what an absolute fool I've been! The answers were staring me in the face the whole time, I just couldn't see them!

Thanks to all for your assistance!
Dave

---

### Post by DustyRider on 2007-12-23
> **SoftWhip said:**
> Cheers **Sabar**. I am currently downloading the boot CD for Ubuntu Studio, and will be using it exclusively from now on! 
Can't believe what an absolute fool I've been! The answers were staring me in the face the whole time, I just couldn't see them!

Thanks to all for your assistance!
Dave
... there is a learning curve to using Linux:), but once up and running, you'll never go back to the dark side young Luke:)

---

### Post by SoftWhip on 2007-12-23
I've installed Ubuntu Studio on my laptop, and chosen to use the whole hard drive for it. Everything has gone well until the reboot, I input the username and password I chose, now I have a black screen with the following line command;

david@ubuntuhome:"$

What should I do now? I thought it was going to boot up and show the GUI!

Please help me (again!).
Dave

---

### Post by njparton on 2007-12-23
I think that's still at alpha (?) so try ubuntu desktop instead and just add the programs you need later :)

---

### Post by SoftWhip on 2007-12-23
How do I get to the Ubuntu Desktop?
This is the first reboot after installation.
Cheers, Dave.

---

### Post by cbtengr on 2007-12-23
njparton is referring to a different version of Ubuntu, the Desktop version.  I believe the Studio version is aimed at video & gaphics editing.  He's suggesting that you reinstall the Desktop version, available here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

I'm in the process of making the same switch.  As a test, I've been running Ubuntu Gutsy on an 8 year old Dell laptop & I'm very impressed.

GH

---

### Post by SoftWhip on 2007-12-23
Thank you! I will install the regular version of Ubuntu. I wonder why Ubuntu Studio failed to install properly?

Thanks again to everyone who gave me advice, it's helped alot!!
You guys rock!! :guitar:

---

### Post by Sabar on 2007-12-23
I can honestly say I was no expert on windows when I started to make the switch to Linux. and to be honest I don't know much about Linux either. Just look at some of the posts I have made. 

But fortunately with allot of help from Google and allot more help from really nice people here on the forums, I am getting kinda the hang of things. Kinda. 

Good luck 
Sabar

---

### Post by silviur on 2007-12-23
Softwhip, another option is to install a Ubuntu version, and after the installation you can install Ubuntu studio, by opening Terminal and typing:

```
sudo apt-get install ubuntustudio-video
sudo apt-get install ubuntustudio-audio
sudo apt-get install ubuntustudio-graphics
```

These commands will install the software in your Ubuntu installation.
If you want to use the Studio theme, you can

```
sudo apt-get install ubuntustudio-theme
```

This way you elude the apparent problems of installing UbuntuStudio from scratch.

Good luck!

---

### Post by Drunky on 2007-12-26
silviur,

I believe your method to upgrade to Ubuntu Studio leaves a few things out; notably the LADSPA (et al) plugins and real-time kernel.

This Ubuntu Help wiki page is how I upgraded to Ubuntu Studio: [UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

Open a terminal and cut/paste:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

I hope this helps.

---

### Post by Prodromoi on 2007-12-26
> **SoftWhip said:**
> I've installed Ubuntu Studio on my laptop, and chosen to use the whole hard drive for it. Everything has gone well until the reboot, I input the username and password I chose, now I have a black screen with the following line command;

david@ubuntuhome:"$

What should I do now? I thought it was going to boot up and show the GUI!

Please help me (again!).
Dave

I installed Ubuntu-Studio on a spare machine a few days ago and I got exactly the same.  However, I'd noticed what I'd done wrong just as I pressed Enter (but it was too late to do anything about it by then).

There's nothing 'wrong' as such with your install.  You just don't have a GUI installed.  You didn't (as I also failed to do) check the install option of 'install Ubuntu-Studio desktop' in the install options.  I reinstalled it and checked this option as well as the "2D/3D editing packages" option, and that fixed the issue and I've got a nice shiny Ubuntu-Studio desktop running.

I feel that the Studio installer package is partly at fault here, since it uses Tab and Enter as the means of selecting install options up 'til that point, then suddenly introduces the use of the spacebar.  By then you've rather got used to the setup procedure and you're not paying complete attention.  (Yes, you should be, but we're all human!)

I feel a better arrangement would be to have the Ubuntu-Studio desktop packages selected as the default (is anyone going to installed a graphics or audio editing suite *without* a desktop GUI, really?) and the user then adds the necessary packages (and can de-select the GUI if they genuinely want to).  A "confirm these are the packages you want to install" page before committing would be good too.

---

