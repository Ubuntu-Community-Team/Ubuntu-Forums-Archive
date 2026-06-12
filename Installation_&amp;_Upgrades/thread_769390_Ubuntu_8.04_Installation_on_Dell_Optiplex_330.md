---
title: "Ubuntu 8.04 Installation on Dell Optiplex 330"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by MartinOpatrny on 2008-04-26
Has anyone had any experience with the installation on **Dell Optiplex 330**? I have had some problems with using my **printer HP Deskjet 500**. It can be configured but **hangs at the beginning of the page** when printing. It only prints the first few lines and then it stops. It takes ages to print some more or it stops altogether.

I have had the similar problems with the latest Knoppix 5.5.1 and Mepis 7.0 on the same Optiplex 330. I have only been trying it with the live CDs, not installing anything.

The Deskjet 500 is now 16 years old but it keeps working very well and I have had no problems using it with Windows 2000, XP and older versions of Linux on older machines.

I shall be very happy to receive some help.

Regards,
Martin

---

### Post by wandalalakers on 2008-04-27
I don't have this printer but trying using a hp deskjet 400, 510 or 520 driver.
Try selecting use raw printer driver only and see what happens.

---

### Post by MartinOpatrny on 2008-04-28
Thank you, PCDoctor.

What do you mean by "raw printer driver"? The closest I could find was Generic => Raw_Queue. I've tried it. It hangs as well and prints gibberish, unfortunately. What problems have you encountered with your printers? 

Meanwhile, I have received some help from elsewhere. The new suggestion is to install hplip and hplip-gui, which is a set of drivers with a human interface for nearly all HP printers, and configure the printer using this hplip. It looks promising. They are explicitly specified for Ubuntu 8.04, among others.

I did install the hplip (using the live CD), but when I enter hplip at the command prompt (or hplip-gui, or sudo hplip, or sudo hplip-gui), nothing happens. So far, all other programs which I have installed "on-the-fly") using the ubuntu live CD user interface or apt-get at the command prompt could be started by entering their name at the command prompt. Why not with hplip?

Who can help me?

Regards,
Martin

---

