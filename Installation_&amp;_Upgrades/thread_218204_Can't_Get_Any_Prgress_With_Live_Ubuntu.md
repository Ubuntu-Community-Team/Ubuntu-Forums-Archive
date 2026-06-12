---
title: "Can't Get Any Prgress With Live Ubuntu"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-07-18
I  can't get anywhere when trying to bott from cd.
if i choose the second option down(something to do with less graphics)
it gets all the way to setting up hardware drivers(right after prepairing restricted drvers)
then it freezes.Does it just take a long time to do it?
i have waited a long time.
here is my hardware.
System Device
    Compaq Presario SR1220NX
    CPU: Intel(R) Celeron(R) CPU 2.93GHz

    BIOS: Rev. 3.03

    Motherboard: PJ517AA-ABA SR1220NX NA440

    Physical Memory

        512MB](*,) 

        512MB](*,) 

    Harddisk: HDS728080PLAT20 (77GB)

    Video Card

        Video Controller (VGA Compatible)

        NVIDIA GeForce FX 5500

    Monitor

        Default Monitor

        SyncMaster 730B(Analog)

    SoundDevice: Realtek AC'97 Audio

    Network Adapter

        Local Area Connection - Realtek RTL8139/810x Family Fast Ethernet NIC (Connected)

        1394 Connection - 1394 Net Adapter (Connected)

    Modem

        Agere Systems PCI Soft Modem

        

    Keyboard: USB Human Interface Device

    Mouse: Microsoft USB Dual Receiver Wireless Mouse (IntelliPoint)

    Mouse: Microsoft PS/2 Port Mouse (IntelliPoint)

I have onboard graphics and a pci video card.
the onboard is disabled.
could it be that there is a conflict of some sort?
as there is with windows.
i also have this problem with kubuntu, and also various form of linux.
Thank You

---

### Post by taurus on 2006-07-18
Try to install Dapper with alternate CD then...  It's the same with the desktop version except it uses text base (old way) as installer.

---

### Post by xptweakerntn on 2006-07-18
what are you taliking about. 
the cd(the pressed ones i orderd)
only comes withone.
are you talking about hitting escape and choosed text method?
i tried that, but i think it froze.
i can't tell, how lond does it take to detect the hardware?
i want ubuntu to work so bad.

---

### Post by stuh505 on 2006-07-18
xptweaker, taurus is suggesting that you download and burn this CD to install with instead:

[http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso)

---

### Post by xptweakerntn on 2006-07-18
i ca't.
i am running on dialup
is there something else i can do?
i read somewhere about geforce cards being hard to setup?
is that true?

---

### Post by taurus on 2006-07-18
> **xptweakerntn said:**
> 
i read somewhere about geforce cards being hard to setup?
is that true?

NOT!  I have an eVGA GeForce FX5600 and it is working just fine with either vesa, nv, or nvidia driver...

---

### Post by xptweakerntn on 2006-07-18
i have a geforce fx5500.
but could it be because of the onboard video adapter?

---

### Post by taurus on 2006-07-18
> **xptweakerntn said:**
> i have a geforce fx5500.
FX5500 or FX5600, they are all the same...

> but could it be because of the onboard video adapter?
I have an onboard video card too and I turn it off in the BIOS so Ubuntu doesn't even know (or see) it!

---

### Post by xptweakerntn on 2006-07-18
if by disabling you mean setting the primary to pci, i did that.
any other reasons it may not work?

---

### Post by taurus on 2006-07-18
> **xptweakerntn said:**
> if by disabling you mean setting the primary to pci, i did that.
any other reasons it may not work?

Disable means turn it, onboard video, off completely!!!

---

### Post by xptweakerntn on 2006-07-18
i don't think i can i my bios, i will check.
within windows doesn't count for anything, does it?

---

### Post by brentoboy on 2006-07-18
in breezy there was a newer geforce chipset (6600 I think -- or maybe 6200) that used to crash X right after the welcome "drums" sound.  It was easy to fix, but you had to search the forums for the places where other people had the issue in order to fix it.

since dapper, I have never seen any nvidia detection / installation issues.  (I have a decent number of various nvidia based cards running here)

---

### Post by xptweakerntn on 2006-07-18
i tried a few new thing, i got the following errors
one time it said something about fixing recursing fault, reboot required

another time it said something about kernel panic not sincing.

what do you need to know to help me?

---

### Post by taurus on 2006-07-18
Again, please try to turn off your onboard video card and see if it works or not first!  Otherwise, see if you can get your hand on the alternate CD and use that to install on your machine then...

---

### Post by xptweakerntn on 2006-07-18
i looked, and i can't disable it.
i can either select 1 or 8 mb of my ram to be used(1 selected)
is there some secret key comination to unlock advanced features?
where could i get the other cd?

---

### Post by bozcrow on 2007-06-10
I know this is old, but for what it's worth I think the problem is your kybd/mse.  I've tried several different distros with the M$ wireless usb dual receiver and NONE recognize it, and about half hang while booting.  Dunno why, but when I use a plug-in usb M$ keyboard and a wireless Logitech usb mouse it works just fine.

---

