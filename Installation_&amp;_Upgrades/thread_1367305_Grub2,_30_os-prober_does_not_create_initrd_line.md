---
title: "Grub2, 30_os-prober does not create initrd line"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by mycenae on 2009-12-29
Hello,

I have installed Karmic Koala, with the grub2 that came with it. On other partitions, I have WinXP and Fedora 12 installed.
When doing update-grub, the os-prober can find WinXP and create menuentry in the grub.cfg file correctly. However, there is a problem with Fedora 12. The menuentry of Fedora 12 only has the line linux /boot/vmlinz..... but there is no entry for initrd .....
Thus, I cannot boot Fedora due to there is no initrd entry in the grub config. I have to manually add menuentry of Fedora to 40_custom.
Although using 40_custom works well, I prefer to use the os-prober so I can fully exploit grub features and I won't have to update the 40_custom every time Fedora update the kernel release.

Any advice ? Thank you.

---

### Post by oldfred on 2009-12-30
If Fedora is still using grub legacy you could install grub legacy to the Fedora partition and chainboot from a 40_custom entry. Then you are working from the update Fedora menu all the time.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1

---

### Post by mycenae on 2009-12-31
Hello, thanks.
This sounds good but I don't dare to try yet. I am afraid that, once installed, the legacy grub will overwrite the MBR of the harddisk, i.e. overwrite grub2 in the MBR.
I will read more on how to install grub until I am sure what to do 
Any suggestion will be appreciated. Thanks.

---

### Post by oldfred on 2009-12-31
You need to be sure to use Fedora's grub, Even though they may both be grub legacy the modifications by each distribution are different.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0) - do not use
# Or
6. [COLOR=Red]Type "setup (hd0,3)". This is key.[/COLOR] Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
qui

---

### Post by mycenae on 2009-12-31
Thanks oldfred and happy new year.

---

### Post by mycenae on 2010-01-02
I have spent sometimes to understand how os-prober work. 
The os-prober will read grub (legacy and 2) config and lilo config of other linux and create the menuentry. So, if other linux has bootloader, there should be no need to manually edit the grub config or use chainload.
If the linux has no bootloader, the os-prober will look for the kernel file name that starts with vmlinu[zx] and the initrd file name that starts with initrd.

In my case, I have installed fedora without bootloader and the initrd file name starts with initramfs. I have made a simple change to the os-prober by make it looking for the file starts with initr instead of initrd.

So, I have the update-grub command working for fedora now. If I happen to install another linux, I will include the bootloader. That will make life easier.

---

### Post by oshunluvr on 2010-02-10
So do you care to enlighten us on what changes you made to make this work????

---

