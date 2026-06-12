---
title: "Should I enable UEFI Secure Boot before changing hardware?"
date: 2021-02-11
forum: Installation &amp; Upgrades
---

### Post by sinceretrader on 2021-02-11
Hi,

I'll be replacing my** HP Pavilion (14bf175tx) **laptop's HDD in a few days. It is damaged and needs to be replaced. Additionally, I'm considering to upgrade it to an SSD instead.

But right now, I'm unable to install third-party drivers as it requires UEFI configuration via the MOK management tool. I need to install Nvidia graphics drivers to use Simulink + MATLAB for my college work.

[I]**My question is this: is it safe to enable UEFI Secure Boot right before changing my HDD? Could that mess up with any configurations in any way?**
[/I]
My guess is that I'll have to repartition my SSD and reinstall Ubuntu anyway, but I need to use some third-party drivers to function for the few days I'm not able to get things done.

BTW, I'm running **Ubuntu 20.04 LTS** on **dual boot** with Windows 10 preinstalled. Because of my damaged hard disk I'm unable to use Windows as of now.

---

### Post by CelticWarrior on 2021-02-11
Welcome.

It's safe with or without Secure Boot and enabling or disabling it has nothing to do with replacing HDDs or SSDs.
If you need to use proprietary drivers like Nvidia's then the usual advice is to simply disable Secure Boot in UEFI. Please note I'm saying UEFI mode + Secure Boot OFF, I'm not saying Legacy/CSM.

---

### Post by CelticWarrior on 2021-02-11
> [COLOR=#000000]BTW, I'm running [/COLOR]**Ubuntu 20.04 LTS**[COLOR=#000000] on [/COLOR]**dual boot**[COLOR=#000000] with Windows 10 preinstalled. Because of my damaged hard disk I'm unable to use Windows as of now[/COLOR]

You can reinstall both Windows and Ubuntu anytime. Or, specifically in this case, install in a new drive. In UEFI mode the order of the installation doesn't matter but still many users find it easier to install Windows first.

---

### Post by sinceretrader on 2021-02-11
Woah, thank you so much! I was in such a chaos for the last few hours, it's so reassuring to hear this. :)

---

### Post by crip720 on 2021-02-11
Have read that secure boot does funny things with stuff like updating [COLOR=#000000]Nvidia's [/COLOR][COLOR=#000000]drivers, so would recommend disable secure boot.  I have installed Windows after Ubuntu in UEFI once and did not have problem(not a recommendation).[/COLOR]

---

