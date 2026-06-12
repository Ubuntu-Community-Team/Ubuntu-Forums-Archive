---
title: "installation goes black (ATI?)"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by diegolaz on 2006-08-05
Hi, I downloaded Ubuntu 6.06 for AMD 64 Desktop.
I boot and tried to install (the first option) and the graphical safe mode (second option). I says is loading stuff, configuring X ok, etc etc...everything ok. I hear a sound like if it's entering the liveCD desktop or something but the monitor has "no signal".
So it looks like it's there wainting for me... but I see nothing.
I have a AMD X2 64 3800, IDE HD, and a ATI X800PRO... is found some tips to install ATI drivers, but that's with a system already warking... I can't even start...
any ideas??
Thanks!
Diego

---

### Post by diegolaz on 2006-08-05
I don't know if it has something to do, but I also have a RAID with windows on it, but I unplugged the power of both HD in the raid before trying to install ubuntu on the third (IDE) drive. I have the SATA cable plugged with the system doesn't see the drives so it shouldn't be a problem, right?

---

### Post by K.Mandla on 2006-08-05
I don't know that this is related or even worth mentioning, but I had a similar problem on a desktop machine with onboard Intel graphics.

Unfortunately, the board I was using (an old HP) didn't completely shut off the onboard graphics at the BIOS. So even when I tried to use a PCI graphics card, I got black screens because Ubuntu sensed the onboard video and configured itself for it.

I don't know if that's of any help at all, but it's the first thing I thought of. :|

---

### Post by Twinsen on 2006-08-06
I have exactly the same problem. 
My specs are
AMD 3500+
ATI X800GTO2 
I have windows installed on my raid and a spare HD for ubuntu ready
1024 mb ram

Could it be that its just not detecting our gfx cards.
The last ubuntu i installed i had to change this manually in some configuration file. But at least it installed that time.
Is there some command we can pass to it before installing that will load it in the correct way.

I also tried switching monitor to the 2nd output on my card but to no avail

ANY Assistance here would be great.
Also wat motherboard are you using i have a DFI Expert board. Doesnt have any onboard video so should be ok.
Maybe i should try taking out my sound and tv card then installing.

---

### Post by diegolaz on 2006-08-06
My motherboard is an GIGABYTE K8N Pro SLI (nforce 4)
NO onboard video.
Sound sounds ok (I can hear something but can't see anything)
But I also have a TV card that don't thinks is linux compatible (PCI kworld tv tunner)... so maybe we are haveing the same problem...

---

### Post by Twinsen on 2006-08-06
I will try it without the tunrer tonight.
I cant hear anything either ohh woe to me.

---

### Post by diegolaz on 2006-08-06
> **Twinsen said:**
> I will try it without the tunrer tonight.


mee too.

Is there any key-combination to swith into text mode to see if there is any error??

---

### Post by Twinsen on 2006-08-06
It works kind of.
It doesnt send no siginal to screen any more 
but it says cant configure x server then starts in text mode.
I think you can change the setting to vesa or something which will work on most cards because thats what i had to do on badger.

---

### Post by mgmiller on 2006-08-06
On booting the cd, instead of accepting the default command, use the up down arrows to select a custom command and then select a different resolution like 800x600 or 640x480.  I forget if you get to this by using the up down arrows, or if you hit a key, the clue is at the bottom of the screen, read the choices there.  This will give you a non graphical boot to a terminal screen.  Then run 
nano /etc/X11/xorg.conf 
and look for the line with your ati driver in it. (you might need to run nano as sudo with a blank password) It'll be in section "device" and have the name of your ati card on one line.  The next line should be the line that says Driver and replace "ati" or whatever it says with "vesa".  next hit ctrl o to save the file then ctrl x to exit the editor.  try typing startx and see what happens.  If you get a gui, you may then want to try installing the accelerated drivers using easyubuntu or automatix.  I have found that sometimes the standard drivers do not work, but the accelerated ones do for ati cards.

good luck

---

### Post by Twinsen on 2006-08-06
what does the nano command do?

---

### Post by diegolaz on 2006-08-06
> **mgmiller said:**
> On booting the cd, instead of accepting the default command, use the up down arrows to select a custom command and then select a different resolution like 800x600 or 640x480.  I forget if you get to this by using the up down arrows, or if you hit a key, the clue is at the bottom of the screen, read the choices there.  This will give you a non graphical boot to a terminal screen.  Then run 
nano /etc/X11/xorg.conf 
and look for the line with your ati driver in it. (you might need to run nano as sudo with a blank password) It'll be in section "device" and have the name of your ati card on one line.  The next line should be the line that says Driver and replace "ati" or whatever it says with "vesa".  next hit ctrl o to save the file then ctrl x to exit the editor.  try typing startx and see what happens.  If you get a gui, you may then want to try installing the accelerated drivers using easyubuntu or automatix.  I have found that sometimes the standard drivers do not work, but the accelerated ones do for ati cards.

good luck

Thanks! I'll try that.
Yes on CD boot with F5 or F6 you can change resolution... but how will changeing resolution give me a terminal screen? if I quit graphical interface I get a terminal with "boot:"... can I call the nano editor from there? does /etc/X11/xorg.conf exist if I havenn't installed / partitioned yeat? (if so I guess its in a ramdrive, right?)

---

### Post by Twinsen on 2006-08-06
Yes i would have thought it would be in the ram.
I have done as you said mgmiller but i then get the nosiginal to my monitor.

---

### Post by mgmiller on 2006-08-06
nano (or pico) for that matter are command line text editors.  Since you are in a terminal enviroment, without a gui, gedit won't work.  You can try them from a termnial window.  just type nano (or pico) and the path to the file name.  Make sure it's a text file.

---

### Post by mgmiller on 2006-08-06
All the settings and files are created on a ram disk as suggested above.  

The suggestions I made worked for me with the 32 bit install of Ubuntu 6.06 with an ATI video card using the svideo out to drive a tv set as the only monitor.    There are enough differences here that I guess something else needs tweaking.  I had the exact same symptoms of a black screen shortly after the install process started, so I thought this might be helpful.  Sorry.

You could try the 32 bit installer just for giggles and see if it works there.  There might be an incompatiblilty between the 64 bit and the vid card you are using.  For best results, in general, nvidia cards give much better compatibility with linux that ATI, (an expensive solution, I know).  I am running an AMD64 with the K7 kernel and it runs great.  Plays UT2004 with good frame rates and all is happy.

One other thing I just thought of, again from the boot screen, there is a choice for kernel modules or  extra commands, or something like that, try putting normal at the end of that string and tell it to boot that way,  That should kick it into a different type of text only boot process.  Watch the command hints at the bottom of the screen, if you do it wrong, the command you entered won't take.  I think maybe the command also has to be in quotes, but I foget, but once you get to that point and use the right arrows to get to the end of the command, you will see the resolution it's trying to use, just change it to normal.

---

### Post by diegolaz on 2006-08-06
I haven't tried your suggestion yet. I'll have to wait until tonight (5-6hs from now). 
I'll let you know how it goes.

---

### Post by mgmiller on 2006-08-06
OK, final thoughts here...
from live/install CD hit F6 to get the command line and at the end of it add a space and then add vga=normal  or try vga=791 or try vga=771  other commands to try adding along with these or by themselves are noapic and no|apic.
So one example might look like:
 vga=normal noapic no|apic
try different combinations of the above, just put a space between each command.

The | key is the one above \ on your keyboard.  it's called a pipe.

One of the commands you will see when you are doing this is splash.  It will appear in the line like
ro quiet splash
you can also try replacing the command splash with the following line:
video=vesafb:1024x768-32,ywrap splash=silent,theme:Ubuntu CONSOLE=/dev/tty1

The last thing you could try is the alternate install CD from ubuntu downloads instead of the live/install cd.  Some people with AMD 64 report that is the only one that works for them.

Finally, as I suggested earlier, try the 32 bit install CD, or substitute nvidia video card for ati $$$

This may be a frame buffer issue, but I am fuzzy on the command to fix it beyond the video=vesafb command above.

I'm about tapped out on this one.

Good Luck.

---

### Post by Twinsen on 2006-08-07
Will try now

---

### Post by Twinsen on 2006-08-07
None of the above worked for me im going to try downloading the alternate install

Where do i download the alternate instalation from

---

### Post by diegolaz on 2006-08-07
same here. 
Thanks mgmiller for so detailed help. I'll try another install.
When I removed the TVTunner I could get a screen saying the video might be not configured... but tried editing xorg.conf changing ati for vesa or for radeon...and the same happened... after startx looks like if it's stating I hear the sound...but nothing in the screen...
Is it possible that the monitor causes a total black screen?? (viewsonic 20.1)

---

### Post by yccheok on 2006-08-07
Hello all, I am having the similar problem as you all. However, I solve my problem with the following workaround. Please refer to my post to see whether it works for your case.

[http://ubuntuforums.org/showthread.php?t=226367&page=2](http://ubuntuforums.org/showthread.php?t=226367&page=2)

---

### Post by mgmiller on 2006-08-07
Where do i download the alternate instalation from?

go to ubuntu.com and click on download on the right side.  Select the mirror closest to you.  On the page that says select an image, just scroll down till you see the alternate install CD list and pick the one for your arch.

Have you had any luck with the 32 bit version?

---

### Post by mgmiller on 2006-08-07
Queston:
Is it possible that the monitor causes a total black screen?? (viewsonic 20.1)

Answer:
Yes, it's possible.  LCD monitors will sometimes just turn off or display black if you feed them an out of range signal.  Make sure your resolution and refresh rates are within specs for your monitor.  Especially the refresh rate, unless you know it can do it, don't go above 60 Hz to start.  Most LCD panels won't go above 75.  Unlike CRT, LCD panels look flicker free at 60 hz.

---

### Post by diegolaz on 2006-08-07
> **mgmiller said:**
> 
Answer:
Yes, it's possible.  LCD monitors will sometimes just turn off or display black if you feed them an out of range signal.  Make sure your resolution and refresh rates are within specs for your monitor.  Especially the refresh rate, unless you know it can do it, don't go above 60 Hz to start.  Most LCD panels won't go above 75.  Unlike CRT, LCD panels look flicker free at 60 hz.

Mmmmm.... I think that might be... I changed the resolution in the xorg.conf but not the refresh rate... and thats what happend to me... the screen goes off. 

I'll try that also, thanks!

yccheok -> thanks too, I see this is a similar solution. i'll let you know both

---

### Post by mgmiller on 2006-08-07
> Mmmmm.... I think that might be... I changed the resolution in the xorg.conf but not the refresh rate... and thats what happend to me... the screen goes off.

Ok, here is some more detailed stuff to try:

When you get the point where you were telling it startx, at least you have a working terminal.  Instead of telling it to startx, give it the following command to stop the gdm:
```
sudo /etc/init.d/gdm stop
```

next, you will reconfigure your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```

make sure you only add in screen resolutions and refresh rates that you know are supported by your monitor.  You can accept the defaults that it suggests for anything you don't recognize.

When you're done, it will create a new xorg.conf and make a backup of the old one with todays date in it.

Finally try starting the x server
```
startx
```

If that doesn't work try restarting gdm:
(gdm stands for gnome-desktop-manager)
```
sudo /etc/init.d/gdm restart
```

I think you are very close to solving this.

Good Luck.

---

### Post by diegolaz on 2006-08-09
Ok. tried all that and nothing. So I stated to download the alternative CD.
While I waited for that I tried with a mandriva 2006 I had. It installed, on first boot crached the x server, I changed the /etc/X11/xorg.conf driver from ati to radeon and startx worked perferct. So hardware should be compatible.
After alternative CD is ready I managed to installl ubuntu in textmode.
But again...startx does not work...is it ok if I try to copy the xorg.conf from mandriva?

---

### Post by ububaba on 2006-08-09
I have been running the computer successfully for quite a few 
months without any changes. Suddenly it has started going black.
Now, the worst has happened. After reboot I don't even get to the 
login screen, as it already turns black! 

How does one solve this one, dear friends and foes?:?:

---

### Post by mgmiller on 2006-08-09
> Ok. tried all that and nothing. So I stated to download the alternative CD.
While I waited for that I tried with a mandriva 2006 I had. It installed, on first boot crached the x server, I changed the /etc/X11/xorg.conf driver from ati to radeon and startx worked perferct. So hardware should be compatible.
After alternative CD is ready I managed to installl ubuntu in textmode.
But again...startx does not work...is it ok if I try to copy the xorg.conf from mandriva?

Are you using the 32 bit installer?  I think you were originally trying to get the 64 bit to work.  I'm not sure what would happen if you copied over the xorg.conf from mandriva, but it certainly can't get any worse than what you have now.

Another thought is in your bios, see if you have agp fastwrites enabled, if you do, disable it.  You can also try changing the agp speed in bios from agp 8x to 4x.  (If you are using pcie video, I have no expderience with that).  Also in the bios disable legacy usb support.

Finally,
See if you can borrow an Nvidia video card from someone and try again.  Sometimes, ATI is just a bear to get working.

---

### Post by mgmiller on 2006-08-09
> I have been running the computer successfully for quite a few
months without any changes. Suddenly it has started going black.
Now, the worst has happened. After reboot I don't even get to the
login screen, as it already turns black!

Do you have a hardware issue?  When is the last time you opened your case and cleaned out all the dustbunnies from every nook and cranny?  Are all your mobo fans (northbridge chipset fan for example)working?  Is the fan on the video card working?  You can also try reseating the video card (pull it out of the slot and put it back a few times.)

Other things to try:

1) In bios, disable legacy usb support.

2) In bios, disable apg fastwrites and try lowering the apg speed from 8x to 4x.

3) When grub starts, hit esc and select an earlier kernel or a recovery kernel and see if that helps.

4) Booting from an alternate install CD, try the "fix broken installation" option.

---

### Post by yccheok on 2006-08-15
I think ububaba is facing same problem as me.

I have a workaround, but it is quite ugly and cumbersome if the problem occur quite frequently. 

Please refer to my post at 

[http://www.ubuntuforums.org/showthread.php?p=1382456#post1382456](http://www.ubuntuforums.org/showthread.php?p=1382456#post1382456)

---

