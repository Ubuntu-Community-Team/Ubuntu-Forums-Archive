---
title: "installed 12.04 now printer does not work."
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by livewire94 on 2012-04-28
I upgraded from 11.10 to 12.04 and now my printer the canon mp620b no longer works.  My printer is setup wireless on  network.  Worked good on 11.10.  I cannot find any new driver updates for 12.04.  I am new to linux and I would need guidance to install.

My canon mp620b is the only thing I need to get working yet on 12.04 so I don't need to boot back into Windows.

I read other threads that where closed about this but no solution.

Thanks for any help.

---

### Post by dino99 on 2012-04-28
what we need to know is which wireless chipset is used on this system, or at least which MB. ( can get it via : sudo dmidecode)

---

### Post by livewire94 on 2012-04-28
The printer has wireless and is connected to my wireless router.  My PC is connected to my router wired.  If I boot into Windows, I can print.

Something changed when upgrading from 11.10 to 12.04.  I also installed 12.04 onto my other computer and cannot install my network printer, the mp620b.

I just need to know how to install my canon printer mp620b which is connected via wireless network, in Ubuntu 12.04 and work.

This is frustrating.  A simple thing as printing should work with a new release of Ubuntu.

---

### Post by dino99 on 2012-04-28
and what about your self effort to answer to the post #2 above ?

---

### Post by livewire94 on 2012-04-28
I don't understand the output of the sudo command thing.  It wont let you copy the entire output of that command.  

I have a M2n-32SLI deluxe motherboard on this computer connected via lan cable to router.  

My other computer is an Acer 5515 laptop connected wireless to router.

---

### Post by darkod on 2012-04-28
Did you try to reinstall the printer in ubuntu?

Does it have a fixed IP? Can you ping that IP from ubuntu?

Are you sure the wi-fi is working in ubuntu?

---

### Post by livewire94 on 2012-04-28
Yes, reinstalled printer.

Yes, has fixed IP.

Yes, can ping IP of Printer.

Not using Wifi in Ubuntu on this PC.  Connected via cable to router.

Please not that I can print with no issues from Windows 7 on this PC.

---

### Post by darkod on 2012-04-28
So, if you installed the printer that means it was discovered, right?

What exactly is happening when you are trying to print?

---

### Post by livewire94 on 2012-04-28
I go to print anything and nothing happens.  If I watch the status, it says idle then when I goto print it says failed to read side channel request.

---

### Post by livewire94 on 2012-04-28
I also found this message.  usr/lib/cups/filter/pstocanonij failed

Have no idea what that means.

---

### Post by darkod on 2012-04-28
This has been reported as a bug but it says it's not really a bug. The reason is that the canon drivers are made for older ubuntu versions. See if there are newer drivers. And google searching for how to install your printer model in ubuntu 12.04, maybe you will find something.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/856028](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/856028)

---

### Post by livewire94 on 2012-04-28
That sucks.  I tried searching for how to install in 12.04 but cannot find any info.  I wonder if the bug will be fixed.  At least Windows 7 will print for now.

---

### Post by darkod on 2012-04-28
Yeah, 12.04 is still new so maybe you will have to wait a little for someone to find a fix.

It's really disappointing that manufacturers rarely develop drivers for linux. And then it looks like windows always works just because they make drivers even before the OS is released.

Double check the Canon website just in case.

---

### Post by livewire94 on 2012-04-30
Got it working.  

Here is how I did it:  [http://ubuntuforums.org/showthread.php?t=1969853](http://ubuntuforums.org/showthread.php?t=1969853)

---

### Post by ratcheer on 2012-04-30
> **livewire94 said:**
> I also found this message.  usr/lib/cups/filter/pstocanonij failed

Have no idea what that means.

I have the exact same problem. The printer works fine in 11.10. In fact, I am having to keep Oneiric on my disk drive just so I can print when I need to.

Here is my thread in the now defunct Ubuntu + 1 (for Precise) forum:

[http://ubuntuforums.org/showthread.php?t=1949038](http://ubuntuforums.org/showthread.php?t=1949038)

Tim

---

