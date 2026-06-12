---
title: "Ubuntu 10 in low-graphics mode"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by moisessalum on 2010-05-03
Hi,

Yesterday I updated my computer from 9.10 to 10.04...
When I restarted my computer it appeared this message.

> Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.
(EE) No devices detected.

After that, it comes a window with the question "What would you like to do?" and 5 options...

> Run UBUNTU in low-graphics mode.
Reconfigure graphics.
Troubleshoot the error.
Exit to console login.
Restart X

I'm going now with the first option, because I used to reconfigure graphics but my computer freezes with no aparent reason in the login window...

Help Please!!

I have a HP Pavilion 7956.

Thanks...

---

### Post by couzin2000 on 2010-05-03
Having the same exact problem - I upgraded from 9.04 to 9.10, worked flawlessly. 5 mins later, upgraded from 9.10 to 10.04 - and got problems.

The upgrade went on without a hitch, though I chose at every turn to not change my menu.lst file (grub-related since I have a dual boot), but nothing bad.
Finally, I reboot. I get the text-only mode, and when the graphics driver tries to load, the screen flickers, and I get the low-graphics mode message:

[INDENT]**Ubuntu is running in low-graphics mode.**
The following error was encountered. You may need to update your configuration to solve this.
(EE)NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE)NVIDIA: system's kernel log for additionnal error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.[/INDENT]
I want to hit the OK button, but gee wiz, the MOUSE DRIVERS AND KEYBOARD DRIVERS AREN'T RUNNING YET.
So I can't do squat.
Any suggestions?

Perhaps loading from live disc and changeing the nvidia module? Point us to the right directions please...

---

### Post by boss_aadi on 2010-05-03
hai to all,

exactly same problem....

i m downloaded **ubuntu-10.04-desktop-i386.iso** torrent, when i m starting installation, at the first step(language selection) it self my Keyboard and Mouse are not working.

After words i searched in Ubuntu forums and tried with **i915 modeset=0 xforcevera** command at installation menu by pressing F6 function key,after words i got error messages like this 

[B]Ubuntu is running in low-graphics mode
EE(VERA:Kernal modesetting driver in use,refusing to load)
EE No devices detected.[/B]



i tried with upgrade from 9.10 to 10.04, after upgrade complete at last step(Restart) again keyboard and Mouse are not working.

my system configuration

[B]Intel(R) Pentium(R) D CPU 2.66GHz 
512 Mb RAM
80 GB Hard disk
ATI Technologies Inc RC410[Radeon Xpress 200]
[/B]
please help to solve this problem.....

---

### Post by couzin2000 on 2010-05-03
Some more info here...

I managed to boot from the Live CD, and I can see that all my drives, files and so on, are all there. What's even better is that the CD is offering to run the restricted-mode video drivers (I get version 179 in the offer).

I'm trying to reach log files but failing miserably at it. Though I do see /var/log, and its contents, I can't understand a word they mean nor do I see anything relevant. I can't even find a date that's set close to today.

Checked /etc/fstab, nothing unusual to report. Not getting the problem of mounting /dev/null.

Think this is maybe related to me having installed a different version of the Nvidia drivers before, then upgrading to 9.10, then again to 10.04, without me changing the version of the driver? I redownloaded the newer version from this article here: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html"), but I don't think I'll even be able to install since I'm running from the live CD. Version downloaded of the Nvidia drivers: 195.36.24. I have a 9600GT inside, and it's an AMD X2 64, running 32-bit version.

What's worse, I can't find a way to boot to terminal mode - I'd probably have to redo my grub, but from live cd, doesn't sem to be working.

Please help!

---

### Post by ganeshmallyap on 2010-05-03
I too faced the same issue on my Lucid LTS AMD64 with NVIDIA GeForce 7100 mother board.  The only thing worked me is the following. I found this information on a website and the link for that article is [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html). 


1) Download Newest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")
 2) Open module blacklist as admin
 [INDENT]gksudo gedit /etc/modprobe.d/blacklist.conf
[/INDENT] Add these lines and save:
 [INDENT]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[/INDENT] 3) Uninstall any previously installed Nvidia drivers:
 [INDENT]sudo apt-get --purge remove nvidia-*
[/INDENT] 4) Reboot your computer
 5) When an error message pops up saying that Ubuntu cannot load  Nvidia drivers, choose Exit to terminal (Exit to console)
 6) Login and cd to the directory where you saved your file
 7)Install drivers
 [INDENT]sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
[/INDENT] 8)Start GDM
 [INDENT]sudo service gdm start
[/INDENT]

---

### Post by couzin2000 on 2010-05-04
> **ganeshmallyap said:**
> I too faced the same issue on my Lucid LTS AMD64 with NVIDIA GeForce 7100 mother board.  The only thing worked me is the following. I found this information on a website and the link for that article is [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html).

Thanks for the reference. I actually posted the same link above, which I totally want to apply to my PC, except that *I need instructions on how to perform this from a LIVE cd* instead of command line -- because as stated above, I have no access to the keyboard or mouse. 

Unless there's a way for me to boot to terminal? (Remember, I haven't updated my grub menu, and I just tried doing that from live cd, and the update failed since it doesn't see the grub app).

---

### Post by texaswriter on 2010-05-05
For the mouse and keyboard problem earlier, you are going to need a usb/pci [read: not wireless] keyboard.

---

### Post by couzin2000 on 2010-05-05
My keyboard and mouse are currently connected through USB. I am not trolling this thread.

Anybody else have an idea as to how to access the terminal from bootup?

---

### Post by boss_aadi on 2010-05-05
i did not get any solution here, were can i go?

---

### Post by couzin2000 on 2010-05-06
Still no results...

I've been trying to get my keyboard/mouse to work, but with no success. I can't access the system while it's in low-graphics mode.

Is there any way I can install the actual cd onto my current system without it erasing the stuff I have in there? Upgrading doesn't seem to work, but I tried installing and the system offers formatting the drive before installation... and there's no way around that. I wish to avoid that.

Anyone? Isn't there a way to get to the terminal mode instead of booting and letting the error compromise the access to begin with?

---

### Post by couzin2000 on 2010-05-07
Well, after trying like mad to find an alternative solution to a full reinstall, I've managed to [FONT="Courier New"]sudo nautilus[/FONT] into my [FONT="Courier New"]/home[/FONT] folder, and copied everything to another hd. I've not found anything to help me, and there is no accessing the terminal mode without a working mouse or keyboard. So I'm reinstalling as we speak.

Let's see if the reinstall gives better results than the upgrade.
Thanks anyway!

---

### Post by couzin2000 on 2010-05-08
So I actually installed from the CD, but there WAS an option not to format. This type of install, where I reinstalled on top of the 9.04 upgraded to 9.10 and 10.04, did not erase what I had, and I was able to boot into the Nvidia driver properly. All works now! Thanks for the help!

---

### Post by jcorriher on 2010-05-08
It didn't solve the overall problem, but I was able to use my USB mouse after the low graphics window pops up by unplugging the USB mouse and plugging it back in.  Still trying to resolve the low graphics issue...

---

### Post by Dr_Willis on 2010-05-16
Ive had the 'going into low graphics mode' issue on and off all during beta testing and now after release. I cant even get it to  do it on a regular basis. It will do it one bootup, but not the next 4.  

When it Does do it ive noticed i can  Go to the console and restart the GDM service and X normally then works corectly.

(from the menu item)

-->_ Exit to console login._

At the console 

[COLOR="Black"]**sudo service gdm restart**[/COLOR]

This seems to be an issue with the time it takes the nvidia drivers to load vs the timeouts in the gdm configs. (from what i am finding on other forums)

Most of the fix's ive seen (that may or may not actually work) Involve altering the GDM timeouts in various gdm configs. 

One potential fix 

in **/usr/share/gdm/custom.conf ** add the 2 lines. 

[B][daemon]
GdmXserverTimeout=30
[/B]

I have also seen guides that say add these 2 lines to these various files.

[B]/usr/share/gdm/defaults.conf
/etc/gdm/custom.conf[/B]

Just to be OVERKILL i added the entries to all 3 files.  :confused:
So far ive not seen the issue happen again. But only time will tell.
Im not sure if this is a proper fix or there may be better ways. but its a lot less intrusive then removing things and trying the drivers from the nvidia.com site.

I also decided to blacklist the modules listed earlier in this thread.

---

### Post by Dejavou42 on 2010-05-16
I can confirm this issue on lucid lynx. I have a nvidia geforce video card, and I get the low graphics mode on every bootup. I tried the suggested fix by Dr_willis, and I still get the same problem. However, after logging in in low graphics mode, I can use sudo service gdm restart, which always allows the nvidia drivers to load. I am going to try changing the timeout of 30 seconds to 60 seconds to see if that fixes my issue.

Edit for new information:

I changed the timeout to 60 seconds instead of thirty, but this did not fix the low graphics mode. I also noticed that the low graphics mode error message has changed a bit. Instead of the normal nvidia drivers error message, I am getting:
> 
**Ubuntu is running in low-graphics mode**

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.


However, as I said before, restarting gdm fixes this until the next reboot.

---

