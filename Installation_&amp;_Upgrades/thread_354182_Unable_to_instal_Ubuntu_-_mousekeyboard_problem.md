---
title: "Unable to instal Ubuntu - mouse/keyboard problem"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by hanning on 2007-02-05
Hi folks,

I've tried to instal ubuntu in the past & ran into the same problem I'm having now, but this time I've decided to persevere and try and sort out what's going wrong.  I don't like being forced into buying a new all singing all dancing PC just to please Mr Gates!

I have downloaded the latest install CD/DVD and had the same problems with both.  So I've downloaded the .iso, burned it to CD/DVD, rebooted my PC, so far everything seems ok, but when it comes to the installation then the problems begin.

1) My plain old PS/2 keyboard doesn't work.  The NumLock light is lit, and that's it.  No response from any of the keys, I can't even turn NumLock off or on.  I tried unplugging keyboard and this time all the lights flash on (capslock, munlock, scroll lock), flash off and the same problem no response from any keys.  I've even tried using another keyboard and the same thing happened.

2) My USB mouse doesn't work.  When I switch on the PC the light in the mouse flickers on quite happily, but as soon as I try and boot the installer the "detection" light (the brighter one you get when you move the mouse, dunno it's real name) comes on permanantly for about 60sec then the whole thing just conks out dead.  No light at all.

I can't for the life of me even hazard a guess as to why such simple devices are just failing during the install.  My machine is only 4 years old, the specs are definately above the minimum requirements.  However, the PC is a branded one that came from Time Computers in the UK (before they went bankrupt and stole all those people's money).  Considering what I've heard from other people the quality of these systems is so shoddy that I'm luck it's lasted so long.

Aside from buying myself a new box (something I'm seriously considering, if anyone knows of where I can get one for £150 let me know!) can any nice ubuntu-knowledgable people help me out?

Thank you lovely people,
CHris

---

### Post by Dylnuge on 2007-02-05
I am assuming that the light you are reffering to is a tracking light from a optical or lazer mouse.

Hate to ask, but are you able to boot into the LiveCD Environment? If not, then your mouse is not going to work (Ubuntu will not detect and track it until you boot into a GUI).

The keyboard is probably not the problem (as another one also fails), so I would hazard a guess that it is a failure in the PS/2 port's detection that Ubuntu is not properly going through. Does it work in BIOS initialization (when you start the computer, before booting into the CD, does pressing the toggle switches (Num, Caps, and Scroll Lock) cause the lights to toggle?

---

### Post by hanning on 2007-02-05
I've managed to get the liveCD to boot, but still no luck with the mouse.  It's a Microsoft USB optical mouse, so I imagine that there's drivers for it.

The keyboard works fine during the BIOS, but freezes as soon as the CD starts to boot.  I even tried using it in the mouse PS/2 port on the off chance and no success either.

CHris

---

### Post by Sef on 2007-02-05
> I've managed to get the liveCD to boot, but still no luck with the mouse. It's a Microsoft USB optical mouse, so I imagine that there's drivers for it.

The keyboard works fine during the BIOS, but freezes as soon as the CD starts to boot. I even tried using it in the mouse PS/2 port on the off chance and no success either.

A couple of ideas:

1) Try the Live CD in another computer and see if the mouse and keyboard work.  If they do, then put in yours and see if they work.

2) Borrow a mouse and keyboard and plug them into your computer and see if they work.

---

### Post by kevinatkins on 2007-02-05
Hi,

Strange problem. Im using a PS/2 keyboard and PS/2 optical mouse without problem.

Do your mouse and keyboard work under XP?

Have you tried a bog-standard PS/2 mouse? There's a possible hardware problem here, but I think you need to eliminate all possiblilities first - try combinations of PS/2 / USB keyboards + mice.

If all else fails, CPC (Premier Farnell) are doing a fairly basic 3GHz Sempron base unit for £175, but I'd persevere and see if you can straighten out the problems first.

---

### Post by hanning on 2007-02-06
> **Sef said:**
> A couple of ideas:

1) Try the Live CD in another computer and see if the mouse and keyboard work.  If they do, then put in yours and see if they work.

2) Borrow a mouse and keyboard and plug them into your computer and see if they work.

1) Keyboard and mouse both seem to work OK on my parent's Dell machine

2) Their PS/2 keyboard & USB mouse don't work with my machine

> **kevinatkins said:**
> 

Do your mouse and keyboard work under XP?

Have you tried a bog-standard PS/2 mouse? There's a possible hardware problem here, but I think you need to eliminate all possiblilities first - try combinations of PS/2 / USB keyboards + mice.



Both mouse and keyboard are working fine with XP (hence I can type this).  I've got a USB-PS/2 adaptor for the mouse which I've tried and it still won't work for either my mouse or parent's USB one.

Could it be possible that the problem has something to do with my motherboard?  Lack of drivers for it in ubuntu or something?

CHris

EDIT: I forgot to mention I've also downloaded the alternative install CD and have the same problem with it as well.

---

### Post by hanning on 2007-02-07
*BUMP*

Anyone else have any suggestions?  Worthwhile me trying other distros and see if I have the same problem?

---

### Post by kevinatkins on 2007-02-07
Hi,

Hmm, this is puzzling. When you boot Ubuntu and you say the keyboard 'Num-Lock' light is on, does pressing the Num-Lock key toggle the light off / on? If so, then it would indicate that the keyboard is at least working. The next possibility then is a problem with the X server (the graphical windowing system).

If the keyboard passes the test above, try pressing 'ctrl-alt-<F1>' all together - the screen should blank and you will be dumped to a standard text console with a login prompt. Try this and post back with results - if we can get to a login prompt, there's a possibility of looking at the X-server log files to see if there's a problem there.....

Kevin.

PS - Are you on a home network; do you have access to another PC? Just another idea running through my head - remote login to your problem PC and view logs that way...

---

### Post by hanning on 2007-02-07
> **kevinatkins said:**
> When you boot Ubuntu and you say the keyboard 'Num-Lock' light is on, does pressing the Num-Lock key toggle the light off / on? 

Trying Num-Lock key has no effect, keyboard is completely frozen

> **kevinatkins said:**
> 
PS - Are you on a home network; do you have access to another PC? Just another idea running through my head - remote login to your problem PC and view logs that way...

Not on a home network I'm afriad, so bang goes that idea.

CHris
(Begining to suspect his PC is some sort of mutant hybrid monster)

---

### Post by kevinatkins on 2007-02-07
> Trying Num-Lock key has no effect, keyboard is completely frozen

Damn.
> 
Not on a home network I'm afriad, so bang goes that idea.

Double-damn.

Er, quickly running out of ideas.... it might be worth checking your BIOS settings, and set to default, also set operating system to 'other' if there's that option, and disable legacy USB. And check anything to do with PS/2 ports...

Other than that, you could try a different distro, but it's quite possible that will run into problems, too. Still, it's worth a go (but I like Ubuntu best of all!)

---

### Post by fozziethebeat on 2007-02-09
I'm having the same exact problem but only with linux-generic

when i boot up in the non generic kernal, everything works fine.  the keyboard also works fine in windows.

---

### Post by hanning on 2007-02-10
How do you go about installing the non gerneric kernel?

CHris

---

### Post by hanning on 2007-02-11
*BUMP*

Is the non-generic kernel the same as installing via the alternative CD?
Is there some paramater I need to enter at the boot menu?

Cheers,
CHris

---

### Post by Cannaregio on 2007-02-11
> **fozziethebeat said:**
> I'm having the same exact problem but only with linux-generic

when i boot up in the non generic kernal, everything works fine.  the keyboard also works fine in windows.


Same here. On a hp desktopo box. With generic. (with 386 edgy or windoze they worked fine)
I have managed a couple of time to have the ps2 keyboard and mouse working during a given session, but by reboot they went dead again, and I was compelled to reuse usb keyboard and mouse.

I dislike having to block  usb port  just to use the crappy hp keyboard and mouse, when I could use some better, ps2 cabled, keyboard and mouse I have.

------------Edited in order to explain matters better -------------------

1) My wireless USB keyboard and USB mouse work well
2) My PS2 keyboard and my PS2 mouse do not work
3) My USB mouse with a USB to PS2 green converter does not work
4) A couple of times my PS2 keyboard and PS2 mouse DID suddendly work, but after reboot they where not working any more and I had to reinstall the USB wireless keyboard and the USB mouse

uname -a = 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

and here the cat /proc/bus/input/devices:
```

cat /proc/bus/input/devices
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c03d Version=2000
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=03f0 Product=0b0c Version=0110
N: Name="BTC USB Multimedia Cordless Kit  "
P: Phys=usb-0000:00:1d.2-2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=03f0 Product=0b0c Version=0110
N: Name="BTC USB Multimedia Cordless Kit  "
P: Phys=usb-0000:00:1d.2-2/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse1 event3 ts1 
B: EV=100007
B: KEY=70000 0 3ff80000 7a c000 1e0000 0 0 0
B: REL=103

```

Note that when (rarely) the PS2 keyboard work,  (as opposed to be frozen with shiftlock light on) 
I also can find this extra snippet at cat /proc/bus/input/devices:
```

I: Bus=0011 Vendor=0001 Product=0002 Version=ab41
N: Name="AT Raw Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

```

It beats me why this PS2 keyboard isn't always recognized.
Why does the "BTC USB Multimedia Cordless Kit " override more generally both ps2 keyboard and mouse?
Anyone can help/suggest?

---

### Post by Cannaregio on 2007-02-13
This seems (googling around) definitely to be a [debian kernel bug]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=b81&q=%28debian+OR+ubuntu%29+ps2+mouse&btnG=Search").

Short history (see posts above for more context):
I have BOTH a keyb+mouse USB and a keyb+mouse PS2
I want to use PS2 stuff to leave USB ports free
PS2 keyboard+ PS2 mouse do not work in my edgy 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
(in fact PS2 keyb+mouse do work 'sometimes' ... without a clear pattern of these "sometimes" I could be able to recognize)

On the otherhand: USB keyboard + USB mouse always perfectly work (funny isn't it?)
But, as said, I WANT to use the PS2 combo instead of the USB combo.

I found a solution that (cross my fingers) seem to work:
simply booting WITHOUT the usb keyb receiver and the usb mouse make my ps2 keyboard and mouse able to work
 
In fact now the devices are recognized:

```
cat /proc/bus/input/devices
```

will now give

```
cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0005 Version=0055
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

While this solution seem simple, why exactly this should happen still beats me. 
In windoze xp AND IN FEISTY AND IN NON GENERIC 386 I can leave both keyboards (USB and ps2) and mice (USB and PS2) connected during boot and they will work both. 
Only Edgy generic (and Dapper 686) seem to have this specific PS2 related problem. Why?

Well, at least my ps2 keyb and mouse both work now... and I have more usb ports free :)

---

### Post by Cannaregio on 2007-02-14
A small add-on
When switching directly back (restart) from windoze xp to Ubuntu the PS2 keyboard and PS2 mouse may freeze (don't work). 
If you then reboot and restart again they will, though.

Why this happens, I don't know, but maybe useful for developers trying to fix this PS2 problem

---

### Post by chickensofdoom on 2007-02-14
So there's no work-around for this at the moment? I'm having the same problem... My ps2 keyboard just displays the numlock key, and nothing on it works. PS2 mouse does nothing. I've tried the keyboard on another ubuntu system, and it works in XP, so I know that isn't the problem. Tried a USB mouse, and that didn't work either. =(

---

### Post by Adam Brockett on 2007-02-17
I've had the same problem as well.  I have a pretty standard setup, besides a ati gfx card that requires me to run the live cd in safe graphics mode.

I have a ps/2 connection for both my keyboard and mouse (they are also wireless, but i don't think that has any effect).

From drudging around the forums, I have found this fix(?) for the keyboard problem.  It seems that if you press keys while the liveCD is booting up, the keyboard seems to work pretty consistently.  Very unscientific, and don't ask me why.  This will at least let you be able to edit configuration files.

As for the ps/2 mouse problems, i've had no luck, besides that it seems to happen exclusively with optical mice.  Driver problem, maybe?  I don't have one of the old rollerball style ones, but if you do, it could sidestep your problems.

If i knew keyboard shortcuts better, or my command-line skills were, well, existent, I'd try this: [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894).  I'm talking about the part where the xorg.conf file is edited.

-EDIT-
Ok, I tried the directions in the thread i linked to, where the mouse driver is changed to evdev in the xorg.conf file.  What happened is the evdev driver seemed to not have any information on "Configured Mouse", and xorg defaulted to a wacom tablet as the input device, then threw a fit when it couldn't find one.
Granted, i did not restart ubuntu like the thread says, as that would over-write the changes (liveCD).  Instead, I simply closed and restarted xorg (ctl-alt-backspace, then Xorg in terminal to restart).  The only phase where i feel that something could have gone wrong is the editing of the local rules for udev, as i don't really understand what is going on there.  Anyone else get any results?

---

### Post by Adam Brockett on 2007-02-18
Through yet more searching, i found this thread: [http://ubuntuforums.org/showthread.php?t=51600](http://ubuntuforums.org/showthread.php?t=51600).
This lead me to this bug report: [http://bugzilla.kernel.org/show_bug.cgi?id=5703](http://bugzilla.kernel.org/show_bug.cgi?id=5703).  It says that a fix has been implemented in kernal version 2.6.16.  I don't know what kernal version ubuntu 6.06 (which is the version i use) has, but this bug report was filed roughly a year ago.  I would assume the fixes would have already been implemented...

---

### Post by 3n1gm4 on 2007-02-18
I have the same problem. I installed debian in the same HD to see if i get that problem, but my keyboard works fine, on debian.

I dont know what "config file" have i to copy in kubuntu but it is so strange!

I installed kubuntu by downloading the "virtual screen keyboard" (i'm missing the name now), and isntalled it. My keyboard works in the installation menu (boot time), but it stops to work after i press enter to "Start or Install ...." 

I have a "microsoft multimedia keyboard 1.0a" but i've tried other 3 keyboard with the same result: all of them worked fine on Windows and on Debian, but not on kubuntu. Why?

Regards, Andrea


EDIT: I used kubuntu 6.10

---

### Post by robophred on 2007-02-19
I have a similar issue.  My usb optical mouse works fine on the livecd, but the keyboard goes through the same issues (numlock on, keyboard completely dead).  I was toying with the idea of installing ubuntu to replace my existing debian install (which works fine, I am using it now).
This is only my second week with linux, so I dont know how it deals with hardware or what commands to get diagnostic info.
I am using Ubuntu live cd 6.10.

---

### Post by hanning on 2007-02-19
Wow! I go away for a few days, come back & I seem to have opened a whole can of worms here!  I haven't had any time to try the various workarounds mentioned, but at least now I knnow I'm not the only one with this problem.  Hopefully this will get noticed and can be sorted for the next release.

CHris

---

### Post by Adam Brockett on 2007-02-19
Apparently the can has been here for awhile, but just hasn't been open reciently.  I think the kernel issue is the root of the problem, but there really is no way around that without recompiling/installing your own kernel, which i don't even think is possible on the live cd.

Also, can someone confirm that the tapping keys during startup makes the keyboard work.  This might just be for the live cd.  It seems like such a random solution, but always has worked for me.  Or am I just going crazy?

Also, I'm using the 6.06 LTS version.  Is this problem present on any other versions.  If i remember correctly, people have stated that it wasn't present in earlier versions (hoary for example).

---

### Post by robophred on 2007-02-20
I used the Herd4 live cd, fixed the issue, as well as other problems I was having with the 6.10 version.

I dont know about tapping keys to have the keyboard function, but in the Herd4 live cd, the monitor shuts off when nautalis loads, and I hitting any keyboard key turns it on again.  This is better than the 6.10, which shuts off the monitor until I hit the power button, then have to cancel the 8 or so 'shutdown' windows that appear.

---

### Post by equestodo on 2007-02-20
](*,) I'm new to Ubuntu... just installed 6.10 and got the same keyboard problem.
No amount of pressing the keys helped.
Keyboard is recognized all during install, setup, bios, and grub boot loader but the moment I hit 'enter' to select Ubuntu to load the keyboard locks. NumLock light is light solid and doesn't change by hitting the num-lock key.
Keyboard also works on other machines and XP on this machine and works in recovery mode.
Even did a complete re-install and same thing.

I can't even get into the server because it asks for my login and I can't type anything.

Please save my sanity... ](*,) 

BTW... it's a P/S2 Keyboard on a Pent. 4  2.4Ghz w/ 1gb RAM.

---

### Post by Adam Brockett on 2007-02-20
I just downloaded the Herd4 release, and i believe it did fix the keyboard issue.  However, my mouse issue still remains.  Where as before it would move erratically whenever the mouse was tapped, then stop working (the keyboard would stop working as well), it now just sits unresponsive in the center of the screen, regardless of my furious mouse-jigglings.

Progress, i guess:-?

---

### Post by jms1989 on 2007-02-20
Hmm, strange I've never had a problem like this. I use a standard 104-key PS/2 keyboard with a USB Logitech mouse on Ubuntu Edgy. They worked fine in dapper as well.

My motherboard is only 2 years old and was widely supported by ubuntu except the wireless card (extracting the firmware fixed that).

---

### Post by Sivart01 on 2007-02-21
I just tried to install ubuntu for the first time and had this problem.  My USB mouse works fine but my PS/2 keyboard freezes after making a selection on the startup screen from the boot cd.

I fiddled with the bios USB settings to see if it helped.  It did, but it may have just been random.  I changed it to detect USB keyboards and disabled legacy support (an option listed in the bios for using USB work in older OS's like MS-DOS).  However, it only worked once and then went right back to not working again after the next boot.

Sorry, I am a newbie and don't know what else would be helpful to know or try.  Hopefully a solution can be found outside of kernel recompiling.

---

### Post by Adam Brockett on 2007-02-21
Alright, I may have found a solution on this thread: [http://ubuntuforums.org/showthread.php?t=179818](http://ubuntuforums.org/showthread.php?t=179818)
As i'm using a liveCd (funny enough, i don't want to install it if i don't know if it will work), i don't know if the changes implemented will work.  If someone with a hard install could try this out, that would be wonderful.  I don't know what effect this will have if the keyboard doesn't work.

> **Micke.Breath said:**
> I found that after I upgraded to Dapper (6.06) my ps/2 mouse that had been working using the workaround above stopped working again - but thanks to others I found the solution.

open a terminal

sudo gedit /etc/rc.local

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart - should have your ps/2 mouse back - again

---

### Post by equestodo on 2007-02-21
Ok, after going home last night and deciding to do an exhaustive search I found a solution that got my ps2 keyboard and mouse working... Thought I would share for anyone else. (I actually found the solution on another discussion that I hadn't seen before and can't re-find it to reference, but the credit goes to them.)

This is written in linux newbie speak, sorry.

At the GRUB loader screen to choose your system, I select the first Kernel and then hit 'e' to edit it.
In the next screen I selected the "/Kernel" line and hit 'e' again to edit it.
At the end of the line between the words 'ro' and 'quiet' I inserted "usb-handoff"
Hit enter to return to the previous screen and then hit 'b' for boot.

This solved it for me and finally got me to the Command line. \\:D/ 
Hope this helps someone else.

---

### Post by Sivart01 on 2007-02-22
I tried your solution Equestodo and it worked.  Thanks.

---

### Post by Sivart01 on 2007-02-22
Oh, and if anyone knows what Equestodo's modication does I would enjoy hearing it.

---

### Post by malicentre on 2007-02-24
I had a similar problem with the Edgy install - i.e., my PS2 mouse/keyboard didn't work.  When I plugged in a USB mouse that worked, but I was still stuck due to the keyboard.  (I didn't have a USB keyboard lying around.) 

I knew it wasn't hardware related as my mouse and keyboard worked fine during BIOS boot and in W2K.  After Googling around I found a tip that worked for me.  In my BIOS settings I disabled the USB mouse and keyboard options, rebooted, and voila both have worked ever since.

Except for this one small issue I was amazed at how easy Edgy was to install.

---

### Post by chickensofdoom on 2007-02-25
I did Equestodo's fix, and it worked quite well. Posting from Ubuntu =)

Thank you so much!

---

### Post by congafx on 2007-02-27
I have a USB mouse and a PS/2 keyboard. Will Equestodo's solution disable my mouse from working?


*edit*
i decided to give it a shot, what the hell its 4am and i am hooked on these energy drinks. well my mouse still works and now my keyboard works. thank equestodos.

---

### Post by dustman on 2007-02-27
Hello


I have a similar problem, my mouse does not work, but the thing is that i have a USB Logitech Mouse, not a PS2 one :|...I wonder if there can be a solution for me also...The funny thing is that mouse works perfectly fine in the first 10sec - 1 min from when I boot, but it suddenly shuts down. It remains lit (it's an optical mouse)...but if I plug it of from the USB (so the light goes off) and then plug it back on, the light does not reappear. Dunno what the problem might be :(

---

### Post by 00h00m on 2007-03-09
adding usb-handoff worked perfectly for me. I have a USB mouse and keyboard and neither worked until I added that bit to the "F6" options during live CD boot.

I am pretty sure that what usb-handoff does is negotiate the the handoff from BIOS to Linux once the BIOS has given over control to the OS.

I still have an issue where my USB mouse stops working at random times during operation and I have to unplug it and plug it back in to get it working again... I am off to look for a fix for that.

---

### Post by Gilgad Drumheller on 2007-03-29
Yep, i can confirm that usb-handoff fixes my PS/2 problems on the LiveCD.
Just make sure you backspace out the little -- they give you when you hit F6.  I just put mine right after "quiet splash" or whatever the last entry was.

---

### Post by dustman on 2007-04-01
Well, I solved the problem with my USB-mouse by adding as boot options : "noapic irqpoll". It works like a dream :)

Cheers!

Radu

---

### Post by Gilgad Drumheller on 2007-04-01
Someone really needs to put up a list of all the boot options and what they do.
Well, come to think of it, i'm sure that exists.  The problem is finding it!

---

### Post by nasch on 2007-09-20
I'm having the same problem.  I'm using the Live CD, Feisty Fawn, and on the boot menu everything is fine, but after it boots into Ubuntu, the PS2 mouse and keyboard are frozen.  I have to hard reset.  I tried the the usb-handoff option, but that didn't fix it for me.  Just to confirm I understand it correctly, in the boot menu I hit F6, delete the -- at the end of the options, and add "usb-handoff".  Then boot using that option.  Correct?  This is on a new HP Pavilion with factory HP mouse and keyboard.  I've checked the CD (actually it's on a DVD but I hope that doesn't matter) for errors.  Unfortunately I don't have access to another keyboard, mouse, or computer.  I would be open to options such as trying another distro such as Debian or something further afield (relative to Ubuntu) if you think that could yield useful information.  Thanks for any help.

---

### Post by Gilgad Drumheller on 2007-09-21
This thread is pretty old, I think I was using the previous version of Ubuntu, or at least a beta release of Fiesty Fawn.  If i remember correctly, fiesty "just worked".

But, yea, the option i used was usb-handoff.  and if i remember correctly you just add it after to boot options.  But it's been awhile.

---

### Post by dustman on 2007-09-23
Well, the problem with the mouse not working persisted in Feisty ( I have a Toshiba Satellite A100-529 ). My first Ubuntu install was Dapper Drake, and the mouse worked, but in Edgy Eft and in Feisty Fawn, it didn't...As I said, if I boot with the options: "noapic irqpoll", the mouse works in all distros. The annoying thing is that every time I install a new kernel, I have to add these options in /boot/grub/menu.lst...I hope that the new release ( Gutsy Gibbon ) will solve this issue.


Cheers!


Radu

---

