---
title: "Reinstalling ubuntu"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by Jerry786 on 2010-12-19
Hi all, i need to wipe out my existing ubuntu and reinstall it again, how do i do this? do i simply remove the partition ubutu is installed on and reinstall again once i create a new partition?

Thanks

---

### Post by Quackers on 2010-12-19
If you just have the one operating system on the disc just run the Live cd and choose "install" then select "use the whole disc" on installation. It will over-write everything on that hard drive.

---

### Post by Jerry786 on 2010-12-19
> **Quackers said:**
> If you just have the one operating system on the disc just run the Live cd and choose "install" then select "use the whole disc" on installation. It will over-write everything on that hard drive.

I have 2 operating systems installed. What to do?

---

### Post by Quackers on 2010-12-19
Boot from the live cd and choose to use the same partition(s) you used before for installing the "old" Ubuntu and check the box(es) for formatting the partition(s).
You will need to choose the "manual" option in the partitioning stage.
Be careful! Don't mistake the Windows partition(s)!!!

---

### Post by Jerry786 on 2010-12-19
> **Quackers said:**
> Boot from the live cd and choose to use the same partition(s) you used before for installing the "old" Ubuntu and check the box(es) for formatting the partition(s).
You will need to choose the "manual" option in the partitioning stage.
Be careful! Don't mistake the Windows partition(s)!!!

Ok, im going to install from USB, same method as using the live CD?

---

### Post by Quackers on 2010-12-19
Yes, it's the same (if your bios supports booting from usb flash).

---

### Post by Jerry786 on 2010-12-19
> **Quackers said:**
> Yes, it's the same (if your bios supports booting from usb flash).

OK, thanks. WIll try and give it a go now. WIsh me luck

---

### Post by Quackers on 2010-12-19
Good luck! :-)
Be careful!

---

### Post by Jerry786 on 2010-12-19
> **Quackers said:**
> Good luck! :-)
Be careful!

Ok I'm stuck. booted from usb, now I'm the allocated space menu

I see sda1, sda5 swap, sda6 ext4 sda2 and 3
what next?

---

### Post by Jerry786 on 2010-12-19
swap and ext4 format box is greyed out when I try to select.

---

### Post by Jerry786 on 2010-12-19
heeeeeeeeeeelp :)

---

### Post by Quackers on 2010-12-19
Sorry, I've had problems myself :-)
Have you selected the same partitions for root and home that you had before and set their mount points?

---

### Post by kansasnoob on 2010-12-19
I'd click on quit and then post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You need to understand device designations, etc.

I also didn't see you mention if you needed to save any data from the old install?

---

### Post by Jerry786 on 2010-12-19
I deleted partition and started over,  installing now. Hope it works...

---

### Post by Quackers on 2010-12-19
In the partitioning window that you had up, if you double-clicked on the partition you wanted to install into you should have been able to leave the same size as it was, set the format to ext4 and the mount point to / and then check the format box. But you needed to know which partition to do that with. As you said you only had one other OS installed (Windows) there should have been only one ext4 partition to choose from (unless you have a separate /home partition.
But the way you have chosen should be fine. As long as you have left the Windows partitions alone.

---

### Post by Jerry786 on 2010-12-19
Thanks for the replies. Its all up and running now thankfully :)

---

### Post by Quackers on 2010-12-20
Glad to hear it :-)

---

