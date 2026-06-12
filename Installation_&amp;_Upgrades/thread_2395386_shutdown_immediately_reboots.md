---
title: "shutdown immediately reboots"
date: 2018-07-01
forum: Installation &amp; Upgrades
---

### Post by usndmac on 2018-07-01
I upgraded a PC from UbuntuStudio 16.04  to 18.04 ( specify UbuntuStudio, but I'm guessing it's not a UBS specific...)

Now selecting the shutdown menu or issuing a shutdown -h now from the terminal does a reboot.

I tried turning off all the power management things from settings managler, but, still have not found the fix.

One thing I note is a message just before the pc screen goes blank (after the shutdown command and before reboot, is a message about "communication has been lost with UPS".
There is no UPS and this PC has never had one and has never set up to use one...

(Note: I've done the same process successfully on at least 3 other PC's and laptops. None have this issue.)

Not sure what to do next...ideas?

Mac

---

### Post by #&amp;thj^% on 2018-07-01
You could try to examine your "/etc/default/grub" file or even add this to try:
```
sudoedit /etc/default/grub
```

set to:
```

GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq quiet splash"
```
then run
```

sudo update-grub
```
Now try a proper shutdown.

---

### Post by usndmac on 2018-07-01
That made no difference.

Another thing I noticed is the Windows 10 partition now does the same thing.

I checked for something obvious in the bios setup that would cause this, but, didn't see anything.

The windows partition hasn't been changed at all and this is the first time I've looked at the bios in years. And I'm the only one with access to this PC.

:(

---

### Post by #&amp;thj^% on 2018-07-01
Wish I would of known this was A dual boot with Windows 10
See if this helps here: [https://www.drivereasy.com/knowledge/solved-windows-10-wont-shut-restarts-instead/](https://www.drivereasy.com/knowledge/solved-windows-10-wont-shut-restarts-instead/)

If your brave enough you can also use regedit in Windows 10 but first try the above.
I'll leave out the edit to the registry for safety reasons. :)

---

### Post by usndmac on 2018-07-01
Hmm...I'm happy to try that (and I'm perfectly comfortable with regedit, don't like the registry concept, but have used regedit plenty...unfortunately. :(  )

But:

- the PC had not been booted to W10 for months while UBS 16.04 was running and happily shutting down correctly.
- the PC was then upgraded from 16.04 to 18.04
- during and after this process (until today) the W10 partition was never booted.


 So, I'm curious why W10 partition would be part of the problem...

---

### Post by #&amp;thj^% on 2018-07-01
> **usndmac said:**
> Hmm...I'm happy to try that (and I'm perfectly comfortable with regedit, don't like the registry concept, but have used regedit plenty...unfortunately. :(  )



Allrighty then:
Edit your registry: "**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\**"
change the key: "PowerdownAfterShutdown" to "**1**"
> **usndmac said:**
> 

 So, I'm curious why W10 partition would be part of the problem...
I have no idea here for that>>>I just flat don't use Windows at all. ;) But if there was no updates taken lately with Windows 10 then this probably won't help. (But also it shouldn't hurt to try)
BTW If still no joy>> you can then remove "acpi=noirq" from /etc/default/grub && update-grub again.

---

### Post by usndmac on 2018-07-01
That didn't change anything.

Interestingly, the power button does power off if I hold it for a few seconds with either OS.

---

