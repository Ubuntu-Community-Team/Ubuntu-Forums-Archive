---
title: "grub does not appear to be loading, can select os via boot selection (bios screen)"
date: 2021-12-02
forum: Installation &amp; Upgrades
---

### Post by usbstick on 2021-12-02
Hello,

After installing Ubuntu, the system would just boot to Windows and I didn't get to see grub when starting the system. I am able to boot into Ubuntu by going to the bios screen and selecting any of the options marked in green (including the one labeled Windows Boot Manager 1 above the most bottom one; excluding P3 and P5 which I have stricken through with red). The option marked with blue will boot to Windows.

I installed Ubuntu onto the 1TB Samsung 980, Windows is also installed on this drive. Before installing, I resized my Windows partition using Gparted. The system uses uefi (motherboard: Gigabyte B150-HD3P).

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289565&stc=1[/IMG]

I have tried:

-Holding (right) shift during booting
-Installing grub via terminal

I have two questions:

1. What exactly is happening? Are these boot overrides items which are stored in a list somewhere on the disk? How does this work? In the past, on a different non-uefi system, I have dual booted Ubuntu and Windows, however this was with the MBR.
2. How can I make the system load grub so that I may select the OS I want when booting?

Thank you and best regards.

---

### Post by tea for one on 2021-12-02
Your screenshot suggests that you can boot either both Windows and Ubuntu via the UEFI boot options - so far so good.

You reduced your Windows partition with Gparted and it is generally better to use Windows utilities to manipulate Windows file systems.

Did you run [COLOR="#0000FF"]chkdsk[/COLOR] within Windows after installing Ubuntu?
When you boot Ubuntu in UEFI mode, you can reach Grub with [COLOR="#0000FF"]Esc[/COLOR]

As you can boot into Ubuntu (Windows must not be hibernating, encrypted etc.), have you tried 
```
sudo update-grub
```

Edit: The command above is executed via the terminal

---

### Post by oldfred on 2021-12-02
To see details of UEFI boot entries.
sudo efibootmgr -v
man efibootmgr

Is Ubuntu also in UEFI boot mode?
Is Windows fast start up off, so grub can add Windows to grub menu?

---

