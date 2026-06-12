---
title: "Screen goes blank after LiveCD Menu Selection"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Acidictadpole on 2007-04-22
I am trying to install ubuntu on my machine currently with the 7.04 livecd.

Booting to the CD's main menu works fine but upon selection to "start or install ubuntu", I get the visual representation of the kernel loading and then the screen goes blank after 100%. 

I would usually let it sit for a bit as it may be detecting graphics settings but the computers processor light and the cd-rom light are inactive. 

The important specs are as follows (I kinda doubt my hardware is the problem right now since I have had ubuntu working with this exact loadout, the possible culprit MAY be bios settings that I'm unaware of):

Radeon X800xl AGP.
Pentium Core 2 Duo 1.8Ghz.
1024Mb DDR RAM.

I can't think about any other specs one would need but if you do just let me know.

---

### Post by davidlt on 2007-04-22
I have the same probelm right now and I am working with a few people who are trying to help me.

Mostly the kernel doesn't load on your machine. After menu is loaded, press F6 key and write "Live" and hit ENTER. And write the same line you are getting. Could you do it?..

Mine stops loading after "SMP motherboard not detected."

Edit: This is how it looks on my machine without any other parameters: [http://www.youtube.com/watch?v=ihoa5jinnxc](http://www.youtube.com/watch?v=ihoa5jinnxc)

---

### Post by Acidictadpole on 2007-04-27
Actually no. My screen ceases getting input from the computer. So it just gives me the "no input" symbol and then goes dormant. Happens at approximately the same stage though.

---

### Post by noobicon on 2007-05-03
having a similar problem (with similar hardware)...initially making any selection from the Live CD menu caused a blank screen, managed to work around this by hitting F4 and selecting 1280x1024x32 (recommended resolution for my flatpanel).  Beyond this point I can get in and install the system, but after reboot and when selecting anything (other than windows) from the grub menu i get the same blank screen and can't boot into ubuntu.  Tried dpkg-reconfigure at various points all to no avail.

---

### Post by Woody on 2007-05-03
Davidlt - your vid shows exactly what is happening with me.   Does anyone have a solution?

---

### Post by auditory on 2007-05-04
I have the same problem.
And from booting message, the last messge reads:

..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1

and booting stops.
I found the next message should be "2 CPU brought up"

---

### Post by markoloka on 2007-05-04
One thing could help... on main menu press F6 and from boot line delete "quiet splash" and leave everything else there and press enter. Now you'll see where it actually stops as you'll see text lines running on your screen.

---

### Post by Ted_Smith on 2007-05-04
Same problem here - driving me mad! In my case, X starts and I hear the drums etc but I have no display unless I Ctrl Alt F6 and go to the terminal.  

I've tried doing various suggestions that I've read on the net such as booting in safe graphics mode, setting vga=771 or 776, changing xorg.conf to vesa driver instead of ait, removing the quite splash option etc, and several other things  that I now forget. 

This is so daft and annoying. The Feisty Fawn was advertised as 'better support for laptops' - yet what is the most common drivers on modern laptops? Nvidia and ATI, yet Ubuntu can't cope with ATI drivers properly (according to what I've read). Swell.  

I give up. I've spent 4 hours this afternoon trying to install it on my nice new HP Laptop and I'm still no nearer. Looks like I'm stuck with Windows on it which does at least work.

---

### Post by Gus_T_Reer on 2007-05-04
I seem to have the same problem here (feisty 64bit), (no signal to monitor after selecting 7.04). ATI x850xt graphics card. Interestingly if I specify vga=0x31A (1280x1024 16bit, my default monitor resolution) at the end of the 'normal' grub menu entry I can see everything and it seems to fail literally at the last hurdle. I know that's not very technical but I can't pin it down. Also, if I select recovery mode from the grub menu and let it finish and then type init 5 I can get the gnome desktop and everything runs fine including the notorious ati proprietry 3d driver.
The first sign of impending trouble was when I installed from the live cd and when it told me to remove the disk, shut the cd tray and press enter it wouldn't take any input from my usb keyboard (which otherwise works fine).
Another problem I seem to be encountering is that the system will not restart or shutdown properly, it just seems to cut out leaving me to have to manually restart the machine and curiously (and I don't understand this) any changes to firefox (themes, bookmarks, etc.) are lost next time I log in. Could this be an acpi problem I wonder? Just guessing 'cos as a first time ubuntu user I'm flailing around looking for answers.

---

### Post by Ted_Smith on 2007-05-04
Fixed it! If you are trying to run the Ubuntu Linux install CD on a laptop that has ATI hardware and you are receiving the blank screen after the initial startup (you might even hear the drums but still no screen) try this (Note - you need to have your laptop connected to the Internet for this to work) :

Boot up laptop and then when the CD activity stops and you have your blank screen press Ctrl Alt F6 which takes you to the terminal. 

Type  : 

```

sudo /etc/init.d/gdm stop

```

and check it says [OK]. It might say [fail], if it does, try again. It should work the 2nd time. 

Then type (one at a time) : 
```

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial

```

Then restart X by typing 
```

sudo /etc/init.d/gdm restart

```

You will be faced with a blue screen asking you whether to restart X despite it running on Display 0: etc etc. Choose Yes. It might not work the first time but if not Ctrl Alt F6 back to the terminal, stop X again as stated above and then run the restart command again. In my case it worked the 2nd time round but not the first.

That should get you up and running within the CD instance and allow you to install the OS. However, you might have to do the 3 steps above again after the installation following a reboot (I did). But it's much quicker doing it using your installed version as opposed to from the CD instance.

That's it - I'm typing this from my laptop in Firefox following those instructions. 

If your a newbie to Linux try not to let this put you off. It's an unfortunate problem related to, I think, ATI not Ubuntu itself (so I take back what I said above!)

Ted

---

### Post by thayerw on 2007-05-04
Have you all tried this thread under the Absolute Beginner Talk forum?

**Installing Ubuntu 7.04: ATI X**** Cards**
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

If you have an ATI card, it's the first thing I would do.  If you simply want to check out the Live CD and not install the OS right away, you can also try my instructions, found here:

**Workaround: Boot Feisty Live CD with ATI X1400 (Dell 6400)**
[http://ubuntuforums.org/showthread.php?t=414723](http://ubuntuforums.org/showthread.php?t=414723)

---

### Post by Boho on 2007-05-05
Ted,

Thanks.  Worked perfectly.

---

### Post by DrowElfDrizzt on 2007-06-05
Hey.

I got the same problem! I insert the livecd 7.0.4 amd64b edition and after I press "start or install bla bla bla" I get the kernel loading screen which goes to a 100% and afterwards my screen enters power saving mode because it gets no signal. Another symptom I get is that my keyboard is flashing its lights repeatedly!
I tried pressing ctrl + alt + f6 but nothing happens; my screen stays in standby mode, my keyboard is still flashing its lights and the dvd-rom doesn't seem to be waking to life again...

I've been trying to install ubuntu for a year now! Every time there is another problem. At first my system was too new. Then my graphics card was not supported and I even got hand made ATI drivers from one of the DEBIAN developers that I met on a support room in IRC and that didn't work (not on xubuntu/ubuntu or debian...). I am starting to lose faith here :(

Is there a fix to this problem apart from changing my hardware to Intel/nVidia?!?!

PC config:
AMD Athlon64 3000+
ATI X800GT 256mb

Please help,
Matan.

---

### Post by Shaydog on 2007-06-17
I'm having the same issue as DrowElfDrizzt.  I load the Live CD and have to press F4 to change my resolution so that I don't get a blank screen.  I can go in and install everything but when it reboots from the hard drive it goes to a blank screen.  No option to change the resolution.  Ctrl + Alt + F6 does nothing.  Has anyone come up with a resolution for this issue?

Sorry, this is my first experience with Linux and I'm not sure if I'm making a completely stupid mistake or not :)

---

### Post by daInvincibleGama on 2007-08-01
I have been having the same issue with my Ubuntu 7.4 Feisty Fawn installation.

My computer specs are:

Intel C2D E6600 | ASUS P5N32-E Plus | nVidia 8800GTS | Addon TV tuner installed (just letting ppl know because of possible hardware conflicts)
Every other feature is basically onboard.

I tried the AMD64 CD (because C2D has the x64 instruction set). CD boots fine into the menu. However, any option that requires linux kernel startup fails the same way.

The "Start or install Ubuntu", "Start Ubuntu in safe graphics mode", and even "Check CD for defects" utility fails.

It displays some text (like in davidlt's first video), but then goes blank and becomes unresponsive. I dont even get the blinking cursor on my screen. All the activity lights on my computer die. When I press the power button, the CD ejects like in a normal LiveCD shutdown, but the PC fails to power off.

Next I tried the 7.4 i386 disc, Everything works perfectly. I'm writing this from the x86 CD.

Hope this helps.

---

