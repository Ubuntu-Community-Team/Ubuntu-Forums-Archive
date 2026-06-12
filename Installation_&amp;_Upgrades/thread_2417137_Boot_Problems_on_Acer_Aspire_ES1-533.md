---
title: "Boot Problems on Acer Aspire ES1-533"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by urstru on 2019-04-21
I'm unable to install and boot ubuntu on an Acer Aspire ES1-533. Pre installed was Win 10 which I removed. 


Acer BIOS is Version V1.08
Secure Boot is Disabled.
Current TPM (TCM) State: Not Installed
Boot Mode: UEFI (Cannot be changed...)


The installation process freezes when installing grub, even the mouse pointer cannot be moved after freeze.

Before the ubuntu installation program starts, a short message shows up: Problem loading UEFI:db X.509 certificate (-65)

I made a check with boot repair:  [http://paste.ubuntu.com/p/v6fKmJxX5y/](http://paste.ubuntu.com/p/v6fKmJxX5y/)


Happy for every support ...

---

### Post by oldfred on 2019-04-23
Have you updated UEFI from Acer, many have needed that.
Is Linux entry named by you after enabling "trust"?

You may want trust on the unknown/shim entry as to enable trust you have to have Secure Boot on.
[ccode]=================== efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,2001,2002,2003
Boot0000* Unknown Device: 	HD(1,GPT,39a14228-8018-41bd-96b6-b36bd045cb85,0x800,0x100000)/File(EFIubuntushimx64.efi)RC
Boot0001* Linux	HD(1,MBR,0x316d386d,0x800,0x77e000)/File(EFIBootgrubx64.efi)RC
[/code]

              
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594) 
    
Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511) 

            Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
[URL="https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing"]https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing
      [/URL]
 Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10) 
    [URL="https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing"]
[/URL]

---

