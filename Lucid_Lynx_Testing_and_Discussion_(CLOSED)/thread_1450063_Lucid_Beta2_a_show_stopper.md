---
title: "Lucid Beta2: a show stopper?"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-04-08
Hi,

I downloaded Lucid beta 2 i386 iso dated April 6/10 a short while ago. Rebooted my laptop.  Plymouth ran a while. The Install window shows 2 buttons: "Try Lucid" and "Install Lucid". I chose the latter, then I got a blank screen.  My laptop has ATI Radeon Xpress 200 M video card.

Any suggestions?

---

### Post by ajgreeny on 2010-04-08
Start again and use the "Try Lucid" button which will at least help you see if the OS will run on your hardware.  ATI is not always the most linux friendly, but you should check your card on the hardware compatibility web page, which seems to suggest it was supported in earlier versions of ubuntu.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

---

### Post by AlanR8 on 2010-04-08
So probably NOT a show stopper I think you'd agree.....

Let us know how you get on.

The community helps people out.

---

### Post by iClouseau88 on 2010-04-08
Hi,

Started again.  This time after Plymouth finished running I got only a blank white window where it is supposed to have language choices on the left hand column and the 2 buttons on the right pane, e.e. "Try Lucid" and "Install Lucid". I could not select any button because the screen went blank immediately. I also tried CTRL+ F2 to F7 but still a blank screen.

My laptop boots fine with Karmic Ubuntu 9.10.

---

### Post by emarkay on 2010-04-08
Did you have Lucid working OK previously - Beta 1 , Alpha?
FWIW did you power off your PC - a cold, hard reboot before booting the CD? 
Strange...
What make/model is the laptop; what are the hardware specs on it?

---

### Post by Lollerke on 2010-04-08
You must boot with pci=nomsi kernel option to be able to boot.
Here's the bug report for this problem (bug status is fix committed so in a couple of days this will be solved): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all)

---

### Post by iClouseau88 on 2010-04-08
Hi emarkay,

Lucid beta 1 did not work on my laptop but it did on my desktop PC which has an Nvidia video card.  This laptop  is Toshiba Satellite A110 with 2 GB RAM, 250 GB HD, ATI Radeon Xpress 200M video.

---

### Post by iClouseau88 on 2010-04-08
Hi Lollerke,

I cannot get onto a command line, so I cannot boot with pci=nomsi kernel option.

---

### Post by LADmaticCA on 2010-04-08
> **iClouseau88 said:**
> Hi Lollerke,

I cannot get onto a command line, so I cannot boot with pci=nomsi kernel option.

You shouldn't need a command line. Just press F6 when the live cd begins booting. It should take you to a menu. The pci=nomsi option may be under the F6 menu, if not I guess you could add it yourself.

*Edit* I happen to have this same graphics card on my laptop. I manually added pci=nomsi to the live boot options, it boots but everything is painfully slow, all graphics all rendering. If I boot the live cd without any options I just get a freeze when the desktop loads.

---

### Post by iClouseau88 on 2010-04-08
Hi everyone,

I tried everything including F6, but eventually have found a solution:

1. Load CD and reboot;
2. Hold LEFT SHIFT key for a while;
3. Screen asks:"Load boot in graphic mode?" Answer=n (No!)
4. Installer Boot Menu appears;
5. **IMMEDIATELY** press **TAB** key to edit:
6.  Add the following to the line "vmlinuz...":
"**vga=792 acpi=off noapic radeon.modeset=0**"
7. Plymouth splash screen appears with 5 dots changing to red;
8. Gnome Desktop appears, so select "Install Ubuntu 10.04", ENTER;
9. Follow screen prompts to select keyboard type, time, etc;
10. Select partition where Lucid will be installed, etc.

At this point I quit because partitioning menu does not allow me to add Lucid to an unallocated space on my HD, otherwise my existing Windows-Linuxes multiboot system would be hosed!

It took me several attempts to figure out the above. The key to avoid black or blank screens is Step 6. Install CD was found to be OK via a media check item of the Installer Boot Menu in a previous trial.

I hope this post helps others.

---

### Post by dcstar on 2010-04-09
> **iClouseau88 said:**
> 
.........
I hope this post helps others.

It might, but if you report it as a bug then it might get fixed so you can be sure it will help others.

---

### Post by danwood76 on 2010-04-09
This bug already has a fix released.

It will take a few days for it to make it into the kernel and it wont be in beta 2 (obviously) but will be in the final release.
You can wait until a new daily build comes out with the patch or wait until release day!

---

