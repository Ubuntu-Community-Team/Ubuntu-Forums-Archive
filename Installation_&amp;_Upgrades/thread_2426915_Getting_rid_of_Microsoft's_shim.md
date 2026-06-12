---
title: "Getting rid of Microsoft's shim*?"
date: 2019-09-15
forum: Installation &amp; Upgrades
---

### Post by NovHak on 2019-09-15
Dear forum readers,

From what I understand, in UEFI mode when booting Ubuntu, a so-called shim signed by Microsoft is loaded first, which then loads the boot loader proper. That's because when UEFI is in standard, user mode, the firmware won't load anything at boot that's not signed by Microsoft.

However, I suppose that if I set my UEFI to custom user mode, enrolling my own PK and adding Canonical's key to the DB variable I could get rid of it and start the boot loader directly, finally having Ubuntu run, if I may say so, "like Windows" ?

Am I right ? If yes, two more questions arise :

[LIST=1]
[*]Are there pitfalls ? I never did that before but I think I would know how, however should I backup current variables first ? Because I don't know if switching from standard to custom will delete current KEK, DB and DBX variables, or if that behaviour is machine-dependent.
[*]Would my setup survive Ubuntu version upgrades ? Or would a future upgrade render my setup unbootable, thus needing additional steps each time ?
[/LIST]

I didn't install Ubuntu on my machine yet, but it's likely only a matter of time.

Your insights are welcome.

---

### Post by ubfan1 on 2019-09-15
Or just turn off secure boot to boot grub directly.  Your concerns about machine dependency are likely well founded.  Probably you would need to resign kernels/modules after each upgrade, I don't think that's been baked into the upgrade scripts (yet).

---

### Post by NovHak on 2019-09-15
Yea of course I could disable secure boot, but I want to keep it and retain its benefits while being able to authorise myself what I want it to run. Concerning the kernels, they're obviously signed already otherwise it wouldn't work with secure boot enabled, so my concern is more about the upgrade procedure not taking that non-shim configuration into account, which I think too is likely. What concerns me too actually, is that it seems one has to disable Secure Boot at the shim level (if I finally decide not to remove it) or UEFI (if I remove the shim) if I want to run third party drivers such as Nvidia's. I would like to authorise the modules instead, either through signing myself or by registering the module's signature, if it's already signed.

---

### Post by ubfan1 on 2019-09-15
Take a look at [https://ubuntu.com/blog/how-to-sign-things-for-secure-boot](https://ubuntu.com/blog/how-to-sign-things-for-secure-boot)

---

### Post by NovHak on 2019-09-16
Very interesting, thanks. While I was already familiar with certificate generation and digital signatures, I didn't know much about this shim functionality that frees me from having to put my UEFI on custom user mode. I didn't know the tools to sign COFF objects such as kernel modules. For the record, the OID mentioned (which I didn't know about but I made some investigations) has been created by Red Hat, and can be referred to sometimes as SHIM_EKU_MODULE_SIGNING_ONLY. I understand the logic behind it, though I'm not sure loading a compromised module is much better security wise than loading a compromised boot loader, both run in protection ring 0 anyway (if I'm correct).

Now that I know this I changed my mind however, I probably won't remove the shim after all !

---

