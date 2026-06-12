---
title: "Dual boot Ubuntu / Windows 10 - Troubleshooting RAID SATA controller"
date: 2018-02-20
forum: Installation &amp; Upgrades
---

### Post by jmbothe on 2018-02-20
[COLOR=#000000][FONT=&amp]I have Windows 10 installed on my brand-new Lenovo 710S-13IKB, and I want to install a linux distro (Ubuntu or Mint) as a dual boot. The problem I ran into is that when live booting Ubuntu or Mint from USB, the installer doesn't detect my SSD drive. It just says "Not enough space on this drive" referring to the USB drive.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I've done a good amount of research and I think the problem is that RAID is currently enabled on my SATA controller driver, and I guess Linux doesn't play nice with RAID. Most of the advice online says that i need to go into UEFI firmware (i.e., BIOS) and switch from RAID to AHCI (and probably re-install windows, or do some other magic handwaving to avoid trouble), but my UEFI firmware menu doesn't even have an option to switch between RAID and AHCI.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Digging deeper, I started to suspect that my chipset isn't able to support AHCI at all. The problem is I am having trouble determining if this is the case or not. SO MY QUESTION: how do I find out?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Here is everything I know:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Secure boot and fast boot are turned off. UEFI is still enabled. I am ahead of the curve on that. I have done dual boots before on other machines.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]- Harddrive is M.2 SSD[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]- In the Windows Device Manager, there is no IDE ATA/ATAPI controller dropdown.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]- There IS a Storage Controllers dropdown, and underneath there is "Intel Chipset SATA RAID Controller" and "Microsoft Storage Spaces Controller"[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]- Windows does not provide a whole lot of info on the motherboard. Under System Information I find the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Baseboard Manufacturer: Lenovo[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Baseboard Model: Not Available[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Basboard Name: baseboard[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Platform Role: Mobile[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]Here are the specs from lenovo:

[http://psref.lenovo.com/syspool/TempFile/cache/d660ba72-6183-4618-9f3d-ce179c083f4a/ideapad%20710S%20(13)%20single%20model%20201802202020.pdf](http://psref.lenovo.com/syspool/TempFile/cache/d660ba72-6183-4618-9f3d-ce179c083f4a/ideapad%20710S%20(13)%20single%20model%20201802202020.pdf)
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]If it turns out that my computer doesnt support AHCI, do I have any options for running a dual boot?[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]THANK YOU!!!![/FONT][/COLOR]

---

