---
title: "is using a separate HDD or SSD for Ubuntu a good alternative to dual booting?"
date: 2017-05-13
forum: Installation &amp; Upgrades
---

### Post by lkali on 2017-05-13
I was thinking of getting a new notebook and dual booting Windows 10 and Ubuntu, but am under the impression that this is either complicated, risky or both. So I'm thinking of physically taking out the drive that the notebook came with and put in a blank drive, then install Ubuntu on it. This way if I need to use Windows, I can swap the drives and know that I should be ok. 

Is this a good idea -- are there technical problems (BIOS settings, etc) I should anticipate using this method?

---

### Post by TheFu on 2017-05-14
The hassle-factor for this is very high.  I wouldn't do it, but yes, you could go this way.

If you get any recent generation Core i3+ system, then you can use virtualization to run either Win10 or Linux. Pick the hostOS for the machine based on which you expect to need the most high-end graphics (i.e. gaming or CAD or video processing).  For Windows-based virtualization, most people use VirtualBox [https://www.virtualbox.org/wiki/VirtualBox](https://www.virtualbox.org/wiki/VirtualBox) . It works fairly well.  Be certain to read the licenses carefully, since different parts of the installation (especially the guest additions) have different license clauses.

I haven't "dual booted" in years.  Virtualization is really good these days.

---

### Post by yancek on 2017-05-14
Using the method you plan on might be safe but you will likely need to boot from the BIOS each time you want to switch from booting Ubuntu to windows and vice versa.
Another factor you need to consider is windows installed using UEFI/GPT.  If so, you should install Ubuntu the same which would simplify things.  Check the Ubuntu documentation on this at the link below.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ubfan1 on 2017-05-14
The hassle factor is more a function of how far the vendor deviated from the UEFI standard, or decided to add their own "improvements".  You didn't mention any specific hardware, but that makes the biggest difference.  An external enclosure, with dual USB3 and eSATA might be the easiest way for you to add a second disk.

---

### Post by Bucky Ball on 2017-05-14
Kind of defeats the purpose of having the SSD. Rule of thumb is the OSs go on the SSD because it's faster and data goes on the HDD. A dual-boot is the preferred method for this, obviously enough. 

Depending on your machine and the manufacturer, a dual-boot is easy or not as easy, but virtually never impossible. Certainly wouldn't be put off doing one due to hearsay. 

Good luck. ;)

---

