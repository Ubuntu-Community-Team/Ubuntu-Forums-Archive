---
title: "Trusty 14.04 install on Hyper-V 2012 R2 doesn't have appropriate drivers for LIS?"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by Doug_Coleman on 2014-04-26
Hello,
I have recently created a brand new fresh gen 2 virtual machine on hyper-v and installed the recently released ubuntu 14.04 version.

Even after apt-get update, upon startup, my Windows server 2012 R2 Hyper-V server complains about downlevel drivers in the hyper-v eventlog  for

synthetic display driver:
Device 'Microsoft Synthetic Display Controller' in 'Dev Ubuntu 14.04 Gen2' is loaded but has a different version from the server.  Server version 3.3 Client version 3.2 (Virtual machine ID 9FC171E7-B2C6-4BD2-9FF0-253209B2A69D). The device will work, but this is an unsupported configuration. This means that technical support will not be provided until this problem is resolved. To fix this problem, upgrade the integration services. To upgrade, connect to the virtual machine and select Insert Integration Services Setup Disk from the Action menu.[COLOR=#262626][FONT=arial]  (of course this doesn't seem to work)
[/FONT][/COLOR]
and

data exchange integration service:
Hyper-V Data Exchange connected to virtual machine 'Dev Ubuntu 14.04 Gen2', but the version does not match the version expected by Hyper-V (Virtual machine ID 9FC171E7-B2C6-4BD2-9FF0-253209B2A69D). Framework version: Negotiated (3.0) - Expected (3.0); Message version: Negotiated (4.0) - Expected (5.0). This is an unsupported configuration. This means that technical support will not be provided until this problem is resolved. To fix this problem, upgrade the integration services. To upgrade, connect to the virtual machine and select Insert Integration Services Setup Disk from the Action menu (similarly, this doesn't seem to work).

Also, hyper-v complains that about the "Integration Services:  Update required" in the Summary tab withing the Windows 2012 R2 hyper-V Manager.

My (evidently mistaken) belief was that the Linux Integration Services had been integrated into the kernel, and thus Trusty would be compatible with 2012 R2 hyper-v services.

Can anyone explain where /how to obtain the updated Integration Services packages for 14.04 and the correct installation procedure so that my ubuntu virtual machines become fully supported using hyper-v 2012 r2?

Many thanks for your help,
Doug Coleman

---

### Post by Victor Miasnikov on 2014-05-07
>the Linux Integration Services had been integrated into the kernel, 
>and  thus Trusty would be compatible with 2012 R2 hyper-v services.

  Both is true

+ see

Abhishek Gupta ( Microsoft) :
==
You can ignore the above warnings as they are extraneous. Please refer the following KB article: 

==


[http://support.microsoft.com/kb/2956569/en-us](http://support.microsoft.com/kb/2956569/en-us)
===
**Cause**

The  various messages shown in the symptoms section occur because the  non-Windows guest integration services may not always have the code to  interoperate with the latest Hyper-V protocols. This is due to the fact  that Windows release cycles are not in sync with the release cycles of  other operating systems.    . . .

**Resolution**

Users  are hereby advised to ignore all messages and warnings that seem to  indicate that no technical support will be provided because integration  services for a non-Windows guest virtual machine are degraded. Microsoft  will provide technical support even if when such messages are visible  while running supported non-Windows guests on Hyper-V. Linux users may  review a list of supported distributions on Hyper-V on the following  page: [Linux Virtual Machines on Hyper-V]("http://technet.microsoft.com/en-us/library/dn531030.aspx")

Note  that it is safe to ignore these messages because Hyper-V protocols are  implemented to be backward compatible. Therefore, even if a certain  non-Windows guest has integration services that were based off earlier  Hyper-V protocols, the guest is expected to run flawlessly on newer  Hyper-V releases.**Note**  This is a "FAST PUBLISH" article created directly from within the  Microsoft support organization.  The information contained herein is  provided as-is in response to emerging issues.
===

---

### Post by juraj2 on 2014-08-17
gen 2 is only for Windows systems and what it does is only to speed up booting. Nothing else. For linux, use gen1

---

