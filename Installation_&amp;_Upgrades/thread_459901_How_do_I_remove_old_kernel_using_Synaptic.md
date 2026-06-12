---
title: "How do I remove old kernel using Synaptic?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by BigSilly on 2007-05-31
OK, I've been using my Ubuntu PC quite happily since the latest kernel upgrade, and reckon I should be safe to remove the old one now. I've had a good read around the forums and understand it's safe to do using Synaptic, but after looking in Synaptic it seems there are a lot of choices. Could somebody recommend the safest way to remove the old kernel using Synaptic please, and let me know exactly which packages I should be removing? Also, do I mark them for complete removal or just removal, and will this update my GRUB menu, as I dual-boot? Thanks all.

---

### Post by floke on 2007-05-31
Just uncheck the kernel in synaptic - I think you can safely select the purge or complete uninstall option - and it will take care of the rest (i.e. the packages to remove). There's no need to remove it though, and I would recommend leaving it on. When the next update comes through you can then remove it. I always like to have at least 2 kernels ready in case something goes wrong!

---

### Post by BigSilly on 2007-05-31
Thanks for your advice. I'll probably keep it as you say then, but I'd still like to know which boxes I would have to select in Synaptic for future reference please.

There seems to be so many options in Synaptic, and selecting any one doesn't automatically select the other relevant options as it would with dependencies etc. Entries relating to kernel 2.6.20.15 are Linux Headers, Linux Headers Generic, and Linux Image Generic. These are the boxes that are marked green and are installed packages. Would I remove them all?

---

### Post by AlexenderReez on 2007-05-31
> **BigSilly said:**
> Thanks for your advice. I'll probably keep it as you say then, but I'd still like to know which boxes I would have to select in Synaptic for future reference please.

There seems to be so many options in Synaptic, and selecting any one doesn't automatically select the other relevant options as it would with dependencies etc. Entries relating to kernel 2.6.20.15 are Linux Headers, Linux Headers Generic, and Linux Image Generic. These are the boxes that are marked green and are installed packages. Would I remove them all?

install new kernel image......it is better install with its header...while using new kernel....remove old kernel image and its header......that is all.....

---

### Post by floke on 2007-05-31
If I wanted to remove 20.15 I would do a search in synaptic for 20.15 and remove everything - image, headers etc. - that it came up with.

---

### Post by BigSilly on 2007-05-31
> **Steve.K said:**
> If I wanted to remove 20.15 I would do a search in synaptic for 20.15 and remove everything - image, headers etc. - that it came up with.

And you're quite sure that's safe to do? It's not going to affect my current kernel?

---

### Post by floke on 2007-05-31
Yes its fine. If you try to remove your existing kernel you get a message saying that doing so could make your system unstable (bit of an understatement really), so don't worry, if you don't see such a message then you're fine; but as I say, unless you've got a real need for disc space then you can just leave it on. If you want to make it invisible during the grub menu then just edit your /boot/grub/menu.lst file and put a # in front of all the entries referring to the old kernel.

---

### Post by BigSilly on 2007-05-31
Many thanks for your detailed reply. I am definitely going to leave it on now, as it makes sense to do so as you say, but I will probably instead edit the GRUB menu. 

Thanks again for your help.

---

### Post by floke on 2007-05-31
btw: ALWAYS make a backup of any system files you edit, before you edit them (probably a bit late now, but I'm sure you didn't bork anything). The format is sudo cp [what] [where] - eg

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

---

