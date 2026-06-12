---
title: "VirtualBox//ubuntu-10.04.1-desktop-i386 Boot Hang after Xorg.conf mod"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Aeneas32 on 2010-09-17
On a fresh install of this ubuntu-10.04.1-desktop-i386 OS under VirtualBox on Q6600//Windows Vista 64 Ultimate//6 GByte Sdram//ATI HD 4550// .
I found that there were only 2 resolution options: 800x600, 640x480.
I found a script through Google to increase the resolution choices which involved modifying the contents of xorg.conf to the following:
[FONT=Courier New]  Section “screen”
  Identifier “screen0”
  Device “Videocard0”
  DefaultDepth 24
  Subsection “Display”
  Viewport 0 0
  Depth 24
  Modes “1920x1200” “1680x1050” “1280x1024” “1024x768”
  EndSubSection
  EndSection[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]However, on the immediate reboot, the Ubuntu boot hung at the point that 5 red dots were displayed.[/FONT]
[FONT=Courier New]How can this sort of hang be cleared, short of reinstalling the whole Ubuntu OS ?[/FONT]
[FONT=Courier New]And what is wrong with this script ?[/FONT]
[FONT=Courier New][/FONT]

---

### Post by lukeiamyourfather on 2010-09-17
Install the VirtualBox additions and you get unlimited resolutions.

```
sudo apt-get install virtualbox-ose-guest*
```

Also see this.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by Aeneas32 on 2010-09-17
I installed something with a name similar to the Virtualbox Additions, which was in the pull down menu, and it gave me one extra resolution.
That was not enough, so I tried the xorg.conf script.
 
How does one clear the Hang, in order to reach that point.
I would like to clear the contents of xorg.conf back to the original empty state, and then try rebooting again, if a command line could be acquired.

---

### Post by lukeiamyourfather on 2010-09-17
> **Aeneas32 said:**
> I installed something with a name similar to the Virtualbox Additions, which was in the pull down menu, and it gave me one extra resolution.
That was not enough, so I tried the xorg.conf script.


Don't install something with a similar name. Install the guest additions using the exact command posted above. :)
 
> **Aeneas32 said:**
> 
How does one clear the Hang, in order to reach that point.
I would like to clear the contents of xorg.conf back to the original empty state, and then try rebooting again, if a command line could be acquired.

Usually there's a backup of the xorg.conf file. Change the names so the backup becomes the active configuration file. If there's no backup then it gets more complicated.

---

### Post by Aeneas32 on 2010-09-17
Again, how does one clear the Ubuntu boot Hang, short of reinstalling the whole Ubuntu Virtualbox ?
As I mentioned:
  [FONT=Courier New]on the immediate reboot, the Ubuntu boot hung at the point that 5 red dots were displayed.[/FONT]
[FONT=Courier New]How can this sort of hang be cleared, short of reinstalling the whole Ubuntu OS ?[/FONT]
[FONT=Courier New]And what is wrong with this script ?[/FONT]

---

### Post by lukeiamyourfather on 2010-09-17
> **Aeneas32 said:**
> Again, how does one clear the Ubuntu boot Hang, short of reinstalling the whole Ubuntu Virtualbox ?


That depends. What did the script do or what was it supposed to do? Any number of things could be hosed up. I'd try choosing an alternate menu item from GRUB. There's usually a "safe" option for each kernel that doesn't load extra kernel modules.

> **Aeneas32 said:**
> 
As I mentioned:
  [FONT=Courier New]on the immediate reboot, the Ubuntu boot hung at the point that 5 red dots were displayed.[/FONT]
[FONT=Courier New]How can this sort of hang be cleared, short of reinstalling the whole Ubuntu OS ?[/FONT]


There's not enough information to determine what is causing the issue. If it was me, I'd just install Ubuntu again on the virtual machine and start over.

> **Aeneas32 said:**
> 
[FONT=Courier New]And what is wrong with this script ?[/FONT]

Not sure, but it obviously didn't work. Installing the guest additions from the repositories is the way to go.

---

### Post by Aeneas32 on 2010-09-17
I see no alternate menu option under the VirtualBox//Ubuntu boot sequence.

---

### Post by lukeiamyourfather on 2010-09-17
Hold down shift when booting to get the GRUB menu.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

That might work, it might not. Somebody else might know how to fix it, but I'd probably just install Ubuntu again. Especially if it was a fresh install with no important data on it.

---

### Post by Aeneas32 on 2010-09-17
The Shift to Grub worked.
That allowed me to delete the erroneous contents of xorg.conf.
I ran that command in the Recovery mode.
I am now able to boot again, but I still see only one additional resolution in the System/Preferences/Monitors menu: 1360x768 .
Where are you seeing the other graphics options ?

---

### Post by lukeiamyourfather on 2010-09-18
> **Aeneas32 said:**
> The Shift to Grub worked.
That allowed me to delete the erroneous contents of xorg.conf.
I ran that command in the Recovery mode.
I am now able to boot again, but I still see only one additional resolution in the System/Preferences/Monitors menu: 1360x768 .
Where are you seeing the other graphics options ?

If you have the guest additions installed, just resize the window or go full screen. The Ubuntu guest will automatically resize to whatever the window size is. If you don't have the guest additions installed then this will not work.

---

### Post by Aeneas32 on 2010-09-18
That works.
It sounds like another example of the failure of Linux versions to properly document at least the critical usability issues.
Clearly, the developers could not care less whether anyone uses the product or not.
A list of the functions performed by the Additions executable should be listed somewhere prominent where you could not miss it.
 
I find whenever anything is entered into xorg.conf, the boot will hang.
For the Shift Key during Boot  to  Boot Safe Mode not to be documented, to escape from such a Boot Hang, should result in the Firing of at least 1 person.

---

### Post by lukeiamyourfather on 2010-09-18
> **Aeneas32 said:**
> That works.
It sounds like another example of the failure of Linux versions to properly document at least the critical usability issues.
Clearly, the developers could not care less whether anyone uses the product or not.
A list of the functions performed by the Additions executable should be listed somewhere prominent where you could not miss it.
 
I find whenever anything is entered into xorg.conf, the boot will hang.
For the Shift Key during Boot  to  Boot Safe Mode not to be documented, to escape from such a Boot Hang, should result in the Firing of at least 1 person.

The guest additions have nothing to do with Ubuntu. They are in the repositories for convenience (otherwise you'd have to compile them from the Oracle kernel module source). Oracle maintains VirtualBox and the guest additions. I'm glad its working for you now but if you had read how to use VirtualBox in the first place you would have saved lots of time and probably frustration.

[http://www.virtualbox.org/manual/ch04.html#id2656909](http://www.virtualbox.org/manual/ch04.html#id2656909)

Most virtual machine products have equivalent technology to guest additions that make using the virtual machine easier. If you're new to virtual machines in general then I suggest studying up and not putting the blame on the software.

---

### Post by Aeneas32 on 2010-09-18
The usage of Linux versions such as Ubuntu as a Guest OS subordinate to a Windows Host has become a norm in the industry.
The primary purpose of VirtualBox is to support Linux in this Windows environment.
I have found that Virtual_PC also works but since it is Microsoft, it probably not the first choice for the Linux family.
 
And Oracle is part of the Linux family and one can assume they collaborate daily with other Linux developers.
It is inexcusable for the 2 critical items I mentioned to be undocumented in an extremely visible manner.
The Linux world needs to get into the habit of Firing someone when this sort of hostility toward the user is exhibited.

---

### Post by lukeiamyourfather on 2010-09-18
> **Aeneas32 said:**
> 
The primary purpose of VirtualBox is to support Linux in this Windows environment.


That might be true come from the perspective of a Windows user. :roll:

> **Aeneas32 said:**
> 
It is inexcusable for the 2 critical items I mentioned to be undocumented in an extremely visible manner.


Just because you didn't read the documents doesn't mean its not documented.

> **Aeneas32 said:**
> 
The Linux world needs to get into the habit of Firing someone when this sort of hostility toward the user is exhibited.


Many open source projects use code from volunteers, what are you going to do? Fire the volunteers? I'm sorry there's no "wizzard" that requires only clicking buttons without reading. :-({|=

---

### Post by Aeneas32 on 2010-09-18
Actually, I believe that Grub is normally part of the Linux distribution.
Thus, Ubuntu bears the responsibility, if there is a Safe Mode, for ensuring the user booting the platform is aware how to enter into the Safe Mode before the Hang occurs.
The times I have installed Linux, Grub, amongst several other bootloaders, is a required selection.
 
Under Windows F8 is the command, but knowledge of this is not necessary because if the previous Boot crashes abnormally, the subsequent boot automatically starts up asking the user if he wants to enter Safe Mode, or Safe VGA mode, or last working registry, etc.
And clearly, when the user is forced to Reset VirtualBox when this Hang occurs, that prevents a normal termination from occurring.
 
And every time I have installed Windows or Linux which usually installs in a safe VGA mode like 800x600, the very first thing I did before installing device drivers or any other software is set the grahics screen resolution to whatever the max of the screen and graphics card can tolerate.
I cannot imagine anyone at Ubuntu not understanding that and ensuring that that process is streamlined.

---

### Post by lukeiamyourfather on 2010-09-18
> **Aeneas32 said:**
> 
I cannot imagine anyone at Ubuntu not understanding that and ensuring that that process is streamlined.

Look, Linux is not Windows and it never will be. You only knew the key to bring up the Windows boot loader options because you use Windows. Not like there's a label that says what key to press on the Windows disc or anything. Now you know that shift if the key for GRUB, why are you whining about it?

If you like the Windows boot loader so much, use it. You can boot into Ubuntu from the Windows boot loader, or any other boot loader for that matter.

---

### Post by Aeneas32 on 2010-09-19
Ubuntu should aspire to be better than Windows, which is definitely possible. They waste a huge amount of R&D money over there on absolute nonsense.
However the Windows people are really interested in the clearest high priority problems, like System Hangs.
They perform a simple check at the end of every system run and if it terminates normally, it sets a flag.
Thus, if when it next boots, it does not see that flag, it knows to present the user with recovery options.
For the user to be forced to reinstall the Ubuntu Linux operating system for such a multitude of boot hang causes, is a complete failure of r&d and software quality assurance.
When selling any operating system product, this sort of thing is expected by the customer.
All Ubuntu and other Linux sellers need to do is Fire the developers and software quality assurance workers responsible, at their companies, when core functionality like this is neglected.
Then suddenly, everything developed at those companies will dramatically improve.
No need to hire anyone additional.
It really works.

---

### Post by lukeiamyourfather on 2010-09-19
> **Aeneas32 said:**
> Ubuntu should aspire to be better than Windows, which is definitely possible. They waste a huge amount of R&D money over there on absolute nonsense.
However the Windows people are really interested in the clearest high priority problems, like System Hangs.
They perform a simple check at the end of every system run and if it terminates normally, it sets a flag.
Thus, if when it next boots, it does not see that flag, it knows to present the user with recovery options.
For the user to be forced to reinstall the Ubuntu Linux operating system for such a multitude of boot hang causes, is a complete failure of r&d and software quality assurance.
When selling any operating system product, this sort of thing is expected by the customer.
All Ubuntu and other Linux sellers need to do is Fire the developers and software quality assurance workers responsible, at their companies, when core functionality like this is neglected.
Then suddenly, everything developed at those companies will dramatically improve.
No need to hire anyone additional.
It really works.

Clearly you're missing the bigger picture here. This has turned into a Linux versus Windows discussion. Can someone move it to the recurring discussions forum?

---

### Post by Aeneas32 on 2010-09-19
> **lukeiamyourfather said:**
> Clearly you're missing the bigger picture here. This has turned into a Linux versus Windows discussion. Can someone move it to the recurring discussions forum?
Windows has nothing to do with the point I have been making.
You have continually raised the issue of Windows and I have stated that Linux versions should not use Windows as a yardstick.
You are beginning to sound like a desperate  software quality assurance/customer service  worker at Ubuntu.
This thread is in the correct forum and moving it would constitute  censorship.

---

