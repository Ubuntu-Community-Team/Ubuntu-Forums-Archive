---
title: "HP TM2 convertible notebook on Lucid  // remaining issues"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dgttm on 2010-02-19
Hi,

short summary of working and (still) not working things on my TM2 (added a Intel X25 160GB SSD).

Boot time after grub -> about 12seconds for ubuntu, about 16 seconds for windows 7.


64 bit lucid - not working at all. I had problems with the disk partitioning utility, it failed to work, even with manual partitioning the installation resettet to the last screen (with username/password things). 

As I do not need 64bit with my 4GB of RAM I installed lucid 32Bit.

Installation went fine, almost all HW configured automatically.

Touchscreen:
Found a solution on the net to get the touchscreen running, even with pressure recognition, working absolutely smoothly in gimp, even better than PS CS4, but probably because it is running 100% of the time on the radeon card (in windows it is running on the GS45 on battery and switching over to the radeon 4500 on AC). 

to get it running, just download and compile the newest wacom driver. ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516777))

Webcam: working fine

Sound: working fine

SD Card reader: working fine

UMTS USB Stick (o2 Surf stick): working fine 

Bluetooth mouse (MS bluetooth notebook mouse): working fine, now sharing between windows and ubuntu without problems with help of this article:
[http://ubuntuforums.org/showthread.php?p=8842235](http://ubuntuforums.org/showthread.php?p=8842235)

Compiz cube with many details, transparency: absolutely working fine without lags or anything.



UPDATE:

things to fix manually:
- if your mouse buttons are not working, just add to (new) file /etc/modprobe.d/options:

options psmouse proto=imps


To disable the ATI Radeon 4500, follow this guide:
[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)
as far as I understood so far, both graphics cards are fully powered with X, as hybrid cards are not supported (correct me if I am wrong). with this fix (just compile a few lines of C and insmod them). after a reboot, you will just find the Intel GS45 in your /var/log/Xorg.0.log.
From that time, the fan will be off most of the time and this will help increasing battery life by a big amount of time as so far only windows is handling hybrid cards well.
compiz cube desktop still running without lags.
(attached "my" hp_acpi.ko compiled against kernel 2.6.32-13, just copy to /lib/modules/2.6.32-13-generic-pae/kernel and add the line "hp_acpi" to /etc/modules)

HDMI output: not working, just a blinking cursor when not "disabling" radeon card as described above. when ati card disabled, no output at all. still investigating. 


HD video playback: 720p no problem,  with both graphic cards working
1080p also working quite well, some frames seem to get dropped, but thats ok (best result with mplayer, vnc and totem NOT working smoothly)

Open issues:

- multitouch touchpad no gesture (is that possible?)

- fingerprint reader 

- HDMI output

- biggest issue: brightness levels not adjustable (buttons working, pop ups are shown, but no impact on brightness - found open ubuntu bug ID)

---

### Post by M42 on 2010-02-19
Thanks for the summary of what works and what doesn't.  I have a tm2 on order and thought it "should" work with Ubuntu but now I know for sure.

---

### Post by dgttm on 2010-02-21
updated first post:

- increasing battery life drastically with disabling radeon 4500
- getting touchpad buttons to work
- hdmi output (not working) and HD video performance tests


tried out the proprietary ati drivers to get HDMI output working from
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English)

but this has not been successful so far. I get this message after following this guide for installation:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

but just results in : (/var/log/Xorg.0.log)

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
dlopen: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: UpdateSpriteForScreen
(EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) UnloadModule: "fglrx"
(EE) Failed to load module "fglrx" (loader failed, 7)
(EE) No drivers available.

read something about that the current driver is incompatible with current Xorg version. will retry in next release..

update: found bugid:
[https://bugs.launchpad.net/ubuntu/+bug/525377](https://bugs.launchpad.net/ubuntu/+bug/525377)

---

### Post by cbanbury on 2010-02-22
Hi, I am also giving this a go. 

Made the mistake of installing the x64 version so downloading the 32bit now. Can you explain how you got the wacom driver working, I keep getting errors :( 

The brightness levels being fixed is really annoying. Do you think its a LED screen issue? Apparently a lot of netbooks & such like have had similar problems.

---

### Post by dgttm on 2010-02-22
hm, i just downloaded the newest one and compiled it. 

I will attach mine compiled against 2.6.32-13-generic-pae

just copy to 

/lib/modules/2.6.32-13-generic-pae/kernel/drivers/input/tablet

and add this line to /etc/modules

wacom


no i don't know. hope this will getting fixed with 2.6.33. but with the radeon disable fix (described above), i have no battery issue anymore. of course, I hope this will get fixed, but I am really fine with my installation now..

---

### Post by M42 on 2010-02-26
hello dgttm,

well my tm2 came yesterday and I'm have a difficult time getting Ubuntu installed.  I am trying a USB drive install for the first time so I may be doing something wrong there.  I have install Ubuntu on half a dozen destops or laptops without this much trouble.  I have tried the alpha2 and alpha3 32 bit versions with little success. I have the U9600, 4MB, ATI, 500 GB hard drive.  A couple of questions please.

which bios versions do you have?  I have F05.

did you use a USB drive installation?

I cannot even get Ubunut to run in the uninstalled mode if the AC power is plugged in.  It starts fine but I believe it tries to engage the ATI graphics and just goes to a completely black screen.  

the disk partitioning doesn't give me the usual options for partitioning the hard drive.  It only allows a clean sweep of the drive, i.e. deleting windows or manual partitioning.  I cannot get it to establish a mount point for my linux partition ( may be the mouse button problem you mentioned).  We these the only two options you have when at the partitioning stage?

any recommendations would be appreciated.

thanks,
M42

---

### Post by manatane on 2010-03-01
hi,

I'm giving this fine tablet a go too and went x86_64 despite the difficulties to get the installer running.
What I did is use a karmic live cd, install then dist-upgrade.
I mainly wanted to let you guys know that I'm actually discussing with ENAC folks to have multitouch working on it though it'll probably take some time to rewrite a driver for the touch panel.

@M42 : try adding "acpi=off noapic nolapic" to your boot options, it helped me with some kernels (especially with karmic and Fedora 12)

---

### Post by M42 on 2010-03-01
manatane,

Thanks for the info on multitouch.  Sounds like it will be a major step forward for tm2 users. 

I'll give your suggestions a try.  I did try them indivually but not all together.  I can get to the partitioning screen but I don't get the usual options for resizing the windows partion to free up space for the Ubuntu partition.  I know my version of the BIOS, F.05, has problems based on comments on another forum so if your suggestions don't work I'm just going to wait until the BIOS is updated and a stable Lucid coming out in April.

M42

---

### Post by manatane on 2010-03-02
I had the same issue with resizing partitions not present in the installer. Just boot from the live as if you were only willing to try ubuntu and then use gparted to resize and create your partitions. Then launch the installer from the desktop, et voilà ! :)
hope it'll help

---

### Post by M42 on 2010-03-02
Thanks manatane, I'll give gparted a try.  I did try turning off acpi, noacpi and nolacpi without success.

---

### Post by M42 on 2010-03-02
manatane,

Thanks for the suggestions.  They led me to my solution.  I had four primary partions from the windows 7 installation.  I had to delete one to allow gparted to install an extended partition.  After that it was all good.

Thanks,
M42

---

### Post by M42 on 2010-03-03
dgttm,

Thanks for the hacks.  They seem to be working for me.  By the way, I have alpha 3 installed and it has wacom support for the E3 device, the one in the tm2, builtin.  Worked out of the box.

I don't believe the wacom tools are included yet so rotation of screen is still a problem.

M42

---

### Post by dgttm on 2010-03-03
> **M42 said:**
> dgttm,

Thanks for the hacks.  They seem to be working for me.  By the way, I have alpha 3 installed and it has wacom support for the E3 device, the one in the tm2, builtin.  Worked out of the box.

I don't believe the wacom tools are included yet so rotation of screen is still a problem.

M42

hi,

good to hear, sorry i was off for a while. you may use the "configure display" applet for the panel , so it is just 2 clicks for a screen rotation..

---

### Post by M42 on 2010-03-03
dgttm,

The configure display works great for rotating the screen.  My styus and touch don't rotate with it.  Do you also have a way to rotate your stylus and touch?

Thanks,
M42

---

### Post by dgttm on 2010-03-04
no unfortunately not, I just use my bluetooth mouse when rotating the screen. but that is also not working with windows 7 (running on ati graphic or the internal, on the other one it is working). 
so i usually do not rotate at all, or just 90° for viewing pdfs (then using the mouse).

---

### Post by M42 on 2010-03-04
That's what I thought.  I believe the Ubuntu developers indicated that wacom tools would be included in the final Lucid version.  Since this is a Wacom tablet the tools should be able to rotate the stylus and touch like has been done for the tx2000.  Someone developed some very useful scripts that I have tied to some icons in a panel and then I just click the rotation orientation I which and the screen, stylus and touch all rotate together.

Once the wacom tools routines are included I will see if I can get those scripts to work and if so I would upload them.

---

### Post by dedd_morozz on 2010-03-04
I went with the 64 bit version of alpha 3. I had some issues partitioning, but it worked at the end.

However my wifi doesn't seem to work. I can see the networks but haven't been able to connect to any of them. It worked fine from the live usb stick. (Edit: Strike that. Tried it agian, and it didn't work there, either.)

Did any of you have this issue?

---

### Post by M42 on 2010-03-04
dedd_morozz,

I installed the 32 bit and had no problem with my wireless.  You might try the 32 bit version and see if that will work for you.  I didn't try the 64 bit version.  Maybe someone that has installed the 64 bit version can let you know about their experiences with wireless connections.

M42

---

### Post by manatane on 2010-03-04
dedd_morozz,

I'm using 64bits alpha3 and didn't have any problem with wifi, I can even disable it and re-enable with fn keys it works like a charm. Didn't try with WEP or unsecured networks though as mine is configured with wpa2. Another difference I can foresee is I'm using a french version of the tm2 (tm2-1050ef which newest bios is F.04, so probably somewhat different to the US F.05 Bios).

A little update about multitouch support : It seems that wacom driver actually DO support multitouch ... BUT, it doesn't comply with the new way of handling multitouch introduced with 2.6.30 kernels, so it will have to get patched somehow. My knowledge about drivers developpment is far too limited to be able to do it myself but I reported the problem here and there and let's hope it will get patched soon enough. If anyone here is willing to help and have some knowledge about drivers developpment,please tell me, I'll give you more details about what needs to be done

---

### Post by M42 on 2010-03-04
Thanks for the update manatane.  Wish I could help with patching the drivers but my knowledge is, I am sure, less than your's.

---

### Post by Pox on 2010-03-06
Anyone else had problems getting the wifi card to be recognised?

I'm using the Lucid Alpha3 x64 LiveCD.

Interestingly, the wifi card (a Broadcom) was detected when I booted from the liveCD, and the restricted drivers were suggested to me - I just hooked up to the ethernet temporarily and installed them, and then the wireless worked.

However, on my fresh install, the wireless simply isn't recognised.  The light on the toggle button is orange, suggesting that it's disabled - but neither of the toggles work.  I've ensured that it's turned on when I shut down Windows; it still turns off when Ubuntu starts.

lshw lists the device correctly as a wireless card, and marks it as UNCLAIMED.  ifconfig and iwconfig don't acknowledge that it exists.

Any tips?

---

### Post by M42 on 2010-03-06
Pox,

I have the Intel Wireless WiFi Link 1000 Series BGN REV=0x6C not the Broadcom card.  This cards seems to work out of the box without a problem.  I'm using the 32 bit alpha3 installation.  It sounds like a driver problem to me.  Did you try to loading the restricted driver manually using the System/Administation/Hardware Drivers application?

M42

---

### Post by Pox on 2010-03-06
Never mind - I ran an apt-get update and then it found the driver.  Wireless is working fine... now to get everything else happening. :P

---

### Post by Pox on 2010-03-06
Anyone managed to get wacomcpl running? It was supposedly in wacom-tools in previous ubuntu versions, but that package has now been replaced by xserver-xorg-input-wacom, which only has xsetwacom included.  I'd like to be able to calibrate my tablet properly.

I have worked out how to rotate the stylus input with xsetwacom - you can get a list of devices with
```
pox@anthony-tablet:~/Downloads$ xsetwacom --verbose --list dev
... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device '"Power Button"' (6).
... Found device '"Video Bus"' (7).
... Found device '"Video Bus"' (8).
... Found device '"Power Button"' (9).
... Found device '"Sleep Button"' (10).
... Found device '"Wacom ISDv4 E3"' (11).
... Found device '"Wacom ISDv4 E3" eraser' (12).
"Wacom ISDv4 E3" eraser ERASER    
... Found device '"Wacom ISDv4 E3"' (13).
"Wacom ISDv4 E3" STYLUS    
... Found device '"HP Webcam"' (14).
... Found device '"AT Translated Set 2 keyboard"' (15).
... Found device '"PS/2 Synaptics TouchPad"' (16).
... Found device '"Macintosh mouse button emulation"' (17).

```

Note the IDs of the devices we want - 12 and 13. (Not sure why 11 is there - it doesn't do anything as far as I can tell).

You can then set the orientation with

```
xsetwacom --set 12 Rotate CCW
```

and the same for 13.  The valid rotations are NONE, CW, CCW, HALF.

I'm going to try whipping up a script to rotate the input and the display at the same time.
Another handy command to make the button on the stylus do a right-click:
```
xsetwacom --set 12 Button2 3
```

Note: Unfortunately, xsetwacom can only rotate the digitizer input - I still have no idea how to rotate the touchscreen input.

---

### Post by M42 on 2010-03-06
Looks like you're making good progress.  I have been looking for the wacom-tools also.  The following was posted on the alpha2 page:

The wacom-tools driver cannot be used with Lucid Alpha 2. It is no longer supported for xserver 1.7, and also requires HAL for configuration which is no longer available. A new driver xf86-input-wacom is under development upstream but was not yet available in time for this milestone release. This is expected to be resolved for the final release of Ubuntu 10.04 LTS. 

Although this text does not appear on the alpha3 page, it appears that they are still working on the drivers for wacom-tools.

---

### Post by Pox on 2010-03-06
Those who have the lenovo_acpi hack to disable the radeon working - are you loading the module in /etc/modules?

When I put it in /etc/modules, I end up with the screen going blank and the machine freezing up (alt-sysrq-b not even working) ~12 seconds after startup.

However, if I insert it once the machine has booted, it works fine, and as far as I can tell it's genuinely worked - my power consumption has gone down by a fair amount (though it's still far from ideal at ~5 hours expected).  The adapter does still appear in lspci, though.

Also, M42: good news about the wacom-tools - hopefully we'll have them in a month or so.

---

### Post by M42 on 2010-03-06
I have lenovo_acpi in the /etc/modules file.  The hack seems to work ok for me.  I just followed the code linked in the first post.  I just took a look at /etc/modules and lenovo_acpi is included three times.  I'm not sure what that is about.

---

### Post by Pox on 2010-03-07
A quick script to rotate the screen and digitizer input:

[http://gist.github.com/324269](http://gist.github.com/324269)

usage example: ./rotate.rb CW

---

### Post by M42 on 2010-03-08
Thanks for the script.  Maked a couple of tweeks for my system.  Works great.

---

### Post by christofj on 2010-03-10
Hello,

today I have tried to install 32bit Lucid. All things worked exept the disabling of the ATI grafics card. I have compile the lenovo_acpi.c with kernel 2.6.32-16. But it dosen't work. I see nothing inside the kernel messages.

filename:       /lib/modules/2.6.32-16-generic/kernel/lenovo_acpi.ko
license:        GPL
srcversion:     0D37CA05A2E758E0A0DD54A
depends:        
vermagic:       2.6.32-16-generic SMP mod_unload modversions 586 

Did I need special xorg.conf file?

I have here a german TM2 with bios F.04.

Any ideas?   -chris

---

### Post by colorprint on 2010-03-10
Is there any way to use the radeon card and to switch between this one and intel video?

---

### Post by M42 on 2010-03-10
christofj,

No, you should not need a special xorg.conf.  I doubt there should be and differences with your German version tm2 with F.04 bios and the one I have. A few questions.  

1.What do believe it is not working?
2.Did you get any error messages when you executed the commands listed in the hack?
3.Have you looked at your /var/log/Xorg.0.log file?  As dgttm described in his first post, the ati device does not show in my /var/log/Xorg.0.log after inserting the mod.
after a reboot, you will just find the Intel GS45 in your /var/log/Xorg.0.log.
4.If you do a lsmod do you see the lenovo_acpi module listed?

M42

---

### Post by M42 on 2010-03-10
To the best of my knowledge, no.

---

### Post by Pox on 2010-03-10
> **colorprint said:**
> Is there any way to use the radeon card and to switch between this one and intel video?

Not yet, but you should be able to in a few months - [vga_switcheroo is entering the mainline kernel](http://www.phoronix.com/scan.php?page=news_item&px=ODAxOA), and I think it's already functional if you want to compile it manually.

Hopefully we'll see gdm integration soon so you can just click a button and have it save your gnome session, log out, switch, and log you back in.

For now, I'm just disabling the Radeon under Linux - I don't really need it for most of what I do, and I'm happy to boot to Windows to play games.

---

### Post by christofj on 2010-03-11
I have tried to disable the ATI Graphic Card with the kernel module from [http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11) . But I don´t works.

I am think that it starts two X Servers: one for the Intel an one the for the ATI Card. So It starts two times gdm and I must login 2x...

I do not think its a German localization HP problem. I am using the standard English  BIOS F.04

I put a lsmod, dmesg and Xorg.0.log to the attachments.

- chris

---

### Post by hypatia on 2010-03-11
I've got the HP TM2 with the Intel-only graphics. Everything works out of the box with the same exceptions as others have reported: no right-click on the touchpad, wifi is a pain, and no multi-touch on the touchscreen.

Anyone have any bright ideas about working around the bios-locking of the wifi card?  I just bought a new one only to find that it's locked out.  There's a thread about unlocking an HP Mini with the same issue here: [http://myhpmini.com/forum/viewtopic.php?f=62&t=2898](http://myhpmini.com/forum/viewtopic.php?f=62&t=2898) - I may have to see if I can adapt that technique :(

---

### Post by M42 on 2010-03-11
christofj,

I looked at your files and it does appear that the lenovo_acpi is loading correctly.  The only difference I see with my system is I have the F.05 BIOS. Wish I could be more help.

M42

---

### Post by colorprint on 2010-03-11
> **Pox said:**
> Not yet, but you should be able to in a few months - [vga_switcheroo is entering the mainline kernel](http://www.phoronix.com/scan.php?page=news_item&px=ODAxOA), and I think it's already functional if you want to compile it manually.

good, I see it is included in the 2.6.34-rc1 kernel here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc1/) (but I see it is not enabled in config, so I will try to enable it and recompile the kernel)...
But I see another problem (I think the vga_switcheroo will not fix this) - I see this in the dmesg log:

```
dmesg | grep radeon
[   11.398083] [drm] radeon defaulting to kernel modesetting.
[   11.398087] [drm] radeon kernel modesetting enabled.
[   11.398184] radeon 0000:01:00.0: power state changed by ACPI to D0
[   11.398194] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   11.398203] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.398213] radeon 0000:01:00.0: setting latency timer to 64
[   11.400739] [drm] radeon: Initializing kernel modesetting.
[   11.417796] radeon 0000:01:00.0: Invalid ROM contents
[   11.417922] radeon 0000:01:00.0: Invalid ROM contents
[   11.417998] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[   11.418061] radeon 0000:01:00.0: Fatal error during GPU init
[   11.418120] [drm] radeon: finishing device.
[   11.454767] radeon 0000:01:00.0: PCI INT A disabled
[   11.454777] radeon: probe of 0000:01:00.0 failed with error -22
```

So, the radeon driver not works with the ATI HD 4500 card?
Is there any way to fix this? Should I try the proprietary driver from amd.com ?

---

### Post by colorprint on 2010-03-12
I have recompiled the kernel with switcheroo enabled,
now my radeon card detected without any errors in dmesg log (firware R700 loaded etc), but when I switched to it and log-off - laptop hangs.
Also I don't see the radeon card in Xorg logs...
Only one string: 
(--) PCI: (0:1:0:0) 1002:9555:103c:3661 ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series] rev 0, Mem @ 0xc0000000/268435456, 0xe4400000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072

Should I add the radeon card in the xorg.conf to use it?
My xorg.conf is empty, but intel card and input devices work fine...

---

### Post by colorprint on 2010-03-12
Added this line to /etc/rc.local:

echo ON > /sys/kernel/debug/vgaswitcheroo/switch


And now I can switch to radeon card with:

echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
gnome-session-save --logout

But it seems I can't switch back to intel and back to radeon after this %) So I can switch to radeon only once after reboot

---

### Post by Pox on 2010-03-12
Hey guys,

Thanks to some help from Brian Murray at his blog ( [http://www.murraytwins.com/blog/?p=65#comment-12981](http://www.murraytwins.com/blog/?p=65#comment-12981) ), I now have screen rotation working with both input devices - the touchscreen now rotates correctly!

See my version of Brian's script at [http://gist.github.com/331086](http://gist.github.com/331086) - I've got a panel icon bound to "wacom_rotate next", which rotates the screen and input counterclockwise.

Anyone worked out how to listen for the screen swivel or rotate button events yet? I get nothing in xev or acpi_listen... I'd love to have automatic rotation when I go into tablet mode, and a physical rotate button is easier than a panel button.

---

### Post by hypatia on 2010-03-13
Hopefully someone else has the same wifi card as my TM2 - Broadcom 4357.  If anyone does, can you share the results of lspci -nv done as root?  I just need the section for the wifi card.

Thanks!

(it's a long story but I gave it to the dude at the shop I bought a replacement card before finding out about HP's stupid #$%@%^^%$ BIOS whitelisting of wifi cards, so I don't have it any more to test with :/)

---

### Post by hypatia on 2010-03-15
new kernel / configs:  right mouse works, no scrolling now though!

---

### Post by mcoleman44 on 2010-03-16
You can still use wacom, but its called xf86-input-wacom, but you have to patch it to recognize hid-n-trig.ko. If you have a multi-touch capable evdev and xorg-server 1.7 or later than you can give multi-touch sub devices. giving you up to 4 fingers depending on your n-trig firmware version. For those of you wanting to use compiz and rotate, here is a script to do that. It works great in karmic, should work in lucid if you have your devices named right.
```
rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal)
    metacity --replace &
    sleep 3s
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set stylus rotate HALF 
    xsetwacom set mttouch rotate HALF
    xsetwacom set touch rotate HALF
    compiz --replace & 
    ;; 
    inverted) 
    metacity --replace &
    sleep 3s
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set stylus rotate  CW 
    xsetwacom set mttouch rotate CW 
    xsetwacom set touch rotate CW
    compiz --replace & 
    ;; 
    right) 
    metacity --replace &
    sleep 3s
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set stylus rotate NONE 
    xsetwacom set mttouch rotate NONE 
    xsetwacom set touch rotate NONE
    compiz --replace & 
    ;; 
esac
```

---

### Post by mcoleman44 on 2010-03-16
Sorry about that, I was reading the post, and you all already know about xf86 wacom.

[http://ubuntuforums.org/showthread.php?t=1252492&page=82](http://ubuntuforums.org/showthread.php?t=1252492&page=82)

Check that link out if you want to get sub devices working, and dont forget that you have to have a multi touch capable evdev.

---

### Post by colorprint on 2010-03-16
Hmm... but there is wacom multitach digitizer in HP tm2, not N-trig like in HP tx2...
Will it work with evdev driver??
I am using Wacom driver, pen and finger touch works fine, but no multitach...

> xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3 Finger"                 	id=11	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3 Pen"                    	id=13	[slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3 Pen" eraser             	id=12	[slave  pointer  (2)]
&#9116;   &#8627; "SynPS/2 Synaptics TouchPad"            	id=16	[slave  pointer  (2)]
&#9116;   &#8627; "Microsoft Wireless Entertainment Keyboard 7000"	id=18	[slave  pointer  (2)]
&#9116;   &#8627; "Microsoft Wireless Laser Mouse 8000"   	id=19	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=6	[slave  keyboard (3)]
    &#8627; "Video Bus"                             	id=7	[slave  keyboard (3)]
    &#8627; "Video Bus"                             	id=8	[slave  keyboard (3)]
    &#8627; "Power Button"                          	id=9	[slave  keyboard (3)]
    &#8627; "Sleep Button"                          	id=10	[slave  keyboard (3)]
    &#8627; "HP Webcam"                             	id=14	[slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"          	id=15	[slave  keyboard (3)]
    &#8627; "HP WMI hotkeys"                        	id=17	[slave  keyboard (3)]

---

### Post by mcoleman44 on 2010-03-16
Ohh... I forgot that you all didnt use n-trig. My bad. Do you all have to patch multitach to make it work?

---

### Post by mcoleman44 on 2010-03-16
But to be honest I dont think It will work with multitach. I know little of nothing about multitach. Sorry, I just assumed you used n-trig.

---

### Post by torkve on 2010-03-18
I have HP tm2-1080er and lucid i386. Tried to disable touchpad while typing (using [this guide]("https://help.ubuntu.com/community/SynapticsTouchpad")). But all attempts to start *syndaemon* results in:
```
$ syndaemon -i 0.5 -d -t -K
Unable to find a synaptics device.
```Also:
```
 $ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3"                            id=11    [slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3"                            id=13    [slave  pointer  (2)]
&#9116;   &#8627; "Wacom ISDv4 E3" eraser                     id=12    [slave  pointer  (2)]
&#9116;   &#8627; "PS/2 Synaptics TouchPad"                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"          id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; "Power Button"                              id=6    [slave  keyboard (3)]
    &#8627; "Video Bus"                                 id=7    [slave  keyboard (3)]
    &#8627; "Video Bus"                                 id=8    [slave  keyboard (3)]
    &#8627; "Power Button"                              id=9    [slave  keyboard (3)]
    &#8627; "Sleep Button"                              id=10    [slave  keyboard (3)]
    &#8627; "HP Webcam"                                 id=14    [slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"              id=15    [slave  keyboard (3)]
``````
$ xinput list-props 16
Device '"PS/2 Synaptics TouchPad"':
    Device Enabled (145):    1
    Device Accel Profile (268):    0
    Device Accel Constant Deceleration (269):    1.000000
    Device Accel Adaptive Deceleration (271):    1.000000
    Device Accel Velocity Scaling (272):    10.000000
    Evdev Reopen Attempts (261):    10
    Evdev Axis Inversion (273):    0, 0
    Evdev Axes Swap (275):    0
    Axis Labels (276):    "Rel X" (153), "Rel Y" (154)
    Button Labels (277):    "Button Left" (146), "Button Middle" (147), "Button Right" (148), "Button Wheel Up" (149), "Button Wheel Down" (150)
    Evdev Middle Button Emulation (278):    2
    Evdev Middle Button Timeout (279):    50
    Evdev Wheel Emulation (280):    0
    Evdev Wheel Emulation Axes (281):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (282):    10
    Evdev Wheel Emulation Timeout (283):    200
    Evdev Wheel Emulation Button (284):    4
    Evdev Drag Lock Buttons (285):    0
$ xinput list-props 17
Device '"Macintosh mouse button emulation"':
    Device Enabled (145):    1
    Device Accel Profile (268):    0
    Device Accel Constant Deceleration (269):    1.000000
    Device Accel Adaptive Deceleration (271):    1.000000
    Device Accel Velocity Scaling (272):    10.000000
    Evdev Reopen Attempts (261):    10
    Evdev Axis Inversion (273):    0, 0
    Evdev Axes Swap (275):    0
    Axis Labels (276):    "Rel X" (153), "Rel Y" (154)
    Button Labels (277):    "Button Left" (146), "Button Middle" (147), "Button Right" (148), "Button Wheel Up" (149), "Button Wheel Down" (150)
    Evdev Middle Button Emulation (278):    2
    Evdev Middle Button Timeout (279):    50
    Evdev Wheel Emulation (280):    0
    Evdev Wheel Emulation Axes (281):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (282):    10
    Evdev Wheel Emulation Timeout (283):    200
    Evdev Wheel Emulation Button (284):    4
    Evdev Drag Lock Buttons (285):    0
```And part of Xorg.0.log, corresponding to touchpad:
```
(II) config/udev: Adding input device "PS/2 Synaptics TouchPad" (/dev/input/event10)
(**) "PS/2 Synaptics TouchPad": always reports core events
(**) "PS/2 Synaptics TouchPad": Device: "/dev/input/event10"
(II) "PS/2 Synaptics TouchPad": Found 3 mouse buttons
(II) "PS/2 Synaptics TouchPad": Found relative axes
(II) "PS/2 Synaptics TouchPad": Found x and y relative axes
(II) "PS/2 Synaptics TouchPad": Configuring as mouse
(**) "PS/2 Synaptics TouchPad": YAxisMapping: buttons 4 and 5
(**) "PS/2 Synaptics TouchPad": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""PS/2 Synaptics TouchPad"" (type: MOUSE)
(**) "PS/2 Synaptics TouchPad": (accel) keeping acceleration scheme 1
(**) "PS/2 Synaptics TouchPad": (accel) acceleration profile 0
(II) "PS/2 Synaptics TouchPad": initialized for relative axes.
(II) config/udev: Adding input device "PS/2 Synaptics TouchPad" (/dev/input/mouse3)
(**) "PS/2 Synaptics TouchPad": always reports core events
(**) "PS/2 Synaptics TouchPad": Device: "/dev/input/mouse3"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""PS/2 Synaptics TouchPad""
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event4)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/event4"
(II) "Macintosh mouse button emulation": Found 3 mouse buttons
(II) "Macintosh mouse button emulation": Found relative axes
(II) "Macintosh mouse button emulation": Found x and y relative axes
(II) "Macintosh mouse button emulation": Configuring as mouse
(**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
(**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
(**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
(**) "Macintosh mouse button emulation": (accel) acceleration profile 0
(II) "Macintosh mouse button emulation": initialized for relative axes.
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/mouse0)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/mouse0"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""Macintosh mouse button emulation""
...
(II) "PS/2 Synaptics TouchPad": Device reopened after 1 attempts.
(II) "Macintosh mouse button emulation": Device reopened after 1 attempts.
```Does anyone know how to fix it?

---

### Post by colorprint on 2010-03-18
(II) XINPUT: Adding extended input device ""PS/2 Synaptics TouchPad"" (type: MOUSE)
This is the reason...
Maybe you have added something like "options psmouse proto=imps" in /etc/modprobe.d/ ? I saw this advice to get the right and left clicks working, but in this case the mouse driver will be used...

---

### Post by torkve on 2010-03-18
Oh, exactly, I did it as mentioned in the first post. But how should I enable my mouse buttons now? I have left click by tapping and edge scrolling (mouse preferences radio button "two finger scrolling" is disabled for unknown reasons). I'm not even dreaming about touchscreen multitouch/right pen button/whatever, just bloody left and right buttons on my touchpad :) Is it real now?
Thanks in advance.

---

### Post by colorprint on 2010-03-19
I have not found a way to fix this...
I think the touchpad drivers should be modified to support this new touchpad model

---

### Post by torkve on 2010-03-19
If it'll help someone, I've created file /etc/udev/rules.d/66-hp-synaptic.rules: [http://paste.ubuntu.com/397903/](http://paste.ubuntu.com/397903/)
Nevertheless, two-finger scroll and two/three-finger tap doesn't work but at least I can emulate right and middle mouse button by pointing bottom right and top right corners correspondingly.

---

### Post by 3qno on 2010-03-22
I've tried the rotation script, it correctly rotate but I got this message :


```

property Evdev Axis Inversion doesn't exist, you need to specify its type and format
property Evdev Axis Calibration doesn't exist, you need to specify its type and format
property Evdev Axis Swap doesn't exist, you need to specify its type and format

```Touchscreen is only working with the pen after this.


simple ? : We updated and use new wacom driver why does the script refers to Evdev ?

---

### Post by M42 on 2010-03-23
> **3qno said:**
> I've tried the rotation script, it correctly rotate but I got this message :


```

property Evdev Axis Inversion doesn't exist, you need to specify its type and format
property Evdev Axis Calibration doesn't exist, you need to specify its type and format
property Evdev Axis Swap doesn't exist, you need to specify its type and format

```Touchscreen is only working with the pen after this.


simple ? : We updated and use new wacom driver why does the script refers to Evdev ?


Which rotation script did you use?  I used the one Pox did in post #41 and it works fine for me for everything.  Remember the device ids change slightly depending on the version of tm2 you have as Pox noted in the post on Brian's page.

---

### Post by colorprint on 2010-03-23
BTW, wacom works fine with 2.6.34-rc1 kernel, but some problems with 2.6.34-rc2: with finger touch cursor jumps to left and bottom sides of the screen :( Stylus works fine.

---

### Post by M42 on 2010-03-23
There seems to be a work around for the lack of brightness control.  See the post by Anton in Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516772](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516772)

So far it is working for me.

---

### Post by nearo on 2010-03-24
Colorprint, is multitouch working too in 2.6.34?

Has anyone tried to disable the ati card in the bios, and then reboot and enable it in the bios if you need it?

Really interested in this tablet. Might buy one if it's available in my country.

---

### Post by colorprint on 2010-03-25
No, multitouch not works.. I think the wacom drivers should be modified to support it...
And there is not option in the BIOS to disable the card..
You can switch the video cards with the vga_switcheroo (with kernel 2.6.34)

---

### Post by waka324 on 2010-04-04
I love this forum and just wanted to contribute a little something...

after messing around, I have auto rotation working just splendidly...

I had to do a few things...

first, add hp-wmi to the startup modules in /etc/modules (I added it before the last module because it seemed not to load... (I also added the xorg.conf file to try and stabilize the intel screen rotation, which may or may not be related to having the hp-wmi module load...))

then, use this script as a startup program ie... bash rotation.sh

```
#!/bin/bash

STYLUS="12"
ERASER="11"
TOUCH="10"

old="0"
while true; do
	if [ -e /sys/devices/platform/hp-wmi/tablet ];	then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then
#			-Close and restart Cairo Dock so it resizes on rotation.
#			killall -9 cairo-dock &
#			sleep 2s
			if [[ $new == "0" ]]; then
				
				xrandr -o normal 
				sleep 1s
				xsetwacom set $STYLUS rotate NONE 
				xsetwacom set $ERASER rotate NONE
				xsetwacom set $TOUCH rotate NONE
				gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/ryan/wallpaper-landscape.png
#				cellwriter --hide-window
			elif [[ $new == "1" ]]; then
				
				xrandr -o right 
				sleep 1s
				xsetwacom set $STYLUS rotate CW 
				xsetwacom set $ERASER rotate CW
				xsetwacom set $TOUCH rotate CW 
				gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/ryan/wallpaper-portrait.png
#				cellwriter --show-window
			fi 
#			cairo-dock -o &
		fi
		old=$new
		sleep 1s
	fi
done
```

it will run in the background and set your screen to the tablet mode every time it is rotated...

as added note, I tried all the synaptics clickpad patches offered, but none of them seemed to do the job... I don't care so much about multitouch, but that no right click is killing me...

---

### Post by dgttm on 2010-04-04
right click is working with:

add to /etc/modprobe.d/options 

```
options psmouse proto=imps

```

but unfortunately, scrolling isn't possible anymore (on the right side of the touchpad)

---

### Post by waka324 on 2010-04-04
is there any way that we could try and get one of these patches working for these tablets?

[http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads)

[https://patchwork.kernel.org/patch/67245/](https://patchwork.kernel.org/patch/67245/)

I have tried and failed unfortunately...

as of yet here is my little list of things I am hoping to get working:

1. Graphical screen calibration. 
2. Back-light brightness controls.
3. Synaptics clickpad with scrolling and disable button.

as a side-note, I tested out the next kernel (2.6.33) and the little led to show the status of mute was working! :P 

also, touch seems to be a little wonkey, but I can't be too sure...

---

### Post by waka324 on 2010-04-05
to fix the id numbers changing upon boot, I added this to my script I posted...

```
ERASER=$( xinput --list | grep  'Wacom ISDv4 E3 eraser ' | grep -o 'id\=[0,1,2,3,4,5,6,7,8,9]**' | grep -o '[0,1,2,3,4,5,6,7,8,9]**')
STYLUS=$(($ERASER+1))

TOUCH=$( xinput --list | grep  'Wacom' | grep -o 'id\=[0,1,2,3,4,5,6,7,8,9]**' | grep -o '[0,1,2,3,4,5,6,7,8,9]**' | grep -v $STYLUS | grep -v $ERASER)
```

this will obviously replace the earlier assignment. I make the assumption that eraser will always come right before stylus (as per observation) and that touch will be the only other remaining wacom device.

I hope this works for you guys.

---

### Post by nearo on 2010-04-09
Anyone tried Fedora Rawhide? It uses kernel 2.6.34RC, according to distrowatch. Maybe VGA_switcheroo is working then. 

HP tm2 is still not available in my country...

---

### Post by colorprint on 2010-04-09
> **nearo said:**
> Anyone tried Fedora Rawhide? It uses kernel 2.6.34RC, according to distrowatch. Maybe VGA_switcheroo is working then. 

I have recompiled the kernel (have 2.6.34-rc3 installed) with enabled VGA_switcheroo and it works fine
> 
HP tm2 is still not available in my country...
I have ordered it at hp.com to the US address and forwarded to Russia with mail-forwarding service ))

---

### Post by colorprint on 2010-04-09
> **waka324 said:**
> is there any way that we could try and get one of these patches working for these tablets?

[http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads)

[https://patchwork.kernel.org/patch/67245/](https://patchwork.kernel.org/patch/67245/)

I have tried and failed unfortunately...


patch works fine on 2.6.34 kernel. Thanks!

---

### Post by torkve on 2010-04-09
> **colorprint said:**
> I have recompiled the kernel (have 2.6.34-rc3 installed) with enabled VGA_switcheroo and it works fine
I have ordered it at hp.com to the US address and forwarded to Russia with mail-forwarding service ))
What driver do you use (ati, radeon etc.)?
Btw, tm2 is available at least in Moscow.

---

### Post by colorprint on 2010-04-09
It was not available in Russia when I have ordered it 2 monthes ago )
And the price in Moscow is over 1600$, it is very high, I have bought it for about 1000$.

I am using radeon driver for the second videocard.
I am using it with external monitor attached by HDMI.

---

### Post by cbanbury on 2010-04-09
> **colorprint said:**
> I have recompiled the kernel (have 2.6.34-rc3 installed) with enabled VGA_switcheroo and it works fine

I have ordered it at hp.com to the US address and forwarded to Russia with mail-forwarding service ))

Glad you got it working. Every time I compile 2.6.34-rc3 I keep getting a kernel panic on boot. 
Can you offer some advice or a link to your compiled kernel. 

Thanks 

p.s. What battery life are you getting in linux with vga_switcheroo working?

---

### Post by colorprint on 2010-04-09
I have used kernel sources package from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

3-4 hours battery life with vga_switcheroo and disabled radeon card, and brightness over 60-75%
Also i have tested it with disabled screen and attached to the external monitor, with disabled radeon card - got 6 hours battery life... 
Anyway, it is far away from 8 hours described on the hp.com :(

---

### Post by cbanbury on 2010-04-09
> **colorprint said:**
> I have used kernel sources package from [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline)

3-4 hours battery life with vga_switcheroo and disabled radeon card, and brightness over 60-75%
Also i have tested it with disabled screen and attached to the external monitor, with disabled radeon card - got 6 hours battery life... 
Anyway, it is far away from 8 hours described on the hp.com :(

Thanks, I tried the source from here. Just recompiled with the vga_switcheroo option on & fails to mount my hard drive. Is there something else I need to do? 

Battery life is indeed disappointing, I was easily getting 9 hours on windows :( (Though that is with WiFi disabled as well).

---

### Post by colorprint on 2010-04-09
9 hours - strange... 
Can't test with Windows, installed Ubuntu right after received the laptop....

---

### Post by waka324 on 2010-04-10
M42, I was just hoping you might be able to clarify wich patch and how? (for the brightness) I tried using the patch at the bottom of that bug submission, but it did not work.

---

### Post by colorprint on 2010-04-10
To change brightness you can use setpci command:

sudo setpci -s 00:02.0 F4.B=FF

where the FF is brightness level (from 0 to FF hex)

---

### Post by colorprint on 2010-04-10
> **cbanbury said:**
> Thanks, I tried the source from here. Just recompiled with the vga_switcheroo option on & fails to mount my hard drive. Is there something else I need to do? 

Battery life is indeed disappointing, I was easily getting 9 hours on windows :( (Though that is with WiFi disabled as well).
It seems that radeon card not always powered off when I switch it off with vga_switcheroo... 
Today (after booting Windows from flash drive and rebooting to Ubuntu) I have got over 6 hours on the battery! And the laptop was not so heated as always.

---

### Post by cbanbury on 2010-04-10
> **colorprint said:**
> It seems that radeon card not always powered off when I switch it off with vga_switcheroo... 
Today (after booting Windows from flash drive and rebooting to Ubuntu) I have got over 6 hours on the battery! And the laptop was not so heated as always.

I'm not sure the heat is coming from the GPU, I managed to get both kernels to run fairly cool by enabling spin down hard disks even when plugged in. It was the hd for me that was getting really hot. 

Still don't get why I can't get 2.6.34 to boot. Can you send me your linux-image/headers from the compile so I can at least test it? (Sorry, I know I'm being a n00b :()

---

### Post by waka324 on 2010-04-10
hmmm... that brightness comand dosen't seem to work for me... now I am worried I will never be able to dim my display to save battery...

lspci shows:
...
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
...

thanks.

---

### Post by colorprint on 2010-04-11
> **waka324 said:**
> hmmm... that brightness comand dosen't seem to work for me... 
Are you running it as root?

---

### Post by colorprint on 2010-04-11
> **cbanbury said:**
> I'm not sure the heat is coming from the GPU, I managed to get both kernels to run fairly cool by enabling spin down hard disks even when plugged in. It was the hd for me that was getting really hot. 

Still don't get why I can't get 2.6.34 to boot. Can you send me your linux-image/headers from the compile so I can at least test it? (Sorry, I know I'm being a n00b :()
Ok, I will upload and share it.
Do you have x86_64 or x86 Ubuntu installed?
I have x86_64, so the kernel package I have compilied is for x86_64 too...

---

### Post by colorprint on 2010-04-11
My patched kernel packages:

[http://dl.dropbox.com/u/4080500/linux-headers-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/4080500/linux-headers-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/4080500/linux-image-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/4080500/linux-image-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb)

---

### Post by waka324 on 2010-04-11
I feel so stupid. That is the one thing I didn't try. Thanks.

---

### Post by waka324 on 2010-04-11
***************************FIXED****************************



so I am back with another script... 

this one changes the backlight automatically for you when you use the buttons or unplug power...

just make the script, make it executable, then copy it to /etc/init.d, then 

sudo update-rc.d script_name_here start 20 2 3 4 5 . stop 20 2 3 4 5 .


```
#!/bin/bash

old=`cat /sys/class/backlight/acpi_video0/brightness`

value=$(((($old)*24)+15))
value=$(echo "ibase=10; obase=16; $value" | bc)
setpci -s 00:02.0 F4.B=$value

while true; do
	if [ -e /sys/class/backlight/acpi_video0/brightness ];	then
		new=`cat /sys/class/backlight/acpi_video0/brightness`
		if [[ $new != $old ]]; then

value=$(((($new)*24)+15))
value=$(echo "ibase=10; obase=16; $value" | bc)
setpci -s 00:02.0 F4.B=$value

		fi
		old=$new
		sleep 1s
	fi
done
```

---

### Post by cbanbury on 2010-04-11
> **colorprint said:**
> My patched kernel packages:

[http://dl.dropbox.com/u/4080500/linux-headers-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/4080500/linux-headers-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/4080500/linux-image-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/4080500/linux-image-2.6.34-rc3-p1_2.6.34-rc3-p1-10.00.Custom_amd64.deb)

Thanks, will try it & let you know how it goes :)

---

### Post by waka324 on 2010-04-11
just discovered a fatal flaw! it fails to exit on shutdown so system halts, you have to restart, and I had to disable fsck to even boot! 

Sorry! do not use yet until I find a way arround it.

---

### Post by colorprint on 2010-04-11
> **waka324 said:**
> just discovered a fatal flaw! it fails to exit on shutdown so system halts, you have to restart, and I had to disable fsck to even boot! 

Sorry! do not use yet until I find a way arround it.
and it also consume 10-20% CPU when running

---

### Post by colorprint on 2010-04-11
and gnome brightness applet shows incorrect brightness level (I still can add brightness when the applet shows 100% brightness, and can low it when applet show 0%)

---

### Post by waka324 on 2010-04-11
the brightness levels are correct for me... hmmm... though I never applied any video patches... check the contents of 
/sys/class/backlight/acpi_video0/brightness... all my script does is read it, and convert it into a hex value between 15-255 (base 10) my values in /sys/class/backlight/acpi_video0/brightness never exceed 10 or go below 0, but if they did go below 0, it would overflow and cause the brightness to skyrocket... hmm... as for the cpu usage, I am looking into that. in the meantime, I discovered that the script was not properly unloading because of the update-rc.d command I used... instead of 

sudo update-rc.d script_name_in_here defaults

it should be 

sudo update-rc. script_name_in_here start 20 2 3 4 5 . stop 20 2 3 4 5 .

---

### Post by waka324 on 2010-04-11
ok... that one was easy... add sleep 1s to it so that it is now... 

#!/bin/bash

old=`cat /sys/class/backlight/acpi_video0/brightness`

value=$(((($old)*24)+15))
value=$(echo "ibase=10; obase=16; $value" | bc)
setpci -s 00:02.0 F4.B=$value

while true; do
	if [ -e /sys/class/backlight/acpi_video0/brightness ];	then
		new=`cat /sys/class/backlight/acpi_video0/brightness`
		if [[ $new != $old ]]; then

value=$(((($new)*24)+15))
value=$(echo "ibase=10; obase=16; $value" | bc)
setpci -s 00:02.0 F4.B=$value

		fi
		old=$new
		sleep 1s
	fi
done

cpu usage is way down.

---

### Post by colorprint on 2010-04-11
yes, the /sys/class/backlight/acpi_video0/brightness changes between 0 to 10, but it seems the gnome applet tries to show only 6 levels ))

---

### Post by cbanbury on 2010-04-11
Thanks again Colorprint for the patched Kernel. Works fine, I think I saw somewhere that theres a bug with vga_switcheroo only allowing you to change the state once per boot. 

With regards to the heat issue, I also changed the BIOS settings for the fan so that its not always on. Not sure if this helps, but might let ubuntu control the fan a bit more.

[Edit] Are you doing echo OFF > switch every time so that only one card is powered on? My laptop gets really hot if I don't

---

### Post by colorprint on 2010-04-12
I have a problem with resume after S3 sleep mode - after this finger touch does not works, only stylus does.
Here is the patch to fix this on E2 and E3 wacom devices (HP tm2 uses E3 one):


--- wacom_sys.c 2010-04-11 19:22:13.000000000 -0700
+++ wacom_sys.c_new     2010-04-11 19:21:07.000000000 -0700
@@ -680,12 +680,13 @@
        if (wacom->open) {
                rv = usb_submit_urb(wacom->irq, GFP_NOIO);

-               /* switch to wacom mode if needed */
-               if (!wacom_retrieve_hid_descriptor(intf, features))
-                       wacom_query_tablet_data(intf, features);
        } else
                rv = 0;

+       /* switch to wacom mode if needed */
+       if (!wacom_retrieve_hid_descriptor(intf, features))
+               wacom_query_tablet_data(intf, features);
+
        mutex_unlock(&wacom->lock);

        return rv;

---

### Post by waka324 on 2010-04-12
just currious, did anyone happen to notice that when you rotate the touch along with the screen, the taping part rotates fine, but when you release your finger, the cursor jumps to where it would be if the screen were not rotated?

---

### Post by nearo on 2010-04-12
Looks like the touchpad will work out of the box in 10.04: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516329")
Fix was released earlier today.

---

### Post by waka324 on 2010-04-12
I made a much more graceful solution to the backlight issue... 

create two files in /etc/acpi/events... one for increasing brightness and one to decrease brightness...
increase:

```

event=video DD03 00000086 00000000
action=/etc/acpi/backlight-script.sh

```
for decreasing:
```

event=video DD03 00000087 00000000
action=/etc/acpi/backlight-script.sh

```

you can double check the value for event by running acpi_listen and hitting the two buttons... now make the script backlight-script in /etc/acpi
and in there put this:
```

#!/bin/bash

sleep 1s
old=`cat /sys/class/backlight/acpi_video0/brightness`
value=$(((($old)*24)+15))
value=$(echo "ibase=10; obase=16; $value" | bc)
setpci -s 00:02.0 F4.B=$value

```

just make sure to make the script executable and if you want to test it out, just run 

sudo restart acpid

to restart acpid, and you can test your brightness buttons, and you can even make a link in /etc/acpi/power.sh to your script like so:

```

#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/policy-funcs
. /etc/acpi/backlight-script.sh

if [ -z "$*" ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

pm-powersave $*


``` 

so that when AC power is connected/disconnected, the brightness levels change.

doing it this way means that you don't have it running in the background taking up resources. :) hats of to you colorprint :)

---

### Post by cbanbury on 2010-04-12
To anyone using vga_switcheroo. It keeps disappearing from /sys/kernel/debug & have no idea why? 

Any ideas?

---

### Post by glimmer00 on 2010-04-14
Very nice waka324.  And to think I'd been making due with my collection of b0 to b10 scripts using the setpci call.  I did change the script to have a .25 second delay and it worked on my TM2 without issue.  I assume at some point though the system won't have time to update the /sys backlight value before the script reads it and you will have issues.

---

### Post by waka324 on 2010-04-14
the acpi method means that a) only the buttons and ac can change brightness... and b) sometimes it isn't fast enough... I hope to make a kernel patch that will fix the backlighting... sometime after exams... :)

also, there is a MUCH better patch for the synaptics... if you want, I attached my psmouse.ko so that you can replace the one in lib/modules/`uname -r`/kernel/drivers/input/mouse with the one I attached. I am using the 2.6.33 kernel posted on the ubuntu ppa site, but if you want to compile your own modules, I also included the 
synaptics source...

Edit:
THANK YOU SO MUCH Takashi Iwai FOR GIVING US THESE BITS OF CODE!

I did not write the patch or code, only applied it to the synaptics source.

Also, I HIGHLY recomend the new wacom drivers, just download, and install:  

[HTML]./configure --enable-wacom --prefix=/usr

make

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[/HTML]

Now, you no longer have to check which devices are which! 

if you use xsetwacom --list, you can see that the devices have become:

Wacom ISDv4 E3 Pen eraser ERASER    
Wacom ISDv4 E3 Pen STYLUS    
Wacom ISDv4 E3 Finger TOUCH    

now you can configure them by reference to these names! (ie. Wacom ISDv4 E3 Pen eraser, Wacom ISDv4 E3 Pen, or Wacom ISDv4 E3 Finger)

Edit: Forgot to mention exactly WHAT the synaptics driver does that the new kernel doesn't...

1) allows to disable the clickpad and shows the led by taping it.
2) disables the movement in the clickpad region
3) allows right and left click and scroll.

Enjoy!

---

### Post by colorprint on 2010-04-15
Can't compile it with 2.6.34 kernel :(
Could you create a diff patch?

---

### Post by Pox on 2010-04-15
> **waka324 said:**
> just currious, did anyone happen to notice that when you rotate the touch along with the screen, the taping part rotates fine, but when you release your finger, the cursor jumps to where it would be if the screen were not rotated?

I've had the same issue for a week or two - it's quite annoying and sometimes makes it difficult to interact.

---

### Post by waka324 on 2010-04-15
you can get the patch information from here: 

[http://gitorious.org/opensuse/kernel-source/commit/83fc815](http://gitorious.org/opensuse/kernel-source/commit/83fc815)

I had to patch it manually (ie, compare lines and copy/paste because for whatever reason, I couldn't patch the orriginal patch with the new patch) by adding the old patch (ie, everything in red) to the synaptics sources, although with the new kernel, you might be able to apply the green code to your sources... 

then I just used the makefile from

[http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads)

and voila!

---

### Post by colorprint on 2010-04-16
> **waka324 said:**
> you can get the patch information from here: 

[http://gitorious.org/opensuse/kernel-source/commit/83fc815](http://gitorious.org/opensuse/kernel-source/commit/83fc815)

I had to patch it manually (ie, compare lines and copy/paste because for whatever reason, I couldn't patch the orriginal patch with the new patch) by adding the old patch (ie, everything in red) to the synaptics sources, although with the new kernel, you might be able to apply the green code to your sources... 

then I just used the makefile from

[http://community.saugususd.org/swattec/page/Synaptics+Clickpads](http://community.saugususd.org/swattec/page/Synaptics+Clickpads)

and voila!
I have applied the latest patch (green lines) and compilied the module. But now right click not works, LED not works not...
Clicks worked before with previous patch...
Also I have read that button clicks support moved from kernel to driver with this patch...("In this version, button events are no longer handled in the kernel sidebut by x11 synaptics driver.  The LED is controlled via evdev events") So maybe synaptic driver should be patched and reinstalled too to get it worked?

---

### Post by waka324 on 2010-04-16
hmmm.... possibly... I tried using that patch with the older kernel without sucess, but used the old patch with good results... do we have the xf86-synaptics in the repos? because once, when I patched the wacom driver, and copied it over, it would refuse to work until I reinstalled the xf86-wacom driver.

---

