---
title: "Trying again but I need a little help..."
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by LinuxUser007 on 2011-09-10
:KS So I have an HP dv7 AMD Phenom(tm) II N620 Dual-Core Processor 2.80 GHz. 4.00GB (3.74 GB usable) 64-bit Operating System. I did the partitions to install Ubuntu for being my 1st time with Linux I think I did good after the 3rd try. My Ubuntu and Window7 both worked fine but as I checked on my computer Ubuntu ignored (or I messed up) the three partitions I made for it. So I had 4 partitions 3 empty and one with both Windows7 and Ubuntu with little memory left to do much and 3 empty partitions that had nothing on them. What did I do wrong? I restored the laptop back to factory setting and its ready for me to try again. Since I'm new to linux I need help...I try to do it on my own but my 1st time my laptop crashed and the 2nd only Ubuntu worked lol But I refused to give up on linux...So I think its time to ask for help...:confused: Help me please! lol ](*,)](*,)

---

### Post by 2F4U on 2011-09-10
What kind of partitioning did you do? If you did manual partitioning, did you assign mount points (for example /home) the freshly created partitions?

---

### Post by saltmarshlamb on 2011-09-10
If you are trying to install to partitions that you've previously created - when you get to the partitioning part of the install you need to pick 'Something Else'

Then as 2F4U says you need to manually assign mount points.

As you said you created 3 I assume they were for swap, / and /home

Select each partition - Edit and then in the new window you can assign mount points for / and /home, for the swap you just need to tell it that its swap in the format box.
[https://help.ubuntu.com/community/GraphicalInstall#To_Install_Ubuntu](https://help.ubuntu.com/community/GraphicalInstall#To_Install_Ubuntu)

---

