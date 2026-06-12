---
title: "Keyboard not working once I log into 22.04"
date: 2022-10-15
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-10-15
This problem occurred this afternoon (US EDT).  I was working in LibreOffice writer, and suddenly the keyboard on my DELL Precision 7720 stopped working.  Mouse still worked.  Logged off and rebooted into Win 11, and everything works fine.  Logged out of Win, and started Ubuntu in recovery mode.  Keyboard worked fine, and no errors with any of the commands in the recovery mode.  Went back to normal login in.  Ubuntu accepts my password from keyboard entry, but once logged in, keyboard entry has no effect.  On screen keyboard doesn't show.  I also tried a known good USB keyboard and rebooted.  It took login password from USB keyboard, and nothing else.  Mouse is working fine.

Also, went to terminal operation in recovery mode and did sudo apt update and sudo apt upgrade.  Installed upgrades and rebooted, but problems remained.  Have three other PCs on my desk, so not lost and current client work requires Windows, so I am far from being out of action.

I am using the Unity desktop build of 22.04.

What steps should I take to fix this problem?

Thank you,

John

---

### Post by TheFu on 2022-10-15
Sometime in the last 2 months, there was an issue with nvidia GPU drivers screwing with keyboards, I vaguely recall.  Might search for those issues in these forums to see what the solution was for them - assuming you have and nvidia GPU.

Otherwise, IDK.  I'm seeing issues with a 20.04 system, freshly installed last month and the keyboard an mount gaining and losing connectivity over and over and over and over constantly.  I have a KVM switch and this issue is only happening with 1 computer of the 4 connect to it.  The problem computer doesn't have an nVidia GPU.  
There have also been keyboard issues with Wayland.  Try using Xorg at login. Perhaps that will fix it?

On my systems, 
If I directly connect the keyboard to the computer (front USB port) the problem doesn't happen.  
I need to test if the USB cable from the computer to the KVM is good. It might not be.
I need to test if the specific port on the KVM switch for the computer is good. It might not be.
I need to test if a different USB port on the computer in the back will work instead.  The current port might not work.

As with most hardware issues, the process is to simplify, exclude, test, then repeat until the exact component that failed is isolated.  Standard troubleshooting stuff.  Hopefully, describing my process will help you.

---

### Post by cigtoxdoc on 2022-10-15
Thank you very much.  Based on the information provided by Win 11 device manager, video is nVidia Quadro P3000 30.0.15.1363.  Win 11 just updated to that driver today.  The Linux equivalent driver downloaded as NVIDIA-Linux-x86_64-520.56.06.run .  I had to download to a directory on one of my exfat partitions.  So, all I think I need to do is boot into the recovery mode, go to the directory where the run file is located, do a chmod +x for the run file and then ./filename.run .  Will that do it, or do I need to copy the run file back into my home directory?

John

---

### Post by cigtoxdoc on 2022-10-15
I downloaded the new driver and installed it.  Unfortunately, it did not fix the problem.

---

### Post by TheFu on 2022-10-15
> **cigtoxdoc said:**
> I downloaded the new driver and installed it.  Unfortunately, it did not fix the problem.

In Ubuntu, you should never go to the GPU drivers website and use anything from them.  Always use the package manager to get proprietary drivers through Ubuntu.  These are specifically tested to work with the kernels Canonical builds and for other things specific to the different Ubuntu desktops. 

I prefer to use the 'ubuntu-drivers' tool myself, but there is a GUI program that does the same thing. Sorry, I don't know the name. It is probably in a menu on stock ubuntu systems, somewhere.

Did you search the forums as suggested?

---

### Post by cigtoxdoc on 2022-10-16
Thank you for your advice.  Unfortunately, Ubuntu does not always have the nVidia driver that is needed.

One piece of evidence I listed was that the on-screen keyboard did not show even though On-screen keyboard was turned on.  I checked another PC running 22.04, and the on-screen board works as expected.

My next step as suggested on another forum was to use a Ubuntu Live thumb drive

John

---

### Post by TheFu on 2022-10-16
> **cigtoxdoc said:**
> Thank you for your advice.  Unfortunately, Ubuntu does not always have the nVidia driver that is needed.
 

Then you probably don't want that driver.  It is unsupported or has known issues.
Did you ever check that Xorg was being used, not Wayland?

---

### Post by cigtoxdoc on 2022-10-16
After much troubleshooting, I found the only culprit being the "Slow Keys" setting under Universal Access had been turned on.  Solution was to turn it off.  Part of my troubleshooting efforts was to run the PC from a Live Ubuntu Unity 22.04 thumb drive.  This showed that the keyboard worked correctly.  However, the on-screen keyboard did not work.  The Universal Access functions appear not to work until the login password is entered.  When I pulled up a blank LibreOffice document after making sure the video drivers were correct, I pushed hard on the several keys and all of a sudden, I was getting text entered into the document.  That is when I looked at the "Slow Keys" setting.  Once I turned that function off, everything went back to normal.  How "Slow Keys" got turned on is a mystery.

John

---

### Post by cigtoxdoc on 2022-10-16
After much troubleshooting, I found the only culprit being the "Slow Keys" setting under Universal Access had been turned on.  Solution was to turn it off.

John

---

### Post by cigtoxdoc on 2022-10-16
After much troubleshooting, I found the only culprit being the "Slow Keys" setting under Universal Access had been turned on.  Solution was to turn it off.

John

---

### Post by TheFu on 2022-10-16
> **cigtoxdoc said:**
> After much troubleshooting, I found the only culprit being the "Slow Keys" setting under Universal Access had been turned on.  Solution was to turn it off.

John

There are 2 different places for input (keyboard/mouse) stuff. They are separate because the GUI isn't part of the OS and it is just another program.

1 is for the console.
2 is for the display server - i.e. X/Windows or Wayland.

Both need to be modified to work for console and GUI.  In X/Windows, there a keyboard map file and some way to deal with specific configurations.  I suspect that's what the DEs do ... but if you change to a different DE, then those settings won't come along.  I know next to nothing about how Wayland works and suspect it requires the DE settings to control anything, but I don't really know.

---

### Post by sachithnalaka on 2023-07-31
Hi

I am having the same issue, but slow keys are not enabled. Any suggestion?
[https://ubuntuforums.org/showthread.php?t=2489449](https://ubuntuforums.org/showthread.php?t=2489449)

---

