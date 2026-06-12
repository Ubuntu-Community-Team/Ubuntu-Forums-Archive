---
title: "Nvidia-glx - 'E: Broken package' problem..."
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by eztoril on 2007-01-22
Hi all,

I recently upgraded my 2.6.17.10 kernel to kernel 2.6.19. However during the upgrade, I damaged my Nvidia graphics drivers. It worked before, showing an Nvidia splash screen at bootup.

When reading the 'HowTo's' concerning Nvidia driver installation, they all say that I should install 'nvidia-glx' driver. However, when trying to install 'nvidia-glx' through 'adept', 
I get **'BREAK (Install)'** message and **'apt-get install'** outputs the following error message:

[B]---------------------------------------------------------------------------------------
root > apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: nvidia-kernel-1.0.9629
E: Broken packages
root >
--------------------------------------------------------------------------------------[/B]

I have an Nvidia 7600 GS graphics card.

How do I solve this problem?

Does anyone have any idea how I uninstall my damaged install to be able to reinstall the 'nvidia-glx' driver again?

Thanks in advance!

Best regards,
Martin

---

### Post by Sef on 2007-01-22
> How do I solve this problem?


System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages.

---

### Post by allio on 2007-01-27
I have this exact problem, also with a 7600GS. Clicking 'fix broken packages' claims that it successfully fixed broken packages, but doesn't change a thing.

Edit: ah, looks like it was unofficial repo madness. Probably beryl! Never mind :p

---

