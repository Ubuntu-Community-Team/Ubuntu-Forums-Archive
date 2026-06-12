---
title: "Live DVD 20.04.1 - only goes to wallpaper  ??"
date: 2020-10-27
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-10-27
This is on a HP Probook 4330s. I have previously had Kubuntu 19.10 on it, although it was a PITA to use, as the monitor was damaged. That is, trying to drive it with an external monitor and the plasma desktop would constantly give problems. Booting was always a challenge to catch it just in time. Anyway, decided to burn the Kubuntu 20.04.1 ISO onto a DVD as booting from USB on this laptop simply doesn't work.

After many tries at changing the BIOS to boot from the CD, it appears to be loading okay, for the live process.  However, I only see the wallpaper, the mouse can be moved, but clicking left or right buttons, nothing,  There is  no shortcut to 'Install ...".  There is no menu, no task bar, only the wallpaper ??

What is it waiting for ?

---

### Post by CelticWarrior on 2020-10-27
It is waiting for nothing.
The problem is that you're seeing the extended desktop in the external monitor and not the main part which is in the internal faulty one.

You can right-click anywhere > Settings. Then go the screens setting and disable the internal one.

Even better, repair it or buy a new one. Problem solved.

---

### Post by oygle on 2020-10-27
> **CelticWarrior said:**
> It is waiting for nothing.
The problem is that you're seeing the extended desktop in the external monitor and not the main part which is in the internal faulty one.

Yes, and that has been the problem when using an installed version.

> **CelticWarrior said:**
> You can right-click anywhere > Settings. Then go the screens setting and disable the internal one.

There is no Kubuntu installed on that hard drive, so right-click won't work. It's in an (almost) live scenario.

> **CelticWarrior said:**
> Even better, repair it or buy a new one. Problem solved.

That would be the best solution; I only have so much hair to pull out ..lol

Thanks for your help.  :)

---

### Post by CelticWarrior on 2020-10-27
> [COLOR=#000000]There is no Kubuntu installed on that hard drive, so right-click won't work. It's in an (almost) live scenario.[/COLOR]


Installed or "live" doesn't matter. It works in standard Ubuntu (Gnome).

---

### Post by oygle on 2020-10-27
As per my first post - >  the mouse can be moved, but clicking left or right buttons, nothing

---

### Post by oygle on 2020-10-27
So, this live 20.04.1 Kubuntu was waiting on something. Found out how to drop to shell, pressed Ctrl, Alt F2, it wanted a username and login. More searching, and I gave it "kubuntu" as username and just pressed ENTER on password. Now at least I can see some files. Usually there is an "install" on the desktop. This screenshot displays the contents of a file which I assume is the one. How do I execute that file ?

---

### Post by oygle on 2020-10-27
More searching and then ran ```
startx
``` from the terminal. Now I can see the 'Install  ..." on the desktop. Have tried several times to execute it from the desktop, or browse with Dolphin and then 'execute'. It does start to access the USB (ISO is on there) for a few seconds, but then nothing ? I have checked in system settings and the external monitor is the primary monitor. Any ideas where to look for errors, or how to execute the desktop file from the terminal please ?

---

### Post by oygle on 2020-10-29
I was hoping to simply execute that desktop file, and therefore sought help in another forum at [https://ubuntuforums.org/showthread.php?t=2452754](https://ubuntuforums.org/showthread.php?t=2452754) , but alas, no go.  :(

---

### Post by sudodus on 2020-10-29
The exec line contains the command

```

**ubiquity kde_ui**

```

This is the installer. If you run that command from a terminal window in graphics mode, it should work 'as intended'.

In text mode it might be difficult or impossible to run ubiquity. You can try without a parameter

```

ubiquity

```

but I don't think it will work without a graphical user interface.

[hr][/hr]
An alternative is to boot in **recovery mode** (selected at the grub menu). That way you might get a primitive but working graphic desktop environment, so that you can run the installer.

---

### Post by oygle on 2020-10-29
> **sudodus said:**
> The exec line contains the command

```

**ubiquity kde_ui**

```

This is the installer. If you run that command from a terminal window in graphics mode, it should work 'as intended'.

In text mode it might be difficult or impossible to run ubiquity. You can try without a parameter

```

ubiquity

```

but I don't think it will work without a graphical user interface.

I did try that. Here is what I had to do to get there...

* On boot from usb, only see the wallpaper, there is a mouse pointer, no task bar, no menus, the mouse moves, but left/right click do nothing. Then ...
* Ctrl, Alt F2, a login screen, enter 'kubuntu' as username and enter on password. So now I'm at terminal. Then "startx", same as before only wallpaper, but mouse has left/right options. Screen flickers and jumps for a while ....
* Now a taskbar and a KDE icon for the menus, plus the icon to "Install Kubuntu ..". Select that, nothing happens other than the usb light flickers for a few seconds.

Drop down to Terminal ..

```

**ubiquity kde_ui**

```

a msg that "Ubiquity is already running"..

> **sudodus said:**
> An alternative is to boot in **recovery mode** (selected at the grub menu). That way you might get a primitive but working graphic desktop environment, so that you can run the installer.

The grub menu doesn't appear though, there is no OS on the HDD either. I never see the usual options like "Try" or "install". Would I be better to try the "live/persistant" option in ```
mkusb
```

Assuming the USB has the correct 20.04.1 on it (the latest), then is there a simple method to copy the ISO contents onto the HDD ?

...Later on .. pressed Shift just after BIOS display, no "recovery mode" option, but there was an option to run from terminal. Now it has come up with the "Try" or "Install", so installing now ... hopefully

---

### Post by CelticWarrior on 2020-10-29
> [COLOR=#000000]* Ctrl, Alt F2, a login screen, enter 'kubuntu' as username and enter on password. So now I'm at terminal. Then "startx", same as before only wallpaper, but mouse has left/right options. Screen flickers and jumps for a while ....[/COLOR]
[COLOR=#000000]* Now a taskbar and a KDE icon for the menus, plus the icon to "Install Kubuntu ..". Select that, nothing happens other than the usb light flickers for a few seconds.[/COLOR]

[COLOR=#000000]Drop down to Terminal ..[/COLOR]

[COLOR=#000000]Code:
**ubiquity kde_ui**[/COLOR]
[COLOR=#000000]a msg that "Ubiquity is already running"..[/COLOR]

[COLOR=#000000][I]
[/I]
[/COLOR]


If it says it's already running then it is **on the other screen**, reason why - again - you aren't seeing it. 
First thing to do when you have access to the settings is to disable the internal monitor, as already suggested.

---

### Post by oygle on 2020-10-29
> **CelticWarrior said:**
> If it says it's already running then it is **on the other screen**, reason why - again - you aren't seeing it. 
First thing to do when you have access to the settings is to disable the internal monitor, as already suggested.

By default, the internal monitor is not enabled. Have been able to get past that stage, and do an actual 'Install", yet on reboot, it says no OS on the Hard drive. Have done the 'Install" twice now, and in the partition setup, there was a 1 Mb free space right at the start of the drive. I could not get rid of it ??  The other day, a HDD reformat was done from the BIOS level, and maybe that 1 Mb at the start is some sort of boot loader that is interfering with this process ?  Possibly HP have some need for it, but not *nix ?

Ceratinly a reformat of the HDD with some sort of *nix tool may help. DBAN or similar.

---

### Post by oygle on 2020-10-29
Have now had a successful installation. The ```
fdisk
``` to reformat the hard drive was obviously what was needed. Some sort of boot sector garbage ??

> $ sudo parted -l  
[sudo] password for **********: 
Model: ATA Hitachi HTS72755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32        boot
 2      539MB   500GB  500GB  extended
 5      539MB   500GB  500GB  logical   ext4


The install has created a 537 Mb fat32 partition as the boot. Is that standard ? I'm used to seeing EXT4 for all partitions. Thanks everyone for your help. Just making myself a note for when the next install is done on this old laptop with a broken screen.

****  At the USB boot, press Shift to see the options, and select the 'Text graphics' option.  ****

---

