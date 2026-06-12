---
title: "Plymouth low res boot screen."
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by ancleessen4 on 2010-04-11
I have searched the forums on this problem and I am still not really clear on the fix for this or even if I should wait for final release.
I am running Lucid 64bit and have upgraded through the cycle from Karmic. I am using nvidia proprietary drivers. All the time that the Plymouth boot screen has been available it has been in low resolution. As we are now at beta 2 I am torn between searching a fix or waiting for the final release...

So, from what I have read I need the 'nouveau' driver to fix this issue.
1. How do I install this in place of my existing nvidia proprietary driver?
2. I am a little bit confused by the hardware drivers selection panel telling me that I have an nvidia driver installed but that it is not in use-I read that this might be a bug??

A clear step by step fix would make a busy guy very happy :wink:

---

### Post by Kow on 2010-04-11
Take a look at /etc/default/grub and change 'GRUB_GFXMODE'. For example, mine is 'GRUB_GFXMODE=1024x768'. After saving the changes, run 'sudo update-grub'. Reboot and enjoy a nice plymouth and the proprietary nvidia driver. I don't give step-by-step fixes in development.

---

### Post by x-shaney-x on 2010-04-11
I posted a similar query yesterday.
I can't comment on  'nouveau' as I have never had any experience but I have found something that seems to be working for me with nvidia:

Edit /etc/grub.d/00_header
Then look for the line "set gfxmode=${GRUB_GFXMODE}"  (line 103 in my case).
Add a line right beneath it like this:
set gfxpayload=1280x1024 (with your desired resolution).

Though the strange thing is this will only allow me to use the dmicode resolution so the aspect ratio is slightly off for me.
My monitor res is 1680x1050 but in grub and plymouth it won't work with that or other resolutions with the same ratio.

I also found this page: [http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html)
With those instructions, using gfxpayload=keep instead of the actual resolution, I found I was often left with a black screen without it reaching the desktop for some reason.

---

### Post by ubername on 2010-04-11
I have found 
```
set gfxpayload=keep
```
works fine for me ( I don't have the probs x-shaney mentions above)

---

### Post by ancleessen4 on 2010-04-11
@ubername @x-shaney-x @kow thanks for your input.
I will try this fix when I get back to my home machine...

---

### Post by x-shaney-x on 2010-04-11
> **ubername said:**
> works fine for me ( I don't have the probs x-shaney mentions above)

I have since seen that solution posted in a lot of places and it seems to work for other people.
It seems to be when my res switches from the boot res to my desktop res something goes wrong but not if I set the boot res for gfxpayload.
[FONT=monospace]Wish I could get the same res for my desktop and for boot.[/FONT]

---

### Post by nanog on 2010-04-11
that solution breaks tty which could be bad if you get the wrong kind of testing breakage. there is a monumentally long thread+bug report. its being worked on and i'm sure it will be fixed by release.

---

### Post by x-shaney-x on 2010-04-11
I found this information in /usr/share/doc/plymouth/README.Debian:

```
High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```

Tried it and it did nothing for me and looking at dmesg it wasn't using vesafb anyway.

---

### Post by philinux on 2010-04-15
> **Kow said:**
> Take a look at /etc/default/grub and change 'GRUB_GFXMODE'. For example, mine is 'GRUB_GFXMODE=1024x768'. After saving the changes, run 'sudo update-grub'. Reboot and enjoy a nice plymouth and the proprietary nvidia driver. I don't give step-by-step fixes in development.

I'm getting a rather large ugly ubuntu logo. Basically it res is too low on my 22" lcd its ugly.

Change the res as above only changes the grub menu res for me.

nVidia 8600

---

### Post by Nightstrike2009 on 2010-04-15
I am experiencing similar problem when ati opensource driver was in use the boot screen was high res. Since using the closedsource ati driver (from hardware wizard) I have a low res boot screen & hi-res desktop.

---

### Post by csaket on 2010-04-15
> **philinux said:**
> I'm getting a rather large ugly ubuntu logo. Basically it res is too low on my 22" lcd its ugly.

Change the res as above only changes the grub menu res for me.

nVidia 8600

I am not sure how to do this with Grub2 but what I ended up doing was to edit the grub.cfg and put in vga=799 in the linux line after ro.
This gave me a good resolution though its aspect ratio is not perfect.

---

### Post by manoynmonic on 2010-04-19
> **Kow said:**
> Take a look at /etc/default/grub and change 'GRUB_GFXMODE'. For example, mine is 'GRUB_GFXMODE=1024x768'. After saving the changes, run 'sudo update-grub'. Reboot and enjoy a nice plymouth and the proprietary nvidia driver. I don't give step-by-step fixes in development.

Perfect!  I changed plymouth to some of the cool splash screens - but that broke suspend.  Reverting to Nvidia drivers and tweaking grub per your post gives me both working suspend and nice looking plymouth splashies.  

I just checked System>Preferences>Monitors and made the grub resolution the same as my default monitor resolution (the text of boot options is TINY now, but who cares?) to keep the boot animation looking right.

Thanks.

---

### Post by sgleo87 on 2010-04-26
> **philinux said:**
> I'm getting a rather large ugly ubuntu logo. Basically it res is too low on my 22" lcd its ugly.

Change the res as above only changes the grub menu res for me.

nVidia 8600

Same here....anybody found a solution for this yet???

---

### Post by wnelson on 2010-04-26
Is there a framebuffer display driver being loaded? Like vesafb?

---

### Post by elkikin on 2010-04-26
There seems to be a workaround:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

I'm tempted to try it...

---

### Post by elkikin on 2010-04-26
> **elkikin said:**
> There seems to be a workaround:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

I'm tempted to try it...

I can confirm that the above fix works with the NVIDIA closed drivers. I can see the default Ubuntu Plymouth splash at my monitor's default resolution (1280x1024-24).

Just follow the steps the author indicates to use uvesafb and what not.

---

### Post by csaket on 2010-04-26
idyllictux's solution looks cool. will try it tonight on my ubuntu&kubuntu setups.
thanks for sharing

---

### Post by Bobhuber on 2010-04-26
> **elkikin said:**
> There seems to be a workaround:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

I'm tempted to try it...

Worked perfectly for me. Don't know what will happen when they update the grub program though.

---

### Post by manoynmonic on 2010-04-26
Hey, I had the same issue.  My quick and dirty fix:

I changed this line in /etc/default/grub

GRUB_RESOLUTION=


Changed the default grub resolution to the regular resolution of my monitor (check in System>Preferences>Monitor - I think that's the path, not on my ubuntu box atm).  This made the text of the grub splash TINY - but also made plymouth boot splash display at the proper resolution.

---

### Post by wnelson on 2010-04-27
> Originally Posted by elkikin  
There seems to be a workaround:

[http://idyllictux.wordpress.com/2010...ricted-driver/](http://idyllictux.wordpress.com/2010...ricted-driver/)

I'm tempted to try it...


This is so much cleaner than my solution.

Thanks.....

---

### Post by sgleo87 on 2010-04-27
Found a solution that works for me. Here is my /etc/default/grub (I marked the changes in bold)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050[/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Note: Don't forget to change "1680x1050" to your native resolution ;)

---

### Post by cottfcfan on 2010-04-27
Anybody know if the above fix also works  for the ATI cards using FGLRX?
 My boot screen is just ugly.

---

### Post by philinux on 2010-04-27
If anyone is happy with the default grub resolution, I am, then just use this bit in /etc/default/grub to set plymouth resolution.

```
GRUB_GFXPAYLOAD_LINUX=**1680x1050**
```

Then 

```
sudo update-grub
```

1680x1050 = my native res as mentioned above by sgleo87.

---

### Post by dino99 on 2010-04-27
got new plymouth releases few minutes ago

---

### Post by x-shaney-x on 2010-04-27
> **dino99 said:**
> got new plymouth releases few minutes ago
Has it improved anything noticeably?

I get about 3 seconds of splash and the rest of it is black screen.
Yet on PCLinuxOS and Fedora it worked perfectly from grub to login.

---

### Post by elkikin on 2010-04-27
> **x-shaney-x said:**
> Has it improved anything noticeably?

I get about 3 seconds of splash and the rest of it is black screen.
Yet on PCLinuxOS and Fedora it worked perfectly from grub to login.

No improvements here with NVIDIA proprietary drivers.

The workaround posted above is still the only way for me.

---

### Post by rliegh on 2010-04-27
> **sgleo87 said:**
> Found a solution that works for me. Here is my /etc/default/grub (I marked the changes in bold)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050[/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Note: Don't forget to change "1680x1050" to your native resolution ;)I'm using the proprietary nvidia drivers and your instructions FINALLY gave me a decent-looking splash screen -**Thank you**! :guitar:

---

### Post by ancleessen4 on 2010-04-27
Now we are at T-2 days to final...
Should I implement this fix or wait:confused:

---

### Post by x-shaney-x on 2010-04-27
> **ancleessen4 said:**
> Now we are at T-2 days to final...
Should I implement this fix or wait:confused:
Well it's pretty easy to reverse, you can simply comment out the lines before you upgrade to final.

I have been using this method a while (=keep didn't work for me) but unfortunately my card doesn't apparently allow widescreen modes on boot so I have a slightly stretched logo but better than the alternative.

---

### Post by ancleessen4 on 2010-04-27
Gave the fix a try-but no change-logo still looks like one or two res levels down on 1680x1050...:(

---

### Post by x-shaney-x on 2010-04-27
You may have the same problem as me in that your desktop resolution isn't available on boot.
Probably getting 1600x1200 or 1280x1024

---

### Post by Sennaista on 2010-04-27
> **elkikin said:**
> There seems to be a workaround:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

I'm tempted to try it...

This works for me but adds around 6s to my boot time. Not sure if it's really worth it.

---

### Post by cariboo on 2010-05-01
A bump for the move.

---

### Post by mattlopezdias on 2010-05-01
The following fixed my low res boot issue with Lucid 10.04 running on a laptop with nvidia graphics card

edit the grub by typing this in a terminal:
sudo gedit /etc/default/grub

add the lines:
GRUB_GFXMODE=1280x800
GRUB_GFXPAYLOAD_LINUX=1280x800
GRUB_VIDEO_BACKEND=vbe

(change the resolution to match your screen)

then:
sudo update-grub

reboot and bob might be your uncle

---

### Post by AkumA on 2010-05-06
> **sgleo87 said:**
> Found a solution that works for me. Here is my /etc/default/grub (I marked the changes in bold)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050[/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Note: Don't forget to change "1680x1050" to your native resolution ;)



Works for me too!
Nvidia GeForce 7900GS
Latest Nvidia driver (nvidia-current, 195.something)
Ubuntu 10.04 32 bits


Thx a lot!

---

### Post by unimatrix on 2010-05-08
> **sgleo87 said:**
> Found a solution that works for me. Here is my /etc/default/grub (I marked the changes in bold)
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[B]GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050[/B]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Note: Don't forget to change "1680x1050" to your native resolution ;)

This doesn't work. It fixes the grub boot menu resolution, but the splash screen is still in crappy 640x480 or some similarly ugly resolution.

EDIT:
It works at 1600x1200. Apparently only some resolutions are supported, while everything else falls back to the ugly one.
To find out what resolutions are supported type ```
hwinfo --framebuffer
```

However even with this "working" resolution the graphic now appears to be corrupted.

---

### Post by jithinkr on 2010-05-08
Fresh install of Lucid had proper boot splash, but after installing nvidia drivers, it becomes low resolution.

I tried the steps listed in this link and it worked for me!
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by sqr47 on 2010-05-22
so, do any of these methods work with *ATI*? It seems that most of them are made for people with nvidia drivers :(

---

### Post by Bobhuber on 2010-05-22
> **sqr47 said:**
> so, do any of these methods work with *ATI*? It seems that most of them are made for people with nvidia drivers :(
Yes the Tux's solution posted above works for ATI as well as Nvidia
Just make sure you use a resolution supported by your monitor.
If in doubt use 1024X768 . It gives a nice splash screen.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by jbakuwel on 2010-06-03
Hi,

My problem might have similarities with the problems discussed here; I've trying to get this fixed for a while but don't know what else to try.

I have Ubuntu 8.04, 8.10 and Windows 7 running natively on a Dell D820 laptop with 945GM chipset. I also have Ubuntu 8.04 running as guest in Virtualbox on the Windows 7 host using raw partitions (ie. the same as when I would run Ubuntu 8.04 natively). This is all working well.

Now I'm trying to do the same thing with the latest Ubuntu 10.04. It works just fine when running natively but hangs during the boot process (I see grub, can select the kernel, see some disc activity then silence) when running as guest in Virtualbox (on Windows 7).

I've added a few more grub entries so I can pass different parameters to the kernel depending on whether I run Ubuntu 10.04 natively or as a guest in Virtualbox on the Windows 7 host.

I haven't been able to get past the point where the cursor either stops blinking in the left top of the screen or disappears altogether, then sits there (forever presumably; haven't tried to wait forever :-) ).

Below my grub entries and an extract from the Virtualbox logs (for both 8.04 which works and 10.04 which doesn't). As you can see Virtualbox gets stuck in attempting to resize the Display?

The 2nd additonal grub entry lists the kernel and initrd from a guest Ubuntu 10.04 installation I did within VirtualBox using a fresh virutal disc (ie not the existing raw partitions. This install works just fine (of course), but its kernel and initrd can't get Ubuntu 10.04 booted from the raw partitions.

Any ideas out there how I could continue to debug this?

Jan


Additional grub entries:

menuentry 'Windows7: Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set <hidden>
#       linux   /vmlinuz-2.6.32-21-generic root=UUID=<hidden> ro quiet nosplash
        linux   /vmlinuz-2.6.32-21-generic root=/dev/sda8 ro quiet video=uvesafb:mode_option=1600x1200,mtrr=3,scroll=ywrap
        initrd  /initrd.img-2.6.32-21-generic
}
 
menuentry 'Windows7: Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set <hidden>
        linux   /vm/vmlinuz-2.6.32-21-generic root=UUID=<hidden> ro
        initrd  /vm/initrd.img-2.6.32-21-generic
}


Few extracts from the vbox.log files:

Ubuntu 8.04 LTS (this works just fine):

00:00:01.803 Guest Log: BIOS: VirtualBox 3.2.0   
00:00:01.803 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:01.901 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.901 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:01.902 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:01.902 ATA: Ctl: finished processing RESET
00:00:01.903 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:01.903 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:01.905 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:04.395 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:04.407 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:04.409 Guest Log: BIOS: Booting from Hard Disk...
00:00:04.414 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.415 ATA: Ctl: finished processing RESET
00:00:04.729 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:04.729 ATA: Ctl: finished processing RESET
00:00:04.732 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:04.733 Guest Log: BIOS: int13_harddisk: function 08, unmapped device for ELDL=81
00:00:08.378 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:08.378 ATA: Ctl: finished processing RESET
00:00:08.382 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:08.383 Guest Log: BIOS: int13_harddisk: function 08, unmapped device for ELDL=81
00:00:14.139 Guest Log: BIOS: KBD: unsupported int 16h function 03
00:00:14.238 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:14.238 Guest Log: BIOS: int13_harddisk: function 02, unmapped device for ELDL=81

Ubuntu 10.04 LTS (this doesn't work):

00:00:03.089 Guest Log: BIOS: VirtualBox 3.2.0
00:00:03.089 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:03.193 PIIX3 ATA: Ctl#1: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.193 PIIX3 ATA: Ctl#1: finished processing RESET
00:00:03.194 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x00 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:03.194 ATA: Ctl: finished processing RESET
00:00:03.195 Guest Log: BIOS: ata2-0: PCHS=16383/16/63 LCHS=1024/255/63
00:00:03.195 PIT: mode=2 count=0x48d3 (18643) - 64.00 Hz (ch=0)
00:00:03.204 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:05.691 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:00:05.696 PIT: mode=2 count=0x10000 (65536) - 18.20 Hz (ch=0)
00:00:05.697 Guest Log: BIOS: Booting from Hard Disk...
00:00:05.700 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:05.700 ATA: Ctl: finished processing RESET
00:00:06.067 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:06.067 ATA: Ctl: finished processing RESET
00:00:06.070 Guest Log: BIOS: int13_harddisk: function 41, unmapped device for ELDL=81
00:00:06.071 Guest Log: BIOS: int13_harddisk: function 08, unmapped device for ELDL=81
00:00:09.823 ATA: Ctl: RESET, DevSel=0 AIOIf=0 CmdIf0=0x20 (-1 usec ago) CmdIf1=0x00 (-1 usec ago)
00:00:09.824 ATA: Ctl: finished processing RESET
00:00:14.836 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:15.156 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:16.163 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:17.168 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:18.158 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:19.158 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:20.168 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:21.158 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:22.153 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:23.158 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:24.169 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=1024c000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:25.170 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=10120000 w=640 h=480 bpp=32 cbLine=0xA00
00:00:33.289 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00000000 w=720 h=400 bpp=0 cbLine=0x0
00:02:03.083 Changing the VM state from 'RUNNING' to 'SUSPENDING'.  
00:02:03.111 Changing the VM state from 'SUSPENDING' to 'SUSPENDED'.

---

### Post by sqr47 on 2010-06-16
Hmm it appears that the boot screen isn't appearing at all anymore, just a weird purple screen that lasts for a couple seconds. And when I log in the screen goes brown temporarily, though that is not really related... Anyone have any fixes for either of these?

---

### Post by konqueror7 on 2010-07-25
> **sqr47 said:**
> so, do any of these methods work with *ATI*? It seems that most of them are made for people with nvidia drivers :(

i have also an ati, but sadly my boot resolution is only up to 1024×768...i will test when i come home with the payload* option if it works

---

### Post by gonkyouka on 2010-08-11
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/) 

works for me but my native monitor resolution is not supported which is 1920x1080 so I used 1280x1024 instead looks decent but not perfect. Now, how can I make my resolution supported? Perhaps, an upgrade to my nvidia card?

---

### Post by buddha001 on 2010-10-19
[http://idyllictux.wordpress.com/2010...ricted-driver/](http://idyllictux.wordpress.com/2010...ricted-driver/) 

^^ Has anyone had problems resuming from hibernate with that solution? That worked for me in getting a high-resolution splash screen, but then I couldn't resume from hibernate. Is there a solution that might give me the nice resolution on the splash AND resume from hibernate properly?

---

