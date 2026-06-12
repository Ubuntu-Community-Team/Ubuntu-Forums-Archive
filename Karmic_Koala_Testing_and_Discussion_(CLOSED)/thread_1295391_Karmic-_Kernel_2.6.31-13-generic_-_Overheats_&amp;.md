---
title: "Karmic- Kernel 2.6.31-13-generic - Overheats &amp; shuts down"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PereUbu on 2009-10-19
My Acer 5315 laptop overheats and shuts down a few minutes after boot.

EDIT: This started after upgrading to beta-version (kernel 2.6.31-11-generic). Kernel 2.6.31-13-generic & 2.6.31-14-generic is no good either.

When running alpha-version (kernel 2.6.31-10-generic), everything is fine.

Can someone help me? 

(I have tried to file a bug in launchpad but I can't really figure out how:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))

> lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


---

### Post by VMC on 2009-10-19
Does this have something to do with fan control.

[http://ubuntuforums.org/showthread.php?t=230673](http://ubuntuforums.org/showthread.php?t=230673)

---

### Post by PereUbu on 2009-10-19
Thanx for the link. 

Frankly, I have no idea!!?? (too geeky stuff for me) 

All I can say is that it overheats with beta-version kernels. With alpha-version kernel it does not overheat. 
EDIT: The fan makes a lot of noise when on beta-kernels, and when on alpha-kernel it is mostly silent.

With my limited knowledge I would ask:
Is this a kernel problem? 

How do I file a bug-report on this issue? (I do have an account)

I have tried:
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect) 
and nothing happens

I have also tried:
[http://bugs.launchpad.net/ubuntu/+source/linux/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/linux/+filebug?no-redirect)
without getting through

Is there anybody else experiencing the same problem?

---

### Post by Eclipse. on 2009-10-19
Hi, this is definitely a kernel problem so to file a bug report do the following,

Hit Alt + F2
Then type: ubuntu-bug linux
Then click run

The ubuntu-bug command is best to be used to report all bugs, just type "ubuntu-bug [package name]"

This will collect info for the developers to fix the problem and will open a web page for you to file the bug.Then just give some details of your problem, be sure to mention that the problem wasnt present on the alpha. :)

---

### Post by PereUbu on 2009-10-19
Thanx for good advice!

All went well, except for me getting a timeout when hitting the 'submit bug report' button. 

Seems like launchpad is overloaded....

I'll try again tomorrow.

---

### Post by allsafeboy on 2009-10-19
Same laptop, same issue. I started using karmic around alpha 5. Last week when I upgraded the kernel went from 2.6.31-12 to 2.6.31-14. The fan runs with 2.6.31-12 but does not run with 2.6.31-14. I've been booting up with 2.6.31-12 to get around it.

I look forward to hearing more. Can you link your bug report?

---

### Post by novafluxx on 2009-10-19
Yeah, just upgrade to the latest kernel, and see what happens

---

### Post by allsafeboy on 2009-10-19
Thanks.

I tried that. I updated a few hours ago and it it did not help.

---

### Post by novafluxx on 2009-10-19
> **allsafeboy said:**
> Thanks.

I tried that. I updated a few hours ago and it it did not help.

Does the Acer include any onboard diagnostic program you can run, something at the BIOS level, like the Dell PSA diagnostics?

Do you have another OS installed that you can test this with (Windows?)? Perhaps an Ubuntu 9.04 LiveCD or another *NIX distro?

---

### Post by allsafeboy on 2009-10-20
> **novafluxx said:**
> Does the Acer include any onboard diagnostic program you can run, something at the BIOS level, like the Dell PSA diagnostics?

Do you have another OS installed that you can test this with (Windows?)? Perhaps an Ubuntu 9.04 LiveCD or another *NIX distro?

Not sure about any Acer diagnostic. The BIOS doesn't let you mess with much. I'll try to see if i can dig something up tomorrow.

I've been running ubuntu on this machine since 8.04. First time this has popped up. After doing a little searching it looks like there have already been a couple of bug reports:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453700](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453700)

Thanks.

---

### Post by icek on 2009-10-20
I may be affected by this too. I have HP 6735s, on karmic teperatures are between 75 and 95 °C. If I try run 3D game, my notebook hangs in few minutes... some times sensors report negative temperatures. Everything was ok in Jaunty...

---

### Post by 6205 on 2009-10-20
> **icek said:**
> I may be affected by this too. I have HP 6735s, on karmic teperatures are between 75 and 95 °C. If I try run 3D game, my notebook hangs in few minutes... some times sensors report negative temperatures. Everything was ok in Jaunty...

Sounds scary.. Man.. these things keeping me from using linux as primary OS. It will never be just working, like in Windows :( I simply cannot understand why it is still after so many years so unreliable, unoptimized etc.. in terms of drivers, system resources etc.

---

### Post by caryb on 2009-10-20
Count yourself lucky that your machine shuts down! I have a Lenovo T61 that got hot 2 days ago & now is toast. It seems to have fried the proccessor.


Cary

---

### Post by monte48lowes on 2009-10-26
I have the very same problem. I waited until the RC to reinstall karmic over jaunty. (I did a fresh install to shift from ext3 to ext4). The fan comes on during BIOS POST, but after the kernel loads the fan shuts off and does not come back on. 

There are known issues with the fan during suspend to disk or suspend to RAM. The fan has not come back on for either of those conditions. I dealt with that since my first install of 7.10. I can live with it.

I cannot currently use the laptop for more than 20 - 30 minutes before it shuts down, unless I place a fan under the installed CPU fan.

Mike

---

### Post by icek on 2009-10-26
I'm back on Jaunty... everything ok here ;)

---

### Post by nowhere@cox.net on 2009-10-26
Wow, three days left to launch and Karmic is burning machines up! Ouch!

---

### Post by monte48lowes on 2009-10-26
I now have a working fan in karmic. I had to install windows, update bios to v1.43, then reinstall karmic. A pain in the buttocks for sure. But it is working now nonetheless.

I tried many different things to get the BIOS updated without first installing windows, nothing I tried worked. I might have made it, if I had an old floppy drive laying around.

Mike

---

### Post by dasunst3r on 2009-10-27
I had that happen to my notebook while I was on a business trip.  I thought my computer was on its way out, but I wasn't going to buy another computer without a fight.  I took it apart, blew out the dust, and replaced the thermal transfer goop with Arctic Silver 5.  Afterwards, I updated.  The computer's running happily since.

---

