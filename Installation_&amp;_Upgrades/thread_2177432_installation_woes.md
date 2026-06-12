---
title: "installation woes"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by jgw on 2013-09-28
I am trying to install ubuntu and have a problem.  I am trying to install 12.4.2 on a system.  The hard drive has had chkdsk run (the drive was a mess)  been reformatted (by windows).  I am using a dvd for installation. the motherboard has a built in sis display which, from my reading is not a good thing.  Anyway, the last time I tried I ran nomodset but had the same problems.  I do get the unix dot thing when it first starts the installation, then I get a blank screen, then it reboots, then I get another blank screen, and this just keeps repeating.  I suspect I am doomed with this motherboard.

Thoughts?   Thank you..........

---

### Post by whitesmith on 2013-09-28
Does the mobo manufacturer have a test suite that you can run? I know ASUS and Intel are pretty good about furnishing these handy tools. While you're at it, download a test for your HDD. Sounds like that's where the problem may be.

---

### Post by jgw on 2013-09-28
Thanks for the reply.  There is not a name on the motherboard.  The system belongs to a friend who asked me to see what was wrong.  It was packed with dust and the drive had a lot of stuff that chkdsk seemed to have fixed (did it 2 times).  The drive is a western digital and I do have a cd for that.  I will run it and see what happens (good idea, given the problems that it had it may be toast)

Thanks again..........

---

### Post by Bashing-om on 2013-09-28
jgw; Hello once more ;
If you are running SIS graphics, try a variation on this as a boot parameter; (grub menu ->"e"->edit boot line)
```

video=sisfb:mode:1024x768x16,mem:4096,rate:70

```
Make sure your monitor will support that resolution, and what the actual refresh rate is; (would not want to burn a monitor up now would we)
from the grub menu -> enter "c" for a command line and terminal code:
```

vbeinfo

``` 
to see what modes your monitor supports.

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by secuono on 2013-09-28
mods delete, sorry

---

### Post by jgw on 2013-09-29
Thanks for the reply.

I tried it again, before I read your last.  Here is what happened.  I, again, stopped the mode thing and proceeded.  It did exactly the same thing.  It continues to mess with the video output (no signal, signal, no signal, etc)  Then it shows me a cursor, on a black screen, then signal no signal, then, after a bit more of blank screen shows me a cursor on a grey background, then signal no signal, then shows me an option to run with law graphics mode, reconfigure graphics, etc. but there is no cursor and the keyboard will not do anything so I can't do anything.  after pressing esc, ^c, < alt del and entry a few times the screen goes blank yet again.

My console is an acer lcd.  It can actually goto 75hz but only for specific resolutions, mostly its 60hz.   I am not sure how to get the grub menu up (hence the stuff below).  The problem is that the screen is blank and so I have no indication how to get there.  I have not tried to just press shift continuously although that might work? (just tried that.  Got "boot:_" which quickly went away)   I also tested the vbeinfo command - got "no such command"  (have have another ubuntu machine up and running all the time so I have a place to do stuff <g>)

Now, your suggestions.  I think you are telling me that when it boots, and the little thing comes up and I press a key and then have options (advanced welcome page options - [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)).   There are a lot of these.  I apologize but my ignorance but there seems to be a whole bunch of stuff available at that point.  Again - any thoughts are certainly welcome and are gratefully accepted.

---

### Post by Bashing-om on 2013-09-29
jgw; Well ..let's try,

If your bios does not have a low resolution driver to even see this far /// I do not know of a thing else to do.

Boot the liveDVD/CD?USB whatever you are using to install from.
As soon as the bios screen clears try depressing and holding the shift key ->
purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> for other additions the boot options kernel boot line is now available, append
```

video=sisfb:mode:1024x768x16,mem:4096,rate:75

```
boot parameter to the end of the line.
Enter key to continue the boot process.

Once we can boot the liveUSB we know what to do in the real install to get a display.

vbeinfo; is a command that is only recognized from the grub boot terminal, when I reboot I will refresh my mind on how to obtain that grub command line on the liveCD.
You will need to adjust the above for a mode that your monitor supports; If you have 2 gigs of ram .. you may increase the mem:4096 to a higher value.

[INDENT][INDENT]we keep try'n
[/INDENT][/INDENT]

---

### Post by jgw on 2013-09-29
Thanks for the reply (we gotta stop meeting like this <G>)

f7 got me the boot line.  I appended what you suggested although I may have screwed that up.  That line ended with "__" and I appended after that, perhaps I should have overwritten the "__", anyway, it started the boot, then gave me the mouse on grey background, returned to black screen (for the last 5 minutes - it also reset the monitor a couple of times).  I will give it some more time.  I have not checked the bios yet (I had it on the welcome menu screen already)  Oh, I changed the line to 70hz as that is what the console had as correct for that resolution (vesa 1152x864 for 75hz)  now screen has remained black for about 10 minutes - will continue to wait.  If nothing happens pretty soon I will check the bios to see what that offers. 

I think this thing has only 1 gig of memory (I may be able to find more memory).  Oh, its an emachine (hp cheap)

Ok, I gave up and rebooted and went to the bios.  Display options were pci express and pci.  I went and got a pci card and put it in to see if that makes any difference.  Its waaay old but........  The back of the machine is towards me and I can see the light on the 10/100 connection blinking which means its accessing the net.  Oh, I also went to the welcome menu and pressed f7 which, for no good reason, asked me if I wanted to run in text mode.  I told it yes.  (in case you didn't notice this is going on whilst I am writing this on another machine (I'm on a kvm for this).  I just checked the machine.  It looks like its at a640x480, I can see unity.  I think I am seeing the desktop from the cd.  There is now an option to instal ubuntu.  I think I will see what happens when I change the bios back to pci express.  Before I put this old card in I was running on the built in video (not a card).  I wonder if the card disables the built in or if I can run both a card and the built in.  I didn't see a switch in the bios.  I will check again.  Nope, the pci card automatically disconnects the built in video, it makes no difference what the card choice is (option must control the slots).  I could actually install ubuntu with the 640x480 card installed but I am not sure this would be the right thing to do.  OH, the console timing table tells me that 640x480 is vga.  I also have available, vesa, svga, xga, sxga, wxga, etc.

I think the grub command line is there but, if not used, goes away rather quickly.  It looks like "Boot:_" and I think I can type there.

Suggestions?

---

### Post by Bashing-om on 2013-09-29
jgw;

Boot with the PCI card enabled ...as you say the onboard is SIS, not to well supported .. let us see what can be done with the better card.

Boot the liveCD  -> "try ubuntu" mode, from the desk top key combo ctl+alt+t yields a terminal.
Let's see what we have to work with:
```

lspci | grep VGA
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

[INDENT][INDENT]where there is life there is hope
[/INDENT][/INDENT]

---

### Post by jgw on 2013-09-29
You are not going to believe this one.  The card is a SIS board (ViRGE - on the board and recognized).  The driver being used is s3fb  (there was a lot of information.  I could put it into some kind of file, wait, I put the results on a thumb drive. 

Anyway, I could also get to the system settings but was unable to change the resolution.  I could also not get to the bottom of the display screen (resolution problem, again)  I do have some other cards, incidentally.  My wife tells me its time for dinner so I must flee. 

I have no idea what I am supposed to do next.........   I also have tried and failed to change the resolution from 640x480 and I have not yet actually installed but am, rather, running with the cd.

Here are the results of your suggested commands:
ubuntu@ubuntu:~$ lspci | grep VGA
00:09.0 VGA compatible controller: S3 Inc. 86c325 [ViRGE] (rev 06)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:09.0 VGA compatible controller [0300]: S3 Inc. 86c325 [ViRGE] [5333:5631] (rev 06)
	Kernel driver in use: s3fb
	Kernel modules: s3fb
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
--
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330] (rev 03)
	Subsystem: Silicon Integrated Systems [SiS] [M]661xX/[M]741[GX]/[M]760 PCI/AGP VGA Adapter [1039:6330]
	Kernel modules: sisfb
ubuntu@ubuntu:~$ sudo lshw -C display
PCI (sysfs)  
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:60000000-67ffffff memory:68000000-6801ffff ioport:e800(size=128)
  *-display
       description: VGA compatible controller
       product: 86c325 [ViRGE]
       vendor: S3 Inc.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master rom
       configuration: driver=s3fb latency=64 maxlatency=255 mingnt=4
       resources: irq:17 memory:f8000000-fbffffff memory:feae0000-feaeffff

---

### Post by Bashing-om on 2013-09-29
jgw; Well, That all looks good !

Are you now up and running ?

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by jgw on 2013-09-30
Thanks for the reply.....

I have not installed yet as I was waiting for your thoughts on the results.  I assume that you think I should install now and then deal with the display?
Also, after I install I am thinking of removing the pc card and trying to go with the built in sis as its probably newer, etc.

Thoughts?

---

### Post by Bashing-om on 2013-09-30
jgw;

Nope, My thoughts are to get the operating system functional in the liveCD "try ubuntu" mode. Whatever it takes to get the display and other things to work in the live environment is the info needed for that actual install.

If you can not get things working in the live environment, there is no sense trying to install to hard disk.

From your last output .. I must assume that you can boot to the live environment to the GUI desktop. Yes ?
And still need to play with the boot parameter to get a better display.
The good news is that " configuration: driver=s3fb" says the driver is loaded.. and you are using the 2nd display port.


[INDENT][INDENT]maybe just a bit of tweaking 
[/INDENT][/INDENT]

---

### Post by jgw on 2013-09-30
Thanks, yet again, for the reply.........

I tried to deal with the resolution in the system setup and failed (stuck on 640x480) I am going to have to try something else.  how about something like video=sisfb:mode:1024x768x16,mem:4096,rate:70 ?

Any commands you might think of would be of real value.  I will simply try them, one after another, until something works.  

If I actually do get the video right THEN I should install?  After installation remove the card and try to deal with the built in stuff?

---

### Post by jgw on 2013-09-30
Thanks, yet again, for the reply.........

I tried to deal with the resolution in the system setup and failed (stuck on 640x480) I am going to have to try something else.  how about something like video=sisfb:mode:1024x768x16,mem:4096,rate:70 ?

Any commands you might think of would be of real value.  I will simply try them, one after another, until something works.  

If I actually do get the video right THEN I should install?  After installation remove the card and try to deal with the built in stuff?

---

### Post by Bashing-om on 2013-09-30
jgw;

What we need to know is the info provided by the "vbeinfo" command that is to be entered at the grub command line. Now, what ever settings we make for the PCI card will not translate back to the onboard graphics....If you want to use the onboard graphics -maybe it will work maybe not-; We would still have to redo the settings because the hardware is different.

Give me a bit and I will refresh my memory on getting to that grub command line. Gonna boot up the Lubuntu liveCD.

back in a bit.

[INDENT][INDENT]we can do this.
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-30
jgw;slap me on the wrist !

I stand in error, one can not get a command line interface on the liveCD grub menu ! I apologize for my misleading and confusing you, not to mention the delay factor.

OK, so go ahead and install using the boot parameter as we now know.. are you sure that your monitor supports a high refresh rate of 75 ?
Might be safer to use a rate of 60 until we know better.

At the install boot screen f6(?) key for the boot options parameters, input the parameter on the boot parameter line.
I suggest for older hardware install NOT to check the boxes for "install updates" or "3rd party software". Will take care of that later after the install is completed.
That boot parameter will be persistent , however, any change we decide to make to it will be done by editing the config file "/etc/default/grub" at a later time.

IF you can install and get a usable display .. rather than "vbeinfo" at the grub boot screen .. activate a terminal and run terminal code:
```

xrandr

```
to see what resolution and refresh rates are supported. (else "vbeinfo" will be used)  

[INDENT][INDENT]stepp'n lightly but getting there
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-03
Results for xrandr are below.  I also have the timing table for the console but its in jpg form and I can't post it here without some pain so I hope the results will work for you (and me!)  The console, however, seems to prefer 60hz althought 1024x768 can use 70 for xga and 1152x864 can use 75hz.  Sorry it took so long to respond but I had to go away for a couple of days.  Oh, I ran xrandr on my other ubuntu machine.  Its running with nvidia but the results shouldn't change much?  When I ran xrandr on the problem machine it said that it couldn't get gamma output and the minimum/maximum size is 640x480 - perhaps I am doomed. 

greg@greg-MS-7222:~$ xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   576x432       120.1  
   512x384       120.0  
   400x300       144.4    120.6    112.7  
   320x240       120.1  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)

---

### Post by Bashing-om on 2013-10-03
jgw; Whoa !

Nvidia and SIS are two different beast.

If the "xrandr" output you provided is from the Nvidia card ... do not attempt to translate it's readings to a SIS graphics.

If "xrandr" provides no useful output, what says "vbeinfo" from a grub command line ?

If that provided output is from the SIS enabled system .. then:
> 
  1024x768 60.0 +
 the "+" says this is the preferred operating mode; I would take that as gospel and not stray too far - if at all. It is what is currently set ("*").
see:
```

man xrandr

```


Doomed:
maybe not.
What boot parameter are you using ? Those parameters can be altered. And as well others may prove more suitable.
But, bear in mind you can not expect good performance with old hardware.

[INDENT][INDENT]it's amazing that a bear talks at all
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-03
I think this machine is just to old to really deal with.  I think I will just put a copy of xp, find a decent password, and be finished with it.  spent enough time trying to fix it right <sigh>
Thanks a lot for all the help and I do appreciate it.
I am going to mark this one done.

---

### Post by Bashing-om on 2013-10-03
jgw;

Hey .. I can understand you are aggravated and exasperated. This should not be a hurdle to high to overcome; To at least get a usable operating system. Apparently it is but a graphics driver issue. Admittedly there may not be a good solution with SIS graphics but there may be a usable solution.
What other options have you tried ?

[INDENT][INDENT]surely, it can be made to happen
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-04
Thanks for sticking with me on this one.

One last try.  I will put in an msi v161 ver 5.2 ati radeon 4350 1gb  pci express video card.  Hopefully ubuntu can deal with it.  I tried it once but it threw a bunch of stuff onto the screen so I put that thought away.  This is a new card, out of the box, which I was saving for another project.  Anyway, I will assume I can get to the cd welcome screen.  Any commands you think might be helpful I can try.

---

### Post by Bashing-om on 2013-10-04
jgw; Welp ..

That is good you want to keep trying ...and yeah the ATI card is a better option .. but , but, but - and I saw a tid bit where this MAY no longer be true -
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)



So what that boils down to is you have to use ubuntu's open source driver. 
Now I fall into that category also - old ATI card - and open source drivers do well for me on an AMD platform.

That said, you should have to do nothing; install the card, fire up ubuntu and the kernel should pick up that card and match it to the monitor. And be real happy with loading the open source driver.

Older hardware still no matter what course you take, is not going to yield high performance.

[INDENT][INDENT]won't take much to try
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-05
LIttle problem.  The card won't even allow me to get to the bios.  It just throws red junk on the screen.  I have tried it several times.  I will give up on that card.  I have a pile of video cards but they are all agp (different iterations) which the motherboard doesn't allow.  I am going to think on this one some.

Thanks for all the help..........................

---

### Post by Bashing-om on 2013-10-05
jgw, Well.

Some times you have some bios setting to adjust for the bios to see the pci card, and also
If the card is ATI or Nvidia, the " nomodeset" boot option may help.
Too bad the ram can not be expanded .. that might help a bunch too.

[INDENT]when all else fails, there is "puppy linux", BTDT 
[/INDENT]

---

### Post by jgw on 2013-10-05
I just rebooted, with the built in sis, after a bit I got a sheet that told me it was running in low res mode and asked me if I wanted to continue.  There was no mouse and the keyboard seemed to do nothing.  I played with the mouse, with no cursor, and then said ok.  Then another box appeared that said that I should standby whilst the display re-started.  There is an ok on that too but I have played with the mouse and nothing.  I assume it will eventually do something although I also suspect that its now stuck as its been on that box for about 10 minutes.  My problem with the cards is that most of those I have are agp and the motherboard doesn't have a slot for those.  Seems I only have 2 pc cards and they are both sis (as is the motherboard display).

Anyway, that's how it stand right now.

---

### Post by Bashing-om on 2013-10-05
jgw; Humm, let's think bios settings.
What bios and version did the manufacturer install. I'll see what I can find out about it.
I will also take a look-about and see what else I might come up with for alternate boot options for the onboard graphics controller.

[INDENT][INDENT]It could happen
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-06
The bios.  American Megatrends v 2.57   I also reset the share memory from 32mb to 128mb (assuming this is for built in video - might help?)

---

### Post by Bashing-om on 2013-10-06
jgw; Hi !

Got your last. Let me have a bit of time for research. I will return if/when I have something constructive to offer .. or I give up.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-07
jgw; Hi !

Try this, in bios - "bios features setup " - disable all shadow ram features, ubuntu kernel does a better job;
in bios - "chipset features setup" disable the memory hole, again the kernel handles better.

And then try this boot parameter.

> 
 you need to add 2 options to the grub config.
You need to add s3fb.mode_option=1024x768-16 to set the resolution, but this wont work if the gfx card is not initialized from the VGA BIOS, so you also need to add vga=791 or similar.
So edit /etc/default/grub with this line:
Code:
GRUB_CMDLINE_LINUX="vga=791 s3fb.mode_option=1024x768-16"
Then do sudo update-grub and reboot.


And Hey, I am still looking.

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-08
Thanks for the suggestions.  I will fix the bios as you suggested.  I think I can edit grub once I get to the cd welcome screen? OR the cd (try ubuntu) screen?  I can get to the cd screen if I have the card in place.  If I try and do it with the built in sis video I get the low res option and then it all goes to hell in a handbasket <g>

---

### Post by Bashing-om on 2013-10-08
jgw; Hey;

I should think you should be able to enter the boot parameters from either the liveCD boot options screen// OR from the install, when booting -> hold the shift key -> ubuntu boot menu, non-recovery kernel highlighted -> "e" key for edit mode and add the parameter to the line containing "quiet splash". At the point of the grub menu the graphics drivers from ubuntu have not been loaded into memory. We are trying to tell the kernel what and how to load.

[INDENT][INDENT]getting beyond bios
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-08
I am also wondering if I should try and update the bios.  That thing is over 7 freaking years old!  Don't know if its possible but it should be.  I went to the ami site, they have a program to check the system and update the bios.  I will only work on windows but, given the amount of time with this thing I suspect it would not take all that long to put windows on, update the bios, then install ubuntu and see what happens and also check any new bios optsions.  Whaddyu think?

---

### Post by Bashing-om on 2013-10-08
jgw; Yeah, That thought had occurred to me .. but messing with bios can be hazardous to the operating systems health if there is a problem.

There is an alternate way to update ones bios, freedos bootable disk with the bios updates installed onto that CD. If it is no big deal, installing windows may be the safer, quicker  approach.

The best I recall, from windows one can save the current bios configuration. Might be of use if there is a problem updating. From the "freedos" method I do not think saving the current config is possible.

I have seen updating bios fix many problems.

[INDENT][INDENT]hey, it is a good thought
[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-08
You are absolutely right about messing with the bios.  However, they claim to have a program that will do it with no problem.  I always wonder about that.  I have literally destroyed machines messing with the bios and this isn't even my machine.  However, in theory, when one updates the bios they re-write the chip which can, then, be re-written yet again.  I will mess with this, in the next couple of days, and see what happens <G>  (and will let you know!)

---

### Post by jgw on 2013-10-11
I have failed but  I have also learned some.  The guy who owned the computer came by.  I had windows up (trying to get bios) and he said it was fine and took it away.  However, I did learn that the so called hp emachines t3504 was something else entirely.  I had a sis motherboard in it.  I needed to get some drivers and I have a program that checks those against the hardware and suddenly I was presented with an entirely different motherboard than was in the system.  I did a little detective work and found out that was actually done by the emachines people so all the specs were wrong (I was having fits loading drivers that didn't work).  I didn't even know sis made motherboards!  Anyway, my project is now dead as I no longer have the machine to make that work.  

I do, however, thank you for all the help you have managed to give me as it was, if nothing else, educational!!  Oh, and that machine was a geniune piece of crap! <G>  thanks again!

---

### Post by Bashing-om on 2013-10-11
jgw; Hey, Not at all any problem on my part to try and assist.
I always look forward to an opportunity to learn more in respect to my operating system of choice ! As well, promote this operating system to those who are inclined to learn.
There will be other times, and other machines !

You would be amazed at all the "trash" computers I have retrieved from the dumpster and passed on to some worthy child - running some form of linux !

[INDENT][INDENT]just doing what little good I can[/INDENT][/INDENT]

---

### Post by jgw on 2013-10-13
Again, thanks for the help.  I cannot tell you how many computers I have been given by people out to buy the latest and greatest.  I try and tell them that unless they are doing weather, video/photo edits, etc. they simply do not need all that power and if they only use the net then no amount of power will increase connection speed.  They always ignore me and over half later tell me that they can see no difference.  We live in a strange world.

Later!

---

### Post by topshelf7 on 2013-10-27
jgw...just a little note that might help you not get discouraged when working through the problems of working on , what most others say , a "trash computer that should be re-cycled".  I have been struggling with an old Sony Vaio, PCV-538DS that was given me along with some cash for services rendered.  It was a complete system, but the last light of day it had seen was Windows 98SE.  Has 500MHz cpu, 256MB ram.  Had MEGA probs installing ANY OS..until...I replaced the CDRW/DVD with a newer one and breezed through installation of Lubuntu 12.04 LTS.  On it as I type.  Just a tad on the slower side but way do-able.  Sometimes it's the simple things that we overlook that make all the diff.   Good luck in your adventures in alternative OS's.

---

