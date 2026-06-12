---
title: "Maverick: black screen during boot after mobo change"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by XEtedBear on 2011-12-19
In an attempt to evade a regular kernel freeze  with my Maverick system I just swapped the motherboard. Original: Asus K8V-VM; replacement Abit A8V. The north and south bridges are identical; I think the only substantial difference (aside from BIOS) is in the LAN hardware. I made no other changes.

grub menu is presented a previously, but boot does not complete: the system hangs with a  blank/black screen. I have the impression that the boot process cannot find the boot device - but Gparted displays it exactly as I suspect - with the uuid that grub is trying to use.

How do I find out what the failure is caused by?

---

### Post by 2F4U on 2011-12-19
I would start by removing the "quiet splash" from the grub kernel parameters, so that maybe we can see an error message. Other thing to try is if you can get into a virtual console by using Ctrl-Alt-F1/F2. If this works, you can try to login and take a look into the system logs.

---

### Post by XEtedBear on 2011-12-19
I tried this, using the 'e' option on the grub menu, deleting these options and then using Ctrl-X to boot (no option to save the edits - right?). I saw a few lines of diagnostic/logging info flash by but then, almost immediately, the blank screen.

---

### Post by MAFoElffen on 2011-12-19
> **XEtedBear said:**
> I tried this, using the 'e' option on the grub menu, deleting these options and then using Ctrl-X to boot (no option to save the edits - right?). I saw a few lines of diagnostic/logging info flash by but then, almost immediately, the blank screen.
Do again, except, instead of just deleting "quiet splash"... replace it with the text" --verbose text".

It should turn on verbose messaging, and yes it will scroll off the screen. No worries.  Use the hotkeys <shift><page up> and <shoft><page down> to scroll through the messages to read them.

If that stopped somewhere before a login prompt, then there was a problem in the kernel or other modules in the base system. Networking and other hardware drivers and firmware are part of that base system. 

If it got to a login prompt, then your problem is in the desktop manager or XServer.

If you can boot into the Live Image of a 10.10 LiveCD... If the above test stopped before a console login, post the installed sys'es /var/log/syslog.  If the above test got to a console login, please post your installed sys'es /var/log/Xorg.0.log.

Tell me how it goes.

---

### Post by TREESofRIGHTEOUSNESS on 2011-12-19
I have a similar issue with 10.10.  Lucid (10.04) works perfectly... but I have to use acpi=off to boot into Maverick.  You might try a live CD of Lucid to see if it boots (if trying the liveCD of maverick wont)
Here are some Kernel boot parameters
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
if it is a Kernel issue please boot into that system and file a bug
```
ubuntu-bug linux
```

---

### Post by XEtedBear on 2011-12-19
I tried the '--verbose text' option - the behaviour was identical to that reported in my previous post. This suggests to me (but what do I know?) that the problem is associated with the display configuration. I have an nVidia Quadro NVS 280 - which Linux sees as an nVidia FX5200 - with 2 screens. Is there a possibility that the kernel cannot correctly drive this hardware before the X-system is loaded? (No, that can't be right- I see about  a page of logging info before the displays go blank).

Is there any point in grabbing the log files you mention before I can get to a command prompt?

---

### Post by MAFoElffen on 2011-12-19
I need some other info/clarification from you...

You said you replaced an Asus K8V-VM with an Abit A8V. 

- The ASUS has onboard S3 Graphics UniChrome Pro IGP, then a PCIEx16, PCIEx1 and 2 PCI slots.

- The Abit has an AGP 4x/8x and 5 PCI slots, with no onboard graphics...

It's obvious to me from those specs, that whatever you used for graphics on your original board has changed, unless you were using a PCI graphics card.  

*** What are you now using for graphics?

---

### Post by XEtedBear on 2011-12-19
Ah, now the story gets interesting: I tried to run 10.10 from Live CD (the one I installed from). After the system has presented me with the option to Try Ubuntu or to Install it (I chose 'Try'), the system hangs with a screen full of msgs of which I  notice:
"* Stopping System V runlevel incompatibility
 <elapsed time counter> BUG: unable to handle kernel null pointer dereference at 00000028"

there follows a lot of logging info, and the system stops with this last entry displayed:
" <elapsed time counter> [drm] nouveau 0000:01:00.0: Output DVI-I-2 is running on CRTC 1 using output B"

Does this tell you anything helpful?

---

### Post by XEtedBear on 2011-12-19
> **MAFoElffen said:**
> I need some other info/clarification from you...

You said you replaced an Asus K8V-VM with an Abit A8V. 

- The ASUS has onboard S3 Graphics UniChrome Pro IGP, then a PCIEx16, PCIEx1 and 2 PCI slots.

- The Abit has an AGP 4x/8x and 5 PCI slots, with no onboard graphics...

It's obvious to me from those specs, that whatever you used for graphics on your original board has changed, unless you were using a PCI graphics card.  

*** What are you now using for graphics?

Ooops, Not quite correct. My error (too many bits of hardware lying around). I replaced Asus A8V with Abit AV8 (I just checked both motherboards to be sure that I have the model numbers correct) 

The I/O slots are - as far as I can see - identical. I'm using the same nVidia Quadro NVS 280 card. Sorry for confusion.

---

### Post by XEtedBear on 2011-12-19
> **MAFoElffen said:**
> I need some other info/clarification from you...

You said you replaced an Asus K8V-VM with an Abit A8V. 

- The ASUS has onboard S3 Graphics UniChrome Pro IGP, then a PCIEx16, PCIEx1 and 2 PCI slots.

- The Abit has an AGP 4x/8x and 5 PCI slots, with no onboard graphics...

It's obvious to me from those specs, that whatever you used for graphics on your original board has changed, unless you were using a PCI graphics card.  

*** What are you now using for graphics?

Ooops, Not quite correct. My error (too many bits of hardware lying around). I replaced Asus A8V with Abit AV8 (I just checked both motherboards to be sure that I have the model numbers correct) 

The I/O slots are - as far as I can see - identical. I'm using the same nVidia Quadro NVS 280 card. Sorry for confusion.

---

### Post by XEtedBear on 2011-12-19
> **TREESofRIGHTEOUSNESS said:**
> I have a similar issue with 10.10.  Lucid (10.04) works perfectly... but I have to use acpi=off to boot into Maverick.  You might try a live CD of Lucid to see if it boots (if trying the liveCD of maverick wont)
Here are some Kernel boot parameters
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
if it is a Kernel issue please boot into that system and file a bug
```
ubuntu-bug linux
```

Sorry, I missed you post. Thanks for this pointer. I notice that my boot options already set acpi=off, so I changed it to acpi=force - and the system has taken me to a command prompt asking me to login.

If I login with the usual details the system hangs - for a while trying to doing something with eth0 and fails (no surprise: the hardware is different) displays a lot of trace info and then hangs.

How do I update the network cards drivers?

---

### Post by MAFoElffen on 2011-12-19
> **XEtedBear said:**
> Ooops, Not quite correct. My error (too many bits of hardware lying around). I replaced Asus A8V with Abit AV8 (I just checked both motherboards to be sure that I have the model numbers correct) 

The I/O slots are - as far as I can see - identical. I'm using the same nVidia Quadro NVS 280 card. Sorry for confusion.
That's what I thought (and was leading to)...

Boot and after the BIOS Messages, hold down shift key... The Grub menu should appear. Use "nomodeset" as a kernel boot option, using these instructions:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

After it boots, go to System > Administration > Hardware Drivers > Install the nVidia driver that has recommended next to it.

Tell me how it goes.

---

### Post by XEtedBear on 2011-12-20
This all worked fine up to the point of selecting Hardware Drivers (actually 'Additional Drivers' on my system). I was able to select this option but there was no output. The same happens on every other application I tried to invoke in System or Preferences or Applications. After a number of attempts the top bar menu disappeared and the system was not responsive to any keyboard//mouse activity. The only effective option was to power off.

---

