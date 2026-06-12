---
title: "USB ports are disabled the moment Ubuntu 10.04 Server installation starts"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by Mohsen_Hameed on 2016-02-07
Hi All,

I am facing quite a strange behavior on this Gigabyte 9100 D3V board while installing Ubuntu 10.04 Server AMD x64.
 
**Problem:** All USB ports are working until I select Install Ubuntu Server on this machine option. After it the screen appears for selection of Language but no USB port is working at this moment. Following are details:
 
OS to be installed: Ubuntu 10.04 AMD x64 Server
Motherboard: Gigabyte 9100 D3V
 
UEFI: UEFI enabled with CSM (means Legacy and UEFI both work)
I have also tried legacy only. But that made no difference.
 
What I have tried?
I tried different combination of UEFI and Legacy boot mode using CSM. Attached screenshot also explain the situation.
 
Please tell me how can I solve this problem?
 
Looking forward to your feedback. Thanks

---

### Post by QIII on 2016-02-07
Before we get too far on this:  You do realize that 10.04 has reached End of Life (EOL) and is no longer supported, do you not?

I would suggest installing a current LTS release of Ubuntu Server (12.04 or 14.04 -- and I would further suggest 14.04 since it is supported until 2019) before proceeding further.

---

### Post by Mohsen_Hameed on 2016-02-07
First thank you QIII for quick reply. 
I do know that its going to be obsolete soon. But I have to use it since many of my company products are developed for this particular version i.e. Ubuntu 10.04. For now I don't have option to use any other. 
Could you please help me solving this problem for now. Thanks

---

### Post by QIII on 2016-02-07
Not soon.  It is already EOL as of April 2015.  I would highly recommend that your employer/clients/customers upgrade if this used for mission-critical assets.

Wait a moment while I find a thread discussing some options for you.

Edit:  Yours is not the same motherboard (I think yours is pretty old, is is it not), but I think you may possibly be running in to a common issue with may Gigabyte boards.

Please have a look at post #31 [here]("http://ubuntuforums.org/showthread.php?t=2111223").

If you do not have a setting for IOMMU for that board, it may be much too old for this to work.

You may need to use a PS/2 mouse and keyboard initially.

---

