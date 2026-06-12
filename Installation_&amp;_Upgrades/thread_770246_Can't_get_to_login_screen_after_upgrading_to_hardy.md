---
title: "Can't get to login screen after upgrading to hardy."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by MasterSander on 2008-04-27
I upgraded to hardy 2 days ago, but when I rebooted it just halts at the login screen. Well actually I don't even get a login screen. The pointer just keeps on being busy. I tried to kill the gtk processes and started xorg manually, because it seemed like it just kept on loading gtkgreeter when I typed sudo top. But when I started xorg I just got a grey screen with a mouse pointer. Perhaps this has something to do with my theme I had in gutsy or something. I changed it for both the login screen and the main theme. Anyone got a possible solution or the same problem?

---

### Post by MasterSander on 2008-04-27
Anyone? I really want ubuntu to work again. I'm not looking forward to a clean install.

---

### Post by catalina on 2008-04-27
Hi there,

Are you using an older computer?  Sometimes it requires the "Alternate Install" cd in order to upgrade.  I am not sure if the version update is intelligent enough to pick up the older drivers.

You should do some browsing regarding /etc/X11/xorg.conf .  You may be able to fix it but you will have to do it from the terminal.

Just to clarify, you do get the Ubuntu splash screen, but it stops displaying as far as the login screen?

I had this problem going from 6.04 to 6.10 and I had to use the alternate install cd in safe graphics mode.

Hang in there, hopefully someone with more knowledge than me will respond.

---

### Post by MasterSander on 2008-04-27
Yeah I only get the orange background with a mouse pointer loading. And my computer is relatively new (6 months), so normally that shouldn't be the problem.

---

### Post by charafantah on 2008-04-27
hi,
i just upgraded from 6.06 to 8.04 it seems to work fine...my machines are a bit old....

the upgrade seems to be fine, but i have the same problem

cant get login screen, just a cursor and a black screen

---

### Post by warped6 on 2008-04-27
YES! Same here exactly. (I started a thread on this same thing before this one popped up.)

---

### Post by piusvelte on 2008-04-27
> **charafantah said:**
> hi,
i just upgraded from 6.06 to 8.04 it seems to work fine...my machines are a bit old....

the upgrade seems to be fine, but i have the same problem

cant get login screen, just a cursor and a black screen

I've the same issue after upgrading gutsy>hardy via internet. I started a separate thread, but perhaps we've all the same issue. I can boot into the recovery kernel, but honestly don't know what to do from there. I added irqpoll to the kernel string in /boot/grub/menu.lst but that didn't help.

---

### Post by Gotit on 2008-04-27
Count me in, I've got the same problem.
I was running Gutsy 7.10 just fine and then decided to upgrade to 8.04
I upgraded on-line and on reboot the Ubuntu splash screen comes up fine, a bunch of lines scroll by and then a blank screen with the "spinning wheel".

Waiting to hear the fix, hope it comes soon :)

---

### Post by chickendude on 2008-04-27
Yep, same here. I've tried a few different things and nothing has seemed to work. I upgraded from Gutsy -> Hardy via the update manager.

---

### Post by MasterSander on 2008-04-27
I'm guessing it has perhaps something to do with my language pack,  what language pack are you guys using? Or an other theme than the default could also cause a problem, did everyone here change their themes?

---

### Post by warped6 on 2008-04-27
My language pack is English. I did change my log in screen not sure what the name of it was but it's the black and white dragon and yin/yang ball.

BTW.. I loaded 8.04 on a different drive and tries to access the original through a USB hub and it says that it can't mount it. No idea if this is a seperate problem or helps point to a solution for this problem.

---

### Post by MasterSander on 2008-04-27
Yeah I also changed my login screen. And it seems a lot of people are having this problem. My graphic card is an intel 945 anyway. Anyone else with this problem got an intel? Oh ... and is there a way to revert to original login screen and default theme, perhaps they are just not compatible.

---

### Post by Gotit on 2008-04-27
I'm also running on English.  However, I haven't changed my Log-in screen.

BTW, if it's of use to anyone in troubleshooting, I tried booting in safe graphics mode and selected dropping to the console option when it was presented.

At the prompt I typed "login" and my user ID and PW when requested.  It logged me in just fine.  I then tried the command 
```
startx
```
in hopes it would fire off "X" once I was logged in and give me the GUI, but no luck.

---

### Post by flippo on 2008-04-27
Hello, this is my first post, so if its not at all helpful I'm sorry.

I had a similar issue after upgrading from 7.10 to 8.04.  My login screen wouldent load at all.  

I replaced the xorg.conf with an old backup I had, and then the logins screen started to load after about 15 minutes of me waiting.  Then I downloaded a new GDM login theme and installed it under Hardy using the graphical login screen manager:
 system > admin >login window then local tab.

After doing this my login screen loads like normal.

Hope this could help somebody, regrettably I don't know enough of how gdm starts to know exactly what this did.

---

### Post by Gakman777 on 2008-04-28
Hello.

I've the similar issue with a brand new install (so no previous backup). It seems that a lot of users encounter this trouble.
This Ubuntu work very well on my desktop but fail to load on my laptop.

My laptop :
Dell Latitude L400 (= Dell Inspiron 2100)
Pentium III M 700 MHz with SpeedStep
chip Intel Integrated ICH 82801AA Ultra ATA/66 EIDE
256Mo PC133-SDRam, -8Mo for graphic card perhpas (don't know)
ATI Rage Mobility M1 AGP2 8Mo
screen 12"1 SVGA, XGA
HDD Hitachi 20Go fully dedicated to Linux
official native CD-Rom drive

I've tried to check the 3 1st options (F6) of the installation boot after reading some forums without any success (acpi=off, noapic, no1apic).

EDIT: my installation language is french, but I've tried in english without solving this black screen.

---

### Post by MasterSander on 2008-04-28
Perhaps it'll come in an update. Meanwhile I'll try flippo's suggestion.

---

### Post by gunbladeiv on 2008-04-28
I think the problem is with the ATI driver, 
If you are using ATI driver, please try refer to my blog as I also encounter the same problem earlier and manage to fix it.

[My Blog About ATI on Hardy Crash On boot]("http://blog.gunbladeiv.com/2008/04/ubuntu-ati-crash-on-hardy-upgrade.html")

But if any how this might not be the case, please let me know, may be i know the other way to fix the issue

---

### Post by MasterSander on 2008-04-28
No I'm using an intel graphics card and I already tried to do a sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Gakman777 on 2008-04-28
I'll try your solution.
Just a question (I'm not an advanced user) : how to do "Simple, just boot into single mode, and do "sudo dpkg-reconfigure -phigh xserver-xorg" " ?
Thank you.

Perhaps has this Hardy Heron a bug with its graphic drivers for Intel or ATI small or old chips ?

---

### Post by gunbladeiv on 2008-04-28
Okay, try this solution. 

Put this line under device section in your xorg.conf
```
Option "AccelMethod" "EXA"
      Option "ExaNoComposite" "false"
      Option "MigrationHeuristic" "greedy"
```
I hope that this will help.  The 3rd line is important.
Tell me if still not solved.

P/s: You can enter safe mode by pressing Esc key on the grub menu list.. and then choose Safe-Mode.  and login to your ubuntu, and just type 'sudo dpkg-reconfigure -phigh xserver-xorg' and enter your password when prompt

---

### Post by Gakman777 on 2008-04-28
I've tried to enter as you said to reconfigure xorg "sudo dpkg-reconfigure -phigh xserver-xorg".
It doesn't change anything.
Actuelly there is a difference : I've the time to see some text just before it shutdown :
_ I see login screen
_ immediateley the screen become black with white letters and write : "Shutting down ALSA..."
_ the PC shut down as before (stand by mode)

I hope that could help you

---

### Post by gunbladeiv on 2008-04-28
gakman777,

Do you use intel chipset too?
and can you login to the login screen normally?
or you had the same problem?

---

### Post by grannyw on 2008-04-28
i guess its some sort of bug,everything run smoothly,i made "SUSPEND" and after that got that login screen,that i've done force reboot and got the normal one

---

### Post by MasterSander on 2008-04-28
I tried editing xorg.conf but it didn't work.

---

### Post by Gakman777 on 2008-04-28
> **gunbladeiv said:**
> gakman777,

Do you use intel chipset too?
and can you login to the login screen normally?
or you had the same problem?


For my Dell L400 its' an Intel 440BX.

Dell Latitude L400 (= Dell Inspiron 2100) :
Processor Intel Geyserville Pentium III M with SpeedStep 700 MHz 
System Chipset Intel 82440BX AGP Set
82443BX PCI AGP Controller 
82371EB PIIX4M 
Intel Integrated ICH 82801AA Ultra ATA/66 EIDE
Memory PC-100 compliant SODIMMs SDRAM -> genuine Dell 265Mo PC100
PC Card (CardBus) Texas Instruments PCI-1410 CardBus Controller 
Zoomed Video PC Card socket 
Video ATI 3D Rage Mobility M1 (Video RAM 4MB)
Audio Crystal CS4281 + CS4297A (AC97 CODEC)
Modem Actiontek (Lucent) 56k LT Winmodem 
NIC 3COM 3C920 10/100 Ethernet card (3C905C-TX compatible) 
12"1 SVGA, XGA screen
+ genuine Dell Multibay CD-Rom 24x
+ Hitachi 20Go 5400 fully dedicated to linux

My problem :
_ I install without any problem
_ when I boot, the laptop goes until the login screen and immediately seems to suspend to Ram. I have that damned black screen, that's why I post here, I think it's the same trouble.

---

### Post by chickendude on 2008-04-28
Yea, neither of those suggestions worked for me either.
After trying to restart X I received this message:
```
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
```

Also, after I hit Ctrl-Alt-Backspace twice, after it boots the second time I am greeted with this message "The greeter application appears to be crashing. Attempting to use a different one." (then nothing happens).

---

### Post by masterscoach on 2008-04-28
Hi,

I upgraded from 7.10 to get the same result.  My case the screen was blue. I played with the TAB key and it causes popup windows to appear.  I ultimately was able to log in.  I just hope I don't go down anytime soon.  Do you have an NVDIA card?  I'm thinking that's the problem.  Until I get into the log in screen, I get default resolution.  I believe what I'm seeing is a small part of a much larger screen and what we need to see if off screen.  

Comments?

---

### Post by Göran Nyström on 2008-04-28
In my new HP L1910 (AMD AthlonX2) I made a partion K: and installed without problem. When starting up the login stopped me, even after repeated install.

What to do ??

---

### Post by chickendude on 2008-04-28
> **masterscoach said:**
> Hi,

I upgraded from 7.10 to get the same result.  My case the screen was blue. I played with the TAB key and it causes popup windows to appear.  I ultimately was able to log in.  I just hope I don't go down anytime soon.  Do you have an NVDIA card?  I'm thinking that's the problem.  Until I get into the log in screen, I get default resolution.  I believe what I'm seeing is a small part of a much larger screen and what we need to see if off screen.  

Comments?
I'm using an NVIDIA card, I just tried that and nothing popped up. I tried typing in my password anyway and hitting enter in case maybe as you say it's off screen, but still no luck. Anyway, the background that I see is the default Ubuntu brown/orangey color (and I had it set up not to ask me for my password when it booted).

---

### Post by MasterSander on 2008-04-28
> **chickendude said:**
> I'm using an NVIDIA card, I just tried that and nothing popped up. I tried typing in my password anyway and hitting enter in case maybe as you say it's off screen, but still no luck. Anyway, the background that I see is the default Ubuntu brown/orangey color (and I had it set up not to ask me for my password when it booted).

I've got an intel graphics card and normally these run smoothly under ubuntu, so perhaps this is just a bug which we're still unable to solve as it seems.

---

### Post by Rallg on 2008-04-28
Did you perform the upgrade from within Gutsy, using the terminal commands? Or, did you re-install from a downloaded CD?

When you re-install, and re-format a partition, the device UUID is changed. That can be a problem if your Grub bootloader is on a different partition (multiboot systems). In some cases, the Grub menu.lst is not updated to reflect the new UUID. Then, during boot, Ubuntu will hang at the point where the boot screen progress bar is moving. It cannot find your partition.

If that is your problem, then you will need to discover the new UUID and manually edit Grub menu.lst. The UUID for each partition can be found via terminal from the live CD or from another Linux installation.

However, if you get as far as the point where the login screen asks you for your user name, then the UUID is not the problem.

---

### Post by MasterSander on 2008-04-28
No I upgraded from gutsy through package manager and as you say:

> Ubuntu will hang at the point where the boot screen progress bar is moving. It cannot find your partition. However, if you get as far as the point where the login screen asks you for your user name, then the UUID is not the problem.

---

### Post by MasterSander on 2008-04-28
If my problem isn't solved in a week or so I'll try a reinstall.

---

### Post by chickendude on 2008-04-28
Yep, I used the update manager as well, updating from Gutsy.

EDIT: And I only have one "partition", my whole HD is dedicated to Ubuntu.

---

### Post by Gakman777 on 2008-04-28
For me it's a fresh new install on a disk which has never been use for Linux before.

---

### Post by MasterSander on 2008-04-28
> **Gakman777 said:**
> For me it's a fresh new install on a disk which has never been use for Linux before.

I'm downloading the ISO as we speak, and I'll see if it works after a fresh install which I'll do in a week like I said above. And elsewise I'll downgrade to gutsy I guess

---

### Post by MasterSander on 2008-04-28
Hardy boots perfectly from the live cd, so I might just reinstall

---

### Post by MasterSander on 2008-04-28
I just reinstalled and everything is working now, well I mean I can login :P My sound and wireless still don't work, had the same prob on gutsy however.

---

### Post by warped6 on 2008-04-28
I also upgraded over the internet. I have an ATI video card. I have the whole HD for Ubuntu. I really don't have the option to reformat and reinstall (I can't loose what is on here. I know dumb.). I will try some of the suggestions when I get back home tonight.

I'm hoping the solution comes up soon!

---

### Post by ichthyostega on 2008-04-28
Hello folks,

just wanted to tell you that we experienced the same problem in our team today after *upgrading* some machines from gutsy and feisty. Surprisingly, the outcome was mixed: in some cases it went without problems, and with two machines we got the problem descibed in this thread.

I can't tell any definitive results, but I managed to get passed the problem and get the desktop working. For all I can tell now, **it doesn't seem to be a problem with the video / display driver**, rather with the session manager. 

Note the symptoms: 
[LIST]
[*]no significant "EE" lines in Xorg log
[*]obviously the basic X starts up (and you see either the gray or coloured background)
[/LIST]

One machine I managed to "cure" (not really, I know ;) ) by installing the xfce-desktop. From this and the symptoms I got the impression that something within Xsession.d is messed up. Thus I managed to get a fresh new Xsesssion.d installed (and moved the existing one away; btw, newbies, please dont' try this if you don't understand what you are doing). After that, I was able to log into both gnome and xfce, but in both cases the session doesn't start up automatically, rather I get a message box telling me that the default XClient could not be stated and that I'll get a xterm instead. Notably, this terminal window has no widow decorations (i.e. no window manager running). Then, in this xterm, if I start gnome-session, or in the case of xfce I start xfce4-session (? I don't recall the full command), then the window manager and everything starts up normally. But I have to do this procedure everytime, it still doesn't start up automatically. I'll investigate further tomorrow.

Just wanted to pass on the information, maybe it's of some use. 

Ichthyo

---

### Post by warped6 on 2008-04-29
OK so I did a little more playing around tonight. I tried Flippo's suggestion and just waited. After about 5-10 minutes the log in screen FINALLY shows up. If I reset it back to a standard one then it boots up in about the usual 2 minutes. So I'm not sure what is the problem but I'm up. If anybody needs any info for debugging this just let me know. I can repeat it on demand.

---

### Post by grkvenom23 on 2008-04-29
I have the same type of issue.  I get the ubuntu symbol with the progress bar and then a black screen with a cursor at the top.  The only difference is i'm still running 7.10.  I started a thread on this too.  But with me i can't run a command in recovery mode.  i enter recovery mode, some code shows up, then a blank line where i can type something in but no command. on my thread someone posted me to try typing this in so this might help you guys if you can enter recovery mode type in:

sudo dkpg-reconfigure xserver-xorg
or
sudo dkpg-reconfigure -phigh xserver-xorg

if anyone can help me out too i would really appreciate it

---

### Post by erginemr on 2008-04-29
> **grkvenom23 said:**
> I have the same type of issue.  I get the ubuntu symbol with the progress bar and then a black screen with a cursor at the top.  The only difference is i'm still running 7.10.  I started a thread on this too.  But with me i can't run a command in recovery mode.  i enter recovery mode, some code shows up, then a blank line where i can type something in but no command. on my thread someone posted me to try typing this in so this might help you guys if you can enter recovery mode type in:

sudo dkpg-reconfigure xserver-xorg
or
sudo dkpg-reconfigure -phigh xserver-xorg

if anyone can help me out too i would really appreciate it

I can guarantee no help, but can you please bypass the progress bar by either:

1. Pressing Alt+F3 when the Ubuntu logo shows up, or

2. Editing the corresponding boot line in Grub (press e) and editing the line with "root" (press e again), deleting the words "quiet splash" and booting (press b to boot).

Try to track down the lines whence the error originates and report back.

---

### Post by chickendude on 2008-04-29
```
* Setting the system clock: no [ OK ] appears
...
* Loading hardware drivers...: [53.238715] intel_rng: FWH not detected

* Setting the system clock
select() to /dev/rtc to wait for clock tick timed out
* Unable to set System Clock to: Tue Apr 29 10:07:35 UTC 2008
* Loading kernel modules: no [ OK ] appears
```
Then it went on to check /dev/sda1 because it's been mounted 30 times without "being checked". I guess that worked out nicely as it gave me time to type things out. Then it skipped by too quickly for me to read anything. Is there an error log somewhere this stuff would be placed in? I checked /var/log/boot and it listed "Warning: Cannot locate the Linux kernel development package for Linux kernel version 2.6.17-12-386. Please install the kernel development package if lining the OSS [Open Sound System] modules fails. [...] Starting OSS failed."

---

### Post by Gotit on 2008-04-29
> **warped6 said:**
> OK so I did a little more playing around tonight. I tried Flippo's suggestion and just waited. After about 5-10 minutes the log in screen FINALLY shows up. If I reset it back to a standard one then it boots up in about the usual 2 minutes. So I'm not sure what is the problem but I'm up. If anybody needs any info for debugging this just let me know. I can repeat it on demand.

I left mine running for 45 min and it's still a tan screen with the "spinning wheel".  When you say you:
> reset it back to a standard one 
are you talking about the login theme?  If so, which one is your standard, Human?  Thanks, still stuck!!

---

### Post by wehrmanweb on 2008-04-29
I was having this same problem last night.

Dell Inspiron 8500, Nvidia graphics card. 
Ubuntu 8.04
Upgraded to 8.04 with package manager
I had a login theme from gnome-look.org [(this one)]("http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883")

After the upgrade on the first reboot it did take a while to get my login screen to display but not too much longer than normal. The same was true for other reboots. This problem didn't seem to be as bad until last night (had been a couple of days without turning the laptop on).

Last night I would get to the gray background with the busy pointer spinning in the center of the screen. Tried restarting X several times, was about to give up. I got up to take the dog out left the laptop running. I came back in 20 minutes later and the login screen was up and waiting for me to login. 

I fixed my problem by changing from my downloaded login theme back to one of the default login screens. Rebooted and all was back to normal. 

Tonight I'm going to try deleting the downloaded theme and reinstalling it.

---

### Post by flippo on 2008-04-29
Since the problem sounds like its coming from GDM having a hard time loading the login window you may consider reinstalling gdm:

```
sudo apt-get install --reinstall gdm
```

I've had to reinstall GDM before and it reset my login window to the default, which seems to be a fix to this problem.  

Good Luck, hope you get the problem solved.

---

### Post by chickendude on 2008-04-29
> **Gotit said:**
> I left mine running for 45 min and it's still a tan screen with the "spinning wheel".  When you say you:

are you talking about the login theme?  If so, which one is your standard, Human?  Thanks, still stuck!!
Same here, I left it running for well over an hour. It started at a standard mouse (I think?) then switched to what I have it customized as (the mouse is a little bigger) and then is stuck at the tan screen. If I hit Ctrl-Alt-Left/Right I can switch between Desk1 and Desk2, and I am able to take screen captures and save them with the PrntScrn button, but no login screen ever comes up.

> **flippo said:**
> Since the problem sounds like its coming from GDM having a hard time loading the login window you may consider reinstalling gdm:

```
sudo apt-get install --reinstall gdm
```

I've had to reinstall GDM before and it reset my login window to the default, which seems to be a fix to this problem.  

Good Luck, hope you get the problem solved.
I just tried this and it didn't seem to do anything for me, unfortunately.

---

### Post by kmullinax on 2008-04-29
I've had the same problem, but I know a little more about how it happened, though I have no idea what to do about it...
Last night I performed the internet upgrade from 7.10 to 8.04 using the update manager.
Everything went fine until it got to the very end of the "Performing Upgrade" section.  It downloaded all of the packages correctly, etc., but when I had only 3 minutes left of the actual upgrade, the computer froze and wouldn't continue to do anything.  In fact, it froze when the language pack "lang-de-pkg" was trying to upgrade.
I finally had to hard boot the system.  Now I have a couple more options from my grub menu.  The first two are the 8.10 standard boot mode and recovery boot mode for 26.16 and the other two are the standard and recovery boot mode for 24.14.
I tried starting up 26.16 and I just get a blank screen.  No matter how long I wait, nothing happens.  Then I tried loading up the 26.16 in safe mode and discovered that the system can't find the boot sector.  It wants me to enter another boot option which answers the question "boot=".
I then tried loading 24.14, and it will start up, but all of my settings from 7.10 are gone (default vid card, etc.)
Does anyone know how I can get 26.16 to boot up properly and finish cleaning up the update without having to do a clean install?

---

### Post by ignun on 2008-04-29
I am having the same problem, I updated from 7.10 to 8.04 via the update manager and everything appeared to go correctly but when I rebooted I just get the spinning wheel for all eternity.

I have tried all the suggestions here thus far and none of them have solved the problem and like someone else here I can't reinstall the machine.

Does anyone have any further thoughts on this and how to solve it?  It's really put a severe kink in my day.

---

### Post by ignun on 2008-04-29
I don't know if this will give anyone a hint as to what the problem is but the following 4 lines are appearing repeatedly in /var/log/auth.log

Apr 29 16:47:27 dylanb-dt gdm[16076]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 29 16:47:27 dylanb-dt gdm[16076]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 29 16:47:27 dylanb-dt gdm[16076]: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 29 16:47:27 dylanb-dt gdm[16076]: pam_nologin(gdm:auth): cannot determine username

---

### Post by mustava on 2008-04-29
Hi Guys,
I'm having similar problem. Was running 7.10 with LAMP installed.
Downloaded the 8.04 alternate cd and while running 7.10, inserted the cd then asked if I wanted to update, said yes, and it started to download (from cd) 970 pkgs, shortly after the pkgs had downloaded, the install started then stopped with an error something like, FAILED TRYING TO OVERWRITE A DESKTOP THEME. Tried a second time with same result.
It wanted to do a restart so went for it, now the pc hangs just before the login screen would appear, completelystuffed, unless someone knows how to patch it.   Hellllllllllll

Mustava..

---

### Post by mastergamer on 2008-04-29
I'm also having this problem after upgrading from 7.10 using the update manager. I have tried to reinstall GDM, edit the xorg.conf file, and it still doesn't work. I can get to a terminal using CTRL+ALT+F1 and login there though (but still no GUI).

---

### Post by davidstillson on 2008-04-30
I upgraded via the upgrade manager as well, and I am having the same issues.  I can get through the login screen, but after credentials are entered, I get a black screen and cursor.

---

### Post by davidstillson on 2008-04-30
> **davidstillson said:**
> I upgraded via the upgrade manager as well, and I am having the same issues.  I can get through the login screen, but after credentials are entered, I get a black screen and cursor.

I installed KDE so that I at least had a GUI and everything works flawlessly.  I believe this to be an issue with Gnome.

```
apt-get install kde
```

and then changed my session to KDE at the login screen.

---

### Post by ignun on 2008-04-30
I have tried removing gdm and reinstalling it but still the same problem.  I fixed the PAM issue (unrelated) by installing a module.  

In Xorg.0.log I am getting this repeatedly (every couple of seconds)  Anyone else noticing anything like this?

in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40971
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): EDID vendor "DEL", prod id 40971
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a00b  Serial#: 844515148
(II) RADEON(0): Year: 2005  Week: 23
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): Serial No: D54285622VGL
(II) RADEON(0): Monitor name: DELL E173FP
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac0ba04c475632
(II) RADEON(0):         170f010368221b78eecaf6a357479e23
(II) RADEON(0):         114f54a54b00714f8180010101010101
(II) RADEON(0):         010101010101302a009851002a403070
(II) RADEON(0):         1300520e1100001e000000fd00384b1f
(II) RADEON(0):         500e000a202020202020000000ff0044
(II) RADEON(0):         353432383536323256474c0a000000fc
(II) RADEON(0):         0044454c4c204531373346500a2000b1

---

### Post by Gotit on 2008-05-01
**ignun**
> I fixed the PAM issue (unrelated) by installing a module. 

I too am getting the same PAM errors in my /var/log/auth.log

What module did you install?  Thanks

---

### Post by The Crazy Parrot on 2008-05-01
I was having a simmilar problem until I tried

sudo apt-get install xdm

it seems that gdm is bugged in the hardy update, once i installed xdm it worked fine, doesn't look as pretty but at least it works.

---

### Post by ignun on 2008-05-01
> **Gotit said:**
> **ignun**
 

I too am getting the same PAM errors in my /var/log/auth.log

What module did you install?  Thanks

apt-get install libpam-smbpass

---

### Post by wehrmanweb on 2008-05-01
Does anyone know of a way to change the login theme from the command line? Reset it to the default? Would it be as simple as deleting the custom themes folder? 

My problem was solved by changing the login theme. I was able to login and change it after letting it sit for 15 minutes or so. 

I would like to see if anyone else can has the same luck.

---

### Post by ignun on 2008-05-01
Was wondering that myself.  I installed xdm and went in and reset the theme but same result....I'm going to go with KDE now I guess until this is solved.  If xdm works then kdm should as well.  I was in xdm long enough to know that the upgrade seems to have broken several other things as well.

If I can get a few things off of the server it might be back to 7.10 for me

---

### Post by stumpalump on 2008-05-01
> **ichthyostega said:**
> Hello folks,

just wanted to tell you that we experienced the same problem in our team today after *upgrading* some machines from gutsy and feisty. Surprisingly, the outcome was mixed: in some cases it went without problems, and with two machines we got the problem descibed in this thread.

I can't tell any definitive results, but I managed to get passed the problem and get the desktop working. For all I can tell now, **it doesn't seem to be a problem with the video / display driver**, rather with the session manager. 

Note the symptoms: 
[LIST]
[*]no significant "EE" lines in Xorg log
[*]obviously the basic X starts up (and you see either the gray or coloured background)
[/LIST]

One machine I managed to "cure" (not really, I know ;) ) by installing the xfce-desktop. From this and the symptoms I got the impression that something within Xsession.d is messed up. Thus I managed to get a fresh new Xsesssion.d installed (and moved the existing one away; btw, newbies, please dont' try this if you don't understand what you are doing). After that, I was able to log into both gnome and xfce, but in both cases the session doesn't start up automatically, rather I get a message box telling me that the default XClient could not be stated and that I'll get a xterm instead. Notably, this terminal window has no widow decorations (i.e. no window manager running). Then, in this xterm, if I start gnome-session, or in the case of xfce I start xfce4-session (? I don't recall the full command), then the window manager and everything starts up normally. But I have to do this procedure everytime, it still doesn't start up automatically. I'll investigate further tomorrow.

Just wanted to pass on the information, maybe it's of some use. 

Ichthyo

I'm thinking this could be related to my problem in my thread [http://ubuntuforums.org/showthread.php?t=777011](http://ubuntuforums.org/showthread.php?t=777011)

Can someone tell me how I could maybe reinstall the session manager completely in recovery mode or from a LiveCD?

---

### Post by harecanada on 2008-05-01
I was having the same problem. Black screen with a prompt. I searched the forms and finally did the following:

sudo aptitude install kubuntu-desktop

It downloaded a ton of stuff and took about45 mins. When it was through it came back to the black screen and the prompt. I rebooted and low and behold I have Ubuntu Hardy. Working great but I wanted Kubuntu. Now I,m trying to figure that out. Also, Adept won't let me make any changes so that's another thing I have to handle. If anybody can help on that it would be appreciated.

---

### Post by Gotit on 2008-05-01
Well, if it's of any help in troubleshooting for anyone I still can't get to the log in screen and here's what my logs show (sorry for the length):

/var/log/syslog
```
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Withdrawing address record for 192.168.57.104 on eth0.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Interface eth0.IPv4 no longer relevant for mDNS.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: New relevant interface eth0.IPv4 for mDNS.
May  1 18:18:39 Home-Ubuntu avahi-daemon[5697]: Registering new address record for 192.168.57.104 on eth0.IPv4.
May  1 18:18:39 Home-Ubuntu NetworkManager: <info>  Old device 'eth0' activating, won't change. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Clearing nscd hosts cache. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
May  1 18:18:40 Home-Ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
May  1 18:18:40 Home-Ubuntu kernel: [  315.348206] NET: Registered protocol family 10
May  1 18:18:40 Home-Ubuntu kernel: [  315.348432] lo: Disabled Privacy Extensions
May  1 18:18:40 Home-Ubuntu kernel: [  315.349927] ADDRCONF(NETDEV_UP): wlan1: link is not ready
May  1 18:18:40 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:18:40 Home-Ubuntu ntpdate[6527]: adjust time server 91.189.94.4 offset 0.078495 sec
May  1 18:18:42 Home-Ubuntu avahi-daemon[5697]: Registering new address record for fe80::216:17ff:fe1e:49a0 on eth0.*.
May  1 18:18:42 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:18:50 Home-Ubuntu last message repeated 5 times
May  1 18:18:51 Home-Ubuntu kernel: [  326.204408] eth0: no IPv6 routers present
May  1 18:18:52 Home-Ubuntu gdm[5628]: WARNING: Couldn't authenticate user 
May  1 18:19:23 Home-Ubuntu last message repeated 18 times
May  1 18:19:27 Home-Ubuntu last message repeated 2 times
May  1 18:19:27 Home-Ubuntu init: tty4 main process (5016) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty5 main process (5017) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty2 main process (5021) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty3 main process (5022) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty6 main process (5023) killed by TERM signal
May  1 18:19:27 Home-Ubuntu init: tty1 main process (6339) killed by TERM signal
May  1 18:19:27 Home-Ubuntu avahi-daemon[5697]: Got SIGTERM, quitting.
May  1 18:19:27 Home-Ubuntu avahi-daemon[5697]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.57.104.
May  1 18:19:29 Home-Ubuntu kernel: [  364.410301] ip6_tables: (C) 2000-2006 Netfilter Core Team
May  1 18:19:30 Home-Ubuntu exiting on signal 15
```
Everything seems OK until I get the "gdm WARNING: Couldn't authenticate user"

So then I went to check my gdm log at /var/log/gdm/:0.log
```
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux Home-Ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 18:18:29 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "i2c" already built-in
(II) Module "ddc" already built-in
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
```

I didn't think this is too bad?  So I went off to check my authentication log because syslog reported an auth error.  Here's what I show in /var/log/auth.log
```
May  1 18:18:35 Home-Ubuntu gdm[5628]: pam_nologin(gdm:auth): cannot determine username
May  1 18:19:03 Home-Ubuntu last message repeated 17 times
May  1 18:19:05 Home-Ubuntu login[5022]: pam_unix(login:session): session opened for user steve by LOGIN(uid=0)
May  1 18:19:05 Home-Ubuntu gdm[5628]: pam_nologin(gdm:auth): cannot determine username
May  1 18:19:26 Home-Ubuntu last message repeated 12 times
May  1 18:19:27 Home-Ubuntu sudo:    steve : TTY=tty3 ; PWD=/home/steve ; USER=root ; COMMAND=/sbin/reboot
May  1 18:19:27 Home-Ubuntu sudo: pam_unix(sudo:session): session opened for user root by steve(uid=0)
May  1 18:19:27 Home-Ubuntu sudo: pam_unix(sudo:session): session closed for user root 
```
Ah ha! I thought, it's PAM causing my problems so I checked /etc/pam.d/gdm
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
```
And I think that looks OK and so does /etc/pam.d/gdm-autologin
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
@include common-account
session required        pam_limits.so
@include common-session
@include common-password
```

HELP!! SOMEONE... PLEASE

---

### Post by gulmer on 2008-05-01
I loaded Hardy from update manager, took all day to load.It loaded OK and rebooted fine, got the login screen,but it was off center.The screen is too far to the right and too low. Fortunately, I can still login,but the options menu is not visible and I like to change from KDE to Gnome desktops.Is there a way to get this login screen centered without too much trouble? Everything else works great, no complaints about Hardy, love the new Firefox 3.

---

### Post by chickendude on 2008-05-02
How would I downgrade to Gutsy from the terminal? Is it as simple as changing every instance of "Hardy" in my sources.list to "Gutsy" and updating?

I tried using XDM instead of GDM and it did give me a login screen, but after that it just froze up.

---

### Post by erginemr on 2008-05-02
> **chickendude said:**
> How would I downgrade to Gutsy from the terminal? Is it as simple as changing every instance of "Hardy" in my sources.list to "Gutsy" and updating?

I tried using XDM instead of GDM and it did give me a login screen, but after that it just froze up.

I wish it were a simple as that. I am sorry but there is no way to downgrade between Ubuntu distros. 

Do you happen to have a separate /home partition? If so, you can save your personal settings for the applications? (I think you can also save them if you tar-zip your home folder, install a clean system with Gutsy Live CD and reopen it to your new /home. But this is a moderately difficult task.)

---

### Post by Gotit on 2008-05-03
Well, I made a little progress... umm... err... at least it's "different" now.

I found in /etc/gdm/gdm.conf the upgrade left the daemon section as:
```
AutomaticLoginEnable=true
AutomaticLogin=ubuntu
```

but in my password file at /etc/password I did not have an entry for "ubuntu".

So I change gdm.conf from "ubuntu" to my login name as it shows in my password file.  This corrected the error in my Auth log of:
```
gdm[5608]: pam_nologin(gdm:auth): cannot determine username
```

Now I get past the "spinning wheel" and I am left with a black screen and mouse pointer.

However, if I set gdm.conf to:
```
AutomaticLoginEnable=false
```
I'm back to the "spinning wheel"

Ahhhhh!!!!

---

### Post by Gotit on 2008-05-03
Well, I had enough of trying to get the update to work.
I did a fresh install from a known good live cd and all is working fine.

Actually, thing are working better in some respects.  My wireless card was found and used without having to use the "ndiswrapper" and my wheel mouse seems to have all the buttons working (left, right, wheel, click scroll, fwd and back) in Firefox (had to select Autoscroll in pref).

So I'm off to installing my most used packages now...

---

### Post by chickendude on 2008-05-04
Is there some way to reinstall the Hardy without losing all my files? I have a lot of things on the computer that are irreplaceable..

---

### Post by Gotit on 2008-05-04
Not that I know of.  

I copied my /Home directory off to another drive and then installed Hardy from the Live CD.  Part of the installation is a reformat of the drive.

For me, most of my apps come from the universe so I can get them back pretty easy using "Add/Remove Software" or the Synaptic Package Manager.  Of course, there is some configuration involved (that's this weekends events!).  

Maybe someone else knows a way around this, but I don't.

Good luck.

---

### Post by UnknownFear on 2008-05-04
I too have this same problem. I upgraded to 8.04, restarted my computer, booted into Ubuntu, but my monitor turns off and I can hear it login to the login screen. But I can't do anything. I can go into the Terminal by hitting CTRL+ALT+F1, but that is it.

---

### Post by fixitdude on 2008-05-04
I am thinking that you had it set to log in directly to a user (no log in password needs to be typed in). So it's going directly to starting X under your user, and the below may apply. (always look at the log too)

On upgrading from Gutsy to Hardy I could get to the log in GUI screen, mouse working and all that but then when I logged in it would show a black screen and then after a little wait return to the log in screen again. (black screen is where X is restarting under the new user, X was working at that point because I had a GUI)

After hours of work on this, here's the solution.

I moved all the ".font" files (from my users home dir) into a new directory (effectively removing them).

(Press ctrl-alt-F3 to get to console, log in as user)
mkdir oldfonts
mv .font* oldfonts/

How I found out is I created a new user and when I logged into that a new KDE started, asking me all the default questions etc. After that I had to figure out what was different from a new user and my old user. A new account didn't have the ".font" files. But of course I figured that out last.

Point is, IF YOU ARE HAVING PROBLEMS, try creating a new user to see if it works then work in "reverse" to figure what the differences are.

(from root, if you wanted to try this new user thing)
mkuser newusername

The logs showed things like "ksplash" and a couple others were segfaulting. 
Really stupid, they should just say bad format in ".font" file or something. Talk about throwing you off the trail.

tail -500 /var/log/messages | less

But I tried a lot of other stuff people suggested here first, so possibly 
something else helped me get to this point, so I will post some of the other stuff that probably won't hurt to do.

Don't forget to make sure you have room left on your HD.
df

Make sure you are upgraded completely on kde
apt-get install kde

If you are using kubuntu, this may help
sudo aptitude install kubuntu-desktop

I didn't use this one but it may help you get X running.
sudo dpkg-reconfigure -phigh xserver-xorg

By the way, this command "sudo update-manager --dist-upgrade" doesn't work if you can't get X to work.

Another error in the log was for "run_parts", so I edited /etc/X11/xorg.conf

Replace line:
RESOURCEFILES=$(run_parts $SYSRESOURCES)

with
RESOURCEFILES=$(run-parts $SYSRESOURCES)

Notice the underscore is changed to "-", this is a known debian bug.

And a side note, for those who tried to switch to "xdm" you can run this
sudo apt-get install --reinstall gdm
---- or ----
sudo apt-get install --reinstall kdm

To get it to ask you which one you want to start with (kdm for the default 
ubuntu style login screen).

Hope this saves you some time. Cost me a whole day. (I may post this in more than one thread, sorry in advance)

---

### Post by chickendude on 2008-05-08
I tried installing Kubuntu, and it got me to the login screen but it didn't bring anything up after i typed my username and password.

---

### Post by erginemr on 2008-05-08
Can it be a misconfigured security/permissions file? Such a thing happened once to me, when I has used "sudo" instead of "gksudo" to start a graphical application with root permissions, which had corrupted either .ICEauthority or .Xauthority, two hidden files in your home folder. For a similar thread:
[http://ubuntuforums.org/showthread.php?t=131546](http://ubuntuforums.org/showthread.php?t=131546)
[http://ubuntuforums.org/showthread.php?t=90361](http://ubuntuforums.org/showthread.php?t=90361)

You can try to delete them by logging in to recovery console:
```
(sudo) rm /home/your_user_name/.Xauthority
(sudo) rm /home/your_user_name/.ICEauthority
```
Using sudo may not be necessary, as you should already be root there.

Give it a try. I hope you will hit the mark this time.

---

### Post by alya84 on 2008-05-08
sign me in too..cant login after upgraded..and i got this error right before it finish upgrade..

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on file-roller; however:
  Package file-roller is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 file-roller
 ubuntu-desktop

---

### Post by davidstillson on 2008-05-08
> **chickendude said:**
> I tried installing Kubuntu, and it got me to the login screen but it didn't bring anything up after i typed my username and password.

you have to click on the gear in the bottom left side of the screen and select "change session"

then select KDE.  When you log in it will ask you if you want to make it your default.

---

### Post by zsuzsika on 2008-05-10
I upgraded to hardy 2 days ago , from 7.10, and it got stuck on 27 minutes before finishing , and I had to reboot. Since then nothing works. Just a red screen
I upgraded from update manager have a dell 6400 n series nvidia video card, Intel board, had changed the login ... 
I tried to download the live cd from the homepage but it would not read it. I am not a programmer , I can install things with a dialog and i cant use the terminal. so how can I save my life inside of my computer (not just data also bookmarks and passwords ) 
Help me

---

### Post by Gotit on 2008-05-11
zsuzsika> I tried to download the live cd from the homepage but it would not read it.
When you copied the download to a CD did it "explode" the ISO file or did it just copy the downloaded ISO file to the CD as an ISO?  You can tell by dropping the CD in another computer and browsing it.  If there are multiple files/folders on the CD it should be bootable.  If it's just one ISO file you need to re-burn the CD with a program that will explode out the ISO.

Once you get a bootable CD, when booting your system you will probably need to press an "F" key to bring up the boot drive menu option from BIOS (mine is F10).  It should show the "F" key to hit when you first turn on your computer.  Once you get the boot drive menu, select the CD/DVD drive and your system should boot from the CD.

---

### Post by kenny1948 on 2008-05-15
> **chickendude said:**
> I tried installing Kubuntu, and it got me to the login screen but it didn't bring anything up after i typed my username and password.

This is what happened to me also. However I got an error message login failed. Then it happened. Tried rebooting, but it starts up with progress icon then blank screen. Can hear hard drive whirring away though like it's doing something.

---

### Post by chickendude on 2008-05-19
Alright! So I've got Kubuntu working (well, most of the apps that I downloaded in Gnome don't work as well as a few other applications, but it boots up and I can access the internet/my files!), but I'm not quite sure how to get Gnome working again. I think I'm just going to try uploading my files to an online storage place and then doing a fresh install..

---

### Post by KBA3AP on 2008-05-21
Hi, I've had similar problem - i had to login twice in a row in order to get into Hardy, after upgrading from Gutsy, and that is considering that i didn't change anything at all in the themes. So i checked the system log and found weird things in there and eventually i ended up [_on this page_]("https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990"). I think your problems have something to do with that as well. Installing libpam-smbpass fixed my issues, so I hope it fixes yours.

---

### Post by GlennW on 2008-08-28
Hi,
I don't know if this is the right thread but being the n00b that I am, I think I've buggered hardy good, at least for my skill level. 

I have a nvidia geforce 6200 graphics card. It has been working fine although after upgrading to hardy I couldn't find any way to tweak any settings. Every time I wanted to access the nvidia settings via the applications menu, it said something to the effect that it couldn't find the directory or path... So, I thought that either upgrading via envy or synaptic would give me access. Well, to make a long and frustrating story short, I've managed to get xorg so screwed up that boot up doesn't happen. If I use the recovery mode and then run through the options, I'm still at the same place. My only option appears to drop to the root shell prompt. I'm thinking that I need to edit xorg from there to at least allow me to bootup but for some reason, I'm not able to access xorg from the root prompt. 

Previous my best resolution was 800x600. I have a Samsung 205bw which has a native resolution of 1680x1050. I really need some help to get it back. 

Thanks for your help.

---

