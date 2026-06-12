---
title: "NVidia driver situation?"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by mistertransistor on 2011-05-28
I'm new to Ubuntu. I've just done a fresh install of 11.04 (three times) on quite an old PC with an NVidia FX 500/600 graphics card.
  Perhaps the first thing to say is that during installation it says that my hardware is not good enough to support Unity so I should choose classic Ubuntu. However, I am never presented with any choice at any point. I would guess that I am in 'classic' Ubuntu, but since those terms mean nothing to me, I don't really know.
 The install works fine, but afterwards Ubuntu tells me that I should install a proprietary driver for the NVidia. I have done so using System/Administration/Additional Drivers. I have done it twice and both times it wrecked my desktop. The screen seems to show part of a much larger image but it is jumping around from part to part. Keyboard and mouse still work so I can get to the command line using ctrl-alt-F1.
  The first time this happened I searched these forums and found many people with roughly similar problems. There seemed to be no clear solution though, and not even clear instructions on how to remove the driver. I tried the ones that looked promising without success. I still have not found how to do this, so a definitive answer to that question would be good because it would allow me to try the driver again without fear of having to rebuild the whole system afterwards.
  That's what I had to do, and then I went to the NVidia site and downloaded a driver from there. I was rather puzzled because during the download the page seemed to show a shell script, and after the download there was nothing in my Downloads directory. I kind of assumed it might have changed the driver so I used Additional Drivers again. It displayed the popup saying 'Downloading and installing driver' which worried me so I clicked the Cancel button. Nothing. I clicked it many times - it went on to download and install and wreck my desktop. Why does the Cancel button not work???

Now, after a third system build, I'm working again but the screen has low resolution, and even worse, a low refresh rate causing flicker. System/Preferences/Monitor says my monitor is unknown and won't offer more than 60Hz. 

Is there anything I can do to resolve this?

Andrew

---

### Post by Herman on 2011-06-11
> Keyboard and mouse still work so I can get to the command line using ctrl-alt-F1.
  The first time this happened I searched these forums and found many  people with roughly similar problems. There seemed to be no clear  solution though, and not even clear instructions on how to remove the  driver. You can disable the driver by removing the file in /etc/X11/ called xorg.conf, 
```
sudo rm /etc/X11/xorg.conf
```or else at least deleting all of the text in it and then if you log out and log back in again your desktop should be back to normal.

To write a new /etc/X11/xorg.conf file and re-activate the driver you might use the following code,
```
sudo nvidia-xconfig
``` You will need to log out and then log back in again.

Another way of recovering from Xserver trouble is to scroll down one line while your GRUB Menu is displayed at boot time and select to boot in recovery mode. There are options in the recovery console for reconfiguring your Xserver and that's another way of getting rid of the /etc/X11/xorg.conf file and allowing you to reboot into a normal desktop again.

If you're not dual booting you may not see your GRUB Menu, and we used to be able to bring it up by tapping 'Esc' after the BIOS boot screens. That didn't work for me today for some reason. To get my GRUB Menu to display at each boot up, I edited a file called /etc/default/grub and placed a hash mark to 'comment' render inactive), the line that says '[FONT=Bitstream Vera Sans Mono]GRUB_HIDDEN_TIMEOUT=0', which is about the 7th line in the file,
[/FONT]```
gksudo gedit /etc/default/grub
``````
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
[COLOR=Red]**#**[/COLOR]GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="elevator=deadline"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```Notice the hash mark in the above file, bolded and shown in red for emphasis.

Finally, I ran 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to write the changes to my grub.cfg file,
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```From now on I'll see my GRUB Menu each boot-up, even though I'm not actually dual booting, (at least not in this particular machine).

Another idea would be to install an auxilliary Ubuntu installation in a USB flash memory stick, but don't make a 'persistence' install which boots with syslinux like a Live CD, but instead make a full, normal installation the same as a hard disk installation so that it boots with GRUB. It's very useful at times when you need to be able to fix things or perform maintenance tasks on your main, hard disk installed operating system. That will also give you access to your GRUB Menu which is sometimes very useful.

Sorry but I don't know how to solve your actual video driver problem. The standard Ubuntu driver should be okay for normal use, except if you need to use Google Earth or play some games, or use the new unity desktop. I have a nVidia Corporation G92 [GeForce GTS 250] (rev a2) card and mine works very well in Ubuntu so I'm lucky.

---

### Post by mistertransistor on 2011-06-15
Thanks very much for your reply Herman. I have spent a good number of hours trying various 'solutions' that are out there. I did manage to get a higher resolution, but not a usable refresh rate. 
  I've now gone back to Windows XP as it works much better on my 'old' PC than Ubuntu. I don't just mean the NVidia situation. Netbeans is *much* slower on Ubuntu than on XP, using the same hardware. That surprised and disappointed me.
  There's also an oddity that a screen 1024 x 768 looks fine in XP but it looks like text is bigger in Ubuntu (icons too) and it's just too small.

  Maybe I'll try again when I have a more powerful PC available. I've still got Ubuntu on my unattended data acquisition box, but I'm not entirely happy there either. After about a week it freezes and I have to power cycle. Not what I expected either.

Andrew

---

### Post by oldfred on 2011-06-16
I have a somewhat newer nVidia 9600GT. But it shows both drivers as options. Did you install the correct driver. And since it is the older driver, then nVidia should at least have a working version.

This from nVidia.
Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

---

### Post by MAFoElffen on 2011-06-16
> **mistertransistor said:**
> I'm new to Ubuntu. I've just done a fresh install of 11.04 (three times) on quite an old PC with an NVidia FX 500/600 graphics card.
  Perhaps the first thing to say is that during installation it says that my hardware is not good enough to support Unity so I should choose classic Ubuntu. However, I am never presented with any choice at any point. I would guess that I am in 'classic' Ubuntu, but since those terms mean nothing to me, I don't really know.
 The install works fine, but afterwards Ubuntu tells me that I should install a proprietary driver for the NVidia. I have done so using System/Administration/Additional Drivers. I have done it twice and both times it wrecked my desktop. The screen seems to show part of a much larger image but it is jumping around from part to part. Keyboard and mouse still work so I can get to the command line using ctrl-alt-F1.
  The first time this happened I searched these forums and found many people with roughly similar problems. There seemed to be no clear solution though, and not even clear instructions on how to remove the driver. I tried the ones that looked promising without success. I still have not found how to do this, so a definitive answer to that question would be good because it would allow me to try the driver again without fear of having to rebuild the whole system afterwards.
  That's what I had to do, and then I went to the NVidia site and downloaded a driver from there. I was rather puzzled because during the download the page seemed to show a shell script, and after the download there was nothing in my Downloads directory. I kind of assumed it might have changed the driver so I used Additional Drivers again. It displayed the popup saying 'Downloading and installing driver' which worried me so I clicked the Cancel button. Nothing. I clicked it many times - it went on to download and install and wreck my desktop. Why does the Cancel button not work???

Now, after a third system build, I'm working again but the screen has low resolution, and even worse, a low refresh rate causing flicker. System/Preferences/Monitor says my monitor is unknown and won't offer more than 60Hz. 

Is there anything I can do to resolve this?

Andrew
@Andrew 
Yes. there is.  There is lots you can do, but it would be a good idea to see what is wrong so you aren't trying to use a sledge hammer to press in a thumb tack.  First we need a snapshot of what you have and what is going on.

Please post the results of:
```

lspci -vv | grep VGA
sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q
lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p

```Which will give us the info on your video card and monitor as 11.04 see's them.  

If hwinfo returns a "command not found" please instal via 
```

sudo apt-get install hwinfo

```And run those commands again to post the info from above.

The next 2 files to post are;
```

/etc/X!!/xorg.conf 
/var/log/xorg.0.log

```That will tell us an idea on what drivers you are using, how they are configured and what modules are being loaded...

---

