---
title: "failing Ubuntu 18.04 installation on dell Latitude 5411 - business laptop"
date: 2021-10-12
forum: Installation &amp; Upgrades
---

### Post by mm28690 on 2021-10-12
Dell Latitude 5411 MLKXCTO, 
i710gen 1085H, NVIDIA-MX250 discrete graphics with thunderbolt TM3, 12 processors, 
1TB M.2 Pcle NVME class 40 SSD, 16GB RAM

Bought preinstalled with ubuntu 18.04 from Dell.

What system config- home, swap, Numa settings,  disabling NVIDIA before ubuntu edition 18.04? can you suggest for this laptop?
This is business laptop, so which ubuntu can I install? - server edition ?
What is the exact and best way to configure this laptop? Can you please provide some guideline ? I have referred to general guides out there but I need advice on system specific config for best.

Actually after NVIDIA driver purge, I freaked (black screen stuck) and recovered OS to factory state. after in between bios updates, etc the installation (using recovered iso) from bootable pendrive showed installer crashed. the system was stuck in OEM mode. Referring to one of the posts, I typed in OEM pw : password and it prompted for setup. I installed this. But still drivers and settings were not normal. Reinstallation with recovered factory iso from Dell keeps saying installer crashed" but sets-up account upon reboot. with std config 8GB swap , etc and no numa node settings. Also it sets up an oem kernel not generic ubuntu. Now my recovery partition is alos wiped off as I cant't see reset to factory OS option while logging in.
I have tried too many things. Please please help.

Is there a way to reach the person who actually installed prepped this particular laptop before shipping? - so that customized installation settings for this laptop can be recovered? Dell tech support has given up stating no support for ubuntu. I am stuck. Please help.

---

### Post by T6&amp;sfpER35% on 2021-10-12
i'd backup everything and do a fresh install of [20.04](https://ubuntu.com/download/desktop/thank-you?version=20.04.3&architecture=amd64)
why purge the nvidia drivers and update bios? i don't scratch where it doesn't itch...
like go back to basics

---

### Post by mm28690 on 2021-10-12
Thanks 3nd. Would this system support 20.04 since it was pre-installed with 18.04 LTS?
Also any idea why the kernel is oem and not generic?

The NVIDIA driver uninstall was wrt cuda uninstall.
The BIOS/kernel  update was prompted by ubuntu 18.04, in between when I had tried to recovered the OS to factory state.

---

### Post by T6&amp;sfpER35% on 2021-10-12
> [COLOR=#000000]Would this system support 20.04[/COLOR]
yes it would support 20.04
> [COLOR=#000000]since it was pre-installed with 18.04 LTS[/COLOR]
i don't see why not , almost all pc's are pre-installed with windows yet one can install linux on them
> [COLOR=#000000]The BIOS/kernel update was prompted by ubuntu 18.04[/COLOR]
not sure what you mean ,BIOS not the same as kernel i doubt an OS is going to ask to update BIOS

---

### Post by mm28690 on 2021-10-12
Actually Dell suggests not to upgrade unless specifically provided for the model.
Although I don't understand whether the ubuntu provided LTS and pre-installed LTS is very different or not, also when i tried downloading iso via dell and boot drive install, it failed all three times - stating crashed installer .Do i need to prepare the laptop with some settings wrt NVIDIA cards before installation?

---

### Post by T6&amp;sfpER35% on 2021-10-12
download the iso from 
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

---

### Post by ActionParsnip on 2021-10-12
You can install server edition if you like. Its the same as the desktop version but has no GUI. Considering this is a laptop it seems a bit counter intuitive but some people do run servers on laptops to repurpose them

---

### Post by mm28690 on 2021-10-12
Thanks ActionParsnip.

As mentioned here 
[https://ubuntu.com/certified/202002-27717](https://ubuntu.com/certified/202002-27717)

This exactly is my device and I would really like to have all the hardware advantage in Ubuntu experience. 

Is there a way to obtain this custom ubuntu set-up for my device?

---

