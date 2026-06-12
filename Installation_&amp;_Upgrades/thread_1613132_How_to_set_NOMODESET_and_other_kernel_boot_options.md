---
title: "How to set NOMODESET and other kernel boot options in grub2"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by P4man on 2010-11-04
On some hardware configurations, you need to set some kernel parameters for ubuntu to boot or work properly. A common one is nomodeset, which is needed for some graphic cards that otherwise boot in to a black screen or corrupted splash, acpi_osi= to fix lcd backlight and other problems, and noapic and nolapic to work around various ACPI BIOS issues. In this how to  I will explain briefly what this is and how to do it.

This how to applies to ubuntu 10.04 and 10.10. It may not apply to wubi, I dont know how to do it in wubi.
(update, see post #8 for the differences with wubi)

[SIZE="4"]
**What are  these options?**[/SIZE]
[SIZE="2"]
**nomodeset**[/SIZE]
The newest kernels have moved the video mode setting into the kernel.  So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a **black screen**. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent, just for one boot until you installed the nvidia drivers.

[SIZE="2"]**acpi_osi=**[/SIZE]
This option frequently solves problems with **LCD backlight**, fan control problems and misreporting of thermal events. What I understand it does (but corrections are welcome), is prevent the kernel from reporting to the bios that its any windows version the bios asks for. By default, the kernel pretends to be all windows versions, that way we are certain the bios executes all the code needed to initialize the hardware. Unfortunately, some bioses contain fixes to fix problems with specific windows versions (notably vista) that arent needed or dont work for other OS's. Setting ```
acpi_osi= 
``` (nothing behind the = sign) as boot option makes the kernel not respond to osi queries.

If the bios has provisions for Linux, you can also try
```
acpi_osi="Linux"
```

Or you can try 
```
acpi_osi="Windows 2006"
```

To make the kernel pretend its vista and make the bios execute routines on machines that require them.

[SIZE="2"]**acpi=off**[/SIZE]
This disables ACPI completely. 
Note: this may not work with all computers and will disable a lot of useful (or even needed) features. In some cases it may even disable some crucial features, like.. fans. Be careful with this option, it might cause your machine to overheat if the fans no longer turn. Think of this as a last resort. Also note some machines require **acpi=ht** instead.

[SIZE="2"]**Noapic and nolapic**[/SIZE]
noapic and nolapic kernel options instruct the kernel to not use  certain programmable interrupt controllers. To understand what that means exactly requires a deep knowledge of PC hardware, I will not go in to that here, Ill limit myself to saying on some bioses, especially for older systems, there are problems in the implementation  of this and it may be necessary to disable either or both to cure a wide range of  obscure problems, often but not always related to **keyboard and mouse and power management (standby/resume issues)**.

**[SIZE="2"]vmalloc=xxxM [/SIZE]**
In some cases kernel drivers can not be loaded due to a lack of virtual addressing space on **32 bit** systems. Logs will show errors like
```
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

```
Details can be found here:
[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

This has been reported by extremejosh  who's machine failed to load the  restricted nvidia drivers on a geforce 7350 and appears more or less common if you have several tv tuners. Increasing the size of vmalloc to 196 or even more may help in such cases.

[SIZE="4"]**How to enable kernel options on the livecd (before install)**[/SIZE]

If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom:

[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see this menu:

[IMG]http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png[/IMG]

If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key. You can close the menu with escape key and resume booting by selecting the option &#8220;try ubuntu without installing&#8221; (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).

If you need to add kernel options not provided by the F6 menu, you can just type them in at the end of the boot options line.

**Important**: if you select a kernel boot option from the F6 menu and proceed to boot and later install ubuntu, those boot options will NOT be applied to your installation. If you needed nomodeset to get the livecd to boot, you will almost certainly need it again once you reboot in to your fresh install. See below how to set those options on an installed ubuntu. And perhaps click the &#8220;affects me too&#8221; on [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526")where I request these settings be applied (semi) automatically.

[SIZE="4"]**How to temporarily set kernel boot options on an installed OS (not wubi)**[/SIZE]

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:

[IMG]http://img5.imagebanana.com/img/hy5mw3s9/dgfdgRunningOracleVMVirtualBox_016.png[/IMG]

Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the  line that starts with

```
linux /boot 
``` and press END keys to position your cursor at the end of the that line usually ending with &#8220;quiet splash&#8221;. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot :D ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

**Important:** setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)

[SIZE="4"]**How to permanently set kernel boot options on an installed OS (not wubi)**[/SIZE]

To permanently change the default kernel boot options, press ALT+F2 or  open a terminal from system > accessories > terminal. Type in the following command:

```
gksudo gedit /etc/default/grub
```

a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX=""
```

add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX=""

```

Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR="Red"]\"[/COLOR]Linux[COLOR="Red"]\"[/COLOR]"
```

Now in the terminal, run the following command to update your grub configuration with the new default settings:
```

sudo update-grub
```

Thats all.  

To do: wubi part.

---

### Post by sanderd17 on 2010-11-04
great tutorial, 

I will put it in my signature. Maybe you can tell something about the "acpi=off" option too.

---

### Post by P4man on 2010-11-04
acpi=off really is a "nuclear bomb" solution IMHO. APCI is an essential part of any somewhat modern PC and turning it off can cause bigger issues than it solves (disable fans etc). If you need it, the above tutorial can help in setting the option, but Im reluctant to advertise the option. acpi_osi= is one option I may  add later though.

---

### Post by sanderd17 on 2010-11-04
I needed to use the acpi=off option with ubuntu versions 9.xx and recently, I've seen someone else who needed to use it with 10.10. Can acpi_osi=... solve the same problems? And what are the differences between the two?

---

### Post by P4man on 2010-11-04
acpi_osi= doesnt disable turn off all acpi functions. It just makes the kernel not pretend its windows to the acpi bios and that can avoid problems with bioses where windows errata are fixed in bios for a specific windows OS (by default linux will pretend to be any windows version). More details here:

[ftp://ftp.suse.com/pub/people/trenn/ACPI_BIOS_on_Linux_guide/acpi_guideline_for_vendors.pdf](ftp://ftp.suse.com/pub/people/trenn/ACPI_BIOS_on_Linux_guide/acpi_guideline_for_vendors.pdf)

adding acpi_osi= commonly fixes problems with LCD backlight, due to a bug in vista that vendors "fixed" in the bios.

---

### Post by quercus54 on 2010-11-07
Really a valuable how-to. It's only thanks to it, that my new and rather expensive Panasonic Toughbook became usable for me.
Meanwhile I made the boot option "acpi_osi=" permanent in the proper place /etc/default/grub, as explained above. My gratitude to P4man !
:D

---

### Post by P4man on 2010-11-08
Can anyone with wubi experience point me in the right direction how to do this in wubi? Wubi uses grub4dos right? Or windows bootloader chainloading grub4dos ?

---

### Post by bcbc on 2010-11-08
Wubi overrides are identical to what is in post #1 - once it is installed. 

To override on the initial install is different and to complicate things, since Ubuntu 11.10 there are two distinct methods to install with Wubi. **NOTE**: this initial Wubi-specific override is effective only for a single boot. After that you need to either make it permanent or continue to override as shown in post #1.

**Method 1** (traditional way, if you downloaded the ISO or ran installed from a CD): after the windows part is completed you reboot to do the actual install (ubiquity is setup to auto-install to the defined virtual disk based on settings provided to wubi.exe in windows). 

The first time you select Ubuntu from the windows boot manager, you'll see 
```
Completing the Ubuntu installation
For more installation options, press ESC now 5...4...3...2...1

```

When you press ESC you get 5 options...
```
Normal mode  (the only option that uses 'quiet splash'; the rest all run ubiquity in debug mode)
Safe graphic mode (uses 'xforcevesa')
ACPI workarounds (uses 'acpi=off noapic nolapic')
Verbose mode (no special override, just debug mode)
Demo mode (I don't know what this is supposed to do but it doesn't work at all on my test computer)
```

You can select any one of the above, however safe graphic mode doesn't do much for the nvidia problem, so I prefer to just hit 'e' on the first entry (Normal) and add 'nomodeset' prior to 'quiet splash'. Then CTRL+X to boot.

The full entry looks something like this after adding nomodeset (local settings for language/keyboard differ):
> linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt [COLOR="Red"]nomodeset[/COLOR] quiet splash  boot=casper ro debian-installer/locale=*en_US.UTF-8* console-setup/layoutcode=*us* console-setup/variantcode= -- rootflags-syncio
initrd /ubuntu/install/boot/initrd.lz


In the same way as the non-wubi install, _the override is only in place for as long as the installation process_. After the unattended install the computer reboots, and the next time you select Ubuntu you get a normal looking grub menu (looks identical to normal installs at a high level) and _you have to again apply the override as described in post #1_. After that, either install drivers, or override using permanently using /etc/default/grub.

**Method 2**:
New with release 11.10, if you run wubi.exe standalone it will download a preinstalled image while in Windows, and there is no 2nd stage install anymore. But on the first boot there is no way to override boot options on the fly. You have to do it in Windows by editing the file: \ubuntu\install\wubildr-disk.cfg

It looks like this:
> loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
search --set=diskroot -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $diskroot
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk preseed/file=/ubuntu/install/preseed.cfg wubi-diskimage ro quiet splash [COLOR="Red"]nomodeset[/COLOR]
initrd /initrd.img
boot
Add boot options after "quiet splash" and then save before rebooting into Ubuntu. I recommend using WordPad (write.exe) as the file has linux style line endings.

In the same way as the non-wubi install, _the override is only in place for the first boot_. However, with Method 2 wubi installs, you can make the override permanent as soon as it's booted. Refer to post#1 for specific instructions on how to do this... i.e. install drivers, or override permanently using /etc/default/grub.

**NOTE**: the grub menu is now hidden by default on Wubi installs. Especially with method #2, if it's not working make sure you hold down the *Shift* key after selecting Ubuntu. This tells grub to display the menu. If you get that grub menu, then you need to follow the override instructions from post #1.

---

### Post by P4man on 2010-11-08
Thanks a lot bcbc. Ill incorporate that info soon.  First Im gonna see if I can mess up my windows VM by installing wubi so I can actually test it (and grab some screenies).

---

### Post by mahy on 2010-11-09
Perfect idea! Although the "nomodeset" option didn't work at all (caused my ubuntu to run in low-graphics mode), the "acpi_osi=" on the other hand really solved all my ACPI problems, such as screensaver working erratically, battery state not reflecting reality and brightness keys not working (Toshiba Satellite A300)! You're a genius!

---

### Post by Mike_tn on 2010-11-09
Woah, that's great. All the stuff I was wondering about lately. Could not figure out why Ubuntu gave no boot options any more. Thanks.  You also helped because I am running Ub10.10 on a new Dell-Intelchipset laptop, runs great, only needed a wireless fix. But now trying to get it to run also via Persistent 8GB USB on my 2006 hp desktop, with its nVIDIA chipset, and offline.  Walls everywhere on that effort. I can't tell you how many times I reinstalled it on the USB. 
things to do lists
... sudo nvidia-xconfig....pray a lot. Then throw it in my home desktop machine. Then add all my laptop's deb packages to the offline hp. I'll be surprised if it works!  I can always use Mandriva on the hp though, it comes with working nVIDIA drivers. But I'd rather stick to one distro. My brain might spill open if I try to put too much Linux in it ....too late, goodnight.

UPDATE:it didn't work.

---

### Post by adilrasheedonline on 2010-11-29
[SIZE=4]**How to temporarily set kernel boot options on an installed OS (not wubi)**[/SIZE]

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:

[IMG]http://img5.imagebanana.com/img/hy5mw3s9/dgfdgRunningOracleVMVirtualBox_016.png[/IMG]

Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

------------------------------------------------------------------------------------------------------------------------------------------------
I have a duel boot machine (Ubuntu 10.04 and Windows XP) DELL Precision M4400. Yesterday I updated my linux system and after that the screen goes blank after the grub menu if I choose to boot my linux. I see two options: Linux and Windows in the grub menu but when I highlight the Linux option and press "E" nothing happens.  I booted my computer with a live cd of Ubuntu and then changed the etc/default/grub file of the already installed ubuntu OS. I have two questions now:

1. Why did the "E" key did not work ?
2. How can I run grub update of the already installed system.

---

### Post by bcbc on 2010-11-29
> **adilrasheedonline said:**
> [SIZE=4]...I have two questions now:

1. Why did the "E" key did not work ?
2. How can I run grub update of the already installed system.

It sounds like you are describing the Windows Boot Manager, not GRUB - in which case you cannot edit the entry and it wouldn't help anyway (you can confirm this by looking at the top of the screen - it will say Windows Boot Manager or similar). Which means you installed with Wubi... and there is a grub update out on 10.04 that is breaking wubi installs. Look at my comment here: [https://answers.launchpad.net/wubi/+question/135755](https://answers.launchpad.net/wubi/+question/135755)

If you need more help I suggest you create a new thread as it doesn't relate to this one.

---

### Post by rmcban on 2010-12-25
For those who might be interested, here's my scenario: 
Dell Inspiron 17R, Ubuntu 10.04, would not shut down (hang) nore go into suspend (just did not do anything) 

Started adding stuff to /etc/default/grub and hereis what I got:

nomodeset -> bombed and X would not start anymore. Had to remove it.

acpi=off -> shutdown ok (fixed) but no sleep options anywhere. Almost there.

acpi_osi=\"Linux\" -> perfect, everything works

Thanks to the original poster
rmcb

---

### Post by mackiecc on 2011-02-11
I'm using Ubuntu 10.10 Kernel 2.6.35-25 on Lenovo Thinkpad SL300. The System failed at suspend to ram forcing me to do a cold start. Syslog said "ACPI: BIOS _OSI(Linux) query ignored" before freezing.
I added acpi_osi=\"Linux\" to the boot options as described above and now it's working perfectly. Syslog says "ACPI: BIOS _OSI(Linux) query honored via cmdline" now :)

Thanks a lot!

---

### Post by Wim Sturkenboom on 2011-04-12
This was the last piece of info that I needed to get grub2 in Ubuntu 10.04 configured with nomodeset so I could get my Geforce 8400GS working.

Thanks so much

---

### Post by jpantin on 2011-04-12
after much angst #8 solved the problem for a dual gpu 4870X2 card as well. thanks!

---

### Post by glococo on 2011-05-02
Hi,

The best workaround for solving backlight ISSUE was for me:

Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local

```
gksudo gedit /etc/rc.local
```

2) Add the command before EXIT 0

```
setpci -s 00:02.0 F4.B-0
```

3) Restart.

You should now be able to boot in UNITY where nomodeset was unable.

---

### Post by MAFoElffen on 2011-05-02
If you don't mind, I referenced this thread from this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I think they go together hand-in-hand.

---

### Post by klpsr on 2011-05-13
Hello,

I have an old HP Vectra VL420 with 1.5GB memory and ATI Rage graphics card.

I can't upgrade from 10.04 to 10.10 or install 11.04 from CD.

The restart, for 10.10, after installation hangs with a black screen and for 11.04 the installations  hangs with a black screen after displaying the word "UBUNTU" with moving dots below it.

I have tried interrupting the boot process and when I press the function keys the choices are displayed, like noapic, nolapic when I press F6.  But none of them has really helped me to boot the system.
Any suggestions will be greatly appreciated.

===================

Since I posted the above, I haven't received any suggestions.  But since I managed to solve my problem, I thought it is worth adding the following for the benefit of any  with the same problem to try.

I came across the post by MAFoElffen ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)) and with the suggestions in the post I managed to install
Ubuntu 11.04 directly from Ubuntu 10.04 using a LiveCD.
All I needed to do was interrupt the boot as outlined in the post, get into the grub and boot with the boot option xforcevesa!

It only took me to 3 days to install Ubuntu 11.04!  

Good luck.

---

### Post by Supergibbon on 2011-05-20
Hi,

Chances are this is something really easy and stupid, but I'll blame it on being a newbie.  
I got the 'Out of range' bit when trying to install 10.10 and have followed this threads advice on adding nomodeset.  It's let me do everything as said, but then on booting asks for my login and password and takes me to a command prompt ie. iaintatam@supergibon:~$  rather than booting into the desktop.  'Welcome to Ubuntu!' it says - ummm...yeah...not the Ubuntu that I know from my laptop.  How do I get from there to the actual operating system?

cheers

---

### Post by P4man on 2011-05-25
"out of range" sounds like a message your monitor would display when the pc is setting a resolution and refresh rate the monitor can not handle. Rather then using nomodeset, try removing the "quiet splash" option in the boot options. That will give you a textual boot, and hopefully allow the graphical login.  What videocard do you have in that machine?

---

### Post by Supergibbon on 2011-05-25
Cheers for answering P4man.  I've tried getting rid of the quiet (there was no 'splash' part or " marks on my grub boot), but that led to 'out of range' again, and nomodeset without the quiet boots you back to the terminal.  I tried lspci once there again and I'm guessing the graphics card line must the the one - 
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200....rev b2) (there's a figure or 2 disappears off the side of my screen between MX200 and rev b2 on the next line).  It's a pretty old computer now - partly why I was trying to move to linux, see if I could get it running a bit faster again.

---

### Post by Bobrm2 on 2011-06-05
I don't know if I'll get an answer, but I have a new install, all new. Ran Gparted and tried to install Ubuntu 11.04, with a ISO. Black screen with white cursor in upper left. then nothing for 36 hours and counting. Believer it is the video card, because, and after restarting many time I finally was able to see "Searching NVRAM".

   But how can I get into a terminal, there's no operating system on the HDD. The partition is /dev/sda.

  Is there someway to just start over, wiping the disk. Going to the CMOS on the motherboard and switching the jumpers?? 

  Help most appreciated.

Bob  R

---

### Post by az-mah-ta-mahi on 2011-06-08
I am neither programmer nor software developer, but am both resourceful and interested in using this operating system (11.04). I once ran Ubuntu on a PC a few years ago, but whatever skills I learned at the time seem dully distant in the brain now (ust establishing my laymanship)

The modeset worked beautifully on the live disk, and I got it up and running, but when I rebooted after premanently installing the OS, all I get is a black screen with a thick, fuzzy purple bar. I guessed this was due to the same problem, but here I encountered a catch. I didn't know how to open the terminal to input the code provided in this tutorial to make the permanent change since I couldn't see anything.

Since my graphics card was the problem, I found what I needed to do here [http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/)

Can you edit this tutorial to include the step between the live disc experience and installation that someone like me would miss as a regular user?

---

### Post by Blasphemist on 2011-06-23
> **rmcban said:**
> For those who might be interested, here's my scenario: 
Dell Inspiron 17R, Ubuntu 10.04, would not shut down (hang) nore go into suspend (just did not do anything) 

Started adding stuff to /etc/default/grub and hereis what I got:

nomodeset -> bombed and X would not start anymore. Had to remove it.

acpi=off -> shutdown ok (fixed) but no sleep options anywhere. Almost there.

acpi_osi=\"Linux\" -> perfect, everything works

Thanks to the original poster
rmcb

I just wanted to mention something about the acpi_osi parameter mentioned in this thread. What is shown here is the correct entry, and not what you'll often see. The back slashes are the proper escape characters to allow the parser to properly write acpi_osi="Linux" to grub. So, this is the correct entry.
```
acpi_osi=\"Linux\"
```
This is often used when solving certain graphics issues and for me and some others it solved my fan control issue.

---

### Post by kamakazi20012 on 2011-07-06
Would someone explain to me what "wubi" is?  Great how-to, I plan to try those out on the eMachine with all on-board nVidia components (nForce 2 architecture).

---

### Post by mörgæs on 2011-07-06
> **kamakazi20012 said:**
> Would someone explain to me what "wubi" is?

I guess a question like this is best answered by some self-studying. There are lots and lots of web pages on Wubi.

---

### Post by amjjawad on 2011-07-06
> **kamakazi20012 said:**
> Would someone explain to me what "wubi" is?  Great how-to, I plan to try those out on the eMachine with all on-board nVidia components (nForce 2 architecture).

[www.google.com](www.google.com)

---

### Post by Bobrm2 on 2011-07-06
Mark my original question "Solved" I did not have a valid disc ISO, thus computer was waiting for setup information that was not forthcoming. Taking my own advice "Always check the switch first!"

---

### Post by iRide113 on 2011-07-11
> **P4man said:**
>  

Now you can type in additional kernel options like nomodeset (**please dont make the same typing error I made for this screenshot** :D ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

**Important:** setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)



I guess I am missing something... What did you mess up on? :confused:

---

### Post by Blasphemist on 2011-07-11
Ah, another spelling challenged person. :)

nomodes**e**t

---

### Post by P4man on 2011-07-13
> **az-mah-ta-mahi said:**
> 
Can you edit this tutorial to include the step between the live disc experience and installation that someone like me would miss as a regular user?

If you read carefully, its already explained.

---

### Post by P4man on 2011-07-13
> **Blasphemist said:**
> I just wanted to mention something about the acpi_osi parameter mentioned in this thread. What is shown here is the correct entry, and not what you'll often see. The back slashes are the proper escape characters to allow the parser to properly write acpi_osi="Linux" to grub. So, this is the correct entry.
```
acpi_osi=\"Linux\"
```
This is often used when solving certain graphics issues and for me and some others it solved my fan control issue.

You need the escape characters when editing grub.cfg file. I mention that near the end of the post, giving pretty much the exact same example :) You do not need them (and it may even not work) when editing the boot options while in grub.

---

### Post by 007casper on 2011-07-25
I originally posted here without knowing this thread
[http://ubuntuforums.org/showthread.php?t=1792765&page=2&](http://ubuntuforums.org/showthread.php?t=1792765&page=2&)

I am on kubuntu 10.4.3 kubuntu

I am a bit stuck.  I took out my video card.  Because I cant get to error screen, or an option to restart x server etc with the card installed.

I hooked up the monitor to on board dvi.
I got the regular error message etc.  Then,  I chose "Run Ubuntu in low graphics mode for just one session"

Then, on console, I added each line one at a time.
> 
cd /etc/default/
sudo su
vi grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
:wq
exit
sudo update-grub

shutdown.  Disconnect power. Install video card.  Power on.  White bars.

Shutdown.  Disconnect video card. Hooked the monitor to on board.
> 
cd /etc/default/
sudo su
vi grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi="
:wq
exit
sudo update-grub

Install video card, nothing. 

Uninstall video card, Power off, on board, power on 

> 
cd /etc/default/
sudo su
vi grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
:wq
exit
sudo update-grub

nothing

it passed the white bars. However, I have the black blank screen.

Any ideas?

I really appreciate it.

I am thinking of trying acpi_osi="Windows 2006" what is the exact line?
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi="Windows 2006""
```
is that correct?

---

### Post by P4man on 2011-07-25
That syntax is not correct; you need to escape the quotation marks, so it would look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Windows 2006\""
```

(I mentioned that in the first post btw, near the end).

Secondly, it might help if you told us what videocard you are using.

Lastly, try pressing control+alt+f1. Do you get a fullscreen terminal? If so, log in, and try

```
startx
```

FWIW, I had a similar issue today. Turned out I forgot to connect the PCI-E power connector. nVidia driver told me that nicely when I ran startx, it only worked in 2d/text mode due to lack of power.

---

### Post by 007casper on 2011-07-25
thank you so much for getting back.

I have Zotac ion graphics card, PCI Express x1, 512MB DDR3, PhysX by Nvidia, OpenGL 3.2, Dual Link DVI.

<Ctrl><Alt><F1> dont get full screen terminal.  I havent tried windows 2006 line yet.  I am going uninstall the card, and use on board to change the grub.

I have a mini-itx dq45ek intel motherboard. The motherboard cant handle my cinema apple display. So, I have Zotac ion graphics card.

---

### Post by 007casper on 2011-07-25
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
GRUB_CMDLINE_LINUX=""
```

I # on grub_hidden timeout=0

now I am able to get the grub menu, after bios loads.  Still cant do ctrl+alt+f1, however, I am able to get to grub.


for zotac I found these instructions, however, I am not sure how to go about it.  Down below it says "load grub at boot and edit your kernel boot line, preferably one of the single user mode lines."  

I am not sure where to put this line.
add: "vga=ask nomodetest nouveau.blacklist=yes" to the kernel parameters; 

is it the same line as GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""

> I installed this on my AMD Opteron workstation (which only has PCIe x1 and x4 slots). To install 

you must do this:

load grub at boot and edit your kernel boot line, preferably one of the single user mode lines.
add: "vga=ask nomodetest nouveau.blacklist=yes" to the kernel parameters

Choose F00 (eff zero zero) as the video mode. When it boots, I chose 'netboot'.
I then did this:
sudo apt-get purge remove xserver-xorg-video-nouveau

I also edited /etc/modprobe.d/blacklist.conf and added:

blacklist nouveau

When I rebooted I found that I needed to boot with special parameters still. This time use a 

normal boot mode (full multiuser graphical boot) but add this to the kernel boot line:
vga=ask nouveaublacklist=yes

I again chose F00 as the mode but Ubuntu booted graphically anyway. From here I could go to 

System -> Administration -> Third-Party Drivers and install the Nvidia driver.

It's unfortunate that nouveau crashes on this card, but the card can be made to work

???

---

### Post by 007casper on 2011-07-25
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""

I have added vga=ask nomodetest nouveau.blacklist=yes

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=ask nomodetest nouveau.blacklist=yes acpi_osi=\"Linux\""

it stated ask legacy no longer supported

---

### Post by 007casper on 2011-07-25
I really appreciate all your help.

I tried all variables one at a time.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\"
and it didnt work for my video card.

but for me vga=0x101 worked.  It posts a funky message during boot.  I got to find out what it says during boot.  It also boots slower than before.  However, it works.  Thats what matters.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=0x101"
```

GRUB> echo $linux_gfx_mode
echo $gfxmode
 set gfxmode=2560x1600
load_video (this line didnt work for me)
insmod gfxterm
 GRUB> vbeinfo

```
append/adding a vga=xxx, where xxx is the mode. 

thank you.

---

### Post by YannBuntu on 2011-09-05
Thanks for this nice tutorial. 
FYI, there is now a little GUI that makes it very easy to permanently set kernel boot options on an installed OS (not wubi), even when this OS cannot boot (in this case the tool must be used in a live-CD):
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[IMG]http://pix.toile-libre.org/upload/img/1312988983.png[/IMG]

hope this helps.

---

### Post by YrrchSebor on 2011-10-18
hi, the nomodeset fix works perfectly with Ubuntu 11.10 on my Acer Aspire 5336. i was wondering if this fix is ok to use a permanent fix... in other words, is it ok to run one's machine in this mode all the time? thx

---

### Post by Quackers on 2011-10-18
Yes it's fine, but may not be necessary if you install the proprietary drivers for your graphics card.

---

### Post by rahul27 on 2011-10-21
I have an Intel GMA 4500 ... I googled for the answers nothing seemed to solve my problem : finally I crossed this link:
[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=712180](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=712180) 
... that says that for acpi_osi=Linux the Brightness meter works in reverse ... which was why my display started with a blank screen .. i.e. since it is reverse, max brightness = blank screen. 

Following are a few interesting notes from the link

> Notes:

1) without i915.modeset=0 the backlight does appear to start in the off
position.  Hitting Fn-brighter once turns it back on.  On my keyboard, brighter
is Fn-left-arrow and dimmer is Fn-right-arrow, which is different than I
usually see.  

2) Starting with kernel modesetting gets me a graphical console that works fine
until X tries to start.

3) X won't start with kernel modesetting, either automatically or from runlevel
3.  X -configure fails.  With nomodeset 1024x768 is the only available
resolution once logged in to a session.  Of note, kdm comes up at the correct
resolution with nomodeset but once the X session starts it falls back to
1024x768.

4) acpi_osi=Linux is required for the backlight keys to function.  I see no
lasting benefit to having turned it on and off as described in Comment #18 -
still doesn't work with it off here.

5) same symptoms booting from the F15 DVD.  nomodeset option works at reduced
resolution, black screen with default graphical installer.So if your display starts with a blank screen, try decreasing the brightness to check if the screen appears. My display works fine now, but in reverse.

Hope this helps ... ;)

---

### Post by taixuanjunzi on 2011-10-21
*.I have been browsing ([wow gold](http://www.bestwowgolds.com)) on the internet a lot more than 3 several hours these days, however We in no way discovered any kind of fascinating post such as your own. It’s fairly ([diablo 3 gold](http://www.cheapdiablo3store.com)) really worth sufficient personally. Individually, in the event that just about all website owners as well as writers created great content material while you do, the web is going to be a lot more helpful compared to ever(<a href="http://www.buyingdiablo3gold.com">Buy diablo 3 gold</a>) prior to

---

### Post by Orographic on 2011-10-27
Hi all, 

I have a first generation core i3 with a GAH55-USB3 motherboard using the onboard graphics. Mint 11 runs perfect for me (with effects on or off) but occasionally in Ubuntu 11.04 (Unity) and Xubuntu 11.04 I get a black screen just before the log in screen. The only apparent way to get out out of this problem is a ctrl-alt-del which reboots fine.

I tried the nomodeset option outlined here and it works fine except that my resolution is then only 1680 by 1050 instead of the usual 1920 by 1080 when nomodeset isn't used.

I only get the black screen once every week or two and it even just happened in Kubuntu 11.10 but it told me in settings that it was a driver issue and it turned off Desktop Effects.



When I enter:

sudo lshw -C video

I get:


description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:fb400000-fb7fffff memory:e0000000-efffffff ioport:ff00(size=8)

Any more thoughts or ideas on this problem? How can I still use nomodeset but keep my highest resolution of 1920 by 1080?

---

### Post by mrcpuhead on 2011-11-03
Awesome how-to!  You saved my ubuntu install, which had suddenly gone into a continuous reboot cycle.  I narrowed the issue using the install DVD and trying setting the various boot options until it successfully booted up.

---

### Post by drillerccg on 2011-11-24
Thank you very much to the original poster. Worked great and posted this link to a few other forums that were asking about this. 

Solve my problem of setting up dual boot Windows 7 Home and Ubuntu 11.10 using a Live CD on an HP All-in-One 200 for a friend.

---

### Post by jvincek on 2011-11-26
Hi all,

I need some help booting my Ubuntu OS (11.10). The problem is the black screen after booting and I can't resolve the problem (or at least not with full success).
As I understand it (by looking at various forums and "guides"), the problem is in the fact that my laptop (HP G72-a26EZ) has 2 graphic chips (one "standard" - ATI HD 5470, and one on the CPU itself - Intel Pentium P6000).

So far I tried most of the options that I found and seemed remotely related to my problem, including but not limited to:
xforcevesa, acpi_osi= , acpi_osi="Linux", acpi_osi="Windows 2006" and some others... Listing the available vga modes with vbeinfo also didn't help.

I got the best results with the "nomodeset" option. Using that, i successfully booted in graphics mode (no black screen), but the problem is that I'm then limited to a low resolution ( 1024x768 ), which is not even the correct aspect ratio (native resolution is 1600x900). I think that using "nomodeset" my laptop is running with the "CPU-GPU" (that's only my guess), but AFAIK there is no way of switching it to the ATI card, or setting a greater resolution.

When I booted with "nomodeset" I tried installing the ATI drivers, and the install was successfull, but again there was the black screen during startup. I read somewhere that after installing the graphic card drivers you could then boot without the "nomodeset", but that didn't work in my case...

If anyone could give me some alternative solutions or share there experience with the same/similar hardware I would be very grateful.

I need to use Ubuntu for OpenGL development but currently I'm limited to the VirtualBox solution which is much slower and more unpractical then the "normal" dual-boot option.

Thanks in advance,
Josip

---

### Post by linuxaddix on 2011-11-29
none of this worked on my hp g-series.i can install ubuntu 11.10 but after that i cant do anything.i edit it and takes me to terminal log in.dont get it and im getting really angry.by the way i used nomodeset cause everything else leads to the black screen.some help as to why i am not able to boot in normally

---

### Post by linuxaddix on 2011-12-17
the nomodeset option to make permanent is bogus.you  just need to use it for temporary boot up then install the needed video drivers then reboot and it'll be fine

---

### Post by iflanery on 2011-12-22
I tried the remedy suggested in the initial post this evening, and it seems to have worked perfectly. While I was unable to set 'nomodeset' from my Kubuntu USB stick, I was able to edit grub in nano and set it to nomodeset that way. 

After I rebooted--and before doing anything else--I took a deep breath and installed nvidia-current, rebooted again, and was able to log in as I normally would. The boot screen resolution is still stuck at 1024x768, but I'm willing to leave well enough alone right now.

All I know is that this information would have helped me tremendously when 10.10 dropped and would've saved me from using a remix of 10.04 LTS with KDE 3.5--if only I'd looked. :P

---

### Post by NiteiaTt on 2012-01-09
OK, I have a weird issue here.
I used nomodeset to install my Oneiric from an usb. 
It surprisingly ran smoothly, and installed completely.
But then, when I try to boot, the same issue I've been having with kernel 3.0.x: the screen shuts down (or the backlight, this problem also showed up when trying to install, but nomodeset fixed it)
I edited the boot options and add nomodeset (the same way I did in order to install), and the system actually seems to be loading, but it stops in the splash screen, and I'm forced to go into console.
I also tried executing "startx", but an error shows up.
Something like "Screen no detected"
and: "Cannot establish connection to X server: Connection refused"
What I don't understand is why the GUI does load when installing under nomodeset, but when I try to boot, already installed, the GUI won't load
:S

---

### Post by tdk77 on 2012-01-17
Ubuntu 9.10 was the last version I have been able to update. Through 9.10, I tried to update to 10.04 version and it stalls on 5 dots on the opening splash page.

[On a side note: later, I burned several CDs of later versions, and the CD comes to me with a message: "EDD: error 8000 reading sector 356379, no default or UI configuration." I get the same message when trying to install Kubuntu, except the sector is "6". No idea what that all means.]

Back to Ubuntu 10.04, when I am in the opening page, I cannot access the grub menu to try to use the nomodeset. On loading I get a message "error probing SMB2", which I think is related to the graphics driver. Don't know if this is related.

Any help would be appreciated.

---

### Post by YannBuntu on 2012-01-17
@tdk77: when you see this logo:
[IMG]http://doc.ubuntu-fr.org/_media/installation/live_cd_maverick1.png[/IMG]
press a key, you will see the "old" menu , which allows to add boot options (nomodeset, or else)

---

### Post by tdk77 on 2012-01-17
Yann, I never reach that page... 
Upon startup, I get BIOS options, then a cursor, then a flash message about my motherboard "9.[alternating number] nforce2 smbus [coordinates]: error probing smb2" and it goes directly to the ubuntu logo with 5 stationary dots.
No keying works to break the computer from this screen other than a hard shutdown.

---

### Post by YannBuntu on 2012-01-17
when we boot on a live-CD/USB, this page (screenshot of my previous message) is normally the first screen to appear after the BIOS screen. 

So please try to press keys between the BIOS and the 5 dots (when you see the cursor, and the flash message).

---

### Post by tdk77 on 2012-01-18
I am able to load 10.04 off the live CD by adjusting it to boot with nomodeset.

However, once downloaded, I cannot enter the grub menu to adjust the boot options as i did off the live CD.
I can't see that the way to enter grub after you see the bios screen is different between computers, but this one is a Systemax laptop fyi.
Edit: 
OK, i was pressing "shift" but not holding it down. Problem solved refering to first page instructions.
I suppose this workaround works for ubuntu 11.10 too.

---

### Post by Carterclan on 2012-01-29
Ok after my son upgraded 11.04 to 11.10 he couldn't boot, just getting the black screen with flashing cursor. I have tried all the boot options mentioned in this thread with no luck. 

It will boot however using an older kernel. Question is how do I get grub to use this kernel by default.

---

### Post by YannBuntu on 2012-01-29
Hello
You can do it via GRUB-Customizer

---

### Post by Carterclan on 2012-01-29
> **YannBuntu said:**
> Hello
You can do it via GRUB-Customizer

Worked a charm, Thanks very much:D

---

### Post by ionraedt on 2012-02-07
I don't understand why Ubuntu still doesn't include a solution for this general problem during the installation process ? What's the problem ?
The solution is easy for us dummy's (see inputs from P4MAN, for which we must be grateful) but they should be implemented asap in the installation procedure!!

---

### Post by owhong on 2012-02-28
Thank you!  

First post from OP helped me to get Ubuntu 11.10 x64 installed on Alienware M14x.

The installation DVD freezed with message

> udevadm settle - timeout of 120 seconds ....

or

> udevd[128]: '/sbin/modprobe -bv pci:v00001 ....

Learned from OP to "press any key" during the initial purple screen after bios and selected "nomodeset" with F6 and get into try Ubuntu without freezes.  Everything worked fine with problem of low resolution display (NVidia 3.0GHz GT555M with Optimus) at trial.  Proceeded to install and later set up Bumblebee and display works fine.

Thank you very much!

---

### Post by Heretic Zed on 2012-03-10
I've tried everything in this thread and still no go.  I upgraded to 11.10 months ago on my PC, AMD Athlon II, Asus M4A77D motherboard, AIT Radeon HD 5450.  Installed through Wubi  

Everything was working fine until a week ago and now I'm getting a black screen on boot up.  I'm hoping someone has a solution soon otherwise I'll be trying a full re-install, but I'd rather not have to if I can avoid it, I had everything set up just the way I liked it.:confused:

---

### Post by bcbc on 2012-03-10
> **Heretic Zed said:**
> I've tried everything in this thread and still no go.  I upgraded to 11.10 months ago on my PC, AMD Athlon II, Asus M4A77D motherboard, AIT Radeon HD 5450.  Installed through Wubi  

Everything was working fine until a week ago and now I'm getting a black screen on boot up.  I'm hoping someone has a solution soon otherwise I'll be trying a full re-install, but I'd rather not have to if I can avoid it, I had everything set up just the way I liked it.:confused:

When you boot in recovery mode what happens? If it's a black screen as well, hit 'E' on the recovery entry and if you see the following line at the top, delete it (it should only be in the normal entry, not recovery; this is/was a bug on wubi installs only):
```
set gfxpayload=$linux_gfx_mode
```.
I don't know much about troubleshooting graphics issues, but maybe uninstalling/reinstalling the drivers might help?

---

### Post by Heretic Zed on 2012-03-10
okay, that's got it into the Busy Box shell, not sure where to take it form here to get back to normal running...

---

### Post by bcbc on 2012-03-10
> **Heretic Zed said:**
> okay, that's got it into the Busy Box shell, not sure where to take it form here to get back to normal running...

Have you tried a previous kernel?

---

### Post by peterbe on 2012-03-10
Thank you! This solved a problem I had posted on Launchpad as Bug #946116 - as a very serviceable workaround for the nouveau driver for nVidia cards. :p

---

### Post by Heretic Zed on 2012-03-10
> **bcbc said:**
> Have you tried a previous kernel?
...

that could only be helpful if you tell me HOW, to do that.  After removing the incorrect entry in the recovery mode, how do I either A) save that change and go back to the GRUB Menu to select the normal startup or a previous version.  or B) how do I work in the busy box shell to do that.  

Also, if I do get ubuntu to boot up properly, what is the permanent solution to this bug so I don't have to deal with this problem again.

---

### Post by bcbc on 2012-03-10
> **Heretic Zed said:**
> ...

that could only be helpful if you tell me HOW, to do that.  After removing the incorrect entry in the recovery mode, how do I either A) save that change and go back to the GRUB Menu to select the normal startup or a previous version.  or B) how do I work in the busy box shell to do that.  

Also, if I do get ubuntu to boot up properly, what is the permanent solution to this bug so I don't have to deal with this problem again.

When you boot you'll see the:
1. Ubuntu, with Linux 3.0.0-16-generic
2. Ubuntu, with Linux 3.0.0-16-generic (recovery mode)
3. Previous Linux versions

If you select 3, you'll see some older kernels (assuming you haven't removed them). Pick the first one. See if it works. 

There's no point speculating as to the fix until we can figure out what the problem is. But sometimes e.g. a kernel update can break the initrd.img (perhaps if the update is interrupted, maybe other reasons) in which case, there is a fix (which we can try after you get it booting).

PS I've flagged this conversation to request it to be moved out of this thread as I think it's not on topic.

---

### Post by Heretic Zed on 2012-03-11
moving the conversation is fine so long as I can find it later.

here's what's happening because I think you are misunderstanding me. 

try to boot ubuntu normally = error message that flashes too fast to read followed by black screen.

Try to boot from Grub Menu = boot freezes, showing the Grub Menu but nothing happens.

Trying to boot from recovery mode = same thing happens

trying to boot from previous Linux versions = same thing happens

the only progress I got for booting was when I removed the incorrect entry in the recovery mode boot option then booted the recovery mode, putting me into the Busy Box shell, which I have no idea how to use.

so I ask again, how to I navigate in the Grub Menu after removing the incorrect entry in recovery mode?  the only option listed is to hit Escape, which undoes the changes before going back to the Grub Menu.  How do I either save those changes in grub so I can go back to try and boot normally or from a previous version, or how to I use Busy Box to try and do the same?

---

### Post by bcbc on 2012-03-11
HereticZed,
you can't save the changes you make in grub. You'd have to mount the virtual disk (e.g. on a live cd) to save changes. If nothing is working, then it's more likely some filesystem corruption:
1. run 'chkdsk /f' from windows
2. if still broken, fsck the root.disk from a live CD. See here for info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by viktor03 on 2012-03-14
could you briefly explain what "quiet splash" does? and what would be the effect or removing it?  thnks

---

### Post by BlauFusion on 2012-03-15
Thanks for this info, I was having a problem installing Ubuntu 11.10 on an old emachines. The F6 option "acpi=off" fixed it. I'll post back if I have any weird problems later.

---

### Post by blackflame0729 on 2012-03-16
Hi,
My backlight seems to go out everytime I boot to Ubuntu (I know its the backlight because if I take a flashlight to the screen, I can just make out the login screen (I used to run a Virtual Box Ubuntu))

Anyways, I had set the nomodest on a new line after the ro quiet splash.  I was just wondering where I would put the acpi_osi=.  Is that a new line after nomodeset (also need to know if I set that to the correct line please).

I am sorry, I am kinda new to this lol :P

---

### Post by YannBuntu on 2012-03-18
Hello
> **blackflame0729 said:**
> I was just wondering where I would put the acpi_osi=.  Is that a new line after nomodeset (also need to know if I set that to the correct line please).

All arguments must be located on the same line, separated by a single space, for example "nomodeset acpi_osi= splash quiet".

An easy way to make the change on an installed Ubuntu is to use the "Edit GRUB configuration file" button of Boot-Repair: [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)
This works even if you can't boot into your installed system, in this case you just need to use Boot-Repair in live-session (the fastest way is to use Boot-Repair-Disk)


[IMG]http://pix.toile-libre.org/upload/img/1312988983.png[/IMG]

---

### Post by mr best buy on 2012-03-18
Please understand that I have a unmodefied HP computer  1 year old.  Standard video card as far as I know.  It has worked fine for a year untill now.  Now it will try to boot in Nornal mode, but flickers at about 40 cps and gets stick.  If you want I can send you  A PHOTO.

I reinstalled twice using the erase option.  No help.  Installed 12.04 and no help.  


Would what you are describing help my problem?  
Thanks

---

### Post by YannBuntu on 2012-03-20
Hello mr best buy,

First I recommend you test several combinations of kernel options via a live-CD (or live-USB) of Ubuntu, as described here: [https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)
... until you find the good options combination (for example, you may need to add 2 options: nomodeset and acpi_osi= ) that allows you to use your hardware correctly in the live session.

Then, you can use Boot-Repair (see my previous post) to add these options to an Ubuntu system that has already been installed on your hard disk.

---

### Post by Detonate on 2012-03-28
I have a question not related to the boot options, which your explanation and instructions have been very helpful.  I would really like to know how you make screen shots of the Grub menu that appears when you boot up?

---

### Post by YannBuntu on 2012-03-28
If your system is not virtualized, i don't know any other solution than a .. camera :)

---

### Post by metal04 on 2012-04-13
> **bcbc said:**
> Wubi overrides are identical to what is in post #1 - once it is installed. 

**Method 2**:
New with release 11.10, if you run wubi.exe standalone it will download a preinstalled image while in Windows, and there is no 2nd stage install anymore. But on the first boot there is no way to override boot options on the fly. You have to do it in Windows by editing the file: \ubuntu\install\wubildr-disk.cfg




It seems to me that there has been a "fix" applied to Wubi.exe! The reason I say this is because there is NO file located by that name in that location for me. :confused: 

I am running a laptop (HP Pavilion g7 with Win 7 preinstalled) with a dual boot Ubuntu 11.10 (wubi install) and Windows 7 situation.

Can any one help me resolve this? 

My son is attending school in Auburn, Alabama, USA and is using Ubuntu 11.10 (soon to upgrade to 12.04) exclusively after a major software crash in Win 7 and I KNOW he WILL have questions later. 

I need to be able to help him and with this problem still in my way............](*,).

I am frustrated with having to continually add the 'nomodeset' command to see my Ubuntu 11.10 install. :mad:

Any help will be appreciated. You can, also, email me directly at [EMAIL="bgann36067@gmail.com"]bgann36067@gmail.com[/EMAIL] if necessary.

THANKS!!

metal04

---

### Post by bcbc on 2012-04-13
> **metal04 said:**
> It seems to me that there has been a "fix" applied to Wubi.exe! The reason I say this is because there is NO file located by that name in that location for me. :confused: 

I am running a laptop (HP Pavilion g7 with Win 7 preinstalled) with a dual boot Ubuntu 11.10 (wubi install) and Windows 7 situation.

Can any one help me resolve this? 

My son is attending school in Auburn, Alabama, USA and is using Ubuntu 11.10 (soon to upgrade to 12.04) exclusively after a major software crash in Win 7 and I KNOW he WILL have questions later. 

I need to be able to help him and with this problem still in my way............](*,).

I am frustrated with having to continually add the 'nomodeset' command to see my Ubuntu 11.10 install. :mad:

Any help will be appreciated. You can, also, email me directly at <email> if necessary.

THANKS!!

metal04
Since 11.04 there are two methods of installing with Wubi. If there is no wubildr-disk.cfg then likely you used the other method. But this only helps with the very first boot into Wubi (to complete the installation).

After that first boot, you have to follow the advice in post #1 to either make it permanent by editing /etc/default/grub and regenerating the grub.cfg (sudo update-grub) or better, install the drivers your graphics card needs (run additional-drivers).

Once you are at the point where you are relying on Ubuntu or using it as (or more) frequently than windows, it makes sense to do a normal dual boot (data is safer).

---

### Post by YannBuntu on 2012-04-14
(@metal04: you should write your email in a way that it is not recognized by spam bots, eg "bgann36067 ATT gmail DOTTcom")

---

### Post by anord on 2012-04-28
thanks a lot big help!

---

### Post by rmason9 on 2012-06-26
Yes...P4man, thanks for the good tutorial.  Unfortunately, adding nomodeset to grub made no difference.  It still boots to a black screen.  I tried it several times to make sure I was following your directions correctly.

I'll try the acpi setting when I get a chance to get back to it.

Just to reiterate...my system will boot fine from the liveCD but after installing from Ubuntu and rebooting it always boots up to the black screen.  I'm running a Presario V6000 laptop, AMD 64, 2GB ram and 80GB HD.  A previous Belarc Adviser report (when my system was running Vista) says my VGA adapter is generic...or something to that effect.

I really want to get Ubuntu working...please post other options to try if possible.

Thanks!!

---

### Post by jintermeister on 2012-07-01
I was one of the unlucky ones who needs to set "nomodeset" and for that information I thank you! The continuing issue is that for people with nvidia cards requiring "nomodeset" to boot properly a new problem arises: the nouveau drivers will fail DRM and you'll be stuck with VESA capabilities, with no dual head support and some other limitations.

[http://nouveau.freedesktop.org/wiki/TroubleShooting#Xorg_fails_to_start_with_.22.28EE.29_.5Bdrm.5D_failed_to_open_device.22](http://nouveau.freedesktop.org/wiki/TroubleShooting#Xorg_fails_to_start_with_.22.28EE.29_.5Bdrm.5D_failed_to_open_device.22)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952574?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952574?comments=all)

So is there any hope for nvidia card owners wanting to use the nouveau drivers?? I'm open to any ideas. If I try to boot without "nomodeset" I just get a few colored lines and have to hard-reboot.

I'd actually like to use the proprietary drivers, but they don't work with my system for some reason. I think it is unrelated, as it loads fine but cannot properly detect screen resolutions / monitors. So it seems I'm stuck.:(

---

### Post by theperfecttime22 on 2012-07-15
when i boot my grub comes up as such..

GNU GRUB  version 1.99-21ubuntu3.1

recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root dee23f2c-5012-403f-8b32-c596883e80e5
linux /boot/vmlinuz-3.2.0-23-generic root=UUID=dee23f2c-5012-403f-8b32-c596883e80e5 ro    quiet splash $vt_handoff
initrd /boot/initrd.img-3.2.0-23-generic



Am I to delete the $vt_handoff and replace it with nomodset or add it onto the end of the line.

Also, I notice that i have a line that gfx and was wondering if any of that or the other lines have anything to do with when I put the nomodset at the end that it continues to show lines on my screen after i apply it for that boot session.

---

### Post by kd5mkv on 2012-07-30
I wish I knew this a week ago, this will be invaluable to me. thanks
:)

---

### Post by Rogoshin on 2012-09-17
I have a problem i think is similar to this, i wonder if anyone can help me. 

I have just purchased an Acer Predator G 3610, and will in this respect install Ubuntu 12.04 on. However, I have run into some problems.

When I insert the installation disk, in comes a kind of dos screen with three options, not the normal Ubuntu installation screen. The three options are try Ubuntu, install Ubuntu, or check the disk for errors. I then selected Install, resulting in the computer is running in about ten minutes, and does so to a halt. I have let it stand for two hours, but nothing happens. If anyone has any information that can help me, I will be very grateful.

Computer Info.

Intel Core i5 processor 2320
6 GB DDR3 memory
NVIDIA GeForce GTX550Ti graphics card

:popcorn:

---

### Post by YannBuntu on 2012-09-17
Hi

> **Rogoshin said:**
> The three options are try Ubuntu, install Ubuntu, or check the disk for errors.

If this is the screen below, your PC has an UEFI firmware, so you need to follow the first paragraph of this page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

If any problem, please open a new thread. (and tell me the link so that I can follow-up).

---

### Post by Rogoshin on 2012-09-17
> **YannBuntu said:**
> Hi



If this is the screen below, your PC has an UEFI firmware, so you need to follow the first paragraph of this page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

If any problem, please open a new thread. (and tell me the link so that I can follow-up).

I already have a thread

[http://ubuntuforums.org/showthread.php?t=2058178](http://ubuntuforums.org/showthread.php?t=2058178)

---

### Post by bspisak on 2012-12-14
Sorry if I'm posting this in the wrong forum or to the wrong audience, but I've been at this on and off all day having tried 2 different USB sticks, 2 different USB utilities (on each stick), 3 different DVD burns on 2 different computers.... You get the idea... 

And THIS is the problem!??!

> **P4man said:**
> The newest kernels ... makes it possible to have high  resolution nice looking splash (boot) screens [blah, blah, blah], Unfortunately, on some cards this doesnt work properly and you end up with a **black screen**. 


Really?  You've got to be kidding. Thanks so much for the beautiful splash screen, but it would be so much better if I could JUST INSTALL THE DAMN SOFTWARE!  ](*,)

Whew.  Just had to get that out of my system.

Seriously though, would it be such a big deal to include a prompt that tells the user to hit any key to get some more options?  Sheesh....  :roll:

Where does one file a bug for this kinda thing?

Brian

---

### Post by patriciosainz on 2013-03-03
> **P4man said:**
> On some hardware configurations, you need to set some kernel parameters for ubuntu to boot or work properly. A common one is nomodeset, which is needed for some graphic cards that otherwise boot in to a black screen or corrupted splash, acpi_osi= to fix lcd backlight and other problems, and noapic and nolapic to work around various ACPI BIOS issues. In this how to  I will explain briefly what this is and how to do it.

This how to applies to ubuntu 10.04 and 10.10. It may not apply to wubi, I dont know how to do it in wubi.
(update, see post #8 for the differences with wubi)

[SIZE=4]
**What are  these options?**[/SIZE]
[SIZE=2]
**nomodeset**[/SIZE]
The newest kernels have moved the video mode setting into the kernel.  So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a **black screen**. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Note that this option is sometimes needed for nVidia cards when using the default "nouveau" drivers. Installing proprietary nvidia drivers usually makes this option no longer necessary, so it may not be needed to make this option permanent, just for one boot until you installed the nvidia drivers.

[SIZE=2]**acpi_osi=**[/SIZE]
This option frequently solves problems with **LCD backlight**, fan control problems and misreporting of thermal events. What I understand it does (but corrections are welcome), is prevent the kernel from reporting to the bios that its any windows version the bios asks for. By default, the kernel pretends to be all windows versions, that way we are certain the bios executes all the code needed to initialize the hardware. Unfortunately, some bioses contain fixes to fix problems with specific windows versions (notably vista) that arent needed or dont work for other OS's. Setting ```
acpi_osi= 
``` (nothing behind the = sign) as boot option makes the kernel not respond to osi queries.

If the bios has provisions for Linux, you can also try
```
acpi_osi="Linux"
```

Or you can try 
```
acpi_osi="Windows 2006"
```

To make the kernel pretend its vista and make the bios execute routines on machines that require them.

[SIZE=2]**acpi=off**[/SIZE]
This disables ACPI completely. 
Note: this may not work with all computers and will disable a lot of useful (or even needed) features. In some cases it may even disable some crucial features, like.. fans. Be careful with this option, it might cause your machine to overheat if the fans no longer turn. Think of this as a last resort. Also note some machines require **acpi=ht** instead.

[SIZE=2]**Noapic and nolapic**[/SIZE]
noapic and nolapic kernel options instruct the kernel to not use  certain programmable interrupt controllers. To understand what that means exactly requires a deep knowledge of PC hardware, I will not go in to that here, Ill limit myself to saying on some bioses, especially for older systems, there are problems in the implementation  of this and it may be necessary to disable either or both to cure a wide range of  obscure problems, often but not always related to **keyboard and mouse and power management (standby/resume issues)**.

**[SIZE=2]vmalloc=xxxM [/SIZE]**
In some cases kernel drivers can not be loaded due to a lack of virtual addressing space on **32 bit** systems. Logs will show errors like
```
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

```
Details can be found here:
[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

This has been reported by extremejosh  who's machine failed to load the  restricted nvidia drivers on a geforce 7350 and appears more or less common if you have several tv tuners. Increasing the size of vmalloc to 196 or even more may help in such cases.

[SIZE=4]**How to enable kernel options on the livecd (before install)**[/SIZE]

If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom:

[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see this menu:

[IMG]http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png[/IMG]

If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key. You can close the menu with escape key and resume booting by selecting the option “try ubuntu without installing” (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).

If you need to add kernel options not provided by the F6 menu, you can just type them in at the end of the boot options line.

**Important**: if you select a kernel boot option from the F6 menu and proceed to boot and later install ubuntu, those boot options will NOT be applied to your installation. If you needed nomodeset to get the livecd to boot, you will almost certainly need it again once you reboot in to your fresh install. See below how to set those options on an installed ubuntu. And perhaps click the “affects me too” on [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526")where I request these settings be applied (semi) automatically.

[SIZE=4]**How to temporarily set kernel boot options on an installed OS (not wubi)**[/SIZE]

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:

[IMG]http://img5.imagebanana.com/img/hy5mw3s9/dgfdgRunningOracleVMVirtualBox_016.png[/IMG]

Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the  line that starts with

```
linux /boot 
``` and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot :D ):

[IMG]http://img26.imageshack.us/img26/3509/dgfdgrunningoraclevmvir.png[/IMG]

press control+X to boot the modified grub entry.

**Important:** setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)

[SIZE=4]**How to permanently set kernel boot options on an installed OS (not wubi)**[/SIZE]

To permanently change the default kernel boot options, press ALT+F2 or  open a terminal from system > accessories > terminal. Type in the following command:

```
gksudo gedit /etc/default/grub
```

a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX=""
```

add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX=""

```

Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\"[/COLOR]"
```

Now in the terminal, run the following command to update your grub configuration with the new default settings:
```

sudo update-grub
```

Thats all.  

To do: wubi part.

Well, well, well, I think your are Great!!!, I was looking for this solution for days (sorry for my english) I didn't know I could edit ubuntu boot pressing shift key and edit Ubuntu boot then with E key for changing boot permanently adding nomodeset. Thanks a lot and lot of kisses +++++++++++++++++++++
I'll tell you what I did for those people that couldn't configure NVIDIA GeForce4 mx 440 AGP 8x because they had the awful message just after de battery check [o] drm... failed to set mode on [number]
In the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" I saw in mine this one: (I mean boot ubuntu boot with E key)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash \$vt_handoff", so I tried this one:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash \ nomodeset" I deleted $vt_handoff but I couldn't delete the \ character, so I typed before nomodeset as you said. After press ctrl+x I typed sudo update-grub.
After this I kept your steps for changing permanently to set kernel, I mean edit /etc/default/boot and add into NOMODESET after quiet splash.
I reboot and I couldn't believe I had reached at least the session menu login, so I shut down the computer to see if it was only an ilusion, but no, It worked properly. Thanks a lot my friend, I love you.

---

### Post by patriciosainz on 2013-03-05
Oh, sorry. 
I forgot to add that I could run at least my 1280x1024 resolution with my NVIDIA driver that couldn't work at all but I got it, only reading the README.txt file in /usr/share/doc/NVIDIA_GLX-1.0/ after installing NVIDIA-Linux-x86-43.23-pkg1.run
YUJUUUUUUUUUUUUUUUUUUU!!!, I Love Linux, I love Ubuntu, Kubuntu and Lubuntu, I love NVIDIA too, they did well, I did wrong :) (I didn't read the readme.txt file that gave me the solution adding the fuc... section "module" at the end of xorg.conf, omg I spent four or five days looking for this problem, and what a nice reward. I love computers... without windows :D

---

### Post by ohmysql on 2013-03-11
I was wondering how to pass these parameters to operating systems that were found by os-prober. I can't seem to find any way to automagically do this. Adding parameters to GRUB_CMDLINE_LINUX_DEFAULT doesn't seem to do the trick.

---

### Post by PoeticTorment on 2013-03-29
Thank you so much for posting this, I'm a new Ubuntu user and this saved me! It was simple to follow and understand for those who happen to have a hard time understanding grub information. Keep up the great work!

---

### Post by dasaint80 on 2013-03-30
I'm having problems with this how to. I've installed ubuntu 12.10 onto my macbook pro 3,1 (nvidia 8600M GT). I've tried every setup and I'm able to boot ubuntu but only onto terminal (no graphics) when I try to run "startx" I get an error NVIDIA: could not open the device file /dev/nvidia0 (input/output error)

---

### Post by roly33 on 2013-04-22
Thank's for this tutorial.

I used the [B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

[/B]and now my Toshiba Notebook auto resumes from Hibanate.

Roland

---

### Post by hans12345 on 2013-06-15
Brilliant. 

Fixed my problem in :
[http://ubuntuforums.org/showthread.php?t=2149656](http://ubuntuforums.org/showthread.php?t=2149656)

Thanks

---

### Post by JakkoChan on 2013-06-28
Thanks so much for this!

---

### Post by marcomarcusda on 2014-03-17
Please someone help me!

I finally get elementary OS working with these nomodeset thing buut...

I hacVe no close/maximize buttons in any window I open.

I have my NVIDIA 96 drivers fora my GeForce 2 mx. Far as i know that driver versión is the One that work with my NVIDIA.

So, please help me c:

---

### Post by jackson21 on 2014-03-29
To P4man,
Great!!!!!  Thank you so much for the detailed advice,
So far I have already seen on black screen  the logos at the bottom
the keyboard and the mannikin  for the kernel options 
Will try ubuntu 14.04 beta2  with the nomodeset option


Thank you so much and greetings from Austria

jackson

---

### Post by jackson21 on 2014-03-29
14.04 is running, !!!
Thank you

---

### Post by mark bower on 2014-04-18
In 12.04LTS I am using an ATI Radeon HD 4650 AGP video card which experiences boot problems.  The system "misfires" maybe one of four initial boots, and locks up on a dark screen.  And when it does this, the system can only be restarted by a hard turn off, ie, turn the power switch at the line off, then on.  And sometimes this switch has to be recycled up to 3 times before the system will complete the boot process.  The "on-off" switch and the "reset" button do not respond when the system locks up.

The following shows the radeon driver is in use.  

rocky@mark:~$ lspci -nnk | grep -iA3 vga 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV730 Pro AGP [Radeon HD 4600 Series] [1002:9495] 
	Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:0028] 
	Kernel modules: radeon 
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38] 

Using "nomodeset" in grub worked wonders.  I did this by going to /etc/default/grub and modifying the line
GRUB_CMDLINE_LINUX-DEFAULT = "quiet splash"    to read
GRUB_CMDLINE_LINUX-DEFAULT = "quiet splash nomodeset"

Then I run update-grub2.

In addition to booting flawlessly, I note that the mouse pointer shows on a dark screen before the desktop opens.

---

### Post by tj-quinn on 2014-07-31
Great tutorial. Thanks very much. Using the nomodeset option on the install medium (usb) solved my nvidia problem. After installation, the graphics were huge and wrong, of course. Installed latest nvidia driver, via "additional drivers" and then rebooted. All perfect.
Thx again.
Tim

---

### Post by lilipop on 2015-04-30
hello,
i have partially solved my problem but when i get to the login screen and i enter my password then the screen turns black and i get again to the login screen to enter my data.
the same happens to the guest sessio, when i just click to enter i get a black screen and after 1 second i get back to the login scree. 
akward....

---

### Post by shadyyx on 2015-07-21
Hi guys.

Thanks for this useful information.

I ran into troubles on my Dell laptop with integrated Intel HD graphics right after upgrading from Ubuntu 14.10 to 15.04. With the upgrade all my graphical *xserver-xorg* drivers have been uninstalled and since I was running on three monitor setup (ntb + 2 monitors) the whole system has frozen during the upgrade process once the drivers were uninstalled. It took me an hour to realize that. After unplugging the monitors I could finally start a new session and finish the upgrade process. I am now *allowed* to plug in one additional monitor (with plugging in second one the system freezes completely). I tried to install the (old) xserver-xorg graphical drivers back again but it looks like they are out of effect on 15.04.

Unfortunately the system is not able to boot while the additional monitor is plugged in. Workaround was before restarting unplugging the monitor and after logging in plugging it back again.

The solution now is using the **nomodeset** option which allows me to keep the monitor plugged in.

I am looking forward to new version of Intel graphic drivers for Linux which should target Ubuntu 15.04 as well. It's like having one less eye when once used to working with three monitors and then one is gone...

---

### Post by gazjohnson on 2016-06-10
Thanks, solved black screen boot problem with 16.04

---

