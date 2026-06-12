---
title: "No grub menu, intel graphics driver &amp; native res not detected"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by zbyszek_p on 2014-08-11
I selected for my old Sony Vaio VGN-C13G the latest Kubuntu 64-bit, as it seems to me the most promising. Unfortunately just after the installation I discovered 2 main issues. I think that they are inter-related. 
1. Since the installation Grub 2 menu has never been shown during the booting process.
2. The intel driver has not been used but vesa and detected resolution is below the native one ie.1280x800. Current resolution is 1024x768
After I switch on my laptop I see Sony splash screen, blank screen for about 30 seconds and then KDE splash screen and later the normal desktop.

Let me give you a bit more details about this laptop - Sony Vaio VGN-C13G released in 2006:

CPU: Intel(R) Core(TM)2 CPU T5500 @ 1.66GHz
Mem: 3GB
Kernel: Linux 3.13.0-32-generic
Let me add that there's only one hard disk and only one OS on my laptop.

What I have tried to rectify the situation:

1. Followed the "Graphics Resolution- Upgrade /Blank Screen after reboot" thread.
To show menu on boot I placed a # symbol at the start of the line GRUB_HIDDEN_TIMEOUT=0, checked GRUB_TIMEOUT=10, run sudo update-grub and rebooted.
reinstalled grub
```
zbyszek@zbyszka-VGN-C13G:~$ sudo grub-install /dev/sda
[sudo] password for zbyszek: 
Installing for i386-pc platform.
Installation finished. No error reported.
zbyszek@zbyszka-VGN-C13G:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
zbyszek@zbyszka-VGN-C13G:~$
```

I followed the post:
If No, reinstall grub and Start Step 1 from Beginning...
changed GRUB_HIDDEN_TIMEOUT=00, updated, rebooted
After i pressed left shift the message "Grub loading" appeared in the top left corner for 1 sec, screen blanked and computer hanged

Uncommented the line in the /etc/default/grub that says gfxmode=680x480, updated grub,rebooted. PC hanged.

2. I checked [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) where I found such info "Frozen splash screen, blinking cursor with no grub> or grub rescue prompt. Possible video issues with the kernel". What I can do???

3. Checked /var/log/Xorg.0.log
I would like you to notice the following errors and warnings (lines are not in a consecutive order):
```
[    35.838] (EE) open /dev/dri/card0: No such file or directory
[    35.838] (WW) Falling back to old probe method for modesetting

[    35.839] (EE) open /dev/fb0: No such file or directory
[    35.839] (WW) Falling back to old probe method for fbdev

[    35.839] (EE) Screen 0 deleted because of no matching config section.

[    36.416] (EE) AIGLX: reverting to software rendering

[    36.416] (EE) AIGLX: reverting to software rendering

     36.350] (WW) VESA(0): Unable to estimate virtual size
    
[    36.350] (WW) VESA(0): No valid modes left. Trying less strict filter...

[    36.350] (WW) VESA(0): Unable to estimate virtual size
[    36.369] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
```

If I cannot successfully boot grub I cannot also implement the most of suggestions from the thread which I mentioned in point 1. The 2 issues are well beyond my experience and I really need your help, please.

---

### Post by kc1di on 2014-08-11
for the boot menu do this:
go to a terminal and open an editor as root ```
sudo kwrite 
``` for kubuntu. I think it's kwrite but you can use any text editor. 

then open /etc/default/grub

when it opens scroll down until you find the following line:
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480 
```
change the #GRUB_GFXMODE=640x480 to read like this
```

GRUB_GFXMODE=1024x768
```
save the file then exit it.
now type this command
in the terminal 
```

sudo update-grub
```
then reboot. you should now be able to see the grub menu. 
good luck

---

### Post by zbyszek_p on 2014-08-11
I followed all your suggestions kc1di but still cannot see grub menu. The only difference was that initially I saw a short horizontal cursor and hundreds of tiny, colorful lines covering the whole screen.

---

### Post by oldfred on 2014-08-11
Are you holding shift key from BIOS until menu appears.
If you only have one install, it will not normally show grub menu.

---

### Post by zbyszek_p on 2014-08-11
I agree in normal circumstances pressing left shift should help but not in my case. As I indicated at the beginning I spent a lot of time following all suggestions from the thread  "Graphics Resolution- Upgrade /Blank Screen after reboot".

---

### Post by grahammechanical on 2014-08-11
Sometimes we get too much information. The steps you took at item 1 should have worked. But this had nothing to do with the reason why the Grub menu was not showing.

> [COLOR=#000000]Uncommented the line in the /etc/default/grub that says gfxmode=680x480, updated grub,rebooted. PC hanged.[/COLOR]

As this a new installation and the problem has gone from getting the Grub  menu to show to getting Ubuntu to boot. I suggest that you re-install. I have many OS on my machine and this is what my /etc/default/grub looks like

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


I get a Grub menu with a 10 seconds delay until it loads the first OS in the list. Later on in that thread the person who started the thread gave a suggestion about forcing Grub to show the menu if putting the hash ( # ) in front of GRUB_HIDDEN_TIMEOUT=0 does not work. His suggestion is to change the file to 

> GRUB_DEFAULT=0
[COLOR=Red]GRUB_HIDDEN_TIMEOUT=""
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=20
[/COLOR]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


I do feel that a re-install at this stage is the best way forward. The problem of the video driver is another matter. If we tick to install third party software during the installation of Ubuntu then we get a proprietary video driver installed.  I understand that Intel video drivers come as standard with Linux installing on a machine with Intel video adapters. We would need more information about your graphic set up to deal with that problem. If it is a problem. VESA = Video Electronics Standards Association. Linux comes with several Xserver video modules to deal with most graphic adapters. Vesa is just one of them. 

Regards.

---

### Post by zbyszek_p on 2014-08-12
I reinstalled Kubuntu and all problems remain the same. If I could find good troubleshooting procedure for Grub 2? Or maybe I should use Grub 1? I think that fixing up grub is really important because I could play with different kernel commands during the boot, just for testing of my video setup

---

### Post by oldfred on 2014-08-12
I still think it may be a video issue. Perhaps grub cannot see your native mode or you have not set it correctly.

From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


---

