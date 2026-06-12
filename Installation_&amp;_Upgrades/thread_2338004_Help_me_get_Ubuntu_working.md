---
title: "Help me get Ubuntu working"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by alaskan25 on 2016-09-23
Hey, Thanks for reading this post. Basically, I've got a Windows 10 OS as my primary OS, but I'm trying to learn about programming/ coding and everyone has recommended I use Ubuntu to get good with Linux. My problem is that I can't seem to get Ubuntu to run at all. I've partitioned my Hard Drive with more than enough space for another OS, I've downloaded Ubuntu 16.04 onto a DVD, I've changed my System Settings to boot from the disk, and I have tried to run Ubuntu without installing as well as tried to just install it. Every time it'll whir for a bit, make a bit of progress, and then the progress dots stop filling up. I get no sort of error report, and I've had the system run diagnostics on itself and it says it's fully functional, so there's no way the files are corrupted or anything like that. Can anyone help?
I forgot my system Specs! 
Processor: Intel(r) Core (TM) i7-6700HQ CPU @2.60 GHz
RAM: 16 GB
64-bit Operating System
Hope this helps!

---

### Post by newbie-user on 2016-09-23
I would suggest installing Ubuntu as a virtual machine first before trying to dual boot. It's generally safer that way. You could use Virtualbox, Vmware, etc. to set up the virtual machine.

But regarding your specific question, you may be able to see error messages by going to one of the terminals: Ctrl+Alt+F1 or some of the other Fkeys

---

### Post by ubfan1 on 2016-09-23
Or the Esc key to switch from the dot page to a text error message page.

---

### Post by oldos2er on 2016-09-23
What video card does your system have? Is it a laptop or desktop? If your system is UEFI you will need to disable Secure Boot, and disable Windows' fast boot option too. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Did you checksum the ISO before burning it to DVD?  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by alaskan25 on 2016-09-23
Alright, it's an Nvidia Geforce GTX on my laptop. It's UEFI. I think you've identified the problem. Yes, I did checksum the software before I burned it, checksum said it was good. I have disabled fast boot, but I did not disable secure boot. I'll try that and report back.

Edit: Tried your solutions. Disabled both Secure boot and Fast boot. Still nothing. :/

---

### Post by ubfan1 on 2016-09-24
Starting with the nomodeset, see what kernel parameters help the skylake:
Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1
i915.enable_execlists=0

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
Probably not needed for kernel 4.4 or later (16.04)

noveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by alaskan25 on 2016-09-24
I'm really sorry, but I'm not sure what any of that means. Am I supposed to enter that into some sort of command prompt or something? If so, how do I get there? I'm a total noob.

---

### Post by pride3 on 2016-09-24
Hey , I have the exact same problem : after I installed ubuntu os , I can't boot it shows a black screen with à underscore moving around à feu seconds then send me back to bois

I have a config close to yours, I saw amd64 everywhere during installation , is it normal as I have Intel ?

---

### Post by ubfan1 on 2016-09-24
Those options are to be entered onto the grub line that boots the kernel -- it starts with vmlinuz...  That line typically ends with the options "quiet splash".  Replace the quiet splash with them, one at a time, then in combinations.  Google for similar hardware (they all will have the same problems).  Edit the grub boot line by typing "e" at the grub menu to
edit the selected grub boot entry (instructions at bottom of page).  Edit the vmlinuz line and F10 or crtl-X to boot with those parameters.  When you fine those which work, you may make them permanent by editing them into  /etc/default/grub (look for the "quiet splash" and replace it or add next to it).

---

### Post by alaskan25 on 2016-09-24
Ok dude, I entered those commands into the grub line and tried those commands you told me to try to boot with those parameters and nothing happened. There was no "quiet splash", unless the quiet splash is that blinking underscore thing at the beginning of a command over which the stuff I type appears. You need to understand that I have taken one computer science course in my entire life, and it was Visual Basic run on Microsoft OS. It was hellish, that's why I'm trying to get into Ubuntu/Linux to actually learn programming. I think I'm going to try to run it as a virtual machine as the other guy suggested, as virtual machines are probably important to know my way around anyways.

Edit: Aaaaand it turns out I can only run VMWare for 30 days without paying for it. Since I need to have this for a long time, that's not an option. Great.

---

### Post by ubfan1 on 2016-09-24
About VMware, the vmplayer is free, so if you create the virtual machine with the 30 day free period, you can run it forever with vmplayer.  Virtualbox from Oracle is another way to run Ubuntu on a Windows VM, but I've had experience with neither on Windows.

The grub menu line to edit looks like (with different  UUID numbers of course):
   linux    /boot/vmlinuz-4.4.0-38-generic root=UUID=ec07926e-d28c-421b-a941-496cad10c44c ro  quiet splash $vt_handoff
You can get to the edit screen by typing e (to edit) instead of return (to boot) the menu choice.
The first thing to try is adding "nomodeset" to the line, and by removing the "quiet", you might see more error messages, or at least know how far into the boot process you get.

---

### Post by alaskan25 on 2016-09-26
Hey, so it let me get a little ways into the Ubuntu installation process, but it's hung up on the screen that asks where I am. It won't allow me to go any further with installation. What do I do now?
Edit: forgot to mention that your solution worked, for the most part. I am now further along in installing Ubuntu than I was before. But now this issue has arisen.

---

### Post by Roger_Williams on 2016-09-27
I second Virtualbox it's free and runs nicely as long as you can dedicate enough resources to the VM.

---

### Post by alaskan25 on 2016-09-28
Alright I've downloaded and run Virtualbox and it's running Ubuntu like a dream. Thanks for the advice,guys. I'm off to become a pro coder.

---

