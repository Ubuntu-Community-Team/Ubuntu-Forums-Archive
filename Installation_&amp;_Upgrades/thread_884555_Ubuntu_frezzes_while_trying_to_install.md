---
title: "Ubuntu frezzes while trying to install"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by etzarfat on 2008-08-09
Hi all,

I've read earlier posts with problem similiar to mine, I tried the suggested solutions but still ubuntu during installation freezes.
After choosing to install ubuntu 8.04 after the kernel is loaded and the HD and the CD is working the screen is shut off (like it gets no data) and then it powers up and displays a white blank white screen and my computer freezes.
I tried to unplug all of my USB devices and left only the mouse and keyboard but still got the same "freeze".
I also tried to choose the option of "using Ubuntu without any changes", after choosing this option I get a Debian command prompt and that's all.
If it helps when trying to install ubuntu, after it loaded the kernel and all, it displays a status of the hardware and etc, and I saw the line "Buffer I/O... Logical error" something like that I didn't had time to copy it.
Does anyone can help me
I'm using XP I have 77.6 GB free space a 1GB Ram, I don't have any partitions.
Does anyone have a solution?
Thanks

---

### Post by overdrank on 2008-08-09
> **etzarfat said:**
> Hi all,

I've read earlier posts with problem similiar to mine, I tried the suggested solutions but still ubuntu during installation freezes.
After choosing to install ubuntu 8.04 after the kernel is loaded and the HD and the CD is working the screen is shut off (like it gets no data) and then it powers up and displays a white blank white screen and my computer freezes.
I tried to unplug all of my USB devices and left only the mouse and keyboard but still got the same "freeze".
I also tried to choose the option of "using Ubuntu without any changes", after choosing this option I get a Debian command prompt and that's all.
If it helps when trying to install ubuntu, after it loaded the kernel and all, it displays a status of the hardware and etc, and I saw the line "Buffer I/O... Logical error" something like that I didn't had time to copy it.
Does anyone can help me
I'm using XP I have 77.6 GB free space a 1GB Ram, I don't have any partitions.
Does anyone have a solution?
Thanks

Hi and welcome, I assume you have tried to edit the kernel line on the live cd and remove the quiet splash and add noapic.

---

### Post by wpshooter on 2008-08-09
Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried installing using the SAFE GRAPHICS mode ?

If the above do not help and you have been trying to install from the LIVE (desktop) version of Ubuntu, then download, burn and try installing from the ALTERNATE (text based) version of Ubuntu.

Good luck.

---

### Post by etzarfat on 2008-08-09
Hi, 
I've disabled the "quiet splash" and add "noapic" and got the following messages:
(initramfs) [96.499680] ata3.00: qc timeout (cmd 0x27)
[96.499718] ata3.00 failed to read native max address (err_mask=0x4
[96.499757] ata3: failed to recover some devices, retrying 5 secs.

after few seconds it contiued and eventually it freezes with on the following lines:
[168.588653] Unifom CD-ROM driver Revision: 3.20
[168.529024] sr 6:0:0:0: Attached scsi generic sg0 type 5

can you help me with that?
Thank you

---

### Post by etzarfat on 2008-08-09
Hi,
I tried to install using "safe graphic mode" and it kind of worked I continued the installation after I chose the type of keyboard I have it gave the option to partition, it somehow didn't recognize my HD and I wasn't able to choose a drive to partion.
also my mouse moved very slowly.
Can you help me?
Thanks

---

### Post by overdrank on 2008-08-09
> **etzarfat said:**
> Hi,
I tried to install using "safe graphic mode" and it kind of worked I continued the installation after I chose the type of keyboard I have it gave the option to partition, it somehow didn't recognize my HD and I wasn't able to choose a drive to partion.
also my mouse moved very slowly.
Can you help me?
Thanks

Ok you may try what wpshooter suggested, check the cd for errors and also
you may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by etzarfat on 2008-08-10
Hi,

Well, the checksum is good and the cd integrity is also good.
Now like I told before when I came to the partion screen (while installing Safe Graphic Mode)
it didn't show me my HD, also it was very hard to move the cursor on the screen his movments on the screen weren't accurate 
My hardware is:
HDD - Sata 150GB, 77.6GB free space
In order for my DVD/CD (SCSI)drive to work normal in XP I needed to install "JMicron JMB controller"
Motherboard: MSI P965 Neo"
Maybe thoses details can give you ideas about my problem.
Thanks

---

### Post by etzarfat on 2008-08-12
Hi,
I've tried to install Live CD and still it freezes after a few minutes with a blank white screen.
can someone help me plz?

---

