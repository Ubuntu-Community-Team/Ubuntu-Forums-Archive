---
title: "Won't boot after kernel upgrade today"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by philip.sargent on 2007-05-26
The only update waiting to happen when i checked my ubuntu fileserver today was kernel 2.6.15-28-386 so I updated and now it won't boot.

gets to ...
...OK, booting the kernel
ACPI: Unable to locate RSDP
crc error
Kernel panic - not syncing: VFS: unable to mount foot fs on wn-block(0,0)


this was booting fineand i have made no other changes.
Is this a known problem with this kernel upgrade?

---

### Post by cantormath on 2007-06-01
BUMP

I am having the exact same problem, what is this?!

---

### Post by Lucifiel on 2007-06-01
Hmmm... you're not able to boot from an earlier kernel? Gah... that's sad. :(

---

### Post by cantormath on 2007-06-02
> **philip.sargent said:**
> The only update waiting to happen when i checked my ubuntu fileserver today was kernel 2.6.15-28-386 so I updated and now it won't boot.

gets to ...
...OK, booting the kernel
ACPI: Unable to locate RSDP
crc error
Kernel panic - not syncing: VFS: unable to mount foot fs on wn-block(0,0)


this was booting fineand i have made no other changes.
Is this a known problem with this kernel upgrade?

I did the simple fix and unistalled all of the kernel updates that cause the problem.  Reinstalling those updates again is something I have yet to try.  If you want to do what I did, just hit esc when grub boots and choose the old kernel,  then uninstall all of the kernel updates that you had updated.  after that run:
```
:-$ sudo update-grub
```
reboot and it should be back to normal.

---

### Post by LarsBjerregaard on 2007-06-02
If you are running Feisty you probably mean "2.6.16-28".
In that case, the main discussion is going on over here: [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)
Stay tuned to:
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996](https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314)

---

### Post by cantormath on 2007-06-02
This issue for me was on dapper with 2.6.15-28-386.  I had to go back to the 2.6.15-26-386 kernal.

> **LarsBjerregaard said:**
> If you are running Feisty you probably mean "2.6.16-28".
In that case, the main discussion is going on over here: [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)
Stay tuned to:
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996](https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314)

---

### Post by bean77 on 2007-09-06
> **LarsBjerregaard said:**
> If you are running Feisty you probably mean "2.6.16-28".
In that case, the main discussion is going on over here: [http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)
Stay tuned to:
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996](https://bugs.launchpad.net/ubuntu/+s...20/+bug/116996)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117447)
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314)

Those last 3 links didn't work.

---

