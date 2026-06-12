---
title: "Ubuntu 6.06LTS installation problems"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by papikondalu on 2006-10-16
I'm having problem with the installation of Ubuntu 6.06 LTS on my Acer (AMD64 processor) laptop. I tried both PC and 64-bit versions. I'm using the Ubuntu shipped installation CDs.

Here is what happens:
(1) I'm able to boot into the GNOME screen. In this mode I'm able to use the PC in the "Live" mode without installation.
(2) After I was satisfied, I double-clicked on the "install" icon. Everything seem to go well until
     (a) The 64-bit version gave a short message that installation failed
     (b) The 32-bit version got stuck in installing grub

I looked at /var/log/install/syslog. For case (a) there were some errors output by some python script, which I could not understand. For case (b) there was a message indicating that grub was already installed, which is not true.

Note: The installation went through successfully with the Ubuntu 5.10 CD.

Any help with 6.06 installation would help me avoid downloading tons of info for upgrading from 5.10 to 6.06.

Thanks

-PK

---

### Post by Sef on 2006-10-17
Try installing with the alternate cd.  It is text based, but easy to follow.  It is on the bottom of the  [download.]("http://www.ubuntu.com/download") list.

(First is Desktop CD, then Server Install CD, then Alternate Install CD.)

---

### Post by joff13 on 2006-10-17
I'm using dapper amd64 on a acer Aspire 5023 (amd64).
I had no problem installing it.

Just a question you want a 2boot with win? I think Acer laptops sometime have  funny behavior, but you should be able to install ubuntu

what exaclty are your configuration and probelms?

---

### Post by papikondalu on 2006-10-18
I tried re-installing all-over again. The installation went through without problems. There were some warnings in the syslog file, which indicated that apt tools are still unstable. The partitioning tool said that there was error in creating two partitions linux-swap and ext3. It created the first one and gave the error. I went back and created the other partition. The installation continued without complaints after that.

Without much sweat, now, I was able to do the basic installation. I'll go ahead with the wireless network configuration and start using the 64-bit version.

The installation would have been nice if the installer had given some advance options:
(1) Select the first OS for Grub
(2) Allow selection of some packages that the user might be interested in

Thank you all for responding.

-PK

---

