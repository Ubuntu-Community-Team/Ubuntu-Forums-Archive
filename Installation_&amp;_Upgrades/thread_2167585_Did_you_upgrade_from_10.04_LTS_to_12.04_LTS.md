---
title: "Did you upgrade from 10.04 LTS to 12.04 LTS?"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by suomalainen on 2013-08-14
Hello Ubunteros!!!!

I have a Dell Inspiron 2200  running 10.04LTS. Now it's time to upgrade to 12.04.02 LTS.

The simplest way to go about this is to:

System --> Administration --> Update Manager       and then click "Upgrade".

On an older machine I had experienced a PAE not supported by CPU issues and want to be sure this does not happen again.


**Questions:**

1. I tried to find out if my Dell 2200 supports PAE but could not find the info I needed. What other approaches can I look at in order to find my answer?

2. How easy is the install via System -> administration? Any known issues?

3. Would it be better to format the partition Ubuntu is now on and do a clean install?

I run Ubuntu from a bootable usb external HDD. The attached screenshot shows how it is partitioned. As you can see it is Dual boot.
[B]
Questions:[/B]

4. Gparted indicated that /dev/sdb1/ has 1 flag issue that relates to boot (see screenshot 1) Then screenshot 2 states that content from this file system cannot be read. I have used this partition since 2010 and store data on it that is accessed on a daily basis. I find the warning hard to believe. Thoughts?

5. In past LTS releases I have copied the .evolution file to a secondary hard drive and then copied it back once the install was finished and each time my email was up and running without issues. This should also work with 12.04 right?

6. On the partition that indicates content cannot be read I have associated icons with each folder that is stored there. What is the best way to ensure that these icons for each associated folder can be seen once again after the install has completed?

Thanks for allowing me to share my questions. If additional information is needed just ask.

Thanks!

---

### Post by mastablasta on 2013-08-14
lshw 

command will give you the CPU and then you can check that PCU against list in wikipedia to see if it supports PAE.

3. yes, if you added soem porgrammes of oyur own and do not sue the preset install.

5. you will need to install evolution as it is not default email client anymore.

---

### Post by suomalainen on 2013-08-14
Thanks *Mastablasta!
lshw gave me

     *-cpu
          product: Intel(R) Celeron(R) M processor         1.40GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.13.8
          size: 1400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts

So it looks like I'm go to go on this point.

As per #3 can you explain little more what you mean?

Regarding #5 You can install evolution and as soon as the install is complete replace the .evolution folder with the one you backed up and You should be good to go.

---

### Post by Bucky Ball on 2013-08-14
*Thread moved to **Installation & Upgrades**.*

Cannot for the life of me fathom why this was in ***Absolute Beginners*** (you have nearly 1200 beans). Please post in the appropriate sub-forums in future to increase your chances of help. 

A further heads up: Thread titles describing your actual question more specifically might also speed things up. This one doesn't address your issue. There is also plenty of room here. Better to post different questions in different threads (this one asks about partitioning, Evolution, icons. Can/will get confusing).

Good luck.

(PS: I would do a clean install. 10.04 uses Gnome, 12.04 Unity. This can create problems and upgrades via the update manager can sometimes be problematic anyway, as attested to by the posts regarding that on this forum.)

---

