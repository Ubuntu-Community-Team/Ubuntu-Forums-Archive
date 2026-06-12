---
title: "[SOLVED] Installed 7.10 on T42 laptop - won't boot. Help Please."
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by wiseloki on 2008-03-15
Hi,

I've probably broken numerous forum rules, as I originally posted this yesterday in "Absolute Beginners (which I am), but I've had no joy there. I know almost zero about unix/Linux/Ubuntu. I thought I'd try in this more specialized forum.

IBM T42 laptop recently acquired off eBay. 1.8 GHz Pentium M. ATI Mobility Radeon 7500 32MB. 1GB RAM. 40GB HDD. Updated BIOS to 2.33 (latest). Laptop runs XP OK. Ethernet cable connected to a broadband router/switch.

I have been running 7.10 (Gutsy Gibbon) off the CD with no apparent issues and finally decided to install as a dual-boot. The plan is to make sure all aspects of the T42 work in Linux (being able to check them in XP if required) then eventually dump XP and free up the disk space.

Before I burnt the image to CD I checked the download with md5sums and the checksum was OK, and this same CD has already successfully installed Ubuntu on a Dell C840 laptop, the only difference being that on the Dell I allowed Ubuntu to take the whole partition (top option on the installer), as it had an XP installation that was 5 years old and had gone a bit flaky.

I read some of the forums and Ubuntu information and decided to have a separate root ('/'), and ‘/home’ so used the partitions utility on the CD to resize the XP NTFS partition to 10GB (files actually use 7.7GB), set up a 4MB swap partition, created a root ('/') of 4GB and '/home' of the rest of the HDD, about 26GB.

I then installed. I restarted the machine and got the OS select table. First I tried XP and  after it had scanned with ScanDisk, XP started OK.

Then I tried Ubuntu – It said “Starting up”, then a couple of lines of text saying “Loading <something>” – too fast to see, then the screen stayed blank with the HDD twitching occasionally. No boot, so I crashed it with the power button.

I tried the recovery mode, and the screen scrolled through the various commands, finally stopping after:

*Mounting local file systems....[OK]
*Activating swapfile swap...[OK]
$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done
*Checking minimum space in /tmp...[OK]
*Configuring network interfaces....[OK]
*Setting up console font and keymap...[OK]
root@pvs-ibm:~#_ <blinking cursor>

After some advice in “Beginners” I tried entering "startx" at the cursor and the screen went black, then into tiny black-and-white checkered squares with the mouse pointer as a black 'X'.

I then got a message that "The session is running as a privileged user" and do I want to quit or continue? Continuing gave the Ubuntu music and the brown screen, then there was a message box saying that "User switcher" has quit unexpectedly. If I opted to reload I repeatedly got the same message. 

"Don't load" got me to the normal Ubuntu desktop with 2 HDD symbols, one marked sda1 and the other sda4. Ubuntu and OpenOffice seemed to start and work OK (but I didn't check out network or wireless), but when I came to quit I couldn't shut down, I just got an box with the option to log out. When I logged out, I got back to the "root@pvs-ibm:~#_" line on the black screen with blinking cursor. So I crashed it with the power button.

I then reinstalled Ubuntu, resizing the '/' partition to 10GB as advised in “Beginners”, disconnected my Ethernet cable (I'd done the previous installation with the Ethernet connected to my router) and this time got a warning about not being able to access security updates.

Installation finished and I rebooted in normal mode - same result as before, black screen and twitching HDD.

Crashed with power button

Rebooted in recovery mode; the screen scrolled with commands being executed to exactly the same point:

And there it sits. It looks like it's awaiting a command, which implies there's something wrong with the boot. The only way out is to crash it. Startx gives the same result as above.

Any help appreciated

---

### Post by Peter09 on 2008-03-15
It seems that your O/S  is working, at least in safe mode. When you use startx in safe mode you get through to the graphical interface. Logging out from safe mode will get you back to the prompt. You would need to type 

```
shutdown -now
```

at the prompt to properly shutdown the machine.

What graphics card has your machine got, it could be that you just need the correct driver for that.

PC

---

### Post by wiseloki on 2008-03-15
Machine specs in the top post.

Graphics card - ATI Mobility Radeon 7500 with 32MB

Noob questions  -why could it be the graphics card if Ubuntu displays OK off the CD and when I type startx? And startx is safe mode?

Thanks for the shut-down info - at least I won't have to crash it now.

---

### Post by Peter09 on 2008-03-15
I think (not sure) that Ubuntu uses a limited form of driver for the default (no 3D rendering etc). When you come to boot the real system it attempts to install a better driver, which sometimes fails. The ATI drivers are notorious for giving problems. ENVY is a simple way of resolving this.

ENVY can be found here:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


PC

---

### Post by wiseloki on 2008-03-15
OK, not trying to gainsay you here and I'm grateful for your help, but would a graphics card explain why it's stopping where it is at "root@pvs-ibm:~#_"?

I have no idea what ENVY is, apart from the feeling I have when I read about people who's Ubuntu installation boots OK.

[Edit} OK, I've had a look at the ENVY page and it required that I install with Ubuntu open - is it OK to do this in safe mode, as it's the only way I can get it to run.

If I uninstall the graphics cards drivers and install the ones Ubuntu needs with ENVY, will XP still boot OK? I don't want to go from no Ubuntu to no laptop.

---

### Post by Peter09 on 2008-03-15
Is that in safe mode? 

That is the terminal prompt which you should get at safe mode if your Graphical session fails. Unlike MSWindows, Ubuntu is a terminal based system (looks like safe mode) upon which a graphical window manager is running. If the window manager fails it drops you back to the terminal prompt.

PC

---

### Post by Peter09 on 2008-03-15
ENVY will just automate the install of the best driver for your card. You download and install it. Then run it and it will do its best - which is pretty good.

PC

---

### Post by Peter09 on 2008-03-15
yes - you can install ENVY from safe mode, it will do all the work after that. It will not affect your XP installation. It does not touch any part of the BOOT process (GRUB).

---

### Post by wiseloki on 2008-03-15
So it's not uninstalling the graphics card drivers that Windows will use?

And, if you read the post above, the only way I can get Ubuntu to start is to run it in Recovery, then type "startx" when it stops, which I was told was safe mode.

I just tried and with Ubuntu running in "safe" mode (if that's what it is) I can't get any Ethernet connection, so I can't access the ENVY website with Ubuntu running.

[Edit] "Shutdown --now" doesn't work, by the way.

---

### Post by Peter09 on 2008-03-15
Ubuntu and Windows are on separated bits of your hard drive. They will not share any programs.

Can you attach your laptop to a wired (not wireless) connection. That should give you an ethernet connection in safe mode.

---

### Post by wiseloki on 2008-03-15
It was on an Ethernet connection - no network or internet

---

### Post by Peter09 on 2008-03-15
Can you see the network ICON (two terminals) at the top of the screen, you need to click on that and enable your connection.

---

### Post by Peter09 on 2008-03-15
if you cannot get your internet working type the following in from the command prompt. When you get to the section asking for your graphics card driver select the visa one. Then reboot.

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

PC

---

### Post by wiseloki on 2008-03-15
No "two terminals" icon

(note - there was when running from the CD and the laptop could access the internet)

I tried to select the network option off System\Admin and got a warning box that said "The configuration could not be loaded - you are not allowed to access the system configuration"

---

### Post by Peter09 on 2008-03-15
OK, we need to get you running in a basic graphics mode, so see my previous post.
PC

---

### Post by wiseloki on 2008-03-15
And I tried "sudo dpkg-reconfigure -phigh xserver-xorg" from terminal from Accessories and I got 
> xserver-xorg postinst warning: overwriting possibly-customised configuration 
     file; backup in /etc/X11/xorg.conf.20080315103623
root@pvs-ibm:~#<blinking cursor>

---

### Post by wiseloki on 2008-03-15
Bear in mind that I'm doing this from the desktop, having entered "startx" at the prompt during the boot

---

### Post by Peter09 on 2008-03-15
Did you not get any interface? If not try without the -phigh bit.
The warning is ok.

PC

---

### Post by Peter09 on 2008-03-15
You can do it from a terminal in the GUI or at the same prompt that you typed Startx from - should not matter. I gave you the wrong command, you did not need the -phigh which is why no interface.

PC

---

### Post by Peter09 on 2008-03-15
Note that you can leave all the rest as defaults, just change the graphics driver to vesa.

PC

---

### Post by wiseloki on 2008-03-15
OK, without the -phigh it worked.

I got asked a shed-load of questions that I had no idea what the correct answer is (I tried to keep my keyboard but I still ended up having to guess various settings for keyboard, screen, etc) and after I'd been through all the options, I ended up with
> xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20080315105428
root@pvs-ibm:~#<blinking cursor>

In a terminal window. The last 4 numbers of the warning have changed. Nothing else appears to have altered. Do I close the terminal now?

---

### Post by Peter09 on 2008-03-15
reboot

PC

---

### Post by wiseloki on 2008-03-15
No change, apart from after "startx" in recovery mode the graphics are now cruder.

No network connection either

---

### Post by Peter09 on 2008-03-15
But can you boot normally, without recovery mode?

What happens when you just let the machine boot up?

PC

---

### Post by wiseloki on 2008-03-15
I left the normal to boot for an extended time, rather than crashing it, and I got a very a partly blue screen with a blocky black message on a white background that says > The display server had been shut down about 6 times in the last 90 seconds it is likely that something bad is going on

There is a lot of "Toe" (but with umlauts and accute accents) down both sides of the white portion of the screen

[Edit. Error message corrected]

---

### Post by Peter09 on 2008-03-15
what was the final state of the machine, did you get to a GUI at all?

PC

---

### Post by wiseloki on 2008-03-15
No, blue and white warning screen - see my last post (I just clarified it)

---

### Post by wiseloki on 2008-03-15
The only way I can get to the GUI is via recovery, then "startx"

---

### Post by Peter09 on 2008-03-15
This is getting complex, it looks like your greeter is crashing :(

Try letting it boot normally and then once you have the strange screen doing a Control-ALT-F1 which I think should get you to a prompt where you may be able to login using your user name and password, then type startx and you may start your normal session (not recovery).

PC

---

### Post by Peter09 on 2008-03-15
Just read your message and agree we will keep to forum.

Suggest first that you get all the upgrades for Gutsey (the upgrade manager should be suggesting that you download them). Then get ENVY. The problem is most probably that your graphic drivers are incompatible with the greeter. 

However downloading the upgrades and using ENVY may well overcome this.

PC

---

### Post by wiseloki on 2008-03-15
OK,

To recap. With the graphics reset to ATI (and the system recognised the card type) I rebooted, after an extended time I did <Ctrl><Alt><Backspace> and, after another lengthy delay, I got to the login screens.

I logged in and got the desktop, with a working network connection.  There was only one HDD symbol on the desktop, correctly identified as IBM_PRELOAD.

Firefox can access internet. OpenOffice opens, keyboard appears to type correct symbols, all seems well.

I tried the Download Manager and was told my software was up to date.

So what is <Ctrl><Alt><Backspace> doing to complete the boot? 

We seem to be very close now.

---

### Post by Peter09 on 2008-03-15
CTRL-ALT-BACKSPACE returns you to the non-GUI login prompt. The problem you have is that the screen that controls the graphical login is crashing.

This may be resolved by putting a better driver in (Hence ENVY). If the fails we can try to reconfigure the login screen so that it works. I suggest that the first thing to do is to get the best driver for your card.

PC

---

### Post by wiseloki on 2008-03-15
When I did <Ctrl><Alt><Backspace> I got the normal GUI login screens - brown/gold in colour

First screen asking for login name in a box

Second screen asking for password

(Unless I misunderstood - this is what I get on the Dell that I installed from this CD)

---

### Post by Peter09 on 2008-03-15
Sorry, thought that you got the command prompt login.

You may find now that just shutting down and restarting may all work as it may have captured the correct settings.

PC

---

### Post by wiseloki on 2008-03-15
You're nearly right.

When I rebooted, I eventually got through to the GUI login screens, but what is happening is that the boot process is happening with a black screen, so you (I) have no idea what is going on.

When the Dell boots, I have the Ubuntu symbol and the scanning progress bar. But the Dell does not have the multi-OS option. So is something in the OS choice stopping me seeing the normal boot-up screens?

Anyway, I can probably live with this if I have to, as at least it boots OK (it just keeps me in suspense with a black screen)

I'm afraid I have to do some RL stuff now - either that or see a divorce lawyer.

Back in a couple of hours - it would be nice to get the proper boot, if we could

---

### Post by Peter09 on 2008-03-15
OK.

Heres is the fix in this thread

[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

PC

---

### Post by wiseloki on 2008-03-15
Excellent!

That post had exactly my problem - screen res of 1280x1024; changed to 1024x768 (I'm going to have to start remembering some of these sodo commands - using a terminal takes me back to my BBC 'B' and W3.1 days).

Changed the screen res, updated the usplash, and the boot time is now about a quarter of what it was, I get the splash screen and progress bar (at least for most of the boot)

I guess I now need to do another complete install to reinstate my separate '/home' partition - but at least I know now how to tweak it to get it to work when I do.

Thanks again :biggrin:

---

