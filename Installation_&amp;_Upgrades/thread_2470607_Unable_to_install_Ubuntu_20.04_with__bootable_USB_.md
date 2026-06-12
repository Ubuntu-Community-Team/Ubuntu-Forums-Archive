---
title: "Unable to install Ubuntu 20.04 with  bootable USB drive on Lenovo Thinkpad T440p"
date: 2022-01-05
forum: Installation &amp; Upgrades
---

### Post by sstephen75 on 2022-01-05
[COLOR=#000000][FONT=Roboto]Hello folks, I downloaded the Ubuntu installation ISO file and then used Rufus to create a bootable USB flash drive.[/FONT][/COLOR]

[COLOR=#000000][FONT=Roboto]On a Lenovo T440p, I changed the boot sequence, it shows a black screen and does not progress past it.[/FONT][/COLOR]

[COLOR=#000000][FONT=Roboto]I tried booting this USB drive with a different laptop, and it seems to work, I am getting the Ubuntu screens. So the problem is not with the USB flash drive, but with the Lenovo 440p.[/FONT][/COLOR]

[COLOR=#000000][FONT=Roboto]What should I do next? TIA![/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]
[/FONT][/COLOR]

---

### Post by oldfred on 2022-01-05
Some with Lenovo have this UEFI setting or something similar. Allowing USB boot is also not "secure" so it may have a setting to prevent it.
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Many systems just have a setting saying allow USB boot or full USB support.

Many also need UEFI update to latest available from Lenovo.

May be similar. Lenovo has a lot of models.
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
 Lenovo T460S unable to update firmware fwupdate disabled boot order lock
[https://ubuntuforums.org/showthread.php?t=2455027](https://ubuntuforums.org/showthread.php?t=2455027)
Lenovo Thinkpad 430s UEFI update 19.10 install
[https://ubuntuforums.org/showthread.php?t=2432688](https://ubuntuforums.org/showthread.php?t=2432688)
[https://ubuntuforums.org/showthread.php?t=2450689](https://ubuntuforums.org/showthread.php?t=2450689)

---

### Post by sstephen75 on 2022-01-05
thank you oldfred for your prompt reply.

>[COLOR=#000000]Allowing USB boot is also not "secure" so it may have a setting to prevent it.[/COLOR]
i verified that the BIOS sets have UEFI boot disabled. Is there some command i can run to show it?

> [COLOR=#000000]The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
[/COLOR]I was able to enable this in the BIOS. Would you like photos of the screen?

> [COLOR=#000000]Many also need UEFI update to latest available from Lenovo.[/COLOR]
I will check on the UEFI update and get back. Will also check the other links you have provided.

TIA!

---

### Post by oldfred on 2022-01-05
You want UEFI boot, but maybe not UEFI Secure boot. Ubuntu will install with Secure Boot on. But proprietary drivers like nVidia may make it a hassle. 
You do not want legacy/BIOS/CSM boot as that is the old BIOS from before 2012. Microsoft has required UEFI boot using gpt partitioning since 2012. Ubuntu will let you install using old MBR and BIOS or UEFI. How you boot install media UEFI or BIOS is then how it installs. Only boot in UEFI mode.

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
See also link below in my signature.

---

### Post by MAFoElffen on 2022-01-06
Just a few notes...

I know on my ThinkPad, that it has both Intel and NVidia GPU's. For yours, if it does have NVidia, it was" optional" for your model (T440p). On mine, if I boot the the LiveCD image, without any boot options, the screen will be blank/black, while it is doing the file integrity checks... I know that it takes about a minute, to a minute and a half to be into those checks. If I don't do anything, it remains blank/black. 

I've done thousands of Linux installs, so I sort of know what to expect, and when. IDK... But I noticed on mine, that the USB activity light on the thumbdrive I was using was flashing, as if it was working on something, so I tried something...

If, during those checks, if I press <Cntrl><C>, which is the hotkey to cancel that test, then 20 seconds later, the video sorts out and resolves itself and is fine... 

I know that may seem like a quark, but it works. That doesn't 'seem" like that should be normal or even matter, but that is something that I did notice on my own machine, which is a ThinkPad. I have never seen it that way on any other machine, but since your's is also a ThinkPad, well...

Also, If I set mine in the BIOS to boot to discreet Intel Graphics, then it boots the install media as normal. If the BIOS is set to boot with the NVidia graphics, then at the Grub Menu, I add 'nomodeset' as a boot parameter, it also boots normally.

My BIOS settings are set to SecureBoot disabled, FastBoot disabled, UEFI boot first (mine does UFEI, then tries CSM). Boot Menu is the <F12> key while booting. Tab at that Boot Menu toggles to page 2 of the Boot Menu...

---

### Post by sstephen75 on 2022-01-16
thank you for your replies to help.

I wanted to put this note for others who might have this issue.

It seems like the issue was with the pen drive.
I used another drive - this time written with Yumi, which apparently uses a different method than rufus.

Also, I changed the bios settings to do both the legacy and uefi with legacy coming first.

finally, i had to write the iso with persistence, when i did without persistence, it failed.

I am now able to boot up the live image, and after that, installed ubuntu 20.04.

---

### Post by MAFoElffen on 2022-01-16
Happy that this is solved for you.

Please go to the "Thread Tools" Link on the upper right of the page to mark your thread as "Solved". That will help  other Users find your solution to help them with their similar problem.

---

