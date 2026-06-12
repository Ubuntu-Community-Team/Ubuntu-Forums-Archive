---
title: "How to apply patch for Atheros A9485, with missing base file"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by choct155 on 2013-07-31
Full disclosure >> this is my first time applying a patch, so any bits of information/points in the right direction would be appreciated. 

I am running a new ASUS laptop that came with Windows 8 installed on it.  After purchase, I immediately set up a dual-boot with Ubuntu 13.04.  Once I got it working, everything looked great except for the wireless signal strength.  I went through the well worn litany of remedies (which can be seen below), but ultimately I had no luck.  I subsequently upgraded my kernel to 3.9.0-030900-generic, but the issue persisted.  

At this point, a good samaritan in the IRC room pointed me to this bug: [https://bugzilla.kernel.org/show_bug.cgi?id=49201](https://bugzilla.kernel.org/show_bug.cgi?id=49201)  The testing there led to this patch:  [https://patchwork.kernel.org/patch/2718041/](https://patchwork.kernel.org/patch/2718041/)

I am afraid that all of the examples of patch application that I have seen were for kernel versions preceding 3.7.  The new site appears less straightforward to my novice eyes, and I am at a bit of a loss.  Nevertheless, from the patch examples I have seen (most notably this one:  [http://www.markusbe.com/2009/12/how-to-read-a-patch-or-diff-and-understand-its-structure-to-apply-it-manually/)]("http://www.markusbe.com/2009/12/how-to-read-a-patch-or-diff-and-understand-its-structure-to-apply-it-manually/") I think I have the basic idea.  The trouble is, when I navigate to the what I think is the appropriate directory, I do not see the file that the patch I am supposed to modify.  

There is another issue as well. It looks like, from the bug, that I am supposed to apply this on top of 3.10-rc5.  I was under the impression, however, that it was a bit premature to delve into Saucy Salamander.  Is it possible to apply the patch to the Raring Ringtail version of 3.9 since 3.10-rc5 sits between 3.9 and 3.10?  Do I need to upgrade to the latest mainline release?

```
choct155@choct155-Q550LF:/lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/ath/ath9k$ pwd
/lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/ath/ath9k
choct155@choct155-Q550LF:/lib/modules/3.9.0-030900-generic/kernel/drivers/net/wireless/ath/ath9k$ ls
ath9k_common.ko  ath9k_htc.ko  ath9k_hw.ko  ath9k.ko
```

I am sure I am missing something basic here, but if someone could provide a little assistance, I would be grateful.  Happy to provide any additional information.


***************************************************************************
##Disabling Power Management

Evidently the power management daemon hinders the perfomance of the network adapter.  I turned this off:

1.  Create /etc/pm/power.d/wireless with the following contents.

    #!/bin/sh
    /sbin/iwconfig wlan0 power off


##Modified 'Debian Avahi' daemon

1.  Open /etc/nsswitch.conf
2.  Make the following change
    Old:  files mdns4_minimal [NOTFOUND=return] dns mdns4
    New:  files dns


##Modify ATH9K Driver

1.  Append the following to /etc/modprobe.d/ath9k.conf

    options ath9k nohwcrypt=1


##Disable n Network Capability
#Note: after a little more digging, I realized this was worthless because I was attempting to modify the wrong driver.

1.  Create /etc/modprobe.d/iwlwifi-disable11n.conf with the following contents:

    options iwlwifi 11n_disable=1


##Deactivate IPv6 Capability

1.  Append the following to /etc/sysct1.conf

    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1
*************************************************************


Hardware:
[LIST]
[*]ASUS Q550LF 
[*]RTL8111/8168 PCI Express Gigabit Ethernet controller 
[*]Atheros AR9485 Wireless Network Adapter 
[/LIST]

---

### Post by choct155 on 2013-08-02
Just in case someone else has this issue, or any issue with the Atheros card signal strength, a much easier solution has been passed my way (thanks starsseed ([http://askubuntu.com/users/180427/starsseed](http://askubuntu.com/users/180427/starsseed))).  Once you have the right file, backporting is quite easy:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809/comments/63](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/971809/comments/63)  

The link includes instructions as well.  My signal strength issue has vanished.

---

### Post by nagual on 2013-08-20
Was there a specific guide you used to get through the UEFI boot issues, and the apparent graphics driver issues?  I was able to disable secure boot and can boot into ubuntu by hitting the escape key during post to boot to ubuntu, but can't get any gui to come up.

---

