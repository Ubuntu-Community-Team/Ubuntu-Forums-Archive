---
title: "I need a new Video Card for Ubuntu 9.10"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by BSG Fan on 2010-02-12
Okay, I already ran the terminal and found my video card is this:
VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

The card is working but I am suspicious that it is the 99% responsible for at least 15 freezing per day.

When I installed the Ubuntu I did it with the "secure-no graphics" (don't know the name) mode because was impossible using the main one (everything was in distortion with lines in the screen).

So, that is why I think changing the card I will solve the problem....
no?

Well,
my questions are:

1- What do you think?
2- What new video card I can buy for?
   (Has to be exactly the same card or I can get a substitute for?)

3- What are the steps to replace it?
   (I mean, without causing a general problem or burn the board...)

I will appreciate ur help









Ps: I don't know if this is the place to post my question

---

### Post by Cabs21 on 2010-02-12
did you update your hardware drivers to ensure that the graphics card is working properly and not being ignored, forcing your computer to use your processor for graphics?

---

### Post by BSG Fan on 2010-02-12
> **Cabs21 said:**
> did you update your hardware drivers to ensure that the graphics card is working properly and not being ignored, forcing your computer to use your processor for graphics?

Nope.

How I can do that?

---

### Post by mhgsys on 2010-02-12
Go to System > Administration> Hardware drivers

(edit: seems to be hard to enable 3d on that card, .. have a look here as well.)
[http://ubuntuforums.org/showthread.php?p=8812432](http://ubuntuforums.org/showthread.php?p=8812432)

edit:

BTW; Thnx to someone else his/ her problems :found this.
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by BSG Fan on 2010-02-12
[QUOTE=mhgsys;8814654]Go to System > Administration> Hardware drivers

I did and it says this:

"[SIZE="6"]**No Proprietary Drivers Are in Use on this System**[/SIZE]"



:(

I went to the terminal and typed "lspci"

00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


==============

I went to this page:
[http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp)

They are asking me for the model: 
Step 1: Ubuntu current
Step 2: Ububtu 9.04
Step 3: Select the type of model (How I do that?  They say: Integrated graphics or Eutherent-
     Networking/Lan/Wlan)
     How can I know that?

Step 4: Don't know yet

---

### Post by recluce on 2010-02-12
From what I read from your system information, your system does not have a dedicated graphics card, but onboard graphics. Adding a dedicated graphics card is likely to add performance to your system and free up some memory (as onboard graphics "share" your main memory).

ATI currently has issues in Karmic for Suspend to RAM - no idea if this is an issue for you on a desktop. Beyond that, ATI drops support for older graphics cards sooner than NVIDIA. The open source driver for ATI seems to come along nicely.

NVIDIA seems to work quite well, the proprietary driver support is good. The open source driver is very basic in its functions.

Without starting a flamewar between ATI and NVIDIA fans (hopefully); I would see a small advantage for NVIDIA at this point in time. Get whatever graphics card seems to offer sufficient performance, if low to mid performance is good enough, go for a passively cooled card - no fan, no noise.

---

### Post by Grenage on 2010-02-12
> **recluce said:**
> Without starting a flamewar between ATI and NVIDIA fans (hopefully); I would see a small advantage for NVIDIA at this point in time. Get whatever graphics card seems to offer sufficient performance, if low to mid performance is good enough, go for a passively cooled card - no fan, no noise.

Good advice, and that would also be my suggestion.  You don't have to pay much for a low-end Nvidia card, and it will make the world of difference.

---

### Post by BSG Fan on 2010-02-12
> **recluce said:**
> From what I read from your system information, your system does not have a dedicated graphics card, but onboard graphics. Adding a dedicated graphics card is likely to add performance to your system and free up some memory (as onboard graphics "share" your main memory).

ATI currently has issues in Karmic for Suspend to RAM - no idea if this is an issue for you on a desktop. Beyond that, ATI drops support for older graphics cards sooner than NVIDIA. The open source driver for ATI seems to come along nicely.

NVIDIA seems to work quite well, the proprietary driver support is good. The open source driver is very basic in its functions.

Without starting a flamewar between ATI and NVIDIA fans (hopefully); I would see a small advantage for NVIDIA at this point in time. Get whatever graphics card seems to offer sufficient performance, if low to mid performance is good enough, go for a passively cooled card - no fan, no noise.

So I may buy a new graphic card (video card) compatible to "VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC]"

The question is:
How I install thus the new card?
I mean, I just turn off the pc, install the new card and turn on the pc?  That's it?
or I have to do something different
sorry but I am not a computer technician in no way :)

---

### Post by Grenage on 2010-02-12
Open the case and check that your computer does have a PCI-E slot, if it's old it might be AGP; if you're very unlucky it won't have one.

Buy the card, slot it in.  Chances are that the BIOS will automatically use the new card, otherwise look in the BIOS to set the primary display adapter.

---

### Post by recluce on 2010-02-12
> **BSG Fan said:**
> So I may buy a new graphic card (video card) compatible to "VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC]"

The question is:
How I install thus the new card?
I mean, I just turn off the pc, install the new card and turn on the pc?  That's it?
or I have to do something different
sorry but I am not a computer technician in no way :)

The "Chrome 9 HC" refers to your onboard graphics and no compatibility is required on behalf of the new card.

As Grenage wrote, find out what kind of graphics card slot your machine has. Opening up the case is one option, a look at your mainboard's manual is probably better.

If PCI Express: verify the "size", like PCIe 8x. Buy any card matching your slot. Be aware of the power consumption of your new card and be sure that your power supply is sufficient.

If AGP: buy any AGP card

If neither PCI Express nor AGP: SOL - your computer is very old and it does not make sense to upgrade the graphics

---

