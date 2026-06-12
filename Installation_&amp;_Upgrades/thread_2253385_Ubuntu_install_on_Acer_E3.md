---
title: "Ubuntu install on Acer E3"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2014-11-19
I&#8217;ve just purchased an Acer Aspire E3 that came with Windows 8.1 with Bing.
I have a good bootable USB stick with 14.04 on it, from which I have installed several times on different machines.
Here&#8217;s what I did:

Created unallocated space on the HDD within Windows
Booted from the USB
Clicked on &#8220;Install&#8221;
Chose &#8220;Something else&#8221; in the next dialog
Created a / partition, a &#8220;Home&#8221; partition and a Swap area.
Clicked on &#8220;Install&#8221;


The install went just like any other install that I&#8217;ve done over the last few years.
When it finished, I clicked on the &#8220;Restart&#8221; button.
The machine restarts, and goes straight into Windows. No sign of the Ubuntu install at all.
If I examine the HDD in Disk management within Windows, there are no formatted partitions in the unallocated space at all.
AFAIK Windows 8.1 with Bing is no different at all to &#8220;normal&#8221; Windows 8.1 so can anyone tell me what&#8217;s going on? (I&#8217;ve tried both with Ubuntu 14.04 and Xubuntu 14.10 - both had the same result).

just tried again, after setting Boot in the BIOS to HDD instead of Windows Boot Loader.
Same result, BUT - in Windows, the three partitions I created in the Ubuntu installer now appear - BUT, they are completely empty!
this gets more and more bizarre by the minute....

---

### Post by cariboo on 2014-11-19
Are you making sure that grub is being installed to the first hard drive in the system?

---

### Post by Gordonbp531 on 2014-11-20
There is only one HDD....
I'm installing grub to the EFI partition just like I've done in other installations on UEFI Windows machines.
I don't think it's a grub or EFI problem at all, as the install procedure *appears* to work, it goes through the whole process with nothing different from other installs I've done, even takes the same length of time but after a re-boot there's nothing there at all. The partitions created by the install routine are completely empty.

---

### Post by Gordonbp531 on 2014-11-21
Solved!
I had to go into the BIOS and on the Security Tab, set a Supervisor password.
I could then go into the Secure Boot setup and add Ubuntu as a trusted boot option.
I then went into the Boot tab, moved Ubuntu to the top, and moved Windows Boot loader to second.
Restarted, and it now boots straight into grub, and not only that, the Windows option in the grub menu works as well, with no other "tweaking" needed. Never had that happen before...
:D

---

