---
title: "MP-BIOS bug: 8254 timer not connected to IO-APIC"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by mousejunkie on 2007-05-21
I'm trying to install Ubuntu Studio. After selecting install Ubuntu Studio from the first menu, I get the error message:

MP-BIOS bug: 8254 timer not connected to IO-APIC

before it goes to the next menu where I select the language (or was it location).

I did not proceed beyond that because I thought I should see what this is about before installing.

I followed the fix in [http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355) and added the noapic option

But when I hit enter after that, I get the following message and it just hangs:

ACPI: SCI (IRQ21) allocation failed
ACPI: Unable to start the ACPI interpreter

I don't want to install if it starts off with an error message that might give  me problems later.

I've got a laptop so there's not much that can be done in the BIOS and I have the last available BIOS update.

---

### Post by mousejunkie on 2007-05-24
I installed anyway. The error still appears during boot but the system starts up.

I added the noapic option in menu.lst, and now the error message is gone but it hangs at the screen with the loading bar at 1 1/2 segments and only reacts to the power off button.

Now  have to manually remove the noapic option during boot (every time until I edit menu.lst again probably) to start the system. The error message then returns during boot, but the system starts.

Considering the speed at which post are generally replied to here, I guess this a tough one :( . I'll be happy for any hint, like :"Read up on that and then look at this" :)

---

### Post by vbmds on 2007-05-24
I have exactly the same error for both ubuntu and kubuntu installations (7.04).

---

### Post by mousejunkie on 2007-05-25
No more error message and system boots fine now. Instead of noacpi (or was it noapic) I had to use acpi=off.

Following change made to menu.lst :

# defoptions=quiet splash** acpi=off**

Now I just have to hope that I don't run into any other problems because it's off :D

...so many more questions... so much more to read

---

### Post by bubbjane on 2007-05-30
This is a problem with Southbridge settings, not ACPI itself.  You can leave ACPI on. Just navigate to your Southbridge settings in BIOS setup, find the control for ACPI HPET and turn it off.  ACPI will maintain its basic functions and your install won't hang up.

---

### Post by GIZ2008 on 2007-07-27
I had the same error installing ubuntu 6.06 LTS on Proliant ML370 G2.
In the BIOS I disabled the two PCI Wide Ultra3 SCSI Controllers since I am only using the Smart Array 221 Controller.  Didn't see options for the SouthBridge.

---

### Post by evilc on 2007-07-30
I have just tried to install Feisty on Toshiba A100 laptop, now getting this 8254 error. Have tried these suggestions but just hangs on startup when acpi added to grub?
Has anyone had any luck fixing this as I can't tell my friend (laptop owner) Ubuntu won't work. (have converted him to linux :))

---

### Post by sfmdk on 2007-08-04
> **bubbjane said:**
> ... can leave ACPI on. Just navigate to your Southbridge settings in BIOS setup, find the control for ACPI HPET and turn it off. ...

That worked for me, with an ASUS M2N-MX motherboard. Thanks a lot, would never have guessed that one, wonder how you did!

---

### Post by faby on 2007-08-08
> **bubbjane said:**
> This is a problem with Southbridge settings, not ACPI itself.  You can leave ACPI on. Just navigate to your Southbridge settings in BIOS setup, find the control for ACPI HPET and turn it off.  ACPI will maintain its basic functions and your install won't hang up.

This solution worked for me too on a ASUS M2N-MX motherboard!!! Thanks to Bubbiane for the great tip...

I really want to  contribute on getting rid of this bug  for the  above-mentioned motherboard. 
This is what i experienced about it....
before of all:
***** my system *****
   motherboard - ASUS M2N-MX Bios Version V0112 (the first and oldest BIOS for this device);
   CPU - AMD Athlon 64 X2 Dual Core Processor 4200+
   RAM - 1 GB DDR - Dual Channel - 533 MHz
   HD - Sata - 80 GB
   DISPLAY Controller: Nvidia Geforce 6100 (integrated on the motherboard)

and then:
**** my problem *****
Ubuntu live CD freezes during startup with apparent monitor/display controller/X server problems; tried any version of Ubuntu/Kubuntu Desktop (Live) CD: 6.06.1 (Dapper), 7.04 (Feisty), 7.10 (Gutzy - tribe 2), also for differents architectures (i386/AMD 64); no result!!!

...tried a different distro (Knoppix 5.1.1 Live CD); same problem: system hangs on boot;
...tried Knoppix 5.1.1. with special boot option: "knoppix acpi=off"...luckly the system starts with no problems!!!

...not so lucky using the same boot option on Ubuntu ("acpi=off"): system hangs displaying a blank Gnome desktop without any icon or menu; no virtual console, nothing of usable...

**** Solutions ******
- the first, and fastest solution (strictly refferred to the V0112 motherboard BIOS Version!):
Get In to the BIOS Setup (...naturally of the motherboard), menu "Power", item "ACPI APIC Support", select it and set it to "Disabled"; save changes and exit from setup (...F10 key)

All Ubuntu Live CD's now boot normally without any special boot option!!!

- the second, and a little bit complicated, solution (i followed this one...): 
download the latest motherboard BIOS Firmware from [http://support.asus.com](http://support.asus.com) (actually version 0804) and the related bios update utility (actually Afudos v. 2.21);
put the downloaded uncompressed files on a bootable floppy disk (Dos boot disk) and use them to update (flash) the motherboard BIOS (instructions on how to do this are present on the txt file accompanying the afudos.exe file);

after the update, and the subsequent BIOS reconfiguration, i experienced the following situations:
- Ubuntu Live CD for AMD 64 bit architecture startup with no problem and without any special boot option (...tried Ubuntu/Kubuntu 7.04 Desktop CD's);
- Ubuntu Live CD for i386 architecture startup only with special boot option "noapic" (...tried Ubuntu/Kubuntu 6.06.1 LTS and 7.04 Desktop CD's); without the above mentioned option boot process hangs indicating the same error: MP-BIOS bug: 8254 etc...

..tried again the bubbiane tip and exactly:
got in to the BIOS Setup, this time on the menu "Advanced" (not present in the old bios firmware), item "Chipset", Sub item "Southbridge Configuration", Sub-sub item "MCP61 ACPI HPET TABLE", selected and setted it to "Disabled"; finally exited from setup saving changes.

With this new BIOS configuration Ubuntu Live CD for i386 architecture startup with no special boot option (..just like using Ubuntu Live CD's for AMD 64 bit architecture) and the error message reported in this forum disappear..

Installation process succeded with no problems at all (actually i used only Ubuntu CD for AMD 64 bit architecture!!).

hope to be helpful...

---

### Post by jonah1980 on 2007-11-04
ok i also have this error, i tried turning off acpi in bios but then gutsy wouldn't boot at all, and i can't see anything about acpi hpet in my bios, altough my award bios seems to have loads of options, how can i fix this. i also have a kernel alive   kernel direct mapping tables up to 1300000000@8000-e000 message on boot also, is this related??

---

### Post by Tonny Hooijer on 2007-12-27
ASUS M2N Beta Bios 0804 here.

Problem solved:

"got in to the BIOS Setup, this time on the menu "Advanced" (not present in the old bios firmware), item "Chipset", Sub item "Southbridge Configuration", Sub-sub item "MCP61 ACPI HPET TABLE", selected and setted it to "Disabled"; finally exited from setup saving changes."

Just found out myself, but read this forum and shared my findings....

:)

---

### Post by juanManuel2007 on 2008-01-22
how to get through bios set-up?, help

I will try to disable the southbrige, my computer also hangs up because of such error, ms bug

The computer's BIOS is Phoenix M550SE/M660SE Rev. 1.00.06. The only advanced settings available are- 
Installed O/S [Other] WinXP/Vista
Legacy USB Support [Enabled] Disabled
Reset Configuration Data [Yes] No
frame Buffer Size [256MB]
__________________

---

### Post by Partyboi2 on 2008-01-23
depending on what system you are running is to what key needs to be pressed at boot to enter the bios
here is a list of some keys to try
[INDENT]     [B]Delete 
      F1
      F2
      F3
      F5
      F10
      Escape
      Insert
      Control + Escape
      Alt + Escape
      Control + Alt + Escape
      Control + Alt + Enter [/B]
   [/INDENT]

---

### Post by Partyboi2 on 2008-01-23
For a Phoenix try
 F1
 F2
Ctrl+Alt+Esc
Ctrl+Alt+S
Ctrl+S
 Ctrl+Alt+Ins

---

### Post by juanManuel2007 on 2008-01-23
The computer's BIOS is Phoenix M550SE/M660SE Rev. 1.00.06. The only advanced settings available are- 

Installed O/S [Other] WinXP/Vista
Legacy USB Support [Enabled] Disabled
Reset Configuration Data [Yes] No
frame Buffer Size [256MB]

do you think the bios is out dated, but this was dated may 5 of 2007
I read some of the forum on other site, they are saying that phoenix bios now are making such chip to block other Operating system other than Windows Vista, is this true?

I dont see anything on bios set up, except the advance above, and date,version,save, hardrive,cd rom.

wait after the above unresolved problem, it goes to the logo
 
The details of my computer are- 
Intel Pentium Core solo T1300 2MB Cache 1.6GHz 667MHz FSB
VIA p4m900 + VT8237A ( clevo m550se/m660se)(vt6363A)(phoenix bios version 6)
2GB DDR2 memory
80GB SATA HD

I select "Start or install Ubuntu" 
The Linux Kernel loads 
An error messages is quickly displayed, something about "Failed to allocate mem resource" with some numbers. 
The Ubuntu screen appears with the moving horizontal bar. 
It then goes through the settings, starting at "Setting preliminary keymap" to "Starting Gnome display manager". 

The following error messages appear during this process- 
* Loading hardware drivers...
modprob: WARNING: Error inserting iw1wifi_rc80211_simple (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iw1wifi/mac80211/origin/ne t/mac80211/iw1wifi_rc80211-simple.ko): Unknown symbol in module, or unknown parameter (see dmesg)

* Configuring net work interface...
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios version: No such file or directory
There is more hard disk activity with a blank screen before the screen displays some unintelligible writing at the top with wide horizontal blue and white lines below. 
The screen goes blank with more hard disk activity. 
All disk (HD & CD) activity stops and the computer freezes with the only redress being to push the power button to turn it off. 
What can I do?

---

