---
title: "Freeze before install begins"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by aetebet on 2013-05-29
Hello,

I'm trying to install Ubuntu 12.04 LTS on my HTPC. The system is an AMD A4-3400 with 8GB of memory running on integrated graphics with a 1TB hard drive. The motherboard is a Gigabyte A75M-UD2H. I've tried installing using multiple bootable USB drives and a disc. All of them begin booting to the OS installation but after the four loading dots turn to orange then white it freezes. The same happens when trying to use Linux Live. This happened when I tried installing over an existing Windows installation and after a format. Windows 7 will boot from the disc and install fine. I've tried Ubuntu 12.04, 12.10, 13.04, and XBMCbuntu 11.0. I've installed at least a handful of distros before on systems to play around with and on virtual machines but none of them have ever had this issue. 

I'd really like to move my HTPC over to Linux but right now I'm at a loss for what is going on! If anybody could provide some advice or ideas on where to start troubleshooting that would be great.

Thanks!

Alex

---

### Post by papibe on 2013-05-29
Hi aetebet. Welcome to the forums ):P

I don't know very well your hardware but it may need some special boot options. Take a look at this [tutorial]("https://help.ubuntu.com/community/BootOptions") and take special attention to the options under 'F6. Other Options'.

The options that solve most of the booting problems are: **acpi=off** and **nomodeset**.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by aetebet on 2013-05-29
> **papibe said:**
> Hi aetebet. Welcome to the forums ):P

I don't know very well your hardware but it may need some special boot options. Take a look at this [tutorial]("https://help.ubuntu.com/community/BootOptions") and take special attention to the options under 'F6. Other Options'.

The options that solve most of the booting problems are: **acpi=off** and **nomodeset**.

Hope it helps. Let us know how it goes.
Regards.

Thank you!

I read through the tutorial and popped in my install disc for another go. I tried acpi=off and nomodeset. When installing from the disc it goes to black screen with blinking cursor, whereas before it would make it to the loading menu. Also running it through Live produces the same results. Both my disc and bootable USB produce this same result. 

Are there any possible BIOS settings that need to be altered? Searching the motherboard and Ubuntu (and Linux in general) didn't produce too much

---

### Post by aetebet on 2013-05-30
Ok, update. I re-ran the installer and opened the console to see where it freezes. It runs through all of the "Starting..." messages then it goes to this:

> Starting CPU interrupts balancing daemon [ OK ]
Stopping save kernel messages
saned disabled: edit /etc/default/saned

I'll do some searching around on this message to see what's up.

---

### Post by aetebet on 2013-05-30
Well looks like one last update for this one. I started thinking a bit and began unpluggin devices from the system. After I removed a NIC, that caused endless issues using Windows, it made it all the way to installation! Chalk this one up to a faulty ASUS PCE-N10 card...

---

### Post by papibe on 2013-05-30
:D Glad you worked it out, and thanks for sharing that.

---

