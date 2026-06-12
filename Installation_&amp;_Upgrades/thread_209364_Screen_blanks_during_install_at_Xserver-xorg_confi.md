---
title: "Screen blanks during install at Xserver-xorg configuration"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-05
I'm trying to install Dapper on my XP machine. I've (finally) figured out my partitioning but I'm still having a hell of a time installing Dapper. I'm running the alternate-386 cd to install. I choose the text mode install and all appears to go well. I enter all my info, and it then installs the base system. 

But then it skips right along into a procedure called 'select and install software' - mind you it didn't let me *select* anything. It gets to about 60% and the screen goes black with a couple of white rectangles. This happens right after I see 'configuring xserver-xorg' above the status bar. The hard drive continues to work sporadically for about 5-10 minutes and then all appears silent. There's nothing I can seem to do except ctrl-alt-delete twice which then reboots the machine. I'm thinking the installer is waiting for me to proceed with the next step but I can't see a thing! 

Upon rebooting I tried the rescue mode and proceed to try and install GRUB to a bootable primary linux partition. I managed to get it to allow me to install it to my /dev/sda2 partition (sda is my first disk) but it gets to 50% and just stalls. 

Anybody got any insights as to what the problem might be? How can I skip the xorg part of the install if that's what the problem is? I've heard the 386-desktop cd is glitchy. Should I be using that instead?

---

### Post by karasu on 2006-07-05
I'm struggling with the [same issue]("http://www.ubuntuforums.org/showthread.php?t=208814"), right down to the white rectangles on the black screen. 

The desktop CD didn't do anything for me.

---

### Post by karasu on 2006-07-05
Also, I've seen similar problems reported [here](http://www.ubuntuforums.org/showthread.php?t=209069) and [there](http://www.ubuntuforums.org/showthread.php?t=188950) and in other places where people insist the iso is at fault and should be burned at a lower speeed, even if the checksum is correct. 

I re-burned the image at 4x, which is as slow as the burner lets me go, but the install still dies at the very same place.

---

### Post by harro0209 on 2006-07-06
I encountered the same problem on a standard desktop PC.
Finally I ended up installing the server version of Ubuntu (which does not install xserver-xorg). After logging into the text console of the server system  I just did a
**sudo apt-get install ubuntu-desktop**
to get the GNOME desktop.

---

### Post by squidward_tentacles on 2006-07-10
I was having the IDENTICAL problem...I think the fault lies in the Xwindows refresh portion, where the screen blanks for a minute while probing video card(?)/ testing available resolutions...after undergoing all the steps/solutions tried above...(right down to redownloading/burning another install cd @ 4x, with the same results...I even went as far as changing Video cards, with the same results. This is a clean install of Dapper, I had previously installed Breezy on this same Machine, without any problems...
My solution to the "white rectangles of death" was to simply watch the hard drive for a while until no activity was taking place and then hit enter. If memory serves, at this point in the install its writing the boot loader, after that completes the CD drive should automatically eject the cd, remove the cd and hit enter again, the system should reboot on its own at that point, as instalation is complete, and it should work normally.
Wouldnt hurt to file a bug report on this either as it seems to be happening to more than a few people.
As far as installing in server mode and adding gnome-desktop enviorment, I would think that would leave the average person with a lot of un-needed/unwanted services:)

---

### Post by richardq on 2006-07-10
What I ended up doing was the following:

1. I used the 'alternate' iso to bring up the installer (not the desktop installer). 

2. I hit F4 (I think) to change the resolution to my lcd monitor's native resolution(1280x1024) and then proceeded with the install.

3. When it came to configuring xserver-xorg, the screen blanked for about 1 full sec (during which time I was expecting the white rectangles) but then it came back to the installer and continued on.

Maybe setting the native resolution before it started the install helped in making it possible for xserver-xorg to configure the video. Dunno for sure.

---

### Post by vietsb on 2006-07-16
> **richardq said:**
> What I ended up doing was the following:

1. I used the 'alternate' iso to bring up the installer (not the desktop installer). 

2. I hit F4 (I think) to change the resolution to my lcd monitor's native resolution(1280x1024) and then proceeded with the install.

3. When it came to configuring xserver-xorg, the screen blanked for about 1 full sec (during which time I was expecting the white rectangles) but then it came back to the installer and continued on.

Maybe setting the native resolution before it started the install helped in making it possible for xserver-xorg to configure the video. Dunno for sure.

I'm installing on a Dell Latitude X200 using the Alternate ISO CD and ran into this exact issue on two attempts.  60%, then it hangs for a bit on xserver-xorg, flashes some screwy graphics, then goes to 2 solid white cursors.  The install appears to proceed in the background as noted, but since I don't want to automatically install GRUB (I'm multi-booting so I used Expert Mode), I was stuck.

I took RichardQ's advice and preset my VGA display to 1024x768x32 (native for my LCD) and it proceeded past that point. :D

Thanks RichardQ! :KS

---

### Post by Choad on 2006-07-16
installing on a toshiba satellite 3000x4 and get the exact same issue (inc. 2 white rectangles)

incidentally, what graphics cards are you using? could be the common denominator here

according to lspci, i have an **Intel Corporation 82830 CGC** card, and it is using the **i810** linux driver in xorg.conf

i solved it as someone mentioned previously, by just leaving it for 15 - 20 minutes to finish up configuring it's packages, and then hitting enter at the appropriate times.

(unfortunately it has not been plain sailing configuring X with this laptop, still got issues)

i have found that if i attatch an external monitor to my laptop and then switch between the displays it can rescue it from the 2 white rectangles scenario.

not so useful for desktop users tho!

---

### Post by datagrok on 2006-07-21
I've experienced the same problem on my **ASUS S5Ne** laptop. (An otherwise awesome little laptop for Linux.)

I'm installing using the text installer because, just like in this other thread here, [the graphical installer was "insanely" slow]("http://www.ubuntuforums.org/showthread.php?t=216722").

Instead, I waited until the hard drive showed no more activity, then rebooted by switching to VT2 (ctrl+alt+f2) and blind-typing "reboot." Since I already had GRUB installed, I was able to make the newly installed Ubuntu boot by specifying the grub options by hand. (Strangely, xorg works fine even though the detection during install fails so badly.) However, many things are left unconfigured. I'm eager to re-install with the "native resolution" trick mentioned above.

Seems this problem affects a lot of us **i810** Intel graphics card users. While blind-typing in VT2, I also tried: 
[B]chroot /target
/usr/X11R6/bin/X -configure[/B]
From this, the xorg.conf.new that was left in / uses **Driver "vesa"** in Section "Device". Seems that it never made it to detection of the intel graphics chip? But /etc/X11/xorg.conf correctly uses **Driver "i810"**. I'm not sure what to make of it.

Here's output from lspci about my video card.

> sh-3.1$ **sudo lspci -v -s 0:2**
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1712
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at feb00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at dc00 [size=8]
        Capabilities: [d0] Power Management version 1

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1712
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [disabled] [size=128M]
        Memory at fea80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: [d0] Power Management version 1


---

### Post by triwave on 2006-11-21
After a lot of searching I finally found a thread that describes my problem EXACTLY! I am anxious to try these remedies at home tonight (cross my fingers).

Incidentally, my laptop is a Dell D610 with an Intel 915 video card. The video display worked perfect when running the live CD, it only fails at install for some reason. 

Is that consistent with you folks too?

---

### Post by richardq on 2006-11-21
I'm not sure about the others but I think it centres around the i810 driver. I think the 915 uses the i810 driver. So yes, I do think they are all related.

---

### Post by triwave on 2006-11-22
I followed this line of thinking and found reference to adding a command at the install which was vga=771 for troublesome laptop monitor configurations. That got me through the install! When the graphics were installing therer was a momentary blanking of the screen, at which point I held my breath, then the screen came back and things continued nicely :) 

Challenge now is to run Ubuntu with my normal screen settings - 1280 x 1024

After install with above method my resolution is limited to a max of 1024 x 768

If anybody knows a good how-to on tweaking your video performance that would be appreciated.

---

