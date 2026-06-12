---
title: "Boot problems"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by Kevin1985 on 2010-02-12
Hey guys,

Forgive me my ignorance but I don't seem to be able to install Ubuntu 9.10 at all.

My first idea was to use USBLive because I have to work on several computers. This didn't work because my Sony Vaio doesn't support booting from a removable device.

Secondly I chose for the dual boot system. This didn't work either. After selecting Ubuntu in the GRUB the computer displayed the logo and moved on to the next screen where it showed this:

[I][#] task events/0:6 blocked for more than 120 seconds
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs"[/I]

Every 5 minutes this same text appears with a different number, hence the [#].

At last I did a complete reset of my computer an put it back to factory settings. Then I started Windows and installed Ubuntu by means of Wubi.
After rebooting the computer and choosing Ubuntu the following appeared in the screen and nothing more happened:

[I]* Starting early crypto disks...

[/I]The only thing that does work is using a LiveCD and run Ubuntu from the cd. Since I'm planning to use OpenFOAM, this won't work for me.

Can anybody help to get Ubuntu running? Besides the use of OpenFoam I would really like to use Ubuntu as my standard OS.

---

### Post by recluce on 2010-02-12
Does the 9.10 live session (boot from Ubuntu CD) work for you?

---

### Post by Kevin1985 on 2010-02-12
Yes, that is the only way I can run Ubuntu without the computer getting stuck halfway the boot procedure.

---

### Post by darkod on 2010-02-12
> **Kevin1985 said:**
> 
[I]* Starting early crypto disks...
[/I]

This message makes me wonder whether you have some setup that you are not even aware of. I'm not trying to offend you, but lately there have been few cases of that. :)
One user for example was not aware that his new computer is running raid. Something you should definitely know when choosing to buy.

Can the word "crypto" mean you have some sort of encryption on the disk(s)? That would really complicate things.

If you have a "plain, standard" setup and installation of windows, I see no reason your dual boot not to work.

Sorry I can't help more.

---

### Post by Kevin1985 on 2010-02-12
I had been wondering that myself since I seem to be the only with this problem.

As far as I know the computer is standard (Model Sony Vaio VGN-FS515E).
The laptop contains a single Fujitsu MHV2080AT PL ATA hard drive which is partitioned into a C: and D: drive. But I couldn't say if it's running raid...

---

### Post by darkod on 2010-02-12
> **Kevin1985 said:**
> I had been wondering that myself since I seem to be the only with this problem.

As far as I know the computer is standard (Model Sony Vaio VGN-FS515E).
The laptop contains a single Fujitsu MHV2080AT PL ATA hard drive which is partitioned into a C: and D: drive. But I couldn't say if it's running raid...

In live desktop running, try in terminal:
sudo fdisk -l

and copy the results here. It will show all the partitions and filesystems.

---

### Post by kansasnoob on 2010-02-12
Since you can run the Live CD the Boot Info Script might provide some useful info:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Can't hurt to take a look :)

---

### Post by Kevin1985 on 2010-02-14
I tried to follow your advices only to find out that my compu wouldn't boot Ubuntu at all, not even from the Live CD.

So I gave up on my Sony Vaio and claimed my girlfriends computer. An eigth year old Medion laptop, and it works like a charm! Although it's not at fast, at least it works.

Nevertheless thank you all for the advice, finally I can enjoy the benefits of Ubuntu!

---

### Post by darkod on 2010-02-14
> **Kevin1985 said:**
> I tried to follow your advices only to find out that my compu wouldn't boot Ubuntu at all, not even from the Live CD.

So I gave up on my Sony Vaio and claimed my girlfriends computer. An eigth year old Medion laptop, and it works like a charm! Although it's not at fast, at least it works.

Nevertheless thank you all for the advice, finally I can enjoy the benefits of Ubuntu!

Conspiracy between MS and Sony. :) And the Vaio costs loads of money too. Shame on them.
Glad you found an option though. :)

---

