---
title: "Installation hangs"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by thebasti on 2006-06-03
Hello,

I am trying to install Ubuntu 6.06 on clean machine (i.e. empty disk). Live system boots without any problems and installation starts (goes through hard partitioning), but it hangs on 66% while copying files. There is no error message of any kind and it just doesn't move past 66%. I've tried it couple times and each time it's the same.

I am installing on computer with following hardware:

Processor: AMD Athlon Thunderbird
Memory: 2GB
Motherboard: MSI KT6V
GFX: ASUS N6600

Does anyone knows what might be the problem? Thanks.

Regards,
Basti

---

### Post by thebasti on 2006-06-03
It might be worth saying that in past 20 minutes or so (while I was posting my previous message) I managed to install older Ubuntu (Breezy) on same machine without any problems.

So, I guess that this has something to do with new version of Ubuntu.

Any help would be appreciated.

Regards,
Basti

---

### Post by kacheng on 2006-06-03
I had problems if I made any changes to the partition defaults from the Live CD.
Does this occur if you use the text install CD method?

Alternatively, this might be something to do with your particular configuration.
Are you using an SATA hard drive?
Do the install parameters 'noapic nolapic' help?

---

### Post by thebasti on 2006-06-03
I didn't change anything regarding partitions. Installer handled everything himself, so it has default partitions.

I am trying to install on Seagate SATA hard disk. I haven't tried with noapic nolapic (I am about to do it), what does it mean?

Again, I should mention that after Dapper install failed I tried Breezy install and it worked without any problems.

---

### Post by thebasti on 2006-06-03
I've just tried adding noapic and nolapic to boot options when starting live cd and again it got stuck on 66%.

Any other ideas?

---

### Post by thebasti on 2006-06-03
I've found a solution. It appears that installation CD had some problems (although initially it went through all checks, when you choose to 'verify cd' in boot menu). I've burned CD again and installation went without a problem.

Either way, thanks for your help. :)

---

### Post by happyisland on 2006-07-13
I am experiencing almost the identical problem as thebasti (except my install makes it all the way to 67%). Can anyone recommend a way to get this thing to work? Should I try the alternate version?

---

### Post by thebasti on 2006-07-14
Hi,

Did you try to record a CD on very low speed, i.e. 4x, and then install?

This helped me.

---

### Post by Yumi on 2006-07-14
Received orginal live CD and intallations hangs on various percentages during Intalling System "copying files". No error, just hangs as described.

Michael

---

### Post by Riverside on 2006-07-14
I am experiencing this also, with the Dapper 6.06 LTS Desktop installation CD.  The installation hangs at different points whilst copying files; currently I am looking at a machine hung at 53%, the time before it hung at 28%.

I have previously installed Ubuntu (various versions), Debian (ditto), SuSE (7.3 - 9.2) and FreeBSD on the machine with no difficulty.  I suspect that there is an undocumented issue with the graphical installer CD which I and others posting to this thread are running into.

---

### Post by Riverside on 2006-07-15
This is definitely an issue of some kind with the graphical installer CD.  I have now downloaded ubuntu-6.06-alternate-i386.iso and used it to carry out a faultless installation on the same machine, with no issues whatsoever.

Since it seems multiple users are experiencing this issue, perhaps it needs formally submitting as a bug?

---

### Post by ferebee on 2006-07-15
After a couple of tries I got it to install sucessfully from the
LiveCD installer, as I'm on dial-up and downloading the alternate installer
wasn't an option.

I used the safe graphics option and added acpi=off noapic nolapic to the boot parameters and that time it worked, no problems. I did have to boot into rescue mode afterward and reconfigure xserver-xorg, but that's not unusual as my video card is a very old ati, and it does not play well with others.

Or maybe it was just third time lucky :-)

---

### Post by Yumi on 2006-07-16
Thanks for this tread. The alternate CD did install for me without problems. Why do they send me 10 CD's but not include the alternate one?

Anyway, I am back on Linux.

Michael

---

### Post by george1984 on 2006-07-17
I am a computer newbie. Apologies in advance for my stupidity.

I have just received through the post from shipit the kubuntu 6.06 LTS cd. Keen to explore kubuntu.

I have attempted to install it on to an IDE hard drive currently running Suse 10.1_32.
When the menu appeared I selected “ start or install “. During about one minute, starting with “ loading essential drivers “ , I think that the kernel was loaded. After this the same plain blue screen appeared with “ KUBUTU “ in bold type, and beneath this what appeared to be an inactive progress bar; but nothing else. Frozen. When this screen appeared, the dvd-rw ran at high speed for about 30 seconds, but the indicator lights showed no activity. It was only possible to escape by switching-off.

From the menu I ran the cd checking program, which confirmed that the cd was ok.

Could there be a fault on the cd? Could it be a hardware problem? Could it be software? Could I be doing something so stupid that it beyond the imagination of a competent computer user? My machine appears to deal with other live/installation cd's ok.

I have a sluggish connection, but I can try downloading a copy of 6.06; but would it be a safer bet to download the ubuntu version. I really want to try (k)ubuntu.

Any comments welcome.

athlon 3500 , asus a8n5x , ide160 , gnr display.

---

