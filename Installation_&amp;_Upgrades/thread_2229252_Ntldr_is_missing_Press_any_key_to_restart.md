---
title: "Ntldr is missing Press any key to restart"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by Sandulescu_Marian on 2014-06-12
Hi all,


I have a problem which started from the wireless issue from my new laptop Dell, running on ubuntu edition 12.04. The issue is that I wasn't able to see the wireless networks available. Being a software problem, I choose to restore the previous ubuntu version. In that moment, a message pop-up appeared with all my data will be erase if I will go futher. Being afraid not to lose my data from the only partition available (500GB), I choose not to go with the restore and cancel it. After cancel it, a reboot happend, and the message Ntldr is missing Press any key to restart appeared.


Also, if I press ENTER the message continues:


Realtek PCIe FE Family Controller Series v1.25 (04/19/11)
PXE-E61: Media test failure, check cable


PXE-M0F: Existing PXE ROM.
No Boot device Found. Press any key to reboot the machine


I checked the BIOS and the boot order is : HDD, CD-ROM and Network;


I tried to recover the data with an old Knopix but I cannot see the HDD.
Can you recommand how can I recover the data or how to fix the Ubuntu OS crashed?


Thanks in advance!
Marian

---

### Post by rahul4557 on 2014-06-12
NTLDR is required for Windows to Boot.
This can be caused by 2 main reasons.
-Partition where Windows is installed is deleted/erased.
-NTLDR file is not found while booting because of incorrect boot information.

Try running live Ubuntu from CD/USB and check if the partition where Windows is installed is intact.
If partition is intact you can use windows disk to repair the boot configuration
else reinstall the windows.

---

### Post by Sandulescu_Marian on 2014-06-12
Hi rahul4557,

This is for the devices runing on windows.

But my laptop is new and comes with already pre-installed Ubuntu 12.04. Doesn't run on any windows os.

What I did right now, is to run ubuntu intaller for windows from an USB but the window is black with an underline sign flashing..

---

### Post by rahul4557 on 2014-06-12
> **Sandulescu_Marian said:**
> Hi rahul4557,

This is for the devices runing on windows.

But my laptop is new and comes with already pre-installed Ubuntu 12.04. Doesn't run on any windows os.

What I did right now, is to run ubuntu intaller for windows from an USB but the window is black with an underline sign flashing..
[B]
How did you run ubuntu installer for windows from an USB??[/B]

---

### Post by Sandulescu_Marian on 2014-06-12
Install ubuntu 12.04 ISO on USB and hoped it would work. But, unfortunately, it couldn't be that simple.. I don't have any idea on how to fix this issue.

---

### Post by oldfred on 2014-06-12
But the old wubi.exe only runs inside Windows. Ubuntu will not run it, unless you also installed .wine and then I am not sure what may happen.
wubi is being discontinued.

Boot into live installer in live mode. Either from live DVD or flash drive what ever you can get to work.
Post this:
sudo parted -l

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

