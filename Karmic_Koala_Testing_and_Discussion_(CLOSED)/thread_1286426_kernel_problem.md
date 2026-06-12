---
title: "kernel problem"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wfp on 2009-10-08
Your system encountered a serious kernel problem.Your system might become unstable now and might need to be restarted. EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded. Just started getting this message today with latest updates. Any one else seeing this.

---

### Post by hal10000 on 2009-10-09
You are not the only one, See this bug-report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536)

---

### Post by wfp on 2009-10-09
Thanks for the info. I added my self to list.

---

### Post by wfp on 2009-10-13
With the new updates to 2.6.31-13 Error messages are resolved.

---

### Post by wfp on 2009-10-22
So I am getting the same error message again with the 2.6.31-14-Kernel. Looks like a regression. I am sure they will figure this out for the final. Hopes:)

---

### Post by fenian on 2009-10-23
I am also getting this error on 2 AMD 64 systems,one system displays the Apport crash error the other does not.both systems show the error in dmesg...
> 
[   13.802428] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   13.802651] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   13.802656] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   13.802657] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   13.802658]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   13.802659]     Might be a BIOS bug, if BIOS says ECC is enabled
[   13.802660]     Use of the override can cause unknown side effects.
[   13.802670] amd64_edac: probe of 0000:00:18.2 failed with error -22

---

### Post by stephanvaningen on 2009-10-25
> **wfp said:**
> So I am getting the same error message again with the 2.6.31-14-Kernel. Looks like a regression. I am sure they will figure this out for the final. Hopes:)
Idem dito

---

### Post by holysmokes on 2009-10-26
I can confirm the same problem. Is there a walk through, or some way I disable this? I have used every other version of Ubuntu up until Karmic.. My hardware has been the same this entire time, for years. Yet, I am now encountering this error message.. and I don't know how to ecc_enable_override  from the command line..

---

