---
title: "Ubuntu 9.10 - nvidia driver 185 - black screen on startup"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by stefano.bolli on 2009-12-08
Yesterday I installed ubuntu 9.10 on a pc with nvidia graphics card mod. Geforce 6200. Enabling recommended restricted nvidia driver v. 185 caused black screen of death on startup because of an acpi error (cat /var/log/Xorg.O.log). I solved my problem in this way:

1) Install driver via Hardware Driver and do not reboot.
2) run a terminal and type: *sudo nvidia-xconfig --nvagp=1*
to create /etc/X11/xorg.conf with nvidia's agp enabled. You don't need to reboot.
3) type in the terminal: *sudo /etc/init.d/gdm stop*
4) log in and type *sudo gdm stop*
5) your pc now should use nvidia driver

I hope to be helpful.

Bye

---

### Post by gamerteck on 2009-12-12
This worked...followed your directions perfectly except I used the 1.90 drivers in the hardware manager!!!

I have been trying to get my Nvidia 6200 to work for a week on my Samsung 46' HDTV and nothing on these forums or Google could help until now. 
It's unbelievable that one simple option, "--nvagp=1", would solve my problem.

My Issue specifically, for search purposes, was that after the Ubuntu splash screen was displayed I would get the blinking input cursor, on the upper left hand side, and after about 5 seconds the cursor would disappear. My TV display would then go blank and would show "No Signal". I couldn't even get into TTY because the mouse and keyboard didn't function. I've attached what my xorg loks like after running "nvidia-xconfig --nvagp=1"

I can't express my gratitude enough.
Thanks again stefano.bolli. You seriously :guitar: out loud!

---

### Post by Perturbed Penguin on 2009-12-23
How did you do all of this if it is freezing on you at boot? I seem to be having the same issue but I have no idea how you were able to do this, would you mind giving me some suggestions? Thanks!

---

### Post by Perturbed Penguin on 2009-12-24
Looks like it may, possibly be a shot graphics card for me actually so never mind, but thanks for the post.

---

### Post by paperdiesel on 2009-12-24
> **stefano.bolli said:**
> Yesterday I installed ubuntu 9.10 on a pc with nvidia graphics card mod. Geforce 6200. Enabling recommended restricted nvidia driver v. 185 caused black screen of death on startup because of an acpi error (cat /var/log/Xorg.O.log). I solved my problem in this way:

1) Install driver via Hardware Driver and do not reboot.
2) run a terminal and type: *sudo nvidia-xconfig --nvagp=1*
to create /etc/X11/xorg.conf with nvidia's agp enabled. You don't need to reboot.
3) type in the terminal: *sudo /etc/init.d/gdm stop*
4) log in and type *sudo gdm stop*
5) your pc now should use nvidia driver

I hope to be helpful.

Bye

Stefano,

I just wanted to say thank you and let people know that your solution worked perfectly for me as well.  I was pulling my hair out trying to figure out why my AGP GeForce 6200 was causing Ubuntu to freeze after log-in.  I installed the latest hardware drivers, typed ```
sudo nvidia-xconfig --nvagp=1
``` and rebooted.  Everything's running great!

Thanks man!

---

### Post by dtkerns on 2009-12-27
This seems to be my exact problem, but like the previous poster, I am unable to access the machine to enter the command. GRUB never gives me any opportunity to edit the boot. ctrl-alt-f1 does nothing. remote login (ssh) is denied.

---

### Post by ngtybear on 2009-12-27
I am having the same issue with 190.53 on a 7900 GS. 

Sad things is, I did not have this issue with earlier versions of the driver. I could simply tell it to use "HD1080i" and it would work. I upgraded the driver for VDPAU support as I am now attempting to do HD.

---

### Post by stefano.bolli on 2009-12-28
> **dtkerns said:**
> This seems to be my exact problem, but like the previous poster, I am unable to access the machine to enter the command. GRUB never gives me any opportunity to edit the boot. ctrl-alt-f1 does nothing. remote login (ssh) is denied.

Hello!

You should select recovery mode in grub boot loader.
In this way you can prevent loading of your graphics system.
Log in with your username and password and then type
1)*cd /etc/X11/*
2)*ls* 
to check if xorg.conf exists (karmik doesn't create it during
setup). if it doesn't exists, run this command:
*sudo nvidia-xconfig* to create a basic xorg.conf
3)now you have to modify it with nano. Type:
*nano xorg.conf*
4)Find this line:
*Driver         "nvidia"*
and replace it with
*Driver         "nv"*
In this way Karmik will use its own driver and not the third party one.
Restart your graphics system (sudo gdm start) and try to follow the steps in my first article.

Regards and
Happy new year! :)

---

### Post by Perturbed Penguin on 2009-12-30
Hmmm... now that is very interesting ngtybear. I also was having this issue and I also was using a 7900GS - I have already ordered a new card because I was convinced it was a hardware issue but that just seems odd that we have the same exact card.

---

### Post by dtkerns on 2009-12-31
thanks for the additional info, but as I said, I'm never given an opportunity to interrupt the boot. (It's a new install so only one kernel present) I could have reinstalled again but my thumb drive got swiped (long story).
My motherboard has both an AGP and a PCI-E slot, once it clicked that this was an AGP issue (some times it's the obvious things that are hardest to see) I stuck in a PCI-E video card I had and world peace was achieved! ;)

---

### Post by dj_flx on 2010-01-09
Fail. :(

WARNING: Unable to find users: no seat-id found

?

AND a complete wipe and fresh install then update later... OK, worked this time!

I got this:

```
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default
Screen".
```

when doing the nvidia-xconfig step but I guess it wasn't a problem.

---

### Post by FrankVdb on 2010-01-17
Same black screen problem here on a Dell XPS M1330 laptop with an nVidia card.

Driver version 185 worked without any issue for about one and a half months. Last week I got the black screen and now I'm back on the default Karmic driver. Version 173 gives me the black screen too...

---

### Post by theham on 2010-01-18
@FrankVdb check out this thread which might relate to your problem (i think i'm experiencing the same) [http://ubuntuforums.org/showthread.php?t=1375950]("http://ubuntuforums.org/showthread.php?t=1375950").

bug listing that i've subscribed to that may also be related to your problem [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/507979]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/507979")

---

### Post by Stubbs3 on 2010-01-21
Help! I think I may have a related issue.
 
Im new to Ubuntu and to typing command strings.
 
I wanted to try this operating system out instead of windows and learn a new thing or two 
 
I have a issue with Ubuntu, i believe its with the video drivers and ive been trying to correct since install.
 
I have Ubuntu 9.01 and a nvidia geforce 8600gt. I reciently installed nvidia restricted driver 185. Upon reboot I recieved only a black screen after loading Ubuntu through Grub.
 
Ive tried a couple of commands and not knowing what i am doing may have done more harm than helped
 
When I open the xorg.conf file using "nano xorg.conf" there is nothing in it!
 
What should I do now!
 
Any suggestions will be appreciated

---

### Post by alphasoup on 2010-03-15
The thread is marked SOLVED, but I am not sure where the solution is.
Does Ctrl-Alt-F1 give a terminal? e.g. to remove the 185 driver.
Was this solved by replacing the card by another one?

It sounds like the card worked before adding the 185 driver, so a workaround could have been to un-install the nvidia driver, the card may then have started to work (again) with the default xorg nv driver...

---

### Post by javierespada on 2010-03-28
For me the solution was lspci
sudo lspci | grep vga

it showed my adapter then i opened xorg.conf with nano and under
the device section added a line

busid      "pci:05:00:00"

thats what lspci showed for my card and problem solved

i am a newbie but i like reading forums!

---

### Post by rigobot on 2010-04-30
I have to resume this thread, i think that neither the new arrived Ubuntu 10.04 have solved the problem...
After a new fresh installation all worked with the vesa driver; I installed the Nvidia 185 driver thinking that the problem wad solved time ago...:(...i was wrong!
I rebooted the machine and...black screen with the led of the monitor blinking.
I remembered that the 173 driver worked fine so i purged the previous (185) driver and installed the 173 one.
Now everything work...
I investigated a bit and found this difference in the /var/log/Xorg.0.log:

boot of nvidia-glx-173:

[...]
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.41.00.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GT at PCI:1:0:0:
(--) NVIDIA(0):     **Samsung SyncMaster (DFP-1)**
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): **Assigned Display Device: DFP-1 **
[...]

boot of nvidia-glx-185:
[...]
(II) Apr 30 15:49:18 NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:1:0:0 (GPU-0)
(--) Apr 30 15:49:18 NVIDIA(0): Memory: 524288 kBytes
(--) Apr 30 15:49:18 NVIDIA(0): VideoBIOS: 60.84.41.00.00
(II) Apr 30 15:49:18 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Apr 30 15:49:18 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 30 15:49:18 NVIDIA(0): Connected display device(s) on GeForce 8600 GT at PCI:1:0:0:
(--) Apr 30 15:49:18 NVIDIA(0):     **Samsung SyncMaster (CRT-1)**
(--) Apr 30 15:49:18 NVIDIA(0): **Samsung SyncMaster (CRT-1)**: 400.0 MHz maximum pixel clock
(II) Apr 30 15:49:18 NVIDIA(0): Assigned Display Device: CRT-1
(==) Apr 30 15:49:18 NVIDIA(0): 
(==) Apr 30 15:49:18 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Apr 30 15:49:18 NVIDIA(0):     will be used as the requested mode.
(==) Apr 30 15:49:18 NVIDIA(0): 
(II) Apr 30 15:49:18 NVIDIA(0): Validated modes:
(II) Apr 30 15:49:18 NVIDIA(0):     "nvidia-auto-select"
(II) Apr 30 15:49:18 NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) Apr 30 15:49:18 NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) Apr 30 15:49:18 NVIDIA(0):     option
(==) Apr 30 15:49:18 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[...]

I have a GeForce 8600GT connected to a Samsung TFT monitor via DVI cable...

I noticed another thing...
The installation of the nvidia 173 led to a reconfigure and "creation" of the kernel module, the 185 didn't.

So...is there any chance to install these driver???

thank you for any advices!

---

