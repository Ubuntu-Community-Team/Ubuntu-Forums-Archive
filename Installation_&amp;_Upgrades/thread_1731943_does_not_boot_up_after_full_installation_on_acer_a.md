---
title: "does not boot up after full installation on acer aspire one"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by banjoman on 2011-04-17
have tried to replace WindowsXP with ubuntu netbook 10.10 on my Acer Aspire one (model ZG5), I opted for erasing the disk completely to just have ubuntu on the machine

it runs perfectly from the USB drive, but will not boot up after a full installation, I just get a black screen with flashing underscore cursor

there are several threads about this problem but I cannot glean a solution, I have used 2 downloads as I thought the first iso might be corrupted, but still cannot get the system to start up

what is the next step, is it worth persevering or trying an alternative distro?

---

### Post by kourasmenos on 2011-04-17
I had a similar problem with dual booting and I solved it by changing the boot device priority, I dont know if that helps.
Did you make the partitions manually?

---

### Post by steveredshaw on 2011-04-17
I didn't make the partitions manually, just let the installation format the entire hard drive and proceed automatically

I have tried changing the boot priority so its definitely booting from its hard disk, but its made no difference

---

### Post by oldfred on 2011-04-17
what video do you have? Hold shift key from BIOS until grub's menu appears and try nomodeset:

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by steveredshaw on 2011-04-19
could not get grub menu to appear, just get the balck screen with flashing cursor

I have opted for Easy Peasy which does boot up on my machine, looks very similar to Ubuntu netbook and uses ubuntu software updates

so will operate with that for time being - thanks for replies....

---

### Post by FreddieMac502 on 2012-11-28
I am currently having the same problems and would love to stay with Ubuntu, any suggestions. Same computer Acer Aspire one ZG5. When it reboots after install all I get is a blinking cursor. No Grup no boot loader NOTHING!!

---

### Post by FreddieMac502 on 2012-11-28
> **FreddieMac502 said:**
> I am currently having the same problems and would love to stay with Ubuntu, any suggestions. Same computer Acer Aspire one ZG5. When it reboots after install all I get is a blinking cursor. No Grup no boot loader NOTHING!!

But it works from the bootable usb, no display issues at all.

---

### Post by oldfred on 2012-11-28
@FreddieMac502
I would normally move you to your own thread as current thread is older. Only because it is the same model computer will I not move it yet. But only if your thread could you change to solved it we get it to work.

Did you do like the OP and just install Ubuntu so it only has one operating system? If so you have to hold shift key from BIOS until menu appears. Then try the nomodeset or other boot options suggested above.

What video chip does it have?

This page has some info:
[https://help.ubuntu.com/community/AspireOne/AOA150](https://help.ubuntu.com/community/AspireOne/AOA150)

---

### Post by steveredshaw on 2012-11-29
I have stopped using Ubuntu, well I now use and enjoy one of its derivatives Mint. I installed Mint 13 on my AcerOne successfully from a USB stick (download the ISO installation image and then use UnetBootIn to create a bootable USB) and that is working really well on the machine.

---

