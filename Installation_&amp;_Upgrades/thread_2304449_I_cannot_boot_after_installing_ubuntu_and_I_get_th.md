---
title: "I cannot boot after installing ubuntu and I get the error 1962"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by Roman_Walther on 2015-11-26
I cannot boot after installing ubuntu and I get the error 1962: No operation system found. 

After running the boot-repair from a live usb it still doesn't work.
This is my repair log: [http://paste.ubuntu.com/13519918/](http://paste.ubuntu.com/13519918/)

I do not know how to move on. Can anybody help?

Thanks
Roman

---

### Post by grahammechanical on 2015-11-26
What model of computer is this? Lenovo? Here is a long thread on the same issue. There does seem to be a solution.

[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

Regards.

---

### Post by yancek on 2015-11-26
You should have a setting in the BIOS setup which you can check on boot for UEFI since you have Ubuntu installed UEFI.
You also have windows boot files in the EFI partition but no windows installation on any partition.  I don't know if that makes a difference since I don't use UEFI myself.

---

### Post by Roman_Walther on 2015-11-27
> **grahammechanical said:**
> What model of computer is this? Lenovo? Here is a long thread on the same issue. There does seem to be a solution.

[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

Regards.


Thanks for your help. It is a Lenovo ThinkCentre and I already read through this thread but the solutions provided there didn't work for me. I want to run Ubuntu as single installation and not together with Windows. I am a complete newbie to Linux so sorry for any dumb questions. 

After researching I found out that the main problem seems to be that Lenovo primarily only accepts the windows boot routine and cannot find this efi file from Ubuntu. I think I have to copy some file like [COLOR=#111111][FONT=Consolas]bootx64.efi[/FONT][/COLOR] to somewhere but I have no idea how to do that. Can you help here?

Thanks

---

### Post by furtom on 2015-11-27
if Ubuntu is the only operating system on your computer, you don't need uefi mode. also, if you are not dual booting, why not use the entire disk for the installation. If you just did that, I'd imagine that would solve your problem.

---

### Post by oldfred on 2015-11-27
Since you only have Ubuntu installed you can change the description from ubuntu to Windows. Then system will think it is booting Windows but really boots shim. You may also need to remove the old entries in UEFI.

This is one of many work arounds for systems that need boot files moved around. More details in link in my signature.
 
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"


Not sure you need this, but you may need to just delete the old /Microsoft folder in the ESP - efi system partition. Normally if UEFI sees files in ESP, it then adds entries to UEFI to boot when you do a full reboot. So best to houseclean ESP, then make sure no entries in UEFI for Microsoft/Windows.
To remove old UEFI entries, check what hex number they are and use that to delete.
 Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to current Windows .
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

Another:
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

