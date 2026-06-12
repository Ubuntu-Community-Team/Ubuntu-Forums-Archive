---
title: "install xubuntu 14.04.1 / 64 on acer ES1-512 (only xubuntu, no dual boot))"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by buhuhu on 2015-01-09
Hi all,

I bought two days ago an acer ES1-512, nice and cheap (the seller warned me there is an uefi bios and there are more than 10 returns from customers related to install issues...).

I follow the known method - usb bootable flash with last version 14.04.1, certainly the normal install way was not working. Trying different bios settings i was finally able to install from usb but after restart (the system stucks at shutdown and it was needed to shutdown manually from start button) i get a black screen. 

Well i began to search for some solutions, finally i found on acer site a short installation placed nowhere (found it by google, on acer site at support it was not to find) - about how to enable the uefi secure boot mode (by default in the few bios settings of this system we can choose only for uefi or legacy, but the secure boot option is grayed and inactive). You  have to create a supervisor password from security (all from bios   settings - by F2), confirm the password and the secure boot (from boot   menu) will be active. Ok, i disabled the secure boot option and hope the system will start - no way.
I return in bios reenable the secure boot mode, go in security settings select the option "select an uefi file as trusted  for executing" and select  HDD0 - then <EFI> - then <ubuntu>  and finally enable one of the 3  efi files inside (shimx64.efi, grubx64.efi and  mokmanager.efi), i enabled all, save all and reboot. 
After this the xubuntu starts normally and half tired / half  astonished that all this fun is happen on my manny payed for this system, i hope to have the system working.

I run a full update, uninstall abi and gnumeric, install libre and allot of other, check the recommended postinstall operations, full update again and the system was working as i need. Ok i say and reboot - but the system has stuck at shutdown (it was needed to shutdown from start button), again at restart i get a black screen. 
Nice work, go to bios, enabled and disabled the secure boot mode and the system starts normally - but not always (if this was not working i go to bios security settings, force uefi factory settings, reenable the efi files as described and then disable the secure boot option, strange but it works). 
But the system works well only until restart (alway shutdown is not  complete and after restart - black screen - instead of the grub menu).

Forgot to say - partitions from gparted:
 sda1 - fat32 mount point /boot/efi (boot)
sda2 - ext4 mount point /
sda3 - linux swap

And also - the system came with linpus linux preinstalled (without x, only terminal).

In conclusion the system is working well (programs runs normally - net, bluetooth, video, sound, all other, speed is good) until shutdown (i let the computer on - as it was a gift for my wife, i say: please newer turn it off, certainly hi does that and i have again fun to play in bios).
I read allot on uefi posts but was not able to find something working on this system.

If somebody solved this, please tell me how to do. 

And all the best for the New Year for all !!!  ;)

---

### Post by lugeperez on 2015-01-09
Hi buhuhu,

I'm experimenting a similar problem with the shutdown: my computer screen freeze with the ubuntu logo on.

In my case this ACER ES1 512  was a gift to my girlfriend as well. She is using ubuntu since many years ago and she prefers it over windows or mac as I do. So we decided to get rid of the windows*; *I did a backup, just in case, and after searching the web on how to install ubuntu in this type of newer machines, I set the BIOS to legacy mode, and it worked well. The only problem is the shutdown. I have installed linux mint, my first time using it, and it happens the same. 

Now the computer has a dual boot with ubuntu 14.10 and linux mint, I like them both, but the same problem in everyone when I try to turn off the system.

Hoping that a more expert person  is able to help us to find a fix to our problem [-o<

Salud!

---

### Post by oldfred on 2015-01-09
Some links
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by buhuhu on 2015-01-09
Hi and thanks for the suggestions,

oldfred - [COLOR=#000000]thanks for the links, i almost read them [COLOR=#000000]before posting[/COLOR] (grabbing on your answer to similar posts, 2 day ago) - there were quite useful. 
One link was specially useful today - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot) - i will spend some time to understand a bit deeper about uefi background, thanks.
 
thanks lugeperez[/COLOR] - i try first to work with legacy but obtained only a quick flickering between bios check and something that yields in a reboot.
I will post news if i find something useful.

Kind regards,;)

---

