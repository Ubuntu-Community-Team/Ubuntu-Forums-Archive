---
title: "Dual boot Windows 10, Ubuntu 15.10"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by xilveen on 2015-10-26
Hello,
I know there have been several threads over the topic, but I tried many of the presented solutions without success.

This is a boot problem, you can skip the Background section, if not needed.

[I][B]Background

[/B][/I]This is an Acer laptop I just bought that had Windows 8.1 pre-installed. I upgraded it to Windows 10. Then I prepared to install Ubuntu:
[LIST]
[*]instead of disabling Fast Startup, I already had disabled hibernation
[*]I disable SecureBoot in the BIOS
[/LIST]

Then, during Ubuntu installation, I chose the install Ubuntu alongside Windows (I actually also tried the Something Else option before that, with both root and swap partition). 

After the installation the boot goes straight to Windows 10. In the boot menu (F12 on startup), the only available option is Windows Boot Manager.

***Boot repair***

Starting a live Ubuntu session (with the Try Ubuntu option), I ran boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). This is the generated pastebin:

[http://paste.ubuntu.com/12968968/](http://paste.ubuntu.com/12968968/)

Boot repair didn't fix the problem and I got brought straight to Windows 10 again. In an elevated command prompt I run the command suggested by boot repair:

```
[COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi[/COLOR]
```

Even though the console said the operation was successful, I still can't boot into my Ubuntu 15 installation.

Any help is greatly appreciated,
thanks in advance

---

### Post by anjo_ed on 2015-10-26
Hello xilveen, how are you doing ?

Well, your laptop has UEFI ? I think that your problem. So, try it:
[http://ubuntuforums.org/showthread.php?t=2247757](http://ubuntuforums.org/showthread.php?t=2247757)

---

### Post by oldfred on 2015-10-26
If you installed Ubuntu in UEFI boot mode, you have to set a supervisor password & enable "trust" on the ubuntu/grub efi boot files. Only Acer seems to have this specific solution.

       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by xilveen on 2015-10-26
> **anjo_ed said:**
> Hello xilveen, how are you doing ?

Well, your laptop has UEFI ? I think that your problem. So, try it:
[http://ubuntuforums.org/showthread.php?t=2247757](http://ubuntuforums.org/showthread.php?t=2247757)

Thanks, fine now on Ubuntu 15 :D 

> **oldfred said:**
> If you installed Ubuntu in UEFI boot mode, you have to set a supervisor password & enable "trust" on the ubuntu/grub efi boot files. Only Acer seems to have this specific solution.

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

Thanks for the help! What I needed to do was in fact setting the grux64.efi file as trusted in the BIOS. That fixed the problem! ( the second answer in this thread you provided is detail about the matter [http://askubuntu.com/questions/62741...-not-dual-boot](http://askubuntu.com/questions/62741...-not-dual-boot))

---

