---
title: "Install &amp; live CD both fail-could it be a HD format problem?"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by sappman2 on 2005-11-07
I wiped Windows ME out because I was sick of Microsoft. It's an HP Pent-III 850 MHz, 512 Mb RAM. I've tried formatting the drive with a Windows start-up disk in different ways: FAT-16, FAT-32, large hard disk support, no large disk support, with partitions, then deleting the partition/partitions AFTER formatting.

I've tried new downloads & new CD burns (On CD-R's, not CD-RW's) I've tried KUBUNTU (In case it might somehow have been GNOME? causing problems). I've tried both CD drives on this PC. This HD is completely empty, so I keep coming back to it being a format issue, with UBUNTU installer not liking the format of the HD somehow. (even though there are no partitions present, not even a primary DOS partition.) Been working for days on this. Any ideas? Any diagnostic tools available out there?   -Chris

---

### Post by rmjokers on 2005-11-07
The Ubuntu installer should not care what is on the hard drive in terms of partitions and filesystem types.  It will allow you to partition the drive and format it however you want.  What happens when you try to boot with the installer / live CD?  Could there be something set wrong in the BIOS maybe?  Have you tried doing a checksum on the CDs to make sure they are burned properly?

---

### Post by sappman2 on 2005-11-08
I found the likely problem on my causing install to fail. I talked to one of my work-mates, who is far more computer-savvy than I. He suggested that I could be having a problem with my RAM. I insisted that the box ran fine on Windows, to which he replied that Windows, which "leaks" memory anyway, has  built-in redundancies that cover over RAM problems. Linux, however, does not.

BINGO! I ran "MEMTEST" from the install CD and only about 12% (Average) of my "brand-new" 512Mb RAM passed, even though my BIOS boot RAM test passed it w/no problems. I sincerely appreciate the UBUNTU community for their attempts at helping. I hope that, as I grow in knowledge, I'll be able to give back and help others and promote the benefits of Linux and Ubuntu. Now... Any ideas on a place to find decent, cheap RAM for a 6 year old Pentium III?      Thanks............... -Chris

---

### Post by rmjokers on 2005-11-08
I suggest you look on pricewatch.com

---

### Post by jatos on 2005-11-08
I personally use planetmicro.co.uk, though I am not sure if it would economic for you. As rule don't get generic RAM, go for Kingston or Corsair as a rule, shouldn't matter where you buy providing its not a shop with a rep for bad parts.

---

