---
title: "Grub Menu Disappears Everytime I Boot into WinXP"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by kiaran on 2011-07-06
I have Ubuntu 10.04 and WinXP Pro setup on a single hard drive. They both work great.

But every time I boot into XP, then restart my computer, Grub is gone! In fact the computer goes into an infinite loop of restarting.

I can use the live cd to repair Grub, but this only works until I need to go into windows again. So not really a solution at all and very frustrating.

Since I need to boot between OS's a lot, this is really, really damaging my workflow.

DOES ANYONE KNOW HOW TO TELL XP TO LEAVE MY MBR AND GRUB ALONE?

---

### Post by drs305 on 2011-07-06
There are several Windows apps that write to the same area of the MBR as Grub does. Each time you boot into Windows the app overwrites what Grub2 has added. These apps include Dell Data Safe, HP ProtectTools, Dell Recovery tools, and Adobe Flexnet, among others.

The solution seems to be to remove the offending application from Windows. Be careful about removing things, especially Dell tools. Dell provides a recovery partition that should be maintained, and a small utility partition which can be removed if desired.

---

### Post by YesWeCan on 2011-07-06
[edit] This won't work because the damage to grub is common to both booting methods.[/edit]
Interesting problem. I don't know how to fix it but I can suggest a work-around:
You can boot Grub from XP instead of XP from Grub: [http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

You need to make sure Grub is installed in the MBR. Boot into Ubuntu. Copy the MBR to a file (assuming your HD is sda):
[COLOR="Navy"]sudo dd if=/dev/sda bs=512 count=1 > grub.bin[/COLOR]
Then copy this file to your Windows C:\ folder.
Then follow the instructions in the link to add grub.bin to boot.ini.

---

### Post by YesWeCan on 2011-07-06
> **drs305 said:**
> There are several Windows apps that write to the same area of the MBR as Grub does. Each time you boot into Windows the app overwrites what Grub2 has added. These apps include Dell Data Safe, HP ProtectTools, Dell Recovery tools, and Adobe Flexnet, among others.

The solution seems to be to remove the offending application from Windows. Be careful about removing things, especially Dell tools. Dell provides a recovery partition that should be maintained, and a small utility partition which can be removed if desired.
Are you talking about the MBR boot code being overwritten or the core.img code after the MBR? I am just curious. If it were the latter then I would not expect Windows to boot at all. I ask because if the latter adding Grub to boot.ini will not solve the problem.

---

### Post by drs305 on 2011-07-06
> **YesWeCan said:**
> Are you talking about the MBR boot code being overwritten or the core.img code after the MBR? I am just curious. If it were the latter then I would not expect Windows to boot at all. I ask because if the latter adding Grub to boot.ini will not solve the problem.

It's an extended area that Grub 2 uses. It's just a few sectors after the MBR (as small as 32KB) and some Windows apps use it for serial numbers, DRM, etc. The Grub manual describes it as the area following the MBR and before the first partition. Since that is where the manual also describes the location of the core.img (if not installed on a partition), then it is possible it *is* the core.img that is being overwritten in this case. I have not seen this written anywhere but I think it can be inferred.

---

### Post by YesWeCan on 2011-07-06
> **drs305 said:**
> It's an extended area that Grub 2 uses. It's just a few sectors after the MBR (as small as 32KB) and some Windows apps use it for serial numbers, DRM, etc. The Grub manual describes it as the area following the MBR and before the first partition. Since that is where the manual also describes the location of the core.img (if not installed on a partition), then it is possible it *is* the core.img that is being overwritten in this case. I have not seen this written anywhere but I think it can be inferred.
I know for a fact that Grub installs boot code to sector 0 and kernel code (a slightly modified core.img) to sectors 1 to about 50.

I am not sure it would be plausible for a Windows app to overwrite the kernel in such as way that it still functions well enough to boot Windows. So I presume that the Grub boot code in the MBR would also have to have been replaced to enable Windows to boot.

So if the problem is just the MBR boot code, then using grub.bin in boot.ini will work. But if both the MBR code and the kernel sectors are being changed then the boot.ini will not work, because it relies on the kernel.

---

### Post by alphacrucis2 on 2011-07-06
> **YesWeCan said:**
> I know for a fact that Grub installs boot code to sector 0 and kernel code (a slightly modified core.img) to sectors 1 to about 50.

I am not sure it would be plausible for a Windows app to overwrite the kernel in such as way that it still functions well enough to boot Windows. So I presume that the Grub boot code in the MBR would also have to have been replaced to enable Windows to boot.

So if the problem is just the MBR boot code, then using grub.bin in boot.ini will work. But if both the MBR code and the kernel sectors are being changed then the boot.ini will not work, because it relies on the kernel.

From what I read of the OP I think he is saying that he can only boot windows once. After that nothing boots. Grub goes into a loop next time any boot is attempted after running windows.

---

### Post by YesWeCan on 2011-07-06
> **alphacrucis2 said:**
> From what I read of the OP I think he is saying that he can only boot windows once. After that nothing boots. Grub goes into a loop next time any boot is attempted after running windows.
Thanks, yes. That fits with the Grub kernel being damaged. So My suggestion to use boot.ini is of no use at all. So either the grub kernel must be relocated or the offending XP apps removed. Ok.

---

### Post by kiaran on 2011-07-07
@YesWeCan - Thanks for the suggestion of editing the boot.ini. But since even XP is not booting (just a an infinite loop of restarting), I don't think that will work (as you appear to have discovered yourself).

@drs305 - I don't have any of the applications you are describing. My machine is custom build. Very few running daemons. Maybe AVG anti-virus is the culprit. It and Skype are the only apps that run at startup. 

Time to test...

---

