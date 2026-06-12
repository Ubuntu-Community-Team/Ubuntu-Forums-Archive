---
title: "Dualboot Win7 x64 with ubuntu on a HP ProBook with UEFI and HP ProtectTools, how to?"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by ScavengerProductions on 2012-07-23
Hi,
I currently have a a HP Probook 4320s with UEFI. It has a Intel Celeron P4600 CPU. Windows 7 Professional x64 is installed on the computer, where HP has supplied ProtectTools which allows Windows and the UEFI to "communicate" meaning that at boot I enter my password in UEFI, but I'm not required to enter my password at Windows login. Windows is still password protected, ie. if I lock my computer etc. I have to enter my password. So-called PreBoot Authentication.  

The question I have is if it's possible to dualboot the system with (any, but preferably 11.04) ubuntu without disrupting this process?

I have installed ubuntu several times, also dualboot, on non-UEFI computers and I'm familiar with the partitioning etc. in those instances. Is there anything I need to be aware of when installing ubuntu on a UEFI system?

Also, in the UEFI under Boot Options, the "UEFI boot mode" is disabled and gives a warning: "The 'UEFI Boot' option on this system is provided for development purposes and is currently NOT fully supported or warranted by HP. PreBoot Authentication and Drive Lock are currently NOT supported under the UEFI Boot mode. HP strongly recommends disabling Preboot Authentication and Drive Lock before enabling UEFI Boot on this system."

Does this mean that the computer is not currently using UEFI when booting? I have very little experience with this. Anyone care to explain and/or reference somewhere that explains this?

Many thanks in advance,
ScavengerProductions

---

### Post by oldfred on 2012-07-23
Post your partition table from the liveCD terminal.

This should not work or just report it is gpt,and  if UEFI as it will be gpt.

sudo fdisk -lu

This will work:

sudo parted /dev/sda unit s print

---

### Post by ScavengerProductions on 2012-07-23
Sadly, I'm not as experienced with the linux commands, I'll create a liveCD and post the results however. 

(This is why I need ubuntu on this computer, going to learn ubuntu more in-depth at school)

EDIT: the screenshot [IMG]http://i.imgur.com/Ggld4.png[/IMG]

---

