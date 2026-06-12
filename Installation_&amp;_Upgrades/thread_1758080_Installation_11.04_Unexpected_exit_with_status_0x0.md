---
title: "Installation 11.04: Unexpected exit with status 0x0009"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by jambel on 2011-05-14
Hi,

I'm trying to make a fresh install on my desktop computer and I got this error on boot:

```
udevd-work[155]: '/sbin/modprobe -bv pci:<followed by some numbers>'

unexpected exit with status 0x0009
```and it stuck there.

Note that I'm trying to install from a usb stick.

---

### Post by jambel on 2011-05-15
Anyone? :(

---

### Post by User4519 on 2011-05-16
> **jambel said:**
> Anyone? :(

Same problem here, with Lubuntu 11.04 (USB stick and CD) and Kubuntu 11.04 (USB stick). Motherboard is ASRock P43Twins1600. I don't get that message when trying to install - the kernel just hangs after detecting drives. Tried waiting 10 minutes to no avail.

I have an old computer I use for playing old XP games, just tried everything there - every installer works. Tried installing Lubuntu 11.04 onto a SATA drive and move it to my ASRock system, on boot I just get a black screen.

I tried unplugging every other disk and every expansion card (save for the PCIe nVidia graphics which I kinda need ;) ), and then I get this error. Specifically,

udevd-work[87]: '/sbin/modprobe -bv pci:v000010DEd00000141sv00001043sd000081EEbc03sc00i00' unexpected exit with status 0x0009.

Seeing as how Lubuntu isn't even based on Ubuntu per se, this really reeks of kernel trouble (again, kernel trouble with 2.6.38 - sigh!!!). I'm gonna try disabling onboard peripherals and see if I can narrow it down, perhaps even boot.

---

### Post by User4519 on 2011-05-16
Hmmm, this looks nVidia related here. Are you using nVidia, too?

Trying to boot in recovery mode is a little more verbose, and the message log is filled with nouveau messages, stranges ones, too - like claiming to do 55+ GHz on the mem at 126% fan speed?!?! Even if this card had a fan, I'm pretty sure I wouldn't be able to clock the mem at 55 Ghz ;)

Will try to see if I can boot without the nouveau driver and confirm or deny this theory.

---

### Post by User4519 on 2011-05-16
Righty-o, confirmed here. Something's amiss with the nouveau module. Blacklisting it will let you boot, using fallback framebuffer instead. When booting, hit TAB to edit the boot parameters. Add this to the end of the line, but before the two dashes ("--"):

nouveau.blacklist=1

Then boot. You may see the screen go messy while you write because the line gets two wide to fit, but don't worry, all is good. You may see a message complaining that nouveau does not have an option, "blacklist" or something like that, but it does, and it does work, and I think maybe that message should've read, "there's no nouveau module to do 'blacklist' on" as the module isn't loaded, and that's probably what the complaint it about. It's also what we want to happen ;)

Once booted, you can install the OS. Use the same trick in the GRUB screen after rebooting, or you'll have a broken kernel message once again (or a black screen).

Then install the proprietary nvidia drivers:
$ sudo apt-get update && sudo apt-get install nvidia-current

This rebuilds the kernel initramfs so from now on you'll be booting not with the broken nouveau module, but the proprietary nvidia module.

My boot is still a bit quirky though - I don't get a splash screen, and sometimes I don't even get GRUB (I've therefore been holding down left shift when I need it), and sometimes I don't even get an X login prompt...

I thought nouveau might still be loaded, so I tried adding "nouveau.blacklist=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and doing sudo update-grub2 to make sure that nouveau would be blacklisted by default, but this actually seems to make the problem worse - as in with this on, I don't get to the X login screen.

I currently run with the proprietary nvidia drivers installed and without the blacklist option in GRUB, and while I only have a black screen while booting, it seems to be pretty consistent in reaching X login, and I still have usable TTYs along with the nvidia accelerated X session.

HTH, 
Daniel :)

---

### Post by NormanFLinux on 2011-05-16
Just upgrade to the latest kernel.

2.6.38 is a POS. The latest version is much more robust.

---

### Post by User4519 on 2011-05-16
> **NormanFLinux said:**
> Just upgrade to the latest kernel.

2.6.38 is a POS. The latest version is much more robust.

I couldn't agree more - 2.6.38 is nothing but trouble. But... It **is** the latest? Unless we go with the odd, or unstable, version. With the only difference being that that one will be **officially** unstable, while the 2.6.38 one is **unofficially** unstable.

Is there an Ubuntu PPA or just debs for recent kernels from the unstable branch? I would love to ditch this broken .38 kernel and go for something else.

---

### Post by User4519 on 2011-05-16
[http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

Gonna try the latest one now :)

---

### Post by User4519 on 2011-05-16
Woops... No 64-bit :(

---

### Post by jambel on 2011-05-16
> **DanielBuus said:**
> Righty-o, confirmed here. Something's amiss with the nouveau module. Blacklisting it will let you boot, using fallback framebuffer instead. When booting, hit TAB to edit the boot parameters. Add this to the end of the line, but before the two dashes ("--"):

nouveau.blacklist=1

Then boot. You may see the screen go messy while you write because the line gets two wide to fit, but don't worry, all is good. You may see a message complaining that nouveau does not have an option, "blacklist" or something like that, but it does, and it does work, and I think maybe that message should've read, "there's no nouveau module to do 'blacklist' on" as the module isn't loaded, and that's probably what the complaint it about. It's also what we want to happen ;)

Once booted, you can install the OS. Use the same trick in the GRUB screen after rebooting, or you'll have a broken kernel message once again (or a black screen).

Then install the proprietary nvidia drivers:
$ sudo apt-get update && sudo apt-get install nvidia-current

This rebuilds the kernel initramfs so from now on you'll be booting not with the broken nouveau module, but the proprietary nvidia module.

My boot is still a bit quirky though - I don't get a splash screen, and sometimes I don't even get GRUB (I've therefore been holding down left shift when I need it), and sometimes I don't even get an X login prompt...

I thought nouveau might still be loaded, so I tried adding "nouveau.blacklist=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and doing sudo update-grub2 to make sure that nouveau would be blacklisted by default, but this actually seems to make the problem worse - as in with this on, I don't get to the X login screen.

I currently run with the proprietary nvidia drivers installed and without the blacklist option in GRUB, and while I only have a black screen while booting, it seems to be pretty consistent in reaching X login, and I still have usable TTYs along with the nvidia accelerated X session.

HTH, 
Daniel :)

I use nvidia as well but I'm not sure I follow.

Can you please make a step by step solution? I start with me as far as I get the error...

1. boot from usb stick
2. Install ubuntu

after a while I get the error message

3. what follows? where to hit TAB, how to disable nouveau, what file should I edit and how (if any)?

Thanks!

---

### Post by User4519 on 2011-05-16
> **jambel said:**
> I use nvidia as well but I'm not sure I follow.

Can you please make a step by step solution? I start with me as far as I get the error...

1. boot from usb stick
2. Install ubuntu

after a while I get the error message

3. what follows? where to hit TAB, how to disable nouveau, what file should I edit and how (if any)?

Thanks!

You hit TAB when you get the splash screen where you see "Try Ubuntu without installing" and a number of other options. Select the option you want (like try or install), then hit TAB. This will show an editable line at the bottom of the screen with the options that are passed to the kernel once you press enter again. Add "nouveau.blacklist=1" to this line just before the two dashes that are at the very end of the line. Then hit enter.

This should work for installing. You'll get the same problem once you try to reboot and start your installed OS. You do the same again, except now you have the usual GRUB menu (if you don't see it, make sure to hold down the SHIFT key just when the BIOS is done with all its blah blah about devices and whatnot). Here, you have to press 'e' to edit the boot options (it says so at the bottom, too).

This time there are a number of lines - find the one that says something about "splash" (might end with "something=7") - it should be the longest line (sorry, I'm not able to reboot right now! :D ).

Just add the same deal there (i.e. "nouveau.blacklist=1"), then press F10 to boot. Once you've booted, do the "sudo apt-get update && sudo apt-get install nvidia-current" bit and try rebooting.

If your problem is the same as mine, you should be rolling by then :)

---

### Post by jambel on 2011-05-22
This is what I get when I set nouveau.blacklist=1
[http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce](http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce)

it looks like a new error

---

### Post by Omegan on 2011-05-22
I get a similar error.  I don't even get to the splash screen with the option to try or install.  I have an acer laptop with switchable graphics and all of the calls above the error appear to be for my radeon HD 5470.  

I am trying to use ubuntu to get some files off my win 7 laptop that will no longer boot.  If this doesn't work, I'm just going to reinstall windows 7 from my recovery disks.

Is it possible I can use a previous version of Ubuntu and have success retrieving my files?

Thanks

UPDATE!  While I was typing this out, I had an idea:  my laptop starts with the above GPU when it is plugged in to A/C and with the integrated graphics when it is not, so I started up while not plugged in and ubuntu started fine.  It will work very well to get my files off the hard drive before re-installing.

---

### Post by User4519 on 2011-05-23
> **jambel said:**
> This is what I get when I set nouveau.blacklist=1
[http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce](http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce)

it looks like a new error

Strrrrrraaannge... Because that looks like the exact error I get **when not** using the blacklist trick :confused: And doubly strange because it's clearly coming from the nouveau module which shouldn't be loaded if the trick worked...

Are you sure you wrote it correctly, with space before and after and before the two dashes at the end?

---

### Post by jambel on 2011-05-23
> **DanielBuus said:**
> Strrrrrraaannge... Because that looks like the exact error I get **when not** using the blacklist trick :confused: And doubly strange because it's clearly coming from the nouveau module which shouldn't be loaded if the trick worked...

Are you sure you wrote it correctly, with space before and after and before the two dashes at the end?

I can't remember, I'll try again and I let you know.

Thanks anyway!

---

### Post by jambel on 2011-05-29
> **DanielBuus said:**
> Strrrrrraaannge... Because that looks like the exact error I get **when not** using the blacklist trick :confused: And doubly strange because it's clearly coming from the nouveau module which shouldn't be loaded if the trick worked...

Are you sure you wrote it correctly, with space before and after and before the two dashes at the end?

OK, I pass the nouveau problem but now, when it boots it has a login screen with "other" option selected and waiting for a password.

---

### Post by User4519 on 2011-05-30
> **jambel said:**
> OK, I pass the nouveau problem but now, when it boots it has a login screen with "other" option selected and waiting for a password.

Makes sense - 11.04 requires 3D acceleration for the default desktop to load, and now that we've blacklisted the nouveau driver and haven't yet installed the nvidia driver, there's no 3D - yet.

If it's possible for you to use an ethernet connection (rather than wifi) you don't need to log in to have a working internet connection. If that is the case, you can just switch to a text login (Ctrl+Alt+F1 when you see the log in screen) and log in there.

Then simply type in this (one line) command:
[FONT="Courier New"]sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-current && sudo reboot[/FONT]

This should update your current system, then install the nvidia driver and reboot your computer. If all is well, you should get a reboot shortly and everything should be working properly.

If you're on wifi, you'll have to log in to the alternate desktop environment that the log in screen suggests, open a terminal, and put in the same command as written above.

The reason I'm suggesting to go to the text only login instead is that booting into a different desktop environment will create a lot of configuration files in your home dir which you don't need and which might - if you're unlucky - cause problems in your "regular" desktop environment. So if at all possible, use an ethernet cable to your router and go to the text only login.

(If you still don't have a connection in the text only login, try using the command [FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT] first, maybe even [FONT="Courier New"]sudo dhclient eth0[/FONT] if that still doesn't cut it.

HTH,
Daniel :)

---

### Post by CLTPilot on 2011-06-01
Had the same error message tonight when trying to install 11.04 via CD to the Sony VAIO VPCSC1AFM "Blue Label" laptop from BestBuy.  It has dual Intel/AMD Radeon HD 6470M graphics.  There's a "Speed/Stamina" slider switch.   I switched it to "Stamina" figuring that would disable the Radeon and then the install worked fine.    Only problem now is the proprietary ATI driver's aren't working so I can't get the Unity desktop to work.  Tried deactivating the proprietary driver and installing the driver from ATI's website but still not working.

---

### Post by jambel on 2011-06-04
> **DanielBuus said:**
> Makes sense - 11.04 requires 3D acceleration for the default desktop to load, and now that we've blacklisted the nouveau driver and haven't yet installed the nvidia driver, there's no 3D - yet.

If it's possible for you to use an ethernet connection (rather than wifi) you don't need to log in to have a working internet connection. If that is the case, you can just switch to a text login (Ctrl+Alt+F1 when you see the log in screen) and log in there.

Then simply type in this (one line) command:
[FONT=Courier New]sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-current && sudo reboot[/FONT]

This should update your current system, then install the nvidia driver and reboot your computer. If all is well, you should get a reboot shortly and everything should be working properly.

If you're on wifi, you'll have to log in to the alternate desktop environment that the log in screen suggests, open a terminal, and put in the same command as written above.

The reason I'm suggesting to go to the text only login instead is that booting into a different desktop environment will create a lot of configuration files in your home dir which you don't need and which might - if you're unlucky - cause problems in your "regular" desktop environment. So if at all possible, use an ethernet cable to your router and go to the text only login.

(If you still don't have a connection in the text only login, try using the command [FONT=Courier New]sudo /etc/init.d/networking restart[/FONT] first, maybe even [FONT=Courier New]sudo dhclient eth0[/FONT] if that still doesn't cut it.

HTH,
Daniel :)

Before I install it and have this problems I'm trying to do the steps in live. I haven't install ubuntu yet and I don't have credentials to log in, because I select the "try ubuntu" and not install.
If I don't bypass those issues I won't go on to installation.

Is there any defaults I can log in, in live cd environment?

I appreciate your help!

---

### Post by User4519 on 2011-06-06
> **jambel said:**
> Before I install it and have this problems I'm trying to do the steps in live. I haven't install ubuntu yet and I don't have credentials to log in, because I select the "try ubuntu" and not install.
If I don't bypass those issues I won't go on to installation.

Is there any defaults I can log in, in live cd environment?

I appreciate your help!

No problem :) But these steps were for an already installed system - I assumed you had installed it :)... So the "other" login option is with the livecd? If so, there's no problem at all logging in and installing from there. Then, once you boot your installed system using the same "tricks" to get it to boot, you should probably see the same "other" login option, and **then** you can use the instructions in my previous post.

If for some reason you can't get the livecd to work properly beyond logging in, you can always download the "alternate" cd and use that instead. It's text-based rather than point and click, but it's pretty straight-forward to work through, and you can always fire up Google on another computer to get a howto or help in general :)

---

### Post by alexkappa on 2011-06-20
Wring thread.... Sorry

---

### Post by agj625cc2 on 2011-06-23
I am using an ATI Radeon video card in a Lenovo T500, and am facing the same error...any ideas on what to do to fix this?

Thanks!

---

### Post by kinglet on 2011-08-23
I have same problem! HP ProBook 4530s with Radeon card. I cannot install Ubuntu 11.04 bcuz of same error. I tried to do step by step that @DanielBuus said. But Tab doesn't work into splash screen, so I tried to do with ACPI OFF, "Unexpected exit with status 0x0009" doesn't show me this time, but I got a new error (Busybox error):
```
(initramfs) Unable to find a medium containing a live file system
```
I select Install in Text Mode, and after configuring keyboard Installation CD-Rom couldn't be mounted :(
Why we cannot install Ubuntu and what we have to do?

Regards

---

### Post by jambel on 2011-08-23
I still have 10.10 on my desktop computer. I hope in 11.10 to do something about that :(

---

### Post by kinglet on 2011-08-24
Any suggestion? needs to install Ubuntu ...

---

### Post by MroiZo on 2011-09-14
Thanks [DanielBuus]("http://ubuntuforums.org/member.php?u=826200"), you made my day :)

---

### Post by p4triarch on 2011-12-05
Sorry for an old bump -

The reason this is occurring is because the laptop is using switchable graphics. 

The fix is simple- go into your bios, change your graphics to 'discrete' and select 'pci express' as default graphics.  Or for less power consumption select your integrated, and so on.

I also disabled OS detection for switchable graphics, didn't test to see which of them was the exact issue.  But this completely resolved any issues.

Thanks.

---

### Post by User4519 on 2011-12-10
> **p4triarch said:**
> Sorry for an old bump -

The reason this is occurring is because the laptop is using switchable graphics. 

The fix is simple- go into your bios, change your graphics to 'discrete' and select 'pci express' as default graphics.  Or for less power consumption select your integrated, and so on.

I also disabled OS detection for switchable graphics, didn't test to see which of them was the exact issue.  But this completely resolved any issues.

Thanks.

Patri, your effort is appreciated, but the fix is not to stop using nvidia graphics, it's to make your system properly access and utilize your (nvidia) hardware as described in this thread. Be it as it may, current releases of *ubuntu don't behave like this anymore AFAIK.

Merry christmas!

---

### Post by madeinspade on 2011-12-16
> **DanielBuus said:**
> You hit TAB when you get the splash screen where you see "Try Ubuntu without installing" and a number of other options. Select the option you want (like try or install), then hit TAB. This will show an editable line at the bottom of the screen with the options that are passed to the kernel once you press enter again. Add "nouveau.blacklist=1" to this line just before the two dashes that are at the very end of the line. Then hit enter.

This should work for installing. You'll get the same problem once you try to reboot and start your installed OS. You do the same again, except now you have the usual GRUB menu (if you don't see it, make sure to hold down the SHIFT key just when the BIOS is done with all its blah blah about devices and whatnot). Here, you have to press 'e' to edit the boot options (it says so at the bottom, too).

This time there are a number of lines - find the one that says something about "splash" (might end with "something=7") - it should be the longest line (sorry, I'm not able to reboot right now! :D ).

Just add the same deal there (i.e. "nouveau.blacklist=1"), then press F10 to boot. Once you've booted, do the "sudo apt-get update && sudo apt-get install nvidia-current" bit and try rebooting.

If your problem is the same as mine, you should be rolling by then :)
I am really new with this stuff i am trying to hit tab in the splash menu and i can write text at the bottom but i do not see the 2 dashes at the end of the line i am not sure if i am putting in the command properly could you help me please?

---

### Post by Erichthonius on 2011-12-24
I had the same error. I followed the instructions from DanielBuus and this made it work. Thank you.

---

### Post by DeadlyOats on 2012-01-02
I've been trying to install *buntu 11.10 32/64 bit versions into my machine.  Here's my [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1902496").  As you can see, I've been getting the very same screen full of text as jambel has been getting, which he took a picture of, as you can see from his link, below. 

> **jambel said:**
> This is what I get when I set nouveau.blacklist=1
[http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce](http://www.mediafire.com/imageview.php?quickkey=ccb6dy2scuuwzce)

it looks like a new error

It seems to me that the problem, which seems to have surfaced from Linux kernel 2.6.38, continues to exist in Linux kernel 3.0.  I don't know how to determine these things, but I'm wondering if a bug report is in order?  Or has one already been submitted to the right people?

---

### Post by DeadlyOats on 2012-01-02
> **DanielBuus said:**
> You hit TAB when you get the splash screen where you see "Try Ubuntu without installing" and a number of other options. Select the option you want (like try or install), then hit TAB. This will show an editable line at the bottom of the screen with the options that are passed to the kernel once you press enter again. Add "nouveau.blacklist=1" to this line just before the two dashes that are at the very end of the line. Then hit enter.

This should work for installing. You'll get the same problem once you try to reboot and start your installed OS. You do the same again, except now you have the usual GRUB menu (if you don't see it, make sure to hold down the SHIFT key just when the BIOS is done with all its blah blah about devices and whatnot). Here, you have to press 'e' to edit the boot options (it says so at the bottom, too).

This time there are a number of lines - find the one that says something about "splash" (might end with "something=7") - it should be the longest line (sorry, I'm not able to reboot right now! :D ).

Just add the same deal there (i.e. "nouveau.blacklist=1"), then press F10 to boot. Once you've booted, do the "sudo apt-get update && sudo apt-get install nvidia-current" bit and try rebooting.

If your problem is the same as mine, you should be rolling by then :)

Thanks, DanielBuus!

I did what you said, to get the installer to work, however, I did something a little bit different.  In Kubuntu, there was a check box that gave me the option to install non-free codecs and drivers and a second check box to download updates during the installation.  Both options requires an Internet connection, however...

I checked the boxes (I have an Internet connection).  After the install completed, and I rebooted the system, it started right up!  I'm guessing it downloaded the proprietary drivers for me during install...  I installed Kubuntu 11.10.

I'll try it again later with Lubuntu 11.10, and again with Ubuntu 11.10.  I normally use Ubuntu, and I don't recall seeing an option to download non-free codecs and drivers during install....  So, perhaps then, I'll have to follow the second step in your instructions to modify grub and, later, the manual install of the proprietary graphical card drivers...  I'll update as needed with my results.

UPDATE:

O.K.  I've installed each of these three: Ubuntu/Kubuntu/Lubuntu 11.10 64bit.

In all three cases, I had to use your method.  I paid better attention to what I did, and this is what I had to do to get it done.  For Lubuntu, it loaded up to the 'select Language menu' and the 'keyboard type menu' before getting to the 'Install Menu', for Ubuntu and Kubuntu, I had to hit the Tab Key right after the BIOS/UEFI screen cleared and the install cd began to load before I got those choices.

I arrow keyed to the choice I wanted, 'Install', then I had to hit the F6 button.  That gave me a dialog box with choices, and under the dialogue box was the command line where you type in the nouveau.blacklist=1 command.  I hit the ESC (escape) key to get rid of the dialogue box, then I used the arrow keys to get the cursor where I wanted it, inside of the two dashes at the end, and I typed the command, and sat back.  The installation worked.  All three times.

In all three cases, there were check-boxes for downloading updates during install, and to load codecs and other proprietary stuff.  I checked the boxes.  In all three cases, it downloaded something....  But even afterwards, I still had to run update manager in Ubuntu and Lubuntu.  I didn't notice if Kubuntu had anymore updates to download...

However, in all three cases, I did not have to perform the second step, in DanielBuus' instructions, update grub, and download the inVidia graphics drivers.  It seems to have done that for me.  In Lubuntu, I was able to verify that nVidia's proprietary drivers were installed and in use.  After stumbling around in Ubuntu's Unity, I found that nVidia's X server settings was in the startup programs menu, and the additional hardware drivers dialogue box showed it was in use - even though I was unable to access it to check its settings - buggy-ness....  I didn't check in Kubuntu.  I'm a Gnome desktop guy, not a Kde Desktop guy...  I was lost in there....

It might have been different in my case because maybe my hardware was a little different?  I'm using an Asrock P67 Extreme4 Gen3 mobo, which uses the UEFI instead of the BIOS.  So, the steps I took were probably a little different from what DanielBuus described because of that?

---

