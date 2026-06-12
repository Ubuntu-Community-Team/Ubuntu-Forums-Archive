---
title: "Ubuntu 18.04 - screen size reverted back to default"
date: 2020-07-24
forum: Installation &amp; Upgrades
---

### Post by cedara2 on 2020-07-24
Hi,

this morning, when I booted the system up, my screen size reverted back to default and the system became pratically unusuable.

For reference: I have an nvidia GTX 750Ti, with the -435 driver. As from what I could recognize, it seemed visually similar to the last time when I was still using the nvidia-390 driver, I purged the driver (sudo apt purge *nvidia*) and reverted back to nouveau for the time being. 

I posted general question on Launchpad (German). Next I did the usual update/upgrade via terminal.  The only thing that was noticable in the update was: 

W: Possible missing firmare /lib/firmware/rtl_nic/rtl8125a-3.fw for module r8169

Now I wonder what I should do now, install the nvidia-440 drivers? They are recommended in the proprietary drivers section. Last time I changed to the 435 from 390. I'm unsure how to proceed, and yes, I do need the nvidia drivers.

---

### Post by cedara2 on 2020-07-24
Someone on launchpad suggested trying the 440, which I installed with:

sudo ubuntu-drivers autoinstall

sudo reboot

and it installed the 440 without any troubles so far. *knocks on wood*

---

