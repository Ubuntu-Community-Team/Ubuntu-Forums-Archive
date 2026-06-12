---
title: "Blank boot screen and consoles"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by LukeKendall on 2010-05-27
I have got myself into a situation where I see nothing during boot until X starts, and I have no text virtual consoles.

I recently replaced my old 9.10 system running on hardware that seemed to be breaking down, with a new system with both an onboard graphics chip (which I disabled in the BIOS as the 1st step), and an Nvidia GeForce 8400 GS card.

I installed Windows XP then Ubuntu 9.10, copied all my files across, modified /etc/fstab, /etc/hosts, etc etc., and as the last step I unplugged the 1920x1440 IBM CRT that I'd used during the install and tweaking, and plugged the display into the BenQ LCD on a Belkin 4-port KVM.  Oh, I also installed Windows and Splashtop (that mini-Linux that fast boots from the Windows NTFS partition).

I had a problem at that point: I had a lot of trouble getting any signal on the LCD monitor, and eventually got it working but with the whole display half-shifted off the screen (everything was shifted to the right about six inches), and the Ubuntu splash during boot (the sort of spotlight effect with the glowing horizontal line with the light animating along it left and right) was shrunk and only occupied part of the screen.

Nor could X detect what kind of monitor it was.  I had a lot of problem with a lot of attempts prodding the LCD monitor to complain "Out of range!" (over the top of the Ubuntu three linked circles).

I couldn't fix the problem, and in the end installed the Nvidia proprietary driver and ran its X configurator, and suddenly everything snapped back and began working correctly: X ran happily in 1680x1050, filling the screen properly, and X could now correctly detect the monitor as a BenQ.

However, now when I reboot I see **nothing**: no BIOS info, no BIOS boot stuff, no Splashtop info, nothing.  I have to blindly hit Enter to get past the Splashtop boot (since luckily it defaults to positioning the mouse over the Exit Splashtop option), then wait, and hit Enter again when grub has loaded.  After about a minute, X is loaded and I'm presented with an hourglass cursor then the gdm login screen and everything is basically good.

But this is obviously an extremely precarious situation, since any error I make in the grub config, or any hardware problem, will make the machine unbootable because it will be undiagnosable!  Nor can I make any BIOS setting changes.

I also noticed that even when X is running, all the virtual text consoles are blank.  If I switch to them, the monitor splashes up a "No Signal Detected!" message.  However,I can login blind, and start X on a 2nd display (e.g. startx -- :1) and that works.

If I hit Del during boot repeatedly, I still see nothing from the BIOS, and have to carefully boot up blind as best I can.

When I plug in the CRT directly via the DVI connector on the Nvidia card, I also see nothing during boot (on either monitor).

If I plug in the PC directly to the CRT monitor via the VGA connector, I still see nothing.

I've changed the /etc/usplash.conf file to set the splash resolution to 1024x768 (it had been 1920x1440) and re-ran update-initramfs.  But even that made no difference when I rebooted.

I've removed "splash" from the default boot options.

I added vga=0x317 to the default linux kernel, and it made no difference (0x317 = 791 decimal).

```

title           Ubuntu 9.10, kernel 2.6.31-21-generic-pae
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.31-21-generic-pae root=/dev/sda6 quiet vga=0x317
initrd          /boot/initrd.img-2.6.31-21-generic-pae

```

I also edited /etc/modprobe.d/nvidia-kernel-nkc.conf and appended the option: NVreg_UseVBios=0
which changed things (after another blind reboot) so that from:
```
grep -i usevbios /proc/driver/nvidia/registry
```
I now get:
```
UseVBios: 0
```
instead of
```
UseVBios: 1
```

I still have blank virtual consoles, and blank during boot.

As you may guess, I'm stumped.  Can anyone help?

Do you think it might help to boot up Windows again?  Or boot again from the LiveCD?  Might that somehow snap things back to sanity?

As you can imagine, I have to be very careful about any grub modifications, and I'm trying to keep reboots to a minimum.

What does a line length of 2048 in this mean - is that a clue?
```

$ dmesg | grep vesafb
[    3.438213] vesafb: framebuffer at 0xfb000000, mapped to 0xf8380000, using 3072k, total 14336k
[    3.438216] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    3.438218] vesafb: protected mode interface info at c000:c6b0
[    3.438220] vesafb: pmi: set display start = c00cc713, set palette = c00cc76e
[    3.438221] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    3.438230] vesafb: scrolling: redraw
[    3.438232] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
```

luke

PS:

```
# dpkg -l | grep nvidia
ii  nvidia-185-kernel-source                   185.18.36-0ubuntu9                                         NVIDIA binary kernel module source
ii  nvidia-185-libvdpau                        185.18.36-0ubuntu9                                         Video Decode and Presentation API for Unix
ii  nvidia-185-modaliases                      185.18.36-0ubuntu9                                         Modaliases for the NVIDIA binary X.Org driver
rc  nvidia-common                              0.2.15.1                                                   Find obsolete NVIDIA drivers
rc  nvidia-glx                                 1:96.43.05+2.6.24.14-22.53                                 NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-173                             173.14.20-0ubuntu5                                         NVIDIA binary Xorg driver
ii  nvidia-glx-185                             185.18.36-0ubuntu9                                         NVIDIA binary Xorg driver
rc  nvidia-kernel-common                       20080825+1ubuntu2                                          NVIDIA binary kernel module common files
ii  nvidia-settings                            180.25-0ubuntu1                                            Tool of configuring the NVIDIA graphics driver
# lsmod | grep nvidia
nvidia               9587272  36 
agpgart                35020  1 nvidia
```

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

dont know what you are calling BIOS

---

### Post by LukeKendall on 2010-05-28
> **dino99 said:**
> mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

dont know what you are calling BIOS

If you don't know what I mean by BIOS, I'm not sure how to explain it.  It's the text that's displayed when the PC is powered on, before the boot loader starts.  There will always be an option to hold down a key (like Del, or F2), to enter the BIOS setup utility.  That's what I mean.

And thanks for the mini howto, but that seems to be about installing a system.  I've already done that, and everything is working fine, except that I can never see BIOS/Splashtop/grub text, nor text consoles.  Something seems to be telling the PC that such stuff is to be displayed in a mode that neither of my monitors can support.  Or else the nvidia card has failed in some strange mode and is no longer capable of generating low-res basic text output (seems unlikely).

luke

---

### Post by LukeKendall on 2010-05-29
Well, things are much worse now, after I almost felt I'd solved it.
I've gone from an almost working system to one where I can't see a single pixel output at any time, and can't boot the system up.



I read the motherboard booklet and followed the basic procedure to reset the bios to factory defaults (power down, change a jumper setting for 10 secs, change it back, power up).  That didn't work.

The manual said if that didn't work, first take out the CMOS battery and do the same again.  I did that, and hey presto, I can see text on power on, can go into the BIOS, etc!  Yippee!  So I set the system time again, disable the motherboard graphics card, set the 1st boot device to the CDROM, and boot up.

All is looking well!  I can now see text from grub while it boots the kernel.  Interestingly, the text is smaller than it was during first install, which I take to mean the kernel is using the vga=719 option appended.  Ubuntu and then X starts up just fine.

I can even flip to other virtual consoles and see text there.

At this point I ran the nvidia xserver config tool, and used it to look at the configuration.  It detected the BenQ LCD and the IBM CRT, but it thought the BenQ was a CRT and was running it at 59.15Hz, and it detected the IBM CRT as a DFP, and was running it at 1680x1050.

So I copied bits out of an older working config for the two screens, and manually tried to fix it up.  Then I logged out to try out the new config, and when I got the Ubuntu "spotlight" splash screen, the machine locked up.  I had to power off and reboot.

It started up, but said the X config was wrong, and so I started up in low graphics mode.  I fixed up the errors, and then ran up a 2nd X session from a virtual console (you know, 'startx -- :1' sort of thing).

X started, and looked roughly okay, but the BenQ LCD put up a panel saying "Out of range" and the mouse wasn't working.  So I flipped back to the virtual console, killed X, and deleted the default high-res modes for the IBM monitor, reducing it to 1680x1050, on the assumption that if X was confused and using the IBM CRT settings to drive the BenQ, it should still work.  (Though I didn't think to change the Horiz and Vert frequency ranges...).

So I started up another X session from the virtual console, and this time the BenQ didn't complain, and the windows were properly sized for the screen.  But still no mouse.  I then switched back to the virtual console, and that's when things went bad.

There was no text, just chunky blocks of colour at places where you might expect to see text characters.  So I did a Ctrl-Alt-Del to reboot, and the blocks of colour changed, as you'd expect if they were a representation of the shutdown messages.

But when the system restarted, I was back to no text of any sort on the screen during power on.  Nor could I see the BIOS output, let alone get as far as grub.  And I suspect it's displaying some BIOS message, but without knowing what it is, I can't get past it to try to boot Linux or boot from CDROM or anything else.

So that's the situation I'm now in.

Oh, I just tried a 3rd time to reset the BIOS.  No difference.

(Though this time, just for added humour value, when I popped the CMOS battery out, it fell down into the innards.  After peering everywhere with a torch, I could just see one edge of thet battery where it had slid into the narrowest portion of the power supply, which is at the bottom of the case, and with conveniently wide grills above the fan, to allow small metal objects to drop inside unimpeded.  So for the next 5 minutes I'm turning the PC upside down and at various angles to try to get the battery out, like it's a jumbo puzzle.  But it came out without too much trouble.)

At this stage, I think I'm going to have to return it to the manufacturer and see what they can do.  I suspect the graphics card has failed.  But then I can't see anything from the motherboard inbuilt graphics controller either.

Pretty sad.

Any thoughts or advice are welcome.

luke

---

### Post by LukeKendall on 2010-11-27
I hadn't updated this thread with a description of what happened next, because although things got working again, I really don't understand how or why.

I sent the PC back to the manufacturer, they tested it and said they could find no problem of any kind - it worked fine for them, charged me for it and sent it back.  They said they thought I had two failed monitors.

By this stage I was getting desperate so I bought a new LCD monitor and plugged the returned PC back into that and it worked fine.  It also worked fine with the old LCD monitor plugged in via the KVM switch.  So basically, with the new display it all seemed to be fine, no problems.  Normal power-on display, normal boot loader display, normal boot sequence, normal X.  Could flip to text consoles and back to X no problem.

But I'm worried now again.  Today I flipped the KVM switch over to my Mac mini and used that for a while.  I adjusted the resolution on the Mac to match the (old) LCD monitor resolution better.  While doing this I selected 1600x1200 which the display said it couldn't handle ("Out of range" plastered over the top of the desktop).  So I went down to 1600x1000, which was fine (though the monitor did it's scary "auto-adjust" dance again).

Then I selected 1600x1080 which seemed better, and left it at that.  I shut down the Mac and flipped back to the main PC and the mouse was playing up (x&y tracking was fine, but random mouse down events seemed to be being generated).

I flipped to a text console, but when I flipped back to X, it looked like the X session had just died - the Ubuntu X splash screen was being displayed on the way to the GDM login window.  So I logged in, and things basically worked, but the mouse was still generated random left click events.  I tried flipping to the text console, and this time I got nothing on both LDC display (the new and the old).  The new display just displayed black (it's plugged in directly to the PC via the DVI cable), and the old LCD (plugged in via VGA to the Belkin KVM) was now displaying chunky green rectangles on a black background.

So it looks like it's gone back into the bad mode, and when I next try to reboot I may be stuffed.

I notice that some of the behaviours described in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623) "Black screen after boot, no text console possible" seem very similar to my situation.  But I'm running kernel 2.6.31-22-generic-pae and the problem seemed to be related to mouse craziness after the KVM switch, and switching into and out of graphics and text mode.

I just thought I'd post this update.

---

### Post by LukeKendall on 2010-11-27
I tried powering the KVM off and on again, BTW.  Apart from disabling the mouse so I had to unplug and replug it, and made no difference.

---

### Post by LukeKendall on 2010-11-27
Long story short: after a reboot, everything is working again just as it should.

---

