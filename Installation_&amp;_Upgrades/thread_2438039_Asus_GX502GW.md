---
title: "Asus GX502GW"
date: 2020-03-04
forum: Installation &amp; Upgrades
---

### Post by loutchoa on 2020-03-04
Dear Forum,

Did anyone manage to install Ubuntu on this laptop? 
I found only very little information about serious problems not being able to change SATA mode de AHCI.


François

---

### Post by oldfred on 2020-03-04
Is this similar to this Asus model.
Vendors often use same UEFI for multiple models with only slight differences for options.

---

### Post by loutchoa on 2020-03-09
Dear Forum,
I actually decided to send back the machine and get a Lenovo instead.
Anyway, here is the answer I got from Asus if it can help someone. 

François

>Dear François,
>
>Do note that we don't provide support Linux and if there should be any issues with installing or if it run's unstable then unfortunately wont be able to provide any support regarding the OS.
>
>
>You can disregard the previous comment with downgrading the BIOS, as that won&#8217;t change anything.
>Instead, you can try to disable secure boot and enable CSM (Compatibility Support Module), as that will provides legacy BIOS compatibility for other OS or ROM&#8217;s.
>this change is needed if Linux don&#8217;t support UEFI BIOS.

Please feel free to rate our service according to the solution provided in the
questionnaire that will be sent to you shortly after our reply to your inquiry.
Your satisfaction is very important for us. If you think we could
have done anything more to assist you please let us know by replying this email.
Your feedback will be passed to the person or persons related.

---

### Post by CelticWarrior on 2020-03-09
> Instead, you can try to disable secure boot and enable CSM  (Compatibility Support Module), as that will provides legacy BIOS  compatibility for other OS or ROM&#8217;s.
>this change is needed if Linux don&#8217;t support UEFI BIOS.

And again the typical bad/uninformed advice. Disabling Secure Boot is fine and recommended if you need to install unsigned drivers like the ones for Nvidia graphics or even virtual drivers for virtualization.
Enabling Legacy/CSM not OK, all modern Linux distros support UEFI and have been supporting it since almost a decade. And if dual-booting with a preinstalled Windows (mandatory UEFI mode since 2012) all the other OSes should be installed in the same mode or you'll have an hard time booting.

---

### Post by oldfred on 2020-03-09
Just about all vendors do not support Linux.
Even Dell with Linux system, may say it does not support installing Linux on its Windows systems. The support folks only have scripts for solving Windows issues.

---

### Post by CelticWarrior on 2020-03-09
> **oldfred said:**
> Just about all vendors do not support Linux.
Even Dell with Linux system, may say it does not support installing Linux on its Windows systems. The support folks only have scripts for solving Windows issues.

They do say that but it's across the board. Vendors support only the preinstalled OS in the consumer products. Servers have a list of supported OSes, mostly Linux.

---

