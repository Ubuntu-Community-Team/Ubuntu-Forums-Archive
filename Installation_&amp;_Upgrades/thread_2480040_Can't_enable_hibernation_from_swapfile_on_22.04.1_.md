---
title: "Can't enable hibernation from swapfile on 22.04.1 LTS"
date: 2022-10-17
forum: Installation &amp; Upgrades
---

### Post by 0x7fffff on 2022-10-17
I'm tying to enable hibernation using my 10 GiB swapfile. I'm running 22.04.1 LTS.

I have followed this guide: [https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html](https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html)

But on running "update-initramfs -c -k all" I see "W: but no matching swap device is available" in the output, which presumably means hibernation is not going to work, if it can't find the swap device. I undid the changes and reran "update-grub" and "update-initramfs -c -k all".

I also read around the internet and found people talking about installing "pm-utils", "hibernate", and "uswsusp", but the latter two have no installation candidates—is hibernation just not supported on this version?

(I was gonna use CODE tags instead of quotes but they don't inline.)

---

### Post by TheFu on 2022-10-17
[https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file](https://askubuntu.com/questions/6769/hibernate-and-resume-from-a-swap-file) has instructions for getting it working in 18.04.  
[https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/](https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/) claims to work for 22.04.

I tend to prefer sources that have "ubuntu" in the DNS part of the URL and provide instructions for the exact release.

I didn't test either, but I know that standby works on encrypted LVM storage. I use it daily on a laptop since 16.04.  That laptop still runs 18.04. Stability is more important to me than "new".
 
The official Debian documentation is here: [https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition](https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition)

It is multi-step and there are some serious security implications in enabling hibernation, but it is your system to use as you think best.

BTW, whenever any instructions anywhere say to run 'sudo gedit' (or any other editor), we should mentally translate to into using 'sudoedit' instead.  That's the safest way to edit system files and not break things elsewhere like 'sudo gedit' does.

---

### Post by ubfan1 on 2022-10-17
I don't hibernate or use a swapfile myself, but I recall seeing setting the RESUME=UUID (where the UUID is the root UUID instead of a swap partition UUID) and adding an offset= to locate the swapfile.Kernel update messages give the location of this variable, but I think it is in /etc/default/grub

---

### Post by 0x7fffff on 2022-10-17
This is all the stuff I had tried already (except for the debian documentation part, that involves "uswsusp" which I can't access on 22)

---

### Post by ne29914 on 2022-10-18
The recipe you linked to in the original post looks OK to me, but as I only use a swap partition (almost same recipe), I can't verify it.
Nothing else should be needed.

---

### Post by 0x7fffff on 2022-10-19
Maybe I should change to a partition and try, since swapfile isn't working?

---

### Post by ne29914 on 2022-10-19
> **0x7fffff said:**
> Maybe I should change to a partition and try, since swapfile isn't working?
In my experience, a swap partition always works. Set it to RAM size plus 20% (or if you plan on adding RAM, according to that size).
There are people voicing concerns about security on hibernating, but whether this applies to both swap files and partitions or just to swap partitions is unclear to me.
As I don't run encryption, it's a non-issue in my case.

---

### Post by 0x7fffff on 2022-10-20
I used a swap partition (and also split / and /home/ into their own partitions) and hibernation works now!

---

### Post by ne29914 on 2022-10-20
Congrats.
And splitting / and /home was a very good decision.

---

