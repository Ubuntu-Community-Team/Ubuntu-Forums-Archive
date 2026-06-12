---
title: "Installing ubuntu on hp dv6 laptop"
date: 2019-06-29
forum: Installation &amp; Upgrades
---

### Post by anas559 on 2019-06-29
I can reach ubuntu but after I install it on another usb flash and try to boot from it I get stuck at at black screen then trying to wait for hours and nothing happens.

---

### Post by yancek on 2019-06-30
Sorely lacking in details?  You don't mention any other operating system so the first questions is, do you have another OS and if so what and which version?
What type of install UEFI/Legacy MBR?
Did you change the boot priority in the BIOS to the second usb on to which you installed Ubuntu?

Might be best to see details by running the boot repair script with the Create BootInfo Summary option selected.  Use the 2nd option of using the ppa described at their site below to download and do NOT try to make any repairs but post the link you are given when it completes here and someone should be able to offer a solution.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by anas559 on 2019-07-01
I am trying to install ubuntu 18.04 LTS (legacy), I can boot from ubuntu  live cd but I can't boot after I install it on another usb drive.

Of course I changed the the boot priority in the BIOS to the second usb.

Here is the file:
[http://paste.ubuntu.com/p/rvxhZ9dNzp/](http://paste.ubuntu.com/p/rvxhZ9dNzp/)

---

### Post by SeijiSensei on 2019-07-01
What do you mean by "install it on another usb drive?" Did you use a tool like usb-creator-gtk or usb-creator-kde on a Linux box, or a Windows program like Rufus?

I have a dv6.  Are you intending to install Ubuntu in a dual-boot arrangement?  You won't get far given how HP uses up all four primary partitions on the main drive.  I posted instructions about how I dealt with this problem in this post: [https://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287](https://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287)

---

### Post by anas559 on 2019-07-01
I used Rufus on 16gb usb flash and I can boot from it. now I need to install Ubuntu it on another external flash drive. I don't need to install Ubuntu in a dual-boot arrangement.

I booted Ubuntu from 16gb and tried to install on another external usb flash. When I try to boot from usb flash, I see blank screen nothing happens after that.

---

### Post by anas559 on 2019-07-02
Someone help please ?

---

### Post by kurt18947 on 2019-07-02
I have done what you are doing. The most likely (IMO) problem is that GRUB did not install on your second USB. Did you use "something else" in the installer then specify the correct USB drive and where you want to install GRUB? The first couple times I did this I removed the primary hard drive to I was CERTAIN I would not overwrite my main hard drive. By not offering any other destinations beside the desired flash drive you insure the install will occur where you desire. 

Of course if you're installing on a portable it may not be simple to disconnect the hard drive. In that case could you disable the primary drive(s) in BIOS so only the live USB and target USB are visible?

---

### Post by anas559 on 2019-07-03
> **kurt18947 said:**
> I have done what you are doing. The most likely (IMO) problem is that GRUB did not install on your second USB. Did you use "something else" in the installer then specify the correct USB drive and where you want to install GRUB? The first couple times I did this I removed the primary hard drive to I was CERTAIN I would not overwrite my main hard drive. By not offering any other destinations beside the desired flash drive you insure the install will occur where you desire. 

Of course if you're installing on a portable it may not be simple to disconnect the hard drive. In that case could you disable the primary drive(s) in BIOS so only the live USB and target USB are visible?

I already used "somethin else" and chose the correct USB drive for the bootloader.
I couldn't disable my primary hard drive in the bios because there is no option like that. There is only boot order option in the bios so I reinstalled again and put the target USB as 1 boot option and removed my primary drive and still getting stuck at black screen when I boot from the target USB.

Here is the file:
[http://paste.ubuntu.com/p/kKFVBBdBtZ/](http://paste.ubuntu.com/p/kKFVBBdBtZ/)

---

### Post by yancek on 2019-07-03
Do you have another computer available on which you can test boot the new usb?. If that works then we know it is not a problem with the usb itself.
When you boot your new usb, do you immediately see a black screen or do you see a Grub menu first which then goes to a black screen?
Legacy/CSM boot enabled in BIOS?

---

### Post by anas559 on 2019-07-03
> **yancek said:**
> Do you have another computer available on which you can test boot the new usb?. If that works then we know it is not a problem with the usb itself.
When you boot your new usb, do you immediately see a black screen or do you see a Grub menu first which then goes to a black screen?
Legacy/CSM boot enabled in BIOS?

Yes I have another computer and I tried to boot from my USB flash that I installed on after I enabled legacy in Bios and I reached the gnu grub with pink screen after that I hit Ubutnu then a black dos screen appeared with recovering journal it was taking long then I quit it.

When I boot the USB drive on hp dv6 laptop,I see a black screen immediately, there is no grub menu showing. There is no Legacy/CSM option on Bios. My laptop is very very old, I bought it in 2012 so I am guessing I need legacy boot solution.

And I was wondering if mount point with "/" is correct or not ?

---

### Post by SeijiSensei on 2019-07-03
The dv6 was released well before Secure Boot became a thing. So you would need to use Legacy mode.

---

### Post by anas559 on 2019-07-04
> **SeijiSensei said:**
> The dv6 was released well before Secure Boot became a thing. So you would need to use Legacy mode.

How?

There is no Legacy,CSM or UEFI option in Bios. And my latpop model is Hp Pavilion dv6 6c65sx.

---

### Post by lizabrown01 on 2019-07-04
I also tried to install ubuntu on hp dv6 laptop but during installation it shows an error [Epson scanner communication error]("https://errorcode0x.com/resolve-epson-scanner-communication-error/"), so i want a proper solution how to remove this error a son as possible.

---

### Post by SeijiSensei on 2019-07-04
Deleted

---

### Post by SeijiSensei on 2019-07-04
> **anas559 said:**
> How?

There is no Legacy,CSM or UEFI option in Bios. And my latpop model is Hp Pavilion dv6 6c65sx.

It predates Secure Boot. So if you create a USB stick in Rufus, don't use UEFI.

> **lizabrown01 said:**
> I also tried to install ubuntu on hp dv6 laptop but during installation it shows an error [Epson scanner communication error]("https://errorcode0x.com/resolve-epson-scanner-communication-error/"), so i want a proper solution how to remove this error a son as possible.

Do you have an Epson scanner? Did you try installing with the scanner disconnected?

---

### Post by anas559 on 2019-07-04
> **SeijiSensei said:**
> It predates Secure Boot. So if you create a USB stick in Rufus, don't use UEFI.

I am already using Rufus, still getting stuck at black screen without reaching grub.

Any other solution?

---

### Post by SeijiSensei on 2019-07-04
Rufus offers multiple formats; are you sure you didn't choose UEFI when you created the stick?

---

### Post by anas559 on 2019-07-04
> **SeijiSensei said:**
> Rufus offers multiple formats; are you sure you didn't choose UEFI when you created the stick?

Yes I am sure. Any other solution ?

---

### Post by SeijiSensei on 2019-07-04
I've never had problems using usb-creator-gtk or usb-creator-kde on an Ubuntu machine.

---

### Post by anas559 on 2019-07-04
> **SeijiSensei said:**
> I've never had problems using usb-creator-gtk or usb-creator-kde on an Ubuntu machine.

I can boot and use Ubuntu normally from the usb stick that I created from Rufus. When I install it on another HD I get stuck at black screen without reaching grub screen, I tried the new usb stick that I installed on MSI laptop I reached grub screen and then chose Ubuntu but I get stuck at recovering journal, it was taking long then I quit it. My hp laptop doesn't have Legacy,CSM or UEFI  option.

Any other solution?


[http://paste.ubuntu.com/p/kKFVBBdBtZ/](http://paste.ubuntu.com/p/kKFVBBdBtZ/)

---

### Post by anas559 on 2019-07-24
I need to install ubuntu 18.04 LTS (legacy) on my hp pavilion dv6  laptop. I booted from the live cd and installed it to another hard drive  but when I boot from the hard drive I get stuck at black screen, there is no Grub menu and I  was sure that I changed the the boot priority in the BIOS.
I don't need to install Ubuntu in a dual-boot.


[http://paste.ubuntu.com/p/kKFVBBdBtZ/](http://paste.ubuntu.com/p/kKFVBBdBtZ/)

---

### Post by ubfan1 on 2019-07-24
What's the video hardware on that machine? Nvidia maybe?  That needs "nomodeset" added to the grub line starting with "linux" at the "quiet splash" words.

---

### Post by anas559 on 2019-07-24
> **ubfan1 said:**
> What's the video hardware on that machine? Nvidia maybe?  That needs "nomodeset" added to the grub line starting with "linux" at the "quiet splash" words.

It is an ATI Radeon 6700m. I added nomodeset and still getting stuck at black screen without reaching grub or anything.

---

### Post by anas559 on 2019-07-26
I tried every option in boot-repair like nomodeset, acpi_osi=, acpi=off, Noapic and nolapic. Nothinge worked for me and still getting stuck at black screen without reaching grub after I install Ubuntu on HDD.

---

