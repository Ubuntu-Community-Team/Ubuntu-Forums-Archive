---
title: "ubuntu 10.04 installation problem(mouse and keyboard not working)"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by boss_aadi on 2010-05-09
i m downloaded ubuntu 10.04(Desktop),when i m trying to install

[COLOR="RoyalBlue"]1)[/COLOR] i tried direct installation at the language selection(first step) it self keyboard and mouse r not working...

[COLOR="RoyalBlue"]2)[/COLOR]next i tried live(without installation) mode this time 3 r 4 only keyboard and mouse r worked,after words they r not worked.

[COLOR="RoyalBlue"]3)[/COLOR]After words i searched in Ubuntu forums and tried with **i915.modeset=0 xforcevera** command at installation menu by pressing F6 function key,after words i got error messages like this 
       
 [B]Ubuntu is running in low-graphics mode
EE VERA:Kernal modesetting driver in use,refusing to load
EE No devices detected.[/B]

my system configuration

[B]Intel(R) Pentium(R) D CPU 2.66GHz 
512 Mb RAM
80 GB Hard disk
ATI Technologies Inc RC410[Radeon Xpress 200][/B]

with ubuntu 9.10 all r working properly.

please provide solution....

---

### Post by jishnu.chatterjee on 2010-05-20
I also have the same configuration and the same problem.
I guess ubuntu has removed driver support for my PC, if thats true I am doomed.:(:(:(


PLZZZ HELP.....:confused::confused:

---

### Post by davidmohammed on 2010-05-20
[QUOTE=
After words i searched in Ubuntu forums and tried with **i915.modeset=0 xforcevera** command at installation menu by pressing F6 function key,after words i got error messages like this 
       
 [B]Ubuntu is running in low-graphics mode
EE VERA:Kernal modesetting driver in use,refusing to load
EE No devices detected.[/B]
[/QUOTE]

the i915.modeset is for intel graphics - you have ati graphics.

ati graphics support in lucid isn't brilliant.

Please try booting with
nomodeset 

and report back

---

### Post by boss_aadi on 2010-05-20
thanks for reply...
i tried with **nomodeset** then also same problem.
it showing desktop and mouse and keyboard r not working.

last week i tried with **text based installation** after complete installation key board and mouse r not worked

thanks...

---

### Post by jesusdlg on 2010-05-26
I'm having this issue as well, mouse and keyboard are not working.

Mouse stops working from the vert beggining, and keyboard stops working on the step 2 where I need to select the region.

Please help, this its my 1st try installing ubuntu, thanks for your help.

Jesus

---

### Post by auntiestacey on 2010-05-26
I am having a similar experience in that my keyboard stopped working after upgrade, but my mouse keeps working. I have narrowed it down to the xorg.conf configuration by:
1) choose recovery mode on grub boot loader, then
2) choose failsafe graphics mode

This allows me to sign into my login with keyboard and mouse working, but with minimal graphics so some applications, like games, are not loading.

I still have not figured out why the conf file is failing. Will post update when I solve it.

---

### Post by alterpinguin on 2010-05-27
mouse and keyboard not working in X11 -?-
There are some big changes in the x11-server allowing x11 to start without a keyboard detected.
There are pros and cons about this new method. But it is possible to disable it in the x11-configuration. (in /etc/X11/...)
Search for how to setup X11 to not start if no input-device can be found. Then you will have the chance to login at the normal text-console and look why it is broken.
The pros for this new X11 feature for the autodetecting is easy to understand, people wanted to add input-devices without restarting everything...

one link to explain settings for x11:
> [http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)
-
in a terminal check manual the xorg-version of installed package like this:
 dpkg -l xorg
..
....
ii  xorg           1:7.5+5ubuntu1 X.Org X Window System

---

### Post by Rytron on 2010-05-29
I installed Ubuntu 10.04 today. Both my keyboard & mouse are a ps2 connection. I have noticed that both have frozen without warning a few times. I then connected a spare USB mouse and that worked. The only fix I have found so far is to reboot. This is very inconvenient!

---

### Post by WinRiddance on 2010-05-29
Try this ... worked on my laptop with external ps2/usb mouse and keyboard.
Restart your computer or power off. Then disconnect external mouse & keyboard followed by starting up again _with mouse and keyboard disconnected._ If you're using a ps2 adapter disconnect the usb end of it from the usb port.  Once you get a screen where you're supposed to enter something plug the mouse and keyboard back in to the usb slot. If the lights flash brief for numlock etc. all should be well ...

---

### Post by Rytron on 2010-05-29
> **WinRiddance said:**
> Try this ... worked on my laptop with external ps2/usb mouse and keyboard.
Restart your computer or power off. Then disconnect external mouse & keyboard followed by starting up again _with mouse and keyboard disconnected._ If you're using a ps2 adapter disconnect the usb end of it from the usb port.  Once you get a screen where you're supposed to enter something plug the mouse and keyboard back in to the usb slot. If the lights flash brief for numlock etc. all should be well ...

A reboot fixes the keyboard and mouse. However they both freeze again after a while of use! Does your method ensure the keyboard and mouse don't freeze again?

---

### Post by bweinel on 2010-06-02
Hi all,

I am also experiencing this same issue as of today on one of my Kubuntu machines here with 10.04 LTS. It occurred after I upgraded it from 9.10. After the upgrade, the box will boot to the X sign on screen and the keyboard and mouse are frozen. So it is impossible to sign on at the console. I can ssh into the box from my other system and sign on just fine. Both my keyboard and mouse are PS2 versions and had no prior problems with 9.10. I haven't investigated enough to find the issue... but its almost certainly the X server. I am also running ATI Radeon on the motherboard video, so that may play into it as well. I'll report back once I have time to investigate further. As always... further suggestions will be appreciated. 

cheers,
Bill

---

### Post by drivesoslow on 2010-06-02
I am having the same basic issue.  I was able to upgrade to 10.04 using APT, but now I get to the login screen and the keyboard and mouse freeze within seconds.  I can boot into single user mode and start all of my services fine.  Another weird issue us that it kills my NIC too.

---

### Post by blur xc on 2010-06-02
Check your system bios to see if usb mouse and keyboard are enabled.  That should fix the keyboard not working at the language selection screen...

dunno about the rest.  simple fix -> get a cheap nvidia card.

BM

---

### Post by CmdrDats on 2010-06-03
I'm having a similar problem after I upgraded from 9.10 Karmic - 10.04 on the new kernel (2.6.32-22-generic) refuses to see my keyboard & mouse post-grub. I noticed something about a new light-weight usb driver being loaded? 

When I select an older kernel (2.5.31-22-generic), my mouse & keyboard works fine. I can probably just remove the new kernel out of the /boot/grub/menu.lst, but I'd really like to upgrade....

Hopefully this helps someone find a solution to the problem?

---

### Post by drivesoslow on 2010-06-03
Turns out there is a open bug for my motherboard that requires passing noapic to the kernel through Grub.  Doing this fixed all of my issues.

---

### Post by codinesh on 2010-06-03
same problem here.. if anybody finds a solution please post it here or mail me at  [email]codinesh@gmail.com[/email]  ,thankyou

---

### Post by bweinel on 2010-06-03
I tried the noapic Grub boot option here and still no luck with my issue. The Xserver still accepts no data from the keyboard or mouse when it starts. The good news is that it IS a problem in the Xserver, as when you ssh in and kill the Xserver task the keyboard and mouse both function normally in a standard console terminal session. Even with the Xserver running you can cat the /dev inputs for the mouse and keyboard and any input data from the keyboard or mouse seems to be all there. ....more looking ahead. :)

cheers Bill

---

### Post by bweinel on 2010-06-05
Ok.. after much reading on launchpad and testing on my system, I realized that even though my video output is an ATI, the problem was likely related to the 'Intel freezing' issues in the Lucid Xorg distro which have been previously reported. ([COLOR="Magenta"]see [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) for all the details[/COLOR]) I ran through the items listed there and first tried drivers (no luck), then retrograding the Xserver (no luck there either); so I finally upgraded the kernel to the mainline 2.6.34 kernel (my Kubuntu install was running 2.6.32) 

[COLOR="Red"]Problem resolved![/COLOR]


So apparently something in the 2.6.32 kernel doesn't like the Intel on board ATI chipset on my D850GB motherboard when running Xorg. 

Hopefully this will save someone else the grief of having to troubleshooting this one.....

cheers, Bill

---

### Post by linux_paul on 2010-06-05
Glad it worked for you, kernel 2.6.34 made no difference for me. Hope someone finds a solution soon.

---

### Post by bweinel on 2010-06-06
Did you try the other suggestions listed in the Lucid8xxFreezes write up? ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)) As others report having varying success rates with the different specific fixes. 

In my case, I was really surprised to find that a different kernel resolved my issue and not retrograding the Xorg server. Particularly since mouse and keyboard inputs were working outside of X.

Apparently, this continues to be an elusive issue for the development team which seems somewhat dependent on the specific hardware being used.

cheers, Bill

---

### Post by linux_paul on 2010-06-06
None of the solutions listed worked for me. This is the most frustrating problem I've ever had with any linux distro.

---

### Post by bweinel on 2010-06-06
Sorry to hear that nothing has worked so far. If I can think of anything else I'll pass it along. Hopefully the developers will have a real solution before too long.

I guess in the meantime (and I know this might sound drastic) you can always retrograde back to the 9.10 release if you really need a working system. I was about to that point on mine when I resolved my issue. Fortunately I had a second system up and running here.. so I could leave the one in question broken for a few days in order to locate the problem.

cheers Bill

---

### Post by linux_paul on 2010-06-07
I've considered switching back, I can't really remember any feature in 10.4 that I had to have, just wanted to latest version.

Just for kicks I tried running a live cd of Fedora 13 and it had the same freezing issues as well. So I don't believe this is an Ubuntu problem.

---

### Post by Rytron on 2010-06-07
> **linux_paul said:**
> I've considered switching back, I can't really remember any feature in 10.4 that I had to have, just wanted to latest version.

Just for kicks I tried running a live cd of Fedora 13 and it had the same freezing issues as well. So I don't believe this is an Ubuntu problem.

Are you using a USB mouse? I switched to a USB mouse from a PS2 mouse but kept my PS2 keyboard. I have had no freezes for almost a week.

---

### Post by linux_paul on 2010-06-07
@Rytron
Thanks for the tip, I am using a USB wireless mouse and keyboard. Only the mouse stops working (then sometimes starts working again.)

---

### Post by linux_paul on 2010-06-09
After restarting the Gnome Display Manager (gdm) I have yet to have any mouse freezes.

---

### Post by Rytron on 2010-06-10
> **linux_paul said:**
> After restarting the Gnome Display Manager (gdm) I have yet to have any mouse freezes.

Did you do this?
```
sudo /etc/init.d/gdm stop
startx
```

---

### Post by linux_paul on 2010-06-10
> **Rytron said:**
> Did you do this?
```
sudo /etc/init.d/gdm stop
startx
```
No I opened a terminal inside gnome and issued the command:
```
sudo service gdm restart
```Then logged in again and experience no more mouse freezing. To bad I have to do it every time I login.

I thought it odd that other livecd distros (fedora 12,13 & opensuse 11.2) had the same issue. But after issuing the *restart* command they work just fine too. Running the 9.10 livecd did not have any freezing problems.:confused: I guess those distros have some similar issue I'm not ready to investigate.

Paul

---

### Post by Rytron on 2010-06-10
Cheers linux_paul. ):P

---

### Post by Kansasguy on 2011-08-10
FWIW,   I'm using 10.04 lucid LTS 2.6.32 Kubuntu on an Asus Netbook, (and love it), have upgraded the Kernel several times, and have had this problem with a USB mouse and a wireless USB mouse.  Happens about once a week, but

     seems to happen only when I am typing somewhat fast, and I "think" it happens when I mistakenly hit a key in the lower left part of the keyboard, like maybe the ALT or Windows, or Fn, or Ctrl key.

hope this helps

---

### Post by KurtCho on 2011-08-10
I had a similar problem but it was caused by my powersupply not delivering enought current and then i got a kernel panic but my screen just froze. The symptom was that USB devices would get not enought power so your keyboard light might turn off. Just check and see if that is the problem

---

