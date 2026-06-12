---
title: "8254 timer not connected to IO-APIC"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by evilc on 2007-07-30
I have just tried to install Feisty on Toshiba A100 laptop, now getting this 8254 error. Have tried various suggestions (including bios update) but it either hangs on startup or  nothing changes when acpi added to grub? I am now trying the add **acpi=off** to grub.lst the warning still shows up but will see if anything changes over time.
Has anyone had any luck fixing this as I can't tell my friend (laptop owner) Ubuntu won't work. (having converted him to linux :smile:) I did attach my comments to a previous thread but got no response, hope I will this time.


[U]Edit:

[/U]Been searching web seems the problem is in the kernel? (pin allocation etc) the answers go over my head, it has only affected some versions. Don't know if that helps anyone.

---

### Post by lisati on 2007-07-31
I've been using Ubuntu 7.04 on a low-end A100 for just over a month now and still get the 8254 timer warning on start-up. The only troubles I've had, other than sound not working straight away (easily fixed) and usb mouse stopping  randomly (also easily fixed), have been largely self inflicted. Unless you are sure it's preventing something you need from working, you probably don't have much to worry about.


EDIT: I occasionally get warnings about a phantom CD-ROM but that is being dealt elsewhere in another thread,

EDIT #2: Is a fresh install an option?

---

### Post by evilc on 2007-07-31
Thanks for the help.

The problem was after 'x' minutes the network and all usb's were going down. I have reinstalled version 6.10 and all working without a hitch now, that should keep them happy until there's a fix (or Gutsy comes out).

---

### Post by univremonster on 2007-08-01
Not that this helps anybody but I have the same error popping up at every bootup of my desktop.  I started using Ubuntu back on Dapper Drake and never had this issue, then did a double-upgrade to Fiesty when it first appeared.  Perhaps this is an issue with hardware?  Here's a description of mine:

Processor:  AMD Athlon 64 3400+ (Venice)
Hard drive: Seagate Barracuda 7200.9 ST3250824AS 250GB 7200 RPM SATA 3.0Gb/s
Motherboard: SAPPHIRE PC-A9RD480Adv Socket 939 ATI Radeon Xpress 200
RAM: Patriot 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200)

---

### Post by univremonster on 2007-08-03
bump

---

### Post by evilc on 2007-08-03
univremonster,

From what I have found out up to now it seem's to be related to ATI?
Latest suggestions say update ATI driver and also try acpi=force irqpoll in boot menu.lst.
I will be trying this when I get hold of the laptop I was installing on.

---

### Post by evilc on 2007-08-04
OK updated ATI driver still failed, tried the acpi to boot no difference?
I have had a look around various sites/distro's this seems to be a common fault since kernel 2.16.x so the  problem to me is the kernel not the ATI drivers etc. Some people suggest installing an older stable version but many don't know where to get them and in the case of Ubuntu most run with the "generic version" auto installed via Synaptic. If there was no need to update this why do they upgrade automatically? 
I would have thought as the problem is widespread and only appeared since the kernel version above, the programmers/developers of this version should/would be able to find where the bug is and correct it. It's not good publicity for Linux in general especially for newcomers, and even worse for the linux users who have been encouraging them.

---

### Post by lisati on 2007-08-04
> **evilc said:**
> univremonster,

From what I have found out up to now it seem's to be related to ATI?
Latest suggestions say update ATI driver and also try acpi=force irqpoll in boot menu.lst.
I will be trying this when I get hold of the laptop I was installing on.

I've got a similar line about acpi in my boot script. I came across that one looking for a solution to USB not working after a few minutes (seems to have helped, even with a "typo" in the line)

---

### Post by univremonster on 2007-08-06
The card was ok with Dapper and Edgy though, it was only on the Fiesty upgrade this started happening.  Additionally (and I don't know if these problems are related) every time that the diskcheck runs at startup it finds an error and wants to reboot.  Still doesn't seem to have affected anything

---

### Post by evilc on 2007-08-08
Have spent 3 hours trying various thing to fix this, have noticed it only happens when the usb mouse is connected? and only lock up when you try to expand/decrease a window with the mouse, all usb ports and network/internet gets diconnected but the touchpad mouse still works. If I run without a usb mouse everything works including any usb attachments other than a mouse. So the problem is mouse related, is there a way of reconfiguring the usb setting for the mouse seems to be a conflict there?

---

### Post by etobico on 2007-08-11
I have a similar warning.

I downloaded and created the ISO Image:

KUBUNTU 7.04 Desktop i386
ubuntu-7.04-server-i386.iso

On booting this ISO image, I would get the following message after selecting run or install ubuntu from the opening menu:

31.869448 ..MP-BIOS bug: 8254 not connected to APIC
32.048467 ..... (text not recorded, but I believe 'panic' was hinted at)
32.048506  *HANGS* (no text)

These three lines would appear after the initial lines ending "loading kernel"

**PARTICULARS OF MY MACHINE**

ASUS' PC-PROBE II v1.04.19 reports the following:

_BIOS INFORMATION (Type0)_
Vendor: American Megatrends Inc
BIOS Version: 0204
BIOS Release Date: 2007.03.12
BIOS ROM Size: 512 KB
BIOS Characteristics: 0x000000017f8bde90

_System Information (Type1)_
UUID: a0 a3 b0 8e 8d fe d5 11 ad d5 0 1a 92 83 57 e1

_System Information (Type2)_
Manufacturer: AUSUTeK Computer INC.
Product Name: M2N-MX
Version: Rev 1.xx

_Processor Information(Type4)_
Manufacturer: AMD
Version: AMD Athlon 64 Processor 3500+
Voltage: 1.5v
External Clock: 200 MHz
Max Speed: 2200 MHZ
Current Speed: 2200 MHz
Status: CPU Enable

The BIOS cannot be updated with the latest available from ASUS since only BIOS released through the vendor's, (Targa) website are recommended or compatible.

FYI, I note that Wikipedia contains a brief reference to BIOS bugs -- it would seem that this is NOT a Linux-only issue:

[Wikipedia]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture#Hardware_Bugs") [http://en.wikipedia.org/wiki/Intel_APIC_Architecture#Hardware_Bugs](http://en.wikipedia.org/wiki/Intel_APIC_Architecture#Hardware_Bugs)

reads as follows (though it refers to the 825_9_ and not to the 825_4_:
[I]
"Hardware Bugs

"There are a number of known bugs in implementations of APIC systems, especially with concern to how the 8259 is connected.

"There are defective BIOSes which do not set up interrupt routing properly. This includes the errors in the implementation of ACPI tables and Intel Multiprocessor Specification tables."[/I]

[B]HISTORY OF HANGING UNDER WINDOWS VISTA
[/B]
Since purchase, I have also been experiencing lock-ups in Windows (Vista) without any logging information generated (even CAPS-LOK and NUM-LOK) lights on PS/2-keyboard frozen).  Again, this would point to a BIOS issue rather than one with the OS, and if it is indeed the BIOS bug identified by UBUNTU's startup code that is causing my lockups under Windows, then MANY THANKS are owed the developer and designer who thought of and implemented this test.

**BIOS SETTING CHANGE TEST**

In order to test this, I went into the BIOS setup program and made one change, the exact location and text of which I will post in a few minutes following a re-boot.   However, IIRC, it was in the chipset options, and I believe it was the third of three options, and had a rather cryptic rubric something like:

MP - APIC - HEPT TABLE ..... or some'at ..... so I selected DISABLED on this and rebooted.  

UBUNTU booted and loaded the kernel and Destktop happily.  I've not tested anything else further.

I'll leave on overnight and report back in a couple of days of normal usage and overnight BOINC processing whether or not the machine has crashed.  It normally would hang, quite unpredictably, at irregular intervals, during the course of two days' running.

**64-BIT UBUNTU**

I had earlier downloaded and created the image
v6.06.1 desktop for AMD64
ubuntu-6.06.1-desktop-amd64.iso

The machine simply hanged after "loading kernel".

**CONCLUSIONS**

As suggested by the error message itself, this appears to be a BIOS bug and not an issue with Linux.

Disabling ummmm, 'that' setting with the MP-APIC-&c. TABLE may ... _MAY_ provide a work-around where no fixed BIOS update is available.  I am not sure what else is sacrificed in doing this, however.  Any advice greatly appreciated.

I shall post again in a few minutes with the exact adjustment I made in the BIOS Settings.

I shall post again in a few days IF the machine hangs in a way which is similar to before (either under Windows or Linux) with the new BIOS setting.

---

### Post by etobico on 2007-08-11
I can confirm that making the following change alone enables / disables Ubuntu 7.04 Desktop i386 boot, where the BIOS is AMI ACPI BIOS v0204:

Advanced
Chipset
Southbridge Configuration
MCP61 ACPI HPET TABLE
: enabled --> Ubuntu does not boot and displays messages as above, panics, hangs
: disabled --> Ubuntu boots and appears to work

I do not know whether either Ubuntu or Windows (Vista) will hang when left running for 'a while'.  I am running BOINC under Vista and will leave this running and use the computer in mundane work over the next few days as usual.  If it hangs in the same way as before, I will post here again.

Best of luck to you all.

---

### Post by etobico on 2007-08-13
It hangs as before, quite unpredictably, under Vista.

It has been left on overnight (only) under ubuntu, but without any BOINC processing and when running from the CD, so daemon interaction with peripherals may have been minimal.

:popcorn:**_I would be very interested to know what BIOS versions other people seeing this message are running._**

---

### Post by evilc on 2007-08-13
> **etobico said:**
> It hangs as before, quite unpredictably, under Vista.

It has been left on overnight (only) under ubuntu, but without any BOINC processing and when running from the CD, so daemon interaction with peripherals may have been minimal.

:popcorn:**_I would be very interested to know what BIOS versions other people seeing this message are running._**

Unfortunately on the Toshiba laptop there are none of the suggestions possible (not there). The bios was updated to latest v.2.2 XP/Vista compatable.

---

