---
title: "Fresh clean install 10.10 goes fine. On reboot it hangs"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by pacut on 2010-10-22
Fresh clean install of kubuntu 10.10 (I formatted previous 10.4 working version). The istall needs some settings by F6 key ("nomodeset"), anyway I successfully installed everything.

On reboot:
- no grub menu (I assume this is fine as long as I don't have other OS installed)
- splash screen comes up, Kubuntu text is visible, and animated dots are visible.
- system tries to switch to kwin for their boot splash screen -> screen garbage and system freezes.

I am willing to launch the system in safe graphics mode. I tried pressing "ESC" or pressing "e" at the very beggining. No way.
I tried to launch LiveCD, pressing F6, adding "s" or "S" or "safemode" under "boot option". No way. System goes ahead and gets hung.

How the hell can I have Kubuntu starting in safe mode ?

I do believe the issue is related to my NVIDIA card (GE Force 8400), so I assume I should replace the driver by "additional driver" tool. Doing this requires safe graphics mode, I assume. Am I wrong ?


Looking forward in getting some suggestions by you.
THANKS

---

### Post by coffeecat on 2010-10-22
> **pacut said:**
> - no grub menu (I assume this is fine as long as I don't have other OS installed)

....

I am willing to launch the system in safe graphics mode. I tried pressing "ESC" or pressing "e" at the very beggining. No way.

With grub2, you need to press SHIFT, not ESC, to reveal the hidden menu. Then you can try adding nomodeset to the boot parameters by pressing 'e' (if I remember correctly) to edit the boot stanza.

If this lets you boot up successfully, you can add nomodeset permanently to your grub boot options by specifying it in the GRUB_CMDLINE_LINUX line in /etc/default/grub and then running 'sudo update-grub'. See here for more:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

There should be instructions there for unhiding the grub menu if you want. Hopefully, that will get you booting until you find a more satisfactory fix.

---

### Post by pacut on 2010-10-25
Correct !
I pressed SHIFT and then was able to customize my Grub.
Everything works now !

Thanks !
paolo

---

