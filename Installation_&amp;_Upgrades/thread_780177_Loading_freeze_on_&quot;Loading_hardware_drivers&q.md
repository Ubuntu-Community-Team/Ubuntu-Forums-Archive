---
title: "Loading freeze on &quot;Loading hardware drivers&quot;"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Capucha on 2008-05-03
Hi, i'm using a laptop HP pavilion zv5000.

After the installation of Ubuntu 8.04 Beta with alternate CD, or booting on the 8.04 Beta Desktop CD, the loading freeze on message "Loading hardware drivers".

Before this installation, all was good with Ubuntu 7.10, no problem on loading, except 2 messages just after Grub : "... PCI failed to allocate mem resource..." (with 7.04 6.10 and 6.06 too).

These lines doesn't appear with this new installation of Hardy Beta.

I just want to be sure that the final version of Hardy will work in these laptop ;-)

Thank you for your help.

---

### Post by hipsterical on 2008-05-03
same thing , this morning I received 15 upgrade packages including kernel 2.4.26.17 and when I rebooted (btw I was NOT asked for a reboot) this afternoon the system couldnt initialise - i think - the restricted NVIDIA modules, thus leaving me with a black screen. But the system was not actually frozen cause the USB was working .

temporary SOLUTION:
 After a forced shutdown and a reboot pressing the ESC key when prompted, load the PREVIOUS kernel (Ubuntu 2.6.24-16.30-generic) . goodbye bros

better solutions - and before all working packages - are welcome

---

### Post by hipsterical on 2008-05-03
solved. it's all with the "NEW" NVIDIA drivers which don't work at least with my NVIDIA GeForce4 MX 440 with AGP8X .

solution: boot the previous kernel, remove the "new" drivers, reinstall the LEGACY drivers and reboot. it worked for me. it's working right now. the Nvidia modules are working
 my running system according dmesg:
Linux version 2.6.24-17-generic (buildd@palmer) (gcc version 4.2.
3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 14:31:33 UTC 2008 (Ubuntu 2.6.24-17.
31-generic)
...
[   71.291633] nvidia: module license 'NVIDIA' taints kernel.
[   72.311042] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 2
2 19:36:58 PST 2008
[   72.353371] ns558 01:01.01: activated


goodbye for now, corrections welcome.

---

### Post by Capucha on 2008-05-03
how did you do it? I´m not a very advanced user of this sistem

---

### Post by PmDematagoda on 2008-05-03
> **Capucha said:**
> how did you do it? I´m not a very advanced user of this sistem

Your laptop seems to be having an ATi card, I am not very familiar with ATi cards so in your case you may want to boot Ubuntu in Recovery Mode and at the terminal execute:-
```
dpkg-reconfigure -phigh xserver-xorg
```
to configure the X-Server to use the vesa driver.

Then reboot the PC with:-
```
reboot
```

Also, something that is not directly concerning your problem, but you may want to use something other than Ubuntu since 256Mb of RAM(unless you had it upgraded) is not really enough to run Ubuntu flawlessly.

---

