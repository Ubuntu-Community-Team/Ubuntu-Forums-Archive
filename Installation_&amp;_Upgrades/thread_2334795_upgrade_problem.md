---
title: "upgrade problem"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by bobipod on 2016-08-22
I was running the last ubuntu system and now responded to to the upgrade prompt to upgrade to 16.04.

It crashed part way through. I now get to a dos (i think) screen asking for login and password.  I have tried the only options i can think of but they keep getting rejected.

I cannot do anything and my pc is inoperable with all my info stuck in it.

Any ideas to help recover from this?

---

### Post by Bashing-om on 2016-08-22
bobipod; Hello;

What results when attempting to activate a console interface ?
At the login screen key combo ctl+alt+F1 .

Can you log into the system here with your credentials ?

If so we then we can look and see what the situation is .

[INDENT][INDENT]'buntu is always fixable
[/INDENT][/INDENT]

---

### Post by bobipod on 2016-08-22
I tried your suggestion and i just get the following

^@^@^@

Then it drops a line and again asks for log in details.

---

### Post by Bashing-om on 2016-08-22
bobipod; Ouch ;

Well, then, let's try and drop down to yet a lower level.
Can you boot to grub's boot menu ?
EFI system: as soon as the firmware screen clears, spam the escape key -> grub boot menu ?
Legacy (MBR) system : as soon as the bios screen clears, depress and hold a shift key -> grub boot menu ?

Else it is going to be a LOT of effort and work to repair this system.

[INDENT][INDENT]we in it for the long haul ?
[/INDENT][/INDENT]

---

### Post by bobipod on 2016-08-24
I'm in the grub menu.

I have the following options.

Ubuntu
Advanced options for ubuntu
Memory test memtest 86+
Memory test serial console.

Where do i go from here?

Not the top one as it is the problem going to login.

---

### Post by ian-weisser on 2016-08-24
Are you saying that your system crashed during a release-upgrade from another version of Ubuntu to 16.04?

If so, do you know the nature of the crash?
Was the system downloading during the crash? Or installing?

It may be possible to recover your system. Then again, it may not.
A simple option maybe to create a 16.04 USB installer, boot using the USB to backup your data, install 16.04 from scratch, then restore your data from the backup.

---

### Post by bobipod on 2016-08-24
Yes the crash was from last upgrade to current upgrade. 

It happened during installation phase.

I don't have the ability to make a boot usb or cd as i now have nothing but an old mobile for internet.

I'm hopeful i can tap in to what is left and recover the system that way.

I think i have the 14.04 on disc in the loft if all else fails.

---

### Post by Bashing-om on 2016-08-24
bobipod; Well .. (not yet) 

> **bobipod said:**
> I'm in the grub menu.

I have the following options.

Ubuntu
Advanced options for ubuntu
Memory test memtest 86+
Memory test serial console.

Where do i go from here?

Not the top one as it is the problem going to login.

Keeping in close mind the advise of ian-weisser, the better course might be a RE-install.
We can continue to see what we can do .
In this grub boot menu choose " Advanced options for ubuntu " Which will give you additional boot options,
In these options is the option to boot a "recovery" kernel . Choose this method, and advise on results .
If we can reach a terminal here, then too we can look and see the state of the system and make plans for restores .
Failing here too, we do something else.


[INDENT]somehow, some way
[INDENT][INDENT][INDENT]we got to get us a terminal interface
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-08-24
> **bobipod said:**
> It happened during installation phase.

That means you have mixed packages from different releases of Ubuntu...incompatible, which is why you cannot boot. 

> I think i have the 14.04 on disc in the loft if all else fails.
My advice: Pretty much all else has already failed. FInd it.
Boot from it.
Backup your data to an external device.
Reinstall 14.04 (which is likely to wipe all your data).
Restore your data from the external device.
Then ration your old mobile's data...installing two years of updates. 

This assumes you don't know what caused the crash, or cannot reproduce it. If you know the cause of the crash, that's different.

What kind of crash was it? What happened? Error message? Return to login screen? Total poweroff?

---

### Post by bobipod on 2016-08-26
I didn't manage to find the discs.

So i bought a usb from canonical store with 16.04 on.

Tried to do a fresh new install.  Waited a while. Error 5 message came up saying couldn't install probable hard drive failure.  Now i need to wait for new one to arrive before i can continue.

---

### Post by bobipod on 2016-09-06
So i now have a new hard drive and once again when i try to install from the newly purchased canonical usb with 16.04 on it i get the same error message stating that the cd or hard drive has an error.

I'm not using the cd and i doubt the new hard drive is faulty, although this i s not impossible.

What is wrong with the 16.04 install program?

---

### Post by QIII on 2016-09-06
In general there is nothing wrong with installing 16.04 (many of us have done so), but you may have a unique situation.

Can you tell if the error is referring to the USB media or the target drive?

---

### Post by bobipod on 2016-09-06
A little more info here on this problem

The error message is 

Errno 5 input/output error.


Problem with hdd or cd drive.  try cleaning cd drive or check hdd.

I have tried numerous ways of installing from the usb stick, with without updates selected nd the same for third party updates.

Same thing everytime.

However when i try to download and install from ubuntu site it stops half way through and says i only have 5mb of space?

It's a brand new fresh hdd


now running format on the hdd to see if that helps, might be a while!

---

