---
title: "Unable to boot Ubuntu from USB, And then goes to Black/No signal"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Corp.Samich on 2011-04-07
Hey Ubuntu fourms. I've recently had to reformat my computer because a virus on Vista, and now I would Like to install Ubuntu 10.10.

I loaded the USB on my friends laptop, and tested it on it as well, All good.

I go and plug it into my Acer Aspire Desktop, and I get to the menu of Either Live or Install, Either one I choose, It goes and loads a long line of code, cuts to black, and then in smaller text size, does more lines of code (Approx. 200~) and then cuts to a No signal screen on my Monitor. It also shows the Ubuntu's 5 dot screen, and goes back to code in that sequence. 

It also did not go past the first selection when I had my Onboard Graphics put in, and proceeded to the smaller text when I took it out. 

Help dudes?   

Specs:2.6 G.Hz dual core intel Pentium processor
Memory: 3gb DDR2
HDD:500GB SATA
OS:None, Formatted system. Formerly Vista.
Model of Computer: Acer Aspire M1641 Desktop
Graphics: Nvidia GT220 1gb Memory Offboard
Onboard: Nvidia 7700 Geforce

---

### Post by garvinrick4 on 2011-04-07
> Graphics: Nvidia GT220 1gb Memory Offboard
Onboard: Nvidia 7700 Geforce 

Most likely a Nvidia issue will bump you back to front lots of users with Nvidia knowledge.
Patience someone will be able to help you.

---

### Post by oldfred on 2011-04-07
Nvidia needs the nomodeset:

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
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by Corp.Samich on 2011-04-08
Tried Nomodeset, Didn't work. 

I kept getting the USB ports saying that it was a new addresses each couple lines.

Any other ideas?

Edit: No Ubuntu Dot screen came up as well.

---

