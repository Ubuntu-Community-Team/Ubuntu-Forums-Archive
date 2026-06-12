---
title: "porting kernerl driver modules from 7.04 beta to 6.10"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by uncleyap on 2007-04-17
I have this Asus motherboard M2NPV-VM which has Nvidia chipset GeForce 6150.

I need to run Ubuntu 6.10 for VMWARE Virtual Machines, but the motherboard's 6150 chipset wont' boot 6.10, I discovered that 7.04 Beta is however OK. This must be a kernel driver module support issue with the relatively new Nvidia 6150 chipset.

I am hoping to port some of Ubuntu 7.04 beta's source code to patch / compile 6.10, but no idea:) exactly how to go about it. Hope there is some experienced users in this community to advice.

Thanks & regards

---

### Post by codejunkie on 2007-04-17
> **uncleyap said:**
> I have this Asus motherboard M2NPV-VM which has Nvidia chipset GeForce 6150.

I need to run Ubuntu 6.10 for VMWARE Virtual Machines, but the motherboard's 6150 chipset wont' boot 6.10, I discovered that 7.04 Beta is however OK. This must be a kernel driver module support issue with the relatively new Nvidia 6150 chipset.

I am hoping to port some of Ubuntu 7.04 beta's source code to patch / compile 6.10, but no idea:) exactly how to go about it. Hope there is some experienced users in this community to advice.

Thanks & regards
you can run vmware in fiesty 7.10 you just need to download the vmware any any patch to patch it for the newer kernels fiesty uses.  i've attached the patch in this post i believe it is the latest version, but i can't find the link to the site where i downloaded it from right now, but if you search in the fiesty development section or on the vmware forums for the vmware any patch you should be able to find the site pretty easy hope this helps.
[ATTACH]29941[/ATTACH]

---

### Post by uncleyap on 2007-04-18
Thank you very much for the info.

Your message mention 7.10, I hope you are referring to 7.0.4,beta.  I am not aware of any 7.10:confused: 

I have read about this vmware-any-any-patch in VMWARE community online. But not sure it covers the betas or not.

I will try to use that on 7.04 and see if VMWARE 5 can be made to run on 7.04 Beta.

Regards

u.y.

---

### Post by uncleyap on 2007-04-18
I have just tried vmware-any-any-update109 on 2 different host PCs.

It helped perfectly on FC6 host which has kernel 2.6.20-1.2944.fc6 and made the WS5 run again. It had trouble after the AutoUpdate changed it kernel. Now that one is fixed.

On the other PC which I had to use Ubuntu 7.0.4 Beta which as kernel 2.6.20-12-generic vmware-any-any-update109 won't make any difference. It is sill not able to make VMMON showing same error as vmware-config.pl

This PC has Nvidia GeForce 6150 chipset (Asus M2NPV-VM) and Ubuntu 6.10 won't even boot. I think the SATA driver is the cause. FC6 also won't do on that Asus M2NPV-VM, and Ubuntu 7.0.4 Beta is the only thing I can get that system to work better - still no VM & no IEEE-1394. I had also tried Open SuSE 10.2 on this Asus M2NPV-VM board, it works, and it can run VMWARE WS5. But NO USB at all. Which means no thumb drive and have to use PS2 mouse. :( 

Regards

---

### Post by codejunkie on 2007-04-18
yes i was referring to the beta version Feisty 7.04 i just mixed the version number up, the any any patch works fine for me in Feisty.

---

### Post by uncleyap on 2007-04-19
May I request you to verify that 2.6.20-12-generic is your kernel verison? 64 bit AMD?

Thanks & regards

:)

---

