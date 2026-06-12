---
title: "Freezes during installaltion - Help"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by rbscairns on 2007-12-12
This is my first time at trying to install Linux. I am trying to install Ubuntu on my new laptop using the ubuntu-7.10-desktop-i386.iso imaged burned to a CD. I checked the burned CD (all OK).

The details of my computer are-
[INDENT]Intel Pentium Dual-Core T2130 1MB Cache 1.86GHz 533MHz FSB
VIA VN896 + VT8237A
1GB DDR2 memory
90GB SATA HD[/INDENT]
[LIST=1]
[*]I select "Start or install Ubuntu"
[*]The Linux Kernel loads
[*]An error messages is quickly displayed, something about "Failed to allocate mem resource" with some numbers.
[*]The Ubuntu screen appears with the moving horizontal bar.
[*]It then goes through the settings, starting at "Setting preliminary keymap" to "Starting Gnome display manager". 

The following error messages appear during this process-
[INDENT]* Loading hardware drivers...
modprob: WARNING: Error inserting iw1wifi_rc80211_simple (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iw1wifi/mac80211/origin/net/mac80211/iw1wifi_rc80211-simple.ko): Unknown symbol in module, or unknown parameter (see dmesg)

* Configuring net work interface...
cat: /var/lib/acpi-support/system-manufacturer: No such file or directory
cat: /var/lib/acpi-support/system-product name: No such file or directory
cat: /var/lib/acpi-support/system-version: No such file or directory
cat: /var/lib/acpi-support/bios version: No such file or directory[/INDENT]

[*] There is more hard disk activity with a blank screen before the screen displays some unintelligible writing at the top with wide horizontal blue and white lines below.
[*]The screen goes blank with more hard disk activity.
[*]All disk (HD & CD) activity stops and the computer freezes with the only redress being to push the power button to turn it off.
[/LIST]
What can I do?:confused:

Must I just return to the MS OS?

---

### Post by src2206 on 2007-12-12
1. Did you checked the CD using the inbuilt Checking system?

2. Please check in your BIOS setting whether you have Virus Protection enabled. That sometimes causes this type of errors. In case you have some type of Write Protection/ virus protection enabled in BIOS, disable that and try again (provided you have an assertive response to my first question :) )

---

### Post by rbscairns on 2007-12-12
1.  Yes. All reported as OK.

2.  There does not appear to be any settings in the BIOS for either write or virus protection.

The computer's BIOS is Phoenix M550SE/M540SE Rev. 1.00.06. The only advanced settings available are-
[INDENT]Installed O/S   [Other] WinXP/Vista
Legacy USB Support   [Enabled] Disabled
Reset Configuration Data   [Yes] No
frame Buffer Size   [256MB][/INDENT]

---

### Post by src2206 on 2007-12-13
Try this:

Create two **unformatted free space/ partition in the HDD** you want to install Ubuntu. One larger (at least 8GB and one smaller about 500 MB). The larger one is for main installation and the smaller one is for SWAP. You may use Free Partition Manager like GParted (look at my sig for a guide). 

Now during installation of Ubuntu, choose manual partitioning and choose to mount the root file system in the Larger free space and SWAP for the smaller free space. Now install Ubuntu.

BTW, if you are having any M$ OS on your PC, I would suggest that you install the GRUB in a floppy. Just choose Advance button while installation setting confirmation appears.

---

### Post by rbscairns on 2007-12-16
> **src2206 said:**
> Try this:
.... 

Now during installation of Ubuntu, choose manual partitioning ....
I wish I could, however the Ubuntu installation does not progress to such an option. The system freezes before that option becomes available.

---

### Post by src2206 on 2007-12-16
Did you try GParted? Can you force Ubuntu to use VESA video driver while booting?

---

### Post by Partyboi2 on 2007-12-16
Not sure what speed your burnt the iso to disk at, but try at a low speed like x4 If you havent done so already.
You could also try using the alternate Cd. Which is a text base installer and see if that works.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

---

### Post by juanManuel2007 on 2008-01-22
Same problem with me

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
What can I do?:confused:

My first time

cd check - ok

---

### Post by rbscairns on 2008-01-22
After days of trying, including all of the above suggestions, the same kept on happening. I have returned to the MS OS for now. I am taking my laptop with me to the Philippines where I have a friend who claims to be a ubuntu "expert". He is going to see if he can get the OS to install.

Until then, MS is it:mad:

---

### Post by juanManuel2007 on 2008-01-22
wait before the installation there was a ms bug acpi appears

the others who come with this, they disable the southbrige controller on acpi

how do I get there:confused:

The computer's BIOS is Phoenix M550SE/M5660SE Rev. 1.00.06. The only advanced settings available are- 

Installed O/S [Other] WinXP/Vista
Legacy USB Support [Enabled] Disabled
Reset Configuration Data [Yes] No
frame Buffer Size [256MB]

---

