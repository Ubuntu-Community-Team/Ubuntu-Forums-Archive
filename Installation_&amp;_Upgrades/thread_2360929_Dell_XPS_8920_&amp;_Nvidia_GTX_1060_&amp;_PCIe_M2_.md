---
title: "Dell XPS 8920 &amp; Nvidia GTX 1060 &amp; PCIe M2 drive Raid : Dual boot Windows10/Ubuntu 16."
date: 2017-05-10
forum: Installation &amp; Upgrades
---

### Post by kracheck on 2017-05-10
When trying to install Ubuntu 16.04.2 on my PCIe based m2 drive, the installer could not locate a hard drive (the installer usually only looks for /dev/sdx by default).  My Dell XPS 8920 came with Windows 10 pre-installed on a PCIe M2 drive that was configured in BIOS as RAID. It also had Secure Boot enabled. First I disabled Secure Boot and then I followed below procedure to change RAID to AHCI (not following below procedure and simply changing RAID to AHCI resulted in Windows 10 not booting correctly).

Source : [http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

*Right-click the Windows Start Menu. Choose Command Prompt (Admin).
*Type this command and press ENTER: bcdedit /set {current} safeboot minimal
*Restart the computer and enter BIOS Setup (the key to press varies between systems).
*Change the SATA Operation mode to AHCI from either IDE or RAID (again, the language varies).
*Save changes and exit Setup and Windows will automatically boot to Safe Mode.
*Right-click the Windows Start Menu once more. Choose Command Prompt (Admin).
*Type this command and press ENTER: bcdedit /deletevalue {current} safeboot
* Reboot once more and Windows will automatically start with AHCI drivers enabled.

After that I shrank the Windows partition via Disk Management. Then I installed Ubuntu as follows.

Source : [https://www.dell.com/support/article/us/en/04/SLN299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=EN](https://www.dell.com/support/article/us/en/04/SLN299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=EN)

Insert the install medium (in my case a USB stick) and reboot. Hit F12 upon boot and choose the install USB to boot from.
When GRUB appears select &#8220;Try Ubuntu without installing&#8221; and hit e (e for edit).
Add the boot parameter nvme_load=YES as described in the link above and also add nomodeset (because in my case the nouveau drivers didn&#8217;t recognise the card and I ended up with a black screen).

In short : add nvme_load=YES", remove "quiet splash and replace with nomodeset to get something like &#8220;boot=casper initd=/casper/initrd.ls nvme_load=YES nomodeset
Hit F10 to boot and wait.
Once Ubuntu is runnining start the installation procedure.
Upon reboot add nomodeset again. In ubuntu select &#8216;additional drivers&#8217; and install the NVIDIA drivers. Reboot, select Ubuntu and hit enter.

---

### Post by stevensjw on 2017-08-12
Hello:

I am using Dell xps 8920,the same computer as yours, and i used your method to install the dual os windows10 and Ubunttu 16.04, but it still some mistakes about boot guide.
The two operating systems can work well if you boot it successfully, but when i reboot from the Ubuntu 16.04, it will show like these "Boot failure on device". If i don't use ubuntu and just use windows, it will be normal, the grub will appear, and you can choose these two operating systems. Once i used Ubuntu, the next time it will be wrong about starting the boot.  I don't know what's wrong with my computer and ubuntu system.
I think there is something wrong with the ubuntu boot guide, but i don't know how to repair it. Can you help me solve this problem? Thank you very much.

by the way, my GPU is Nvidia GTX 1070, CPU is i7 7700. I installed these two systems in SSD.

Best wishes.

Steven

---

### Post by oldfred on 2017-08-13
Does it boot ok, if you choose the ubuntu entry in UEFI boot menu, I think Dell is f12.
Is fast boot off in UEFI?
Fast boot assumes no system hardware or software changes and immediately starts boot as if system is identical to when shutdown.
Is Secure Boot in UEFI on or off?

---

### Post by stevensjw on 2017-08-13
I have made the Secure Boot off in UEFI, but i don't know there is a fast boot option, and also i didn't see it in Bios.

---

### Post by stevensjw on 2017-08-13
I knew what it is. I am sure i have made fast boot off.

---

### Post by oldfred on 2017-08-13
Dell support thread on dual booting.
 [https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 

 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)

---

### Post by stevensjw on 2017-08-13
This is the error show.
[IMG]https://thumbnail0.baidupcs.com/thumbnail/d6f3b344176e7ae1f452ddb65f6781c1?fid=444952619-250528-115403065723452&time=1502676000&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-EgR%2B2075jz4XcO%2BtGSFyKTZ7uB8%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=5228291905241241907&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video[/IMG]

---

### Post by oldfred on 2017-08-13
That still seems to be something in Dell settings, but just to be sure everything is installed correctly run this report.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

