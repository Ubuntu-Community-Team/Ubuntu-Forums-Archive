---
title: "General Ubuntu and Grub Install Fail, Acer Aspire es1-533 [Help]"
date: 2018-02-10
forum: Installation &amp; Upgrades
---

### Post by xiremy on 2018-02-10
I cannot get ubuntu (16.04 LTS) to boot on my Acer Aspire ES1-533 Laptop, already tried the solution listed here: [https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing](https://community.acer.com/en/discussion/471754/acer-aspire-es-15-es1-533-c3uw-legacy-bios-missing)



More Info;
My first attempt on Installing froze during grub install. (Every time)
Secure boot is dsiabled in bios.
Attempted Upgrading Bios but my Laptop wouldn't detect the USB with bios update file.
Ripped the hard drive out of my laptop put it in another one successfully installed Ubuntu and grub2, put the hard drive back and returns this error on boot: "No Bootable Device".
After the latest attempt i erased the disk and attempted to reinstall ubuntu only to hang at grub install of course.

Been messing with this for a week, will probably never buy another Acer machine ever again.
Let me know What else i can do/provide to help me solve this issues, thanks!

---

### Post by oldfred on 2018-02-10
Acer is actually one of the better ones.
But it has a unique requirement of Setting an UEFI password and enabling "trust" on the Ubuntu/grub .efi boot files from within UEFI.
Some with now older Acer UEFI have to upgrade UEFI. Old threads had users downgrading UEFI, but newer threads say installing newest UEFI from Acer works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by xiremy on 2018-02-10
> **oldfred said:**
> Acer is actually one of the better ones.
But it has a unique requirement of Setting an UEFI password and enabling "trust" on the Ubuntu/grub .efi boot files from within UEFI.
Some with now older Acer UEFI have to upgrade UEFI. Old threads had users downgrading UEFI, but newer threads say installing newest UEFI from Acer works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

A lot of these mention: "[COLOR=#000000][I]Select an UEFI file as trusted for executing"
[/I][/COLOR]which is not an option in my bios.

INFO:
System Bios Version: v1.08
GOP Version: Intel(r) GOP Driver [10.0.1030]
CPU INFO: Intel(r) Celeron(R) CPU N3350 @ 1.10 Ghz

---

### Post by oldfred on 2018-02-11
Then you may have one of the older UEFI that needs updating.

Some also use the fallback or hard drive entry which is /EFI/Boot/bootx64.efi and boot a hard drive entry not the ubuntu entry in UEFI.
Boot-Repair now copies shimx64.efi automatically to bootx64.efi.
Some also use rEFInd, but I think it also uses the bootx64.efi as a fallback if its entry does not work.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by highballmint182 on 2018-03-05
Xiremy, I hope you don&#8217;t mind if I enter your conversation, because I am on a quest to solve this thing. I have tried many times to get a simple dual boot going on the same drive, unsuccessfully. I have what appears to be the same setup except for the UEFI bios, which did successfully update, but no change in application:

 
[LIST]
[*] 500 GB HDD on  Aspire ES-1533,     Apollo Lake processor, chipset and south bridge. 
[*] Main board  =Acer Stego_AP,      Windows 10 pre-installed and re-installed 
[*] UEFI [BIOS] InsydeH20 setup     utility rev5.0, ver 1.12  [UEFI bios] 
[*] GPT, UEFI = enabled,  secure     boot = re-enabled 
[*] (U)EFI partiton = n/a 
[*] fastboot = disabled 
[/LIST]
 The same problem:
 Enter EUFI bios, then:
 
[LIST=1]
[*] [COLOR=#000000]go to "Set     Supervisor Password" press ENTER (I set pass "a")     check, good there.[/COLOR] 
[*] [COLOR=#000000]no menu     entry for &#8220;s[/COLOR][COLOR=#000000]elect an UEFI file as     trusted for executing:" [/COLOR][COLOR=#000000]no matter     what I do[/COLOR] 
[*] no n[COLOR=#000000]ew page     appear[/COLOR][COLOR=#000000]s[/COLOR][COLOR=#000000]     with listed [/COLOR][COLOR=#000000]hard drives[/COLOR][COLOR=#000000]:[/COLOR] 
[/LIST]
[COLOR=#000000]                                                - HDDO
                           - HDDO
[/COLOR]
[COLOR=#000000]Like yours, "[/COLOR][COLOR=#000000]*Select an UEFI file as trusted for executing" *[/COLOR][COLOR=#000000]is not an option in my bios. Also, [/COLOR][COLOR=#000000]I [/COLOR][COLOR=#000000]can&#8217;t press ENTER on the first HDD0 [/COLOR][COLOR=#000000]since[/COLOR][COLOR=#000000] no sub list with the name "<EFI>" comes up. Since [/COLOR][COLOR=#000000]no [/COLOR][COLOR=#000000]sublist comes up, no shimx64.efi, grubx64.efi or MokManager.efi [/COLOR][COLOR=#000000]are there. [/COLOR][COLOR=#000000]This was true on both UEFI bios setups. [/COLOR] 
 
[LIST]
[*] [COLOR=#000000]Did I miss     something, or is my UEFI bios missing something, like the entries     listed above? [/COLOR] 
[*] [COLOR=#000000]Should I     re-[/COLOR][COLOR=#000000]reflash my EUFI bios with the update     again, or maybe downgrade it?[/COLOR] 
[/LIST]
 [COLOR=#000000]This all appears to be unique to the Acer Aspire [/COLOR][COLOR=#000000]ES1-533 [I call it the ES-1533, but no difference] I have tried for over 3 weeks to get a simple dual boot going on this machine, tried many different suggestions, variations and setup routines. Still no dual boot. [/COLOR] 

The truth is out there.

---

### Post by highballmint182 on 2018-03-05
I forgot to mention that my installs always hang up at the same place too, during grub installation. ALWAYS fails. Plus,I only see this next thing for less than a second, but after grub v2.02 [beta] comes up when booting from USB stick, there are lines saying that there's "a problem loading EFI files", "no caching mode page found", "assuming drive cache - write through" or something like that, I can't get the code that goes by too fast for me to read them. That sounds messed up

---

### Post by wildmanne39 on 2018-03-06
Hello and welcome to the forum highballmint182, please start your own thread because even though the issue appears to be the same they may have different causes and the OP of this thread as well as yourself will receive better help if only one persons issue is being worked on in each thread.

Thanks

---

### Post by highballmint182 on 2018-03-06
no worries. new thread coming soon to the forum. thanks for the heads up, makes sense to me. ciao for now

---

