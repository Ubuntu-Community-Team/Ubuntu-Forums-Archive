---
title: "Black window after update kernel 5.3.0-28 to 5.3.0-40"
date: 2020-02-20
forum: Installation &amp; Upgrades
---

### Post by oscmar on 2020-02-20
Hi,

Three days ago I bought a new laptop with ryzen 3 3200u processor.
I installed ubuntu with kernel version 5.3.0-28 and all looks good. I can access and work but, when I update SO (with upgrade and dist-upgrade), kernel version 5.3.0-40 is installed and I can&#8217;t load SO after reboot.
The only thing that appears its a black screen that I can&#8217;t remove.
I tested possible solutions like install amd drivers, disable c6 states&#8230; and nothing work. If I go to "advanced options" in grub, I can select 5.3.0-28 kernel version and all works (boot options are same).
Any idea?

Thanks!

---

### Post by billsime on 2020-02-20
Hello oscmar - I think you meant 5.3.0-28 to 5.3.0-40, right?  Assuming you did, I recently updated my kernel to 5.3.0-40.   I have an older Intel chip on mine.   I backed off to 5.3.0-28 because my laptop would not resume after suspend under the newer kernel.  I experienced similar to what you describe (black screen) when attempting to resume.  The only remedy I could find was to reboot the laptop.  Thinking maybe a 4.15 kernel would fix my issue, I installed 4.15.0-88 but had same issue.  With the previous kernel (4.15.0-76), the suspend-resume works fine.  I've just started digging.   If I find something, I'll provide an update here.  Maybe not exact same situation, but looks very similar to me.

---

### Post by oscmar on 2020-02-21
Hi billsime, 

Thanks for the reply. 
Yes, that was a confusion, is already modified.
Soon I will install other kernels and distributions to try to identify the problem. I also will provide an update.

Good luck!

---

### Post by venzislav on 2020-03-10
The same thing with my hardware : 

[h=1]Lenovo IdeaPad S340-14API[/h]

[LIST]
[*]AMD Dual Core R3-3200U Processor, 2.0 GHz (1M Cache, up to 3.5 GHz)
[*]8 GB DDR4
[*]256 GB SSD | &#1052;.2 PCIe NVMe (2280)
[*]AMD Radeon Vega 3
[/LIST]

---

