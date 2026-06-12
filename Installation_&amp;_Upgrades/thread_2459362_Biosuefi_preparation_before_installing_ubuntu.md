---
title: "Bios/uefi preparation before installing ubuntu"
date: 2021-03-17
forum: Installation &amp; Upgrades
---

### Post by dimitargeorgiev5 on 2021-03-17
Hello, guys,

I tried intsalling different distros, several times, and i cant firn a way to successfully find a way to have a dual boot. As far as my reading lead me i found that i have problems with my bios and its secure boot disabling. I am on an HP EliteBook 8560w, and it runs some strange version of Bios and i dont find an option to disable the Secure Boot. The bios version is 68svd ver F.63.

I would huighly appreciate any help.

Thanks

---

### Post by CelticWarrior on 2021-03-17
Does it have Nvidia graphics? If not, disabling Secure Boot is optional.
Problems with dual-booting in HPs aren't related with Secure Boot. You may need to explicitly select Ubuntu from the UEFI settings menu each time you wan to boot Ubuntu. Otherwise it might boot Windows regardless of the settings, that's the way it is with some HP models. Consider installing Ubuntu only if you really don't need Windows with access to the full hardware performance. You can install Windows in a VM inside Ubuntu.

I conclusion, please post your actual problem, not your assumptions.

---

### Post by dimitargeorgiev5 on 2021-03-17
Thank you for your answer.

I do have Nvidia hardware. I cant ditch windows, the first thing is that i need to use Exchange and many more apps on it.

---

### Post by CelticWarrior on 2021-03-17
The question is not about ditching Windows, the question is about needing it installed in "bare-metal" or as a virtual machine.
Exchange works fine in a VM. Unless the "many more apps" include video editing/rendering or games then there's no difference either.

Now, for the Nvidia graphics, the first thing to do is to make sure you're booting and installing in UEFI mode with Secure Boot disabled (you have UEFI, not BIOS, regardless of the persistence of the misuse of "BIOS" for UEFI hardware from some manufacturers). How to disable Secure Boot depends on your specific firmware. It may appear exactly as "Secure Boot" or buried under some unassuming names like "OS selection" where "Windows 8/10" means Secure Boot ON and "Other/ Windows 7/Android, Linux, etc. etc." means Secure Boot OFF. Please check your user's manual.

And, again, please describe your actual problem with the Ubuntu installation.

---

### Post by oldfred on 2021-03-17
The only other Elitebooks, in my notes and this one seems to have a unique setting in UEFI.
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

Elitebook 745 G2  Newbie trying to install Ubuntu as dual boot  with Windows10 us
[https://ubuntuforums.org/showthread.php?t=2412901](https://ubuntuforums.org/showthread.php?t=2412901)

---

