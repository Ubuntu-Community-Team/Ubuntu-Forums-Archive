---
title: "Installing Ubuntu on Acer Aspire XC-780"
date: 2017-01-02
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2017-01-02
so today i bought an  Acer Aspire XC-780 which HAD windows 10 on it

first i tried to install ubuntu 16.04 LTS but when i reloaded only windows was there


so i went back to my live USB got gparted and knocked off windows which i do not want anyway

now due to uefi in machine firmware i have nothing


so  please let us kindly help this idiot here :      this is gparted now   >>>    [ATTACH=CONFIG]272997[/ATTACH]   read from the live usb


what do i need to do now?

this is the message i get when i try to install again

[ATTACH=CONFIG]272998[/ATTACH]


what to do now? should i continue in uefi mode  ... i am puzzled


thanx for all useful support


shan

---

### Post by hanspeteriv on 2017-01-02
Hi, since you intend to install Ubuntu as your only operating system you can safely ignore the warning and hit "Continue in UEFI mode". The warning is only important if you want to also use another OS which has been installed in BIOS mode.

---

### Post by RobGoss on 2017-01-02
Seeing you're only wanting to install Ubuntu run the** live installer **and choose **install now,** you can use the entire disk for your installation

The window you see in that screen shot is allowing you to install all the necessary updates for the new system and installing third party software as well, you can simply check both boxes and begin your installation

I recommend you should be connected to the internet to install any update, you might want to use a **wired connection** until everything is installed then you can configure your wireless connection if needed

---

### Post by shantiq on 2017-01-03
thanx guys for support

i got there and at some point i think deleted the uefi partition? which was about 50Mb using the - button then used the entire 1TB ...    would that make sense?
i will not claim i understood any of this but i think now it is the grub route which is used
this is not a part of linuxing i understand or like   ....    it feels like a rite of passage  ... like De Caprio and his 2 friends jumping in the rockpool in The Beach [for the cognoscenti]

anyway thanx for what you said it helped  ....    i wish i understood more what i did but i am grateful to have got in the door


bloody uefi   ...    was easier when only Legacy was around ...


PS    want to add that in this instance reading up-to-date info it told me not to use my usual ubuntu unetbootin  but pointed me in the direction of using [Rufus]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") to create live-usb from the Windows setup before deleting/dual booting as if i understand it it will cater for both uefi and grub in a way some of the older linux tools do not as yet   ...    if i understood what i read

---

### Post by oldfred on 2017-01-03
Acer UEFI has required you to set a Supervisory password in UEFI and then enable 'trust' from UEFI on ubuntu/grub .efi files in ESP - efi system partition.

Some have mentioned downgrading UEFI. But newer threads mention upgrading UEFI works. so make sure you have newest UEFI from Acer.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

