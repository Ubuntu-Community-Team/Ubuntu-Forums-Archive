---
title: "[RESOLVED]Installing any flavour of Ubuntu on eMachines 520 Issues"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by Burgy on 2017-04-23
I have a netbook
(Specs:
Intel Atom N270 Processor,
1GB RAM,
160GB HDD)
And it was running Windows and was very slow. I wanted to format the drive and install a Linux distro like Lubuntu so I made a USB Boot Drive for Windows 10, allowing me to format the drive. Then I made a USB Boot Drive for Xubuntu and when I boot to the drive I get these errors:


```
  ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20160930/dsfield-211)
    ACPI ERROR: Method parse/execution failed [\_SB.PCIO._OSC] (Node f5094ba0), AE_ALREADY_EXISTS (20160930/psparse-543) 

```Then, the splash screen starts and loads for a little then leaves again, leaving me at a initramfs console with these errors above it:


```
 usb 1-1: device descriptor read/64, error -110
    usb 1-1: device descriptor read/64, error -110
    usb 1-1: device descriptor read/64, error -71
    usb 1-1: device descriptor read/64, error -71
    usb 1-1: device not accepting address 4, error -71
    usb 1-1: device not accepting address 5, error -71
    usb usb1-port1: unable to enumerate USB device
    usb 2-1: device descriptor read/64, error -71
    usb 2-1: device descriptor read/64, error -71
    usb 2-1: device descriptor read/64, error -71
    usb 2-1: device descriptor read/64, error -71
    usb 2-1: device not accepting address 4, error -71
    usb 2-1: device not accepting address 5, error -71
    usb usb2-port1: unable to enumerate USB device

```

These are my Rufus settings when I made the USB
 [IMG]https://i.stack.imgur.com/1KZFs.png[/IMG]



Ubuntu gives the same errors, then Lubuntu gets me to the graphical installer and then has these issues, cannot even try Lubuntu from the USB drive.
(My USB drive is a SanDisk 32GB USB 3.0 Drive if that helps.)
I've been unable to find a good help thread with someone who has a similar problem if someone knows of a thread and could link me it, or just has a solution that would be wonderful. Thanks :)

---

### Post by termibuntu on 2017-04-23
Hello. Your rufus settings look fine. The errors come from the acpi. It means something is wrong with it. Are there any power issues you are facing? Since acpi manages power consumption and stuff like that.

---

### Post by Autodave on 2017-04-23
You may want to take a look at this: [https://bugzilla.redhat.com/show_bug.cgi?id=1413342](https://bugzilla.redhat.com/show_bug.cgi?id=1413342)

I know it is redhat, but same kernel as Ubuntu,Lubuntu, etc.

---

### Post by Burgy on 2017-04-24
I left it off for a while, unplugged. And now I don't get the ACPI messages but I'm still getting the USB errors, do you think I should just try a different USB?

---

### Post by Burgy on 2017-04-25
Found an old 2GB drive that is admittedly way slower than my new 32GB drive, must be the USB 3.0 vs USB 2.0 speeds. But it is installing properly so far :)

---

