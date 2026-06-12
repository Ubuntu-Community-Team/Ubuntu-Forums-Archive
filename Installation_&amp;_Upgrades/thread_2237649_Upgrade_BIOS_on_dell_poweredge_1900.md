---
title: "Upgrade BIOS on dell poweredge 1900"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2014-08-03
I have been trying to upgrade the bios on my dell poweredge 1900 for a month now from 1.5.1 to 2.7.0
I have made a dos bootup dis because the upgrade file is .exe but whenever I use this to boot up and try to execute the file I get the message 'bad command or file name'.
It is a LONG time now since I used windows/DOS.
How can I execute the upgrade?

---

### Post by Vladlenin5000 on 2014-08-03
In the link below you'll find two versions. You need to use the "Non-Packaged" format. That *.exe will run from a DOS bootable USB mass storage device whereas the first one is intended to run in a full fledged Windows OS.


[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=5TTF1&fileId=3000129137&osCode=WNET&productCode=poweredge-1900&languageCode=EN&categoryId=BI](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=5TTF1&fileId=3000129137&osCode=WNET&productCode=poweredge-1900&languageCode=EN&categoryId=BI)

---

### Post by tgalati4 on 2014-08-03
Another way to do it is to create a small partition on your drive with freedos.  Put the flasher and the BIOS binary in the top level directory of the freedos partition.  Update grub so that freedos shows up in your grub menu list.  Boot into freedos and then run the flasher from the C:\ prompt.  So you have at least 3 options:  create a bootable freedos USB flash drive; create a bootable CD with freedos and the flasher and the BIOS binary; or create a small freedos partition on your disk drive and boot from that.

---

### Post by astarmathsandphysics on 2014-08-05
I get the same error using the non packaged version.
At the command prompt I type
PE1900-202700C.exe 
and I get the message 'BAD COMMAND OR FILE NAME'

Is it anything to do with permissions?
The exe file belongs to group astarmathsandphysics - not root.
Should I change ownership or permissions of this file?

---

### Post by Vladlenin5000 on 2014-08-05
No, it shouldn't be, considering you're trying to run it from a DOS environment where such things as permission don't apply.
Perhaps you should contact Dell Customer Support. You'll be redirected to the specialized servers support.

---

### Post by tgalati4 on 2014-08-05
I bet that executable is not the flasher program, but a self-extracting (zip) file that needs to be opened on a Windows machine.  It should break itself out into 2 or 3 pieces.  Copy those pieces to your freedos partition, then run the flasher.exe or similar program.  It's been a few years since I upgraded my Dell PowerEdge 1750's.  At the time I created a bootable CD using instructions I found on the web.  It booted to FreeDOS and then I had to run the flasher.exe program and it checked the existing BIOS, the new BIOS, backed up the old BIOS (answer no on a CD since you can't write to it, unless it is RW) then uploaded and tested the new BIOS, then asked to reboot.  It was simple.  The most difficult part was making the CD with the correct pieces on it.

---

### Post by astarmathsandphysics on 2014-08-06
Will try that last suggesting

---

### Post by Mark Phelps on 2014-08-06
Just make sure that whatever you use allows you to save off the existing BIOS -- in a form that you could restore from, if the BIOS upgrade goes badly; otherwise, you're risking completely trashing the PC.

---

