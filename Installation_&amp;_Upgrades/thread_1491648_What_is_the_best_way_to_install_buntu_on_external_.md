---
title: "What is the best way to install *buntu on external HDD?"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by D1Knight on 2010-05-23
What is the best way to install a *buntu to external HDD? FYI-external HDD is much faster than my internal HDD. Also, I want to be able to boot from external HDD. I do understand adjusting BIOS to read external HDD first. Thanks for any help.:)

I made an attempt, already to install Kubuntu to external HDD. It did not work, would not boot/read from external HDD. I used internal HDD, to check contents of external HDD and it appears the Kubuntu OS files are on the external.

---

### Post by leclerc65 on 2010-05-23
Put Grub onto the external HDD as well ? (In the last step before the installation, click on 'Advanced' ...).
I often test distros on my eeePC using SD cards that way, should be the same for your case.

---

### Post by wilee-nilee on 2010-05-24
> **leclerc65 said:**
> Put Grub onto the external HDD as well ? (In the last step before the installation, click on 'Advanced' ...).
I often test distros on my eeePC using SD cards that way, should be the same for your case.

That is the way, also I just use a key prompt to choose what to boot from, f12 is the usual but the opening screen tells you what key it is you just have to look fast.

---

### Post by mahershi on 2010-05-24
Hi! Here is what I did some time back:

My laptop came with Vista installed on it (yeah! that was ages ago). Then I decided to switch to Ubuntu (this was probably in the 7.x or 8.y time line). So, here is what I did:

1. Bought an extra SATA laptop HDD
2. Also bought an hdd enclosure ... that came with USB cable for connecting the enclosure to my laptop
3. Pulled out the original HDD (with Vista) from my notebook
4. Installed the new HDD (blank) into the notebook
5. Boot from Ubu liveCD and installed it on the new HDD
6. Reboot the system to make sure things were working fine
7. Pulled out the new HDD (with Ubuntu on it) and put it into the enclosure
8. Put the original HDD (with Vista) into the notebook and boot up the notebook to ensure Vista worked (duh!)
9. Then connected the external HDD (with Ubuntu) over USB to the notebook and boot the notebook from the USB drive

With this setup I was able to choose what OS to boot without putting them both on the same HDD. Also, since most of my data was on my Vista partition, I could open/read/write it in Ubuntu.

Eventually, I realized that Vista really sucked. So, I removed the Ubuntu HDD from the enclosure and installed it as the only HDD in the laptop. The Vista HDD became my LARGE data drive (although Vista did eat some significant part of that drive).

HTH!

---

### Post by D1Knight on 2010-05-24
> **leclerc65 said:**
> Put Grub onto the external HDD as well ? (In the last step before the installation, click on 'Advanced' ...).
I often test distros on my eeePC using SD cards that way, should be the same for your case.

Hi leclerc65.:) Thanks for your post. Right on, that is exactly what I did (advanced step). When I re-booted, with BIOS changed to read external HDD 1st, I just got a blank screen. I shall attempt again, maybe it will take a little longer to read/boot?:confused:

---

### Post by D1Knight on 2010-05-24
> **wilee-nilee said:**
> That is the way, also I just use a key prompt to choose what to boot from, f12 is the usual but the opening screen tells you what key it is you just have to look fast.

Hi wilee-nilee.:) Thanks for the f12 hint, that is very useful.

---

### Post by D1Knight on 2010-05-24
> **wilee-nilee said:**
> That is the way, also I just use a key prompt to choose what to boot from, f12 is the usual but the opening screen tells you what key it is you just have to look fast.

Hi wilee-nilee.:) Thank you for the f12 hint, that is very useful.

Oooops. Duplicate post. Sorry.

---

### Post by D1Knight on 2010-05-24
> **mahershi said:**
> Hi! Here is what I did some time back:

My laptop came with Vista installed on it (yeah! that was ages ago). Then I decided to switch to Ubuntu (this was probably in the 7.x or 8.y time line). So, here is what I did:

1. Bought an extra SATA laptop HDD
2. Also bought an hdd enclosure ... that came with USB cable for connecting the enclosure to my laptop
3. Pulled out the original HDD (with Vista) from my notebook
4. Installed the new HDD (blank) into the notebook
5. Boot from Ubu liveCD and installed it on the new HDD
6. Reboot the system to make sure things were working fine
7. Pulled out the new HDD (with Ubuntu on it) and put it into the enclosure
8. Put the original HDD (with Vista) into the notebook and boot up the notebook to ensure Vista worked (duh!)
9. Then connected the external HDD (with Ubuntu) over USB to the notebook and boot the notebook from the USB drive

With this setup I was able to choose what OS to boot without putting them both on the same HDD. Also, since most of my data was on my Vista partition, I could open/read/write it in Ubuntu.

Eventually, I realized that Vista really sucked. So, I removed the Ubuntu HDD from the enclosure and installed it as the only HDD in the laptop. The Vista HDD became my LARGE data drive (although Vista did eat some significant part of that drive).

HTH!

Hi mahershi.:) Thanks for your post, very informative. Ok, so it is possible to boot from either external and internal HDDs.

---

### Post by D1Knight on 2010-05-26
Yes! Solved.:guitar: When installing a *buntu to external HDD, the last step in install process-click advance button and install bootloader (GRUB)to external HDD. Make sure it is marked to correct location (mine was sdb not sda).

FYI- after install and BIOS was set to read external B4 internal, I had to restart twice (shrugs:confused:)YMMV. This was only the first time, now boots up proper to external HDD, every time there after.

Thanks to all the posters for their help and advice.

I hope this will help someone else, too.:)

---

