---
title: "preseed : loaded OK but still interactive"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by guermonprez on 2010-06-22
Hello

I am trying to automate the installation of systems starting from a usb netbook key.

The preseed key is loaded fine as i can see the default choices are now mine.
But i'd like to automate totally the process and not ask anything : boot from USB and image everything.

I tried "preseed/interactive=false" in the syslinux config, i also tried "d-i preseed/interactive boolean false" at the beginning of the seed file.

Note that "only-ubiquity" in the syslinux config is not working as i see a choice between run live and install at the beginning.

I am missing something ...

Thanks, paul

---

### Post by oldfred on 2010-06-23
I have not done a server install with automation but have saved some info:

[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)
[http://searchsystemschannel.techtarget.com/generic/0,295582,sid99_gci1377934,00.html](http://searchsystemschannel.techtarget.com/generic/0,295582,sid99_gci1377934,00.html)

I think to use the kickstart way would require the USB install of grub2 so you have a grub.cfg to launch the installer. Then you can edit the command line to include the extra parameters. I have done that to get my lucid install to accept nomodeset on install boot from USB.

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

