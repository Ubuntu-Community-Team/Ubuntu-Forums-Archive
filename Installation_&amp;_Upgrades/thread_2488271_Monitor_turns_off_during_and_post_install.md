---
title: "Monitor turns off during and post install"
date: 2023-06-29
forum: Installation &amp; Upgrades
---

### Post by Tanarotte on 2023-06-29
Hello, 

When trying to start a live cd image of ubuntu 23.04 system tries to boot from pendrive, then monitor turns off and theres no further reaction. When starting the installer with "safe graphics" mode
everything is fine, ive updated and installed the system. However on first and any further boot i get the same issue, theres like a second or two of boot animation and then screen turns off with no further reaction. 

From what I understand my computer, being AMD based (ryzen 3700, rx6800 ) and not the latest, it should be like completely well supported by the build in drivers and require very little or no intervention from my side. 
Since it does with safe gfx and not without i have tried to edit boot thing and add nomodeset after the splash thing, this however did not yeld the success i was hoping for. Is there anything I can do to fix it or 
my machine is just like banned from using ubuntu. (In my tests fedora, nobara and manjaro do work, at least their live cd work without safemode).

---

### Post by TheFu on 2023-06-29
IDK, but it is likely a GPU driver and kernel version problem.  Gathering that information for the working and non-working configurations will help you figure out what might be the common factor for both working and non-working boots.

Also, whether you are using X11 or Wayland could matter. Try both.

Hope that makes sense.

---

### Post by Tanarotte on 2023-06-29
yes well i would have tried using x11 or something, its however hard to do with turned off screen. Is there any way i can start installed ubuntu with the safemode gfx like in iso?

Shouldnt 6800 use the same mesa driver as entire 68xx and 69xx family of products? Such catastrophic failure should be therefore more common no?



So far according to my tests: 
Nobara 37 - all versions - works
Nobara 38 - all versions - works
Fedora 38 - 6.2.9.300 - works
Linux mint 21,1  5.15.0-76 - works
RHEL 9 - works


Debian - screen turns of then pc dies during live cd boot. 
ALL Ubunty flavours 23.4  - screen turns of then pc dies during live cd boot.
Garuda dragonized gaming - screen turns of then pc dies during live cd boot.
Opensuse tumbleweed - screen turns of then pc dies during live cd boot.


What on earth is going on in here ;(

---

### Post by MAFoElffen on 2023-07-01
First test with the LiveUSB, 

At boot, at the Grub2 boot menu, press the <E> key. <Arrow-Down to the line that starts with the word "linux". <Arrow-Right> until you get to the words "quiet splash" Delete "quiet". <Arrow-Right until after "splash"...

Add a <Space> the type in the text "radeon.modeset=0 amdgpu.noretry=0 amdgpu.dc=1" (without the quotes). Then press <Cntrl><X>. See if it boots wthout loosing your screen.

If the screen goes blank, press <Cntrl><F4> and see if it toggles to vtty4 at a login prompt... If not then do the same as above, but replace all at and after "quiet splash" with "--- 3 --verbose debug drm.debug=0xe plymouth:debug "

While boting, pay attention to the displayed boot messages...

When you get to a login... Login with your credentials.

Run the UbuntuForums 'system-info' Script and post the URL of where the report uploads to a pastebin
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```

---

### Post by Tanarotte on 2023-07-02
UPDATE: Ubuntu lts works perfectly fine too

I have tested the boot command modification you sir have suggested. The only difference is my computer turns off the screen then restarts, instead of hanging for all eternity. 
During booting system displays like 2 seconds of incredibly fast scrolling wall of text, which i had to capture on camera to read as it moves too fast. It does look like normal boot messages, no mention of any failure 
to do something. This is quite puzzling to me. I am currently on nobara 38, working perfectly fine, killed many many demons today in D4 with no interruptions and yet ubuntu and debian of all things fails to even start a live cd. 

There doesnt seem to be other reports of such failures so it could be a *me* issue?, gpu bios incompatibility or something ? is there a way to make live cd write logs into lets say a different attached pendrive ?

---

### Post by MAFoElffen on 2023-07-02
Well, try this also...

At the start of the LiveUSB boot process there is a fsck and file verification process to check the integrity of the Livre Image on the LiveUSB. At default, I think going to a blank screen was a bad idea... and they should have rather at least shown a prompt of what is going on during that process, so the User doesn't mistakenly think something has gone wrong.

In another test, when the screen goes blank, press the <Arrow-Down> Key. This may bring up the underlying screen showing what may be going on. Then quickly press <Cntrl><C>. That should cancel that file check process.

Do that to see if that may be causing that blank screen being there. Which would mean it is doing normal things, but is causing that misunderstanding. That way, we can at least rule that out as a problem. 

That being blank during that process, is a common reported issue that causes misunderstandings (that there might be a problem, when there is none).

Next, if those boot options work, then use those to boot the installation media, then on your firs boot. While booted in that first session, then use them in your /etc/default/grub file in the GRUB_CMDLINE_LINUX_DEFAULT= line... Remember to use update-grub to pick up that change. 

Those kernel boot options will tell the kernel to use the amdgpu driver in the kernel, and fixes a common wake from suspend problem with AMD GPU's.

---

