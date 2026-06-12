---
title: "Can not boot Ubuntu on seperate drive"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by sam156 on 2015-11-16
Hi everyone,     :confused:

Yesterday I decided to install Ubuntu on a separate drive. Having had many problems before with Linux installations, I unplugged my Windows drive and installed Ubuntu from a flash drive. I was following a guide from the net and it encourage me to create 4 partitions. 1 was the Primary called /boot @ 500 MB. One was a logical drive called / @ 15000 MB. The 3rd partition was a logical drive called /Home @ 100,000 MB. And the last was swap partition @ 5000 MB.
Then I rebooted and Ubuntu fired up with its menu system. (But no Windows because of the unplugged drive.) Ubuntu worked flawlessly.

Now I do not know anything about Ubuntu except that I have tried it a dozen time in the past and it inevitably causes problems with my Windows system eventually. That was the reason to unplug my Windows drive while I set up Ubuntu. So, I re plugged in the Windows drive, made it primary and sure enough Windows fired up as usual. I know that the windows boot manager was available with a 3rd party program called EasyBCD, so I downloaded it and then went to add in the Ubuntu system to the windows boot manager.
                                        

         
     
 I have been trying to get this to work now for the last 8 hours. No luck.
When I try to add in the Ubuntu program it offers up those 4 partitions as choices. I have tried them all but when I re-boot and choose Ubuntu, I just get a flashing flat cursor in the upper left of my black screen. 
So, I reload windows and try again but nothing happens. If I unplug the windows drive, it works flawlessly.

Can anyone help?... (I do not want Ubuntu to control my menu system. In the past this has cause me considerable grief!)

Thanks.
Sam

---

### Post by oldfred on 2015-11-16
I do not know EasyBCD.
But you should not need it. It typically forces grub to install to a partition which grub does not recommend. Grub then has to use a different mode to install using hard coded addressed call blocklists. But you have grub installed to MBR for directly booting from BIOS or one time boot key.

But you should just be able to set the Linux drive as default boot in BIOS and run this which will then add Windows to grub menu. If you then ever need to directly boot Windows just change BIOS or boot with one time key. Grub does only boot working Windows, so best to have a way to boot a Windows repairCD/flash or many times its internal boot partition may boot to repair mode with f8 when Windows is not working.

sudo update-grub

---

### Post by yancek on 2015-11-16
It might be useful if you posted which windows you are using.  If you are using a newer system with UEFI there are additional complicating factors.

Your second paragraph indicates the failure is in not being able to get the third party windows software (Easy BCD) to function properly.  Have you checked the neosmart site?  Not sure if they have a forum but they should have an FAQ.  Did you get any messages when you tried to use Easy BCD to add Ubuntu to the windows menu?

---

### Post by sam156 on 2015-11-16
I am using Windows 10 and Ubuntu 15.4

---

### Post by oldfred on 2015-11-16
That still does not say if UEFI or BIOS. Both versions can be UEFI or BIOS installs.

But because you mentioned logical partitions, then you probably have BIOS.
UEFI requires gpt partitioning which only has one type of partition, no primary, extended nor logical.
And with gpt one partition has to be the ESP - efi system partition for UEFI boot. Or with Ubuntu only on gpt you can have a bios_grub partition for BIOS boot.

---

### Post by yancek on 2015-11-16
The link below is to the neosmart site discussing EasyBCD on UEFI systems.  Since you want to use it to boot both windows 10 and Ubuntu, I suggest you go there and read the explanation.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

