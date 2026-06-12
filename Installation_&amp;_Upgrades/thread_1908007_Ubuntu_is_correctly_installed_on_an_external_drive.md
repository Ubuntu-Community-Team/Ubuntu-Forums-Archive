---
title: "Ubuntu is correctly installed on an external drive, but my computer cannot access it"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by amc92 on 2012-01-12
The title pretty much says it.  I have an HP Pavilion dv6 that runs windows 7 on the primary hard drive and I want Ubuntu installed alongside it.  Originally I wanted to install Ubuntu on a partition within the primary drive, but neither Windows nor the Ubuntu installer are letting me do that.  The free space is listed as "unusable space" and I get an error that says I cannot have more than 4 partitions, which are all in use from factory settings.  I think they're using dynamic partitions, where the partition size is just extended when it needs to be larger.
 
After that didn't work, I went out and got a Seagate hard drive and successfully installed Ubuntu on there.  I didn't think it was a success at first because I either got a "grub rescue>>" prompt or a black screen with a blinking cursor at the top.  I tried to reinstall and repair grub as many ways as I could but it made no difference.  Then I tried the Seagate on my dad's work labtop (which is some sort of HP EliteBook I believe), just to see if something would miraculously happen and it did.  It booted up Ubuntu, asking for my login and everything, just like it's supposed to, but my machine still can't handle it.  What can I do about this?

---

### Post by oldfred on 2012-01-12
HP's usually use all 4 primary partitions. And if you use Windows to create more, it converts from basic to dynamic which will not work with Linux and some Windows repair tools.

Often a boot issue is related to video drivers, BIOS settings (laptops often have few) or other boot parameters.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

