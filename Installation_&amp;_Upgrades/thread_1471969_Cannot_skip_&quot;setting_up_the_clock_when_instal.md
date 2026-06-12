---
title: "Cannot skip &quot;setting up the clock when installing ubuntu 10.04&quot;"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by jahjahlove on 2010-05-04
Hi! big time newb!

I have an old Sager 4760 with 1 gig of RAM with the ATI Radeon card. I have installed Ubuntu 9.10 from the Cd. Zero prob. 

Now i am trying to install 10.04 and i am stuck at that screen:
[http://3.bp.blogspot.com/_r_DUjwGxwzE/S9wLUx4dgSI/AAAAAAAABZ8/_ATTRaBEMqE/s1600/ubuntu+1004+03.jpg](http://3.bp.blogspot.com/_r_DUjwGxwzE/S9wLUx4dgSI/AAAAAAAABZ8/_ATTRaBEMqE/s1600/ubuntu+1004+03.jpg)  (link as a ref only)

My screen is stuck at 0%. I cannot skip it no matter how many time i click on "skip". There must be a way to force the system to skip it, a short cut maybe?. Even if i plug the laptop to the internet to get that  famous time from a network server does not work :-(. I tried to eject the CD and "reload" it again but nothing happen. It does not even spin.

I am sure it could be something simple but.. i am stuck. I need help.

Thx a lot.


I have a built-in floppy drive (that i have disabled in the Bios), a cardbus reader and 3 usb ports.

---

### Post by CallForSanity on 2010-10-20
Exactly the same problem here...
The strange thing is. It did work before on the same machine.

Thanks for any advices.

---

### Post by sikander3786 on 2010-10-20
This is a pretty old thread, no solutions so I will suggest this.

Not a perfect solution but you can try to disconnect your network cable, and reconnect it after it skips the time synchonization step. You'll need to manually set the time and date afterwards.

---

### Post by tweezak on 2010-11-01
I just got this working. I used information from this thread:

[http://ubuntuforums.org/showthread.php?t=841281](http://ubuntuforums.org/showthread.php?t=841281)


Here's what I did:

1. Shrink the Win7 partition from Windows Disk Management (defrag first)
2. Format the new partition with NTFS.
3. Put the Ubuntu CD image on a flash drive. I used the Startup Disk Creator on another Ubuntu machine.
4.  Boot from that flash drive and RUN Ubuntu rather than choosing the  install option. Then in Ubuntu there is an installation icon on the  desktop. Run that.

When I rebooted into Windows7 again for the  first time (note that GRUB is now the boot loader and Windows is a ways  down the list) it flashed a bluescreen at me and rebooted. It then ran a  checkdisk. After that it booted very slowly the first time. Eventually  it was okay and then seemed to boot normally.

Ubuntu is fine as well.

So, it all seems good....so far...

Cheers!


Edit: I should mention this was 10.10 not 10.04.

---

