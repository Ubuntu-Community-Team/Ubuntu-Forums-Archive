---
title: "Installing more than one Ubuntu version"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2010-08-27
I have had problems previously when i have updated my Ubuntu installation and have since started using xubuntu on my laptop. I am wondering if I should upgrade to the full 10.04 Ubuntu but am worried about the number of issues I had previously.

Is there a way to install the new version 'seperatly' to my current installation so that I can assess it first?

Thanks,

---

### Post by Nick_Jinn on 2010-08-27
Usuing virtual box is a fairly easy way of testing alternate versions within your main version. Parallels is also good.

Sometimes its been easy to use more than one version of Ubuntu, and sometimes when I am using offshoots they crash....like I cant use Mint with MoonOS, both Ubuntu based. I think there might be a problem with OSs that use Grub and ons that use Grub2.

Another solution is to simply have more than 1 desktop environment and choose at startup. A few of the settings will need to be adjusted every time you log in, but maybe ther are scripts to automate those changes? I am not skilled enough to do that, but I bet its easy for some people. 

Sometimes it works just fine. I had equally updated versions of Mint and Ubuntu Studio on the same hard drive and it worked great....I have problems though with Grub2 when it comes to multiple operating systems on multiple hard drive. I have only been able to use a second hard drive as a /data partition.

---

### Post by Rubi1200 on 2010-08-27
> **bigtel said:**
> I have had problems previously when i have updated my Ubuntu installation and have since started using xubuntu on my laptop. I am wondering if I should upgrade to the full 10.04 Ubuntu but am worried about the number of issues I had previously.

Is there a way to install the new version 'seperatly' to my current installation so that I can assess it first?

Thanks,
If you have enough space on the drive and are **very** comfortable with partitioning and booting (including knowing how to reinstall bootloaders when needed), then yes it is possible to do what you want.

For example, I have a test laptop that dual-boots Ubuntu Karmic and Lucid; I use Karmic for stable work and Lucid to test various features, play around trying to fix bugs etc.

However, I agree with Nick_Jinn that the safe option is to use something like VirtualBox.

---

