---
title: "Menu bar disappears after first reboot"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by hondaman900 on 2010-09-21
I have reinstalled 10.04 several times and have the same result. After the install everything works and looks great. Then after the first power down and reboot the top menu bar and bottom panel are gone.

The desktop wallpaper (bare of anything) is there, still responds to right-clicks, etc, and the system seems to function, but the menu bar is missing. The extents of the desktop are still the same, so it's not the desktop extending outside of the screen display area (mouse doesn't disappear over the edge). 

I can alt-F1 to get to the menu bar menu items, and they function - appearing from the top edge of the screen, but cannot activate them via mouse. I have reinstalled several times and this consistently happens every time. I had 8.10 on this box and it didn't do this. I reinstalled 8.10 and it was fine again, and then back to this with reinstalled 10.04. The 8.10 was a virgin install and I reformatted the drive on every install so there's no legacy crap clinging on. 

I can use ctrl-alt-del to shut down/restart/etc., and alt-F2 gets me the command line. All seemingly functional.

Any ideas?


EDIT
In case someone googles the thread, this might help:
[http://ubuntuforums.org/showpost.php?p=12292664&postcount=828](http://ubuntuforums.org/showpost.php?p=12292664&postcount=828)

---

### Post by w9fcc on 2010-09-21
I just developed a similar problem. Everything was fine, then there were some updates tonight. Now when it boots, the top and bottom bars are gone, but only for a minute or so. Then they appear and everything is ok.
What the heck did they do!!??

---

### Post by hondaman900 on 2010-09-22
Mine are totally gone. I've left it on for a day and they don't appear.
 
I should mention that this is running on a Dell Optiplex GX150, 1GHz PIII with 512Mb. 
On boot up it displays the messages:
 
error: no suitable mode found
error: unknown command "terminal"
 
Any ideas?

---

### Post by w9fcc on 2010-09-22
> **hondaman900 said:**
> Mine are totally gone. I've left it on for a day and they don't appear.
 
I should mention that this is running on a Dell Optiplex GX150, 1GHz PIII with 512Mb. 
On boot up it displays the messages:
 
error: no suitable mode found
error: unknown command "terminal"
 
Any ideas?

I had the same error message after rebooting after
the upgrade. I rebooted again and that went away,
but the top and bottom panels are still delayed in
displaying about 30 seconds. 
Emachnes 3 gig machine with 3 gig of RAM.

---

### Post by hondaman900 on 2010-10-15
<bump>
 
Any ideas anyone?

---

### Post by aeronutt on 2010-10-15
Help! I have the exact same problem. During boot of a clean install of 10.04, the following comes up on a black screen:

error: no suitable mode found
error: unknown command "terminal"

And then, the desktop background appears but no panels. FYI, I do get the right-mouse-click menu.

Quick help would be much appreciated...this is my Mom's computer that I'm upgrading to LTS, and I'm only visiting for 2 days. I convinced her to change from Windows last year...and now she has no computer!!

UPDATE:

It boots fine from live CD, all menus appear and everything seems ok.
Here's some more info:

lspci

```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory 
Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics 
Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
01:09.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
```

cat /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

sudo fdisk -l

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009925e

  Device Boot      Start        End      Blocks  Id  System
/dev/sda1  *          1      14762  118571008  83  Linux
/dev/sda2          14762      14947    1486849    5  Extended
/dev/sda5          14762      14947    1486848  82  Linux swap / Solaris
```

---

### Post by aeronutt on 2010-10-15
Update:  From reading another thread, I just tried editing the grub file, by changing 
     #GRUB_TERMINAL=console
to
     GRUB_TERMINAL=console

However, when I ran sudo-update grub, I got:
    /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I'm trying this from the liveCD. Is that a problem?

---

### Post by aeronutt on 2010-10-15
Hondaman900, I hope I'm not viewed as thread-jacking your original problem. I was hoping together we could get the answer to our question, with the assumption we have the same problem. My apologies if I've highjacked your thread.  

Here's an update.

- Using alt-F2, I ran update-manager, and installed all updates. No change.

- Then, in a terminal, I changed the following in grub, and ran update-grub.
      #GRUB_TERMINAL=console
      to
      GRUB_TERMINAL=console
After this change, I no longer get these 2 errors at boot up:
      error: no suitable mode found
      error: unknown command "terminal"

- Then, I noticed that if I maximize a terminal screen, it goes full-size as if the panels are there! That is, there's a gap at the top and bottom of the screen exactly where the panels should be. So I ran the following commands as if to reset the gnome panels:

```
gconftool –-recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
and the panels appeared!!

But after rebooting, they disappear again. 

Ideas??

---

### Post by hondaman900 on 2010-10-16
Actually resolved it this evening after an intense deep-dive into this with my buddy Mr. Google.
 
Here's what worked for me (though the guy on the post where I found it didn't find this successful for him):
 
In terminal (use Alt + F1 and arrow keys to get menus) use the following command lines to remove compiz
 
```

sudo apt-get remove compiz
sudo apt-get remove compiz-core
```
 
Then when you're done, exit Terminal and reboot. My OptiPlex GX150 has been booting and restarting just fine since. I still get the errors on startup but they don't seem to matter now.
 
I also updated the Intel i815 graphics chipset drivers as per instructions here:
 
wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes
 
That made the whole interface/UI much faster and slicker.
 
I believe compiz provides the graphical special effects (like fades and drop shadows) and that if you turn on that option again it will reinstall compiz and the issue will return. Mine is working great and I don't miss those bells adn whistles.
 
Hope this helps, and best of luck.

---

### Post by Richard-S on 2010-10-18
I have the same problem with both 10.4 and 10.10 in a Dell Optiplex 150 box. I did the ***sudo apt-get remove compiz*** on the 10.10 install, and now the top and bottom bars load fine, but now it won't shut down. Any way I try shutting down ,including ***sudo halt***, freezes the computer.    

In the 10.4 install, I found that if I do an Alt-F1, and then an Alt-F6 and then an Alt-F5, I get the top bar, compacted. Then an Alt-F10 re-sizes it to the full width of the screen. 

I had 7.4 Kubuntu on this machine before, and that worked fine for years. I think maybe I'll go back to that.   

Richard

---

