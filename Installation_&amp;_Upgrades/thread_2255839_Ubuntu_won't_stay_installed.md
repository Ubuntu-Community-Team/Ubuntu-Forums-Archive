---
title: "Ubuntu won't stay installed"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by hayden7 on 2014-12-08
So i have tried installing multiple times.  Using a USB.  Its a system restore so overwriting everything.  I get it to install and then i restart when prompted after the OS is installed.  (I unplug my usb as soon as it is done installing)  This first restart everything is cool and working well.  After the next restart i get the error that i need to choose a proper boot device.  I have been trouble shooting all day.  I don't know what to do.  Every time the bios boot option resets to ST1000DM003-1.  No idea what that is and it doesn't boot into anything either.

---

### Post by Bucky Ball on 2014-12-08
Welcome. Have you tried changing the boot order in the BIOS? May be a silly question, but just in case ...

Depending on the BIOS, there can be a couple of options. You want to set the HDD Ubuntu is on to first in the list in every option.

---

### Post by grahammechanical on 2014-12-08
> [COLOR=#000000] Every time the bios boot option resets to ST1000DM003-1. No idea what that is[/COLOR]

That is the manufacturer model number of your hard disk. That is your hard disk. When exiting the BIOS settings utility did you choose the Save and Exit option? Unless we do that changes will not be made to the BIOS settings. So, it is not Ubuntu that is not staying installed. Ubuntu cannot un-install itself. So, the problem must be something else.

Regards.

---

### Post by hayden7 on 2014-12-08
When i first install it i set it to the usb but on that first restart when everything still is working fine, i change my bios to the hard disk where i set it to ubuntu.  And yes, i always save and exit

---

### Post by hayden7 on 2014-12-08
Just tried installing again.  I installed from my usb just fine.  I could login, use the internet, anything.  Unplugged my usb, changed my bios to boot from ubuntu off of my hard drive, restarted it, now back to "Reboot and select proper boot device".  Havent touched my bios since changing them to boot ubuntu from my hard drive.  They changed themselves to UEFI ST1000DM003-1.  Again, i didnt change that.  And i go into the hard disk drive priority and ubuntu is no longer there.  No idea what to do.

---

### Post by Bucky Ball on 2014-12-09
Sounds to me like not installing to the hard drive. Could you boot from the USB>Try Ubuntu>get to a desktop>install Gparted>take a screen shot of your hard drive>post that screenshot here so we can see what you have.

---

### Post by hayden7 on 2014-12-09
> **Bucky Ball said:**
> Sounds to me like not installing to the hard drive. Could you boot from the USB>Try Ubuntu>get to a desktop>install Gparted>take a screen shot of your hard drive>post that screenshot here so we can see what you have.

ok.  i can do that later today

---

### Post by oldfred on 2014-12-09
It sounds like a UEFI install.
And some vendors modify UEFI to only automatically boot Windows. So we have to create work arounds to set Ubuntu as a boot choice.
What brand/model system. What video card/chip?

Post link to summary report from this:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bucky Ball on 2014-12-09
> **oldfred said:**
> It sounds like a UEFI install.
And some vendors modify UEFI to only automatically boot Windows. So we have to create work arounds to set Ubuntu as a boot choice.


Makes sense and would explain it.

---

### Post by hayden7 on 2014-12-09
> **oldfred said:**
> It sounds like a UEFI install.
And some vendors modify UEFI to only automatically boot Windows. So we have to create work arounds to set Ubuntu as a boot choice.
What brand/model system. What video card/chip?

Post link to summary report from this:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


i have an acer predator.  It came with windows 8 preinstalled.  Running an NVIDIA GTX 760 15.gb

---

### Post by oldfred on 2014-12-09
You have a UEFI system as all Windows 8 pre-installed systems are UEFI.
But the Ubuntu installer is both BIOS & UEFI, so it depends on which choice you make in UEFI menu to boot flash drive on whether it installs with UEFI or BIOS.
And with nVidia you often need nomodeset, sometimes even for live installer, often on first boot after install or until you install the nVidia drivers from the Ubuntu repository.

Post link to summary report, you install Boot-Repair into Ubuntu live installer as shown in link on Boot-Repair.

---

### Post by hayden7 on 2014-12-09
im unsure what to do again at this point.  Sorry, some of this stuff is over my head language wise.  I got into the "try ubuntu" and did everything that it said to do (the boor-repair).  Changed my bios to the one it indicated.  Rebooted and still had the same issue.  It just keeps reverting to the [COLOR=#000000] UEFI ST1000DM003-1.  The UEFI Boot and install article honestly makes no sense to me.  I dont understand what it is saying to do.[/COLOR]

---

### Post by hayden7 on 2014-12-09
Yea.  My bios "forget" ubuntu and auto switch back to "Windows boot manager".  Ubuntu is no longer and option.  But when i go to re-install ubuntu, it still recognizes that a previous ubuntu is installed.

---

### Post by hayden7 on 2014-12-09
> **oldfred said:**
> You have a UEFI system as all Windows 8 pre-installed systems are UEFI.
But the Ubuntu installer is both BIOS & UEFI, so it depends on which choice you make in UEFI menu to boot flash drive on whether it installs with UEFI or BIOS.
And with nVidia you often need nomodeset, sometimes even for live installer, often on first boot after install or until you install the nVidia drivers from the Ubuntu repository.

Post link to summary report, you install Boot-Repair into Ubuntu live installer as shown in link on Boot-Repair.

just saw this.  i will post the link of the summery report

---

### Post by hayden7 on 2014-12-09
[http://paste.ubuntu.com/9448175/](http://paste.ubuntu.com/9448175/)

---

### Post by oldfred on 2014-12-09
Some Acer need a password.

 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Since you only have Ubuntu, and if Acer is one of those vendors who modify UEFI to only Boot "Windows" we can change the ubuntu entry to be "Windows".

See D:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

**D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

You can also use grubx64.efi instead of shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\grubx64.efi"

more info on efibootmgr

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by hayden7 on 2014-12-09
> **oldfred said:**
> Some Acer need a password.

 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Since you only have Ubuntu, and if Acer is one of those vendors who modify UEFI to only Boot "Windows" we can change the ubuntu entry to be "Windows".

See D:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

**D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

You can also use grubx64.efi instead of shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\grubx64.efi"

more info on efibootmgr

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

[ATTACH=CONFIG]258480[/ATTACH]

---

### Post by oldfred on 2014-12-09
The efibootmgr is only in the UEFI boot of the live installer. If you boot in BIOS mode it will not work.
Make sure you are booting in UEFI mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you check if your model requires passwords in UEFI like other Acer?

---

### Post by hayden7 on 2014-12-10
> **oldfred said:**
> The efibootmgr is only in the UEFI boot of the live installer. If you boot in BIOS mode it will not work.
Make sure you are booting in UEFI mode.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you check if your model requires passwords in UEFI like other Acer?

Is there a youtube video out there that can help me with this??

---

### Post by oldfred on 2014-12-10
Did you review video in post #16 on unlocking Acer UEFI?

These are now older versions, but install process is the same or better as newer UEFI works better.

 Asus 3632QM Install on external drive with Windows 8 on internal- Irv June 2014
[https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be](https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be)
[http://ubuntuforums.org/showthread.php?t=2229968](http://ubuntuforums.org/showthread.php?t=2229968)
Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)
Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)
Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by hayden7 on 2014-12-10
> **oldfred said:**
> Did you review video in post #16 on unlocking Acer UEFI?

These are now older versions, but install process is the same or better as newer UEFI works better.

 Asus 3632QM Install on external drive with Windows 8 on internal- Irv June 2014
[https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be](https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be)
[http://ubuntuforums.org/showthread.php?t=2229968](http://ubuntuforums.org/showthread.php?t=2229968)
Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)
Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)
Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

i turned "csm" on in my bios and now it is finally working!!!!!!!!  idk what that did but its working and thats all that matters to me

---

