---
title: "Cant install obuntu"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by alex502 on 2016-02-08
Iam  trying  to install the os  and when I'm trying to boot it it's entering a black grub screen...
How do i fixing it?!
There is the photo of it:
[https://app.box.com/s/ao2b23ucp341eja8gwz262qmmavwz7wn](https://app.box.com/s/ao2b23ucp341eja8gwz262qmmavwz7wn)

Tnx a lot

---

### Post by yancek on 2016-02-08
Did you download Ubuntu from the officical site?
How are you trying to install it?  Did you burn the iso file as an image to a DVD?  Did you use the appropriate software to create a bootable flash drive?  If so, which software?
Have you tested the medium you are using in another computer to verify that it will boot?  Can you post some information on your hardware?

---

### Post by alex502 on 2016-02-08
Yes I downloaded it from the official site.
I made a bootable usb drive using rufus.
 I didn't try it on another computer.
Bios secure boot is turned off.

 Something else do you need to know ?

Thanks

---

### Post by slickymaster on 2016-02-08
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by grahammechanical on 2016-02-08
I am confused. Are you seeing this after you have installed Ubuntu? Or when running the Ubuntu live/install session. Grub is used by an installed version of Ubuntu. 

Another thing that confuses me is that it is Grub version 1.99. The newest versions version of Ubuntu use Grub version 2.02. So, what version of Ubuntu are you using? It might be a version that has reached end of life and is no longer supported.

You could also give us information about the computer hardware and what other OS are on the machine. If Ubuntu is one of 2 OS on the machine we should see a Grub boot menu which should give us the option to load Ubuntu or the other OS. Do you get that menu? Does the other OS load as it should? When you select Ubuntu do you then arrive at the Grub prompt as seen in the photograph?

When Grub starts to do its work, it will look to the partition with Ubuntu on for its configuration file. If it cannot find it, then we will get that Grub prompt. My advice would be to load the Ubuntu live session and install Boot Repair and get a boot repair summary report. Boot Repair will store the report online and give you a URL to where the report is stored. Post the URL in this thread so that we can see the summary report for ourselves and give you better advice.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by alex502 on 2016-02-08
I downloaded the latest version of ubuntu from the official website.
I'm trying to dualboot with my win 10 and the first thing that appears after boot process is this grub screen!

---

