---
title: "I'm unable to install WSL (Windows Subsystem for Linux)"
date: 2024-07-28
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2024-07-28
Some time ago, I managed to successfully install Ubuntu in WSL in Windows 10 running in VirtualBox on my host Ubuntu 22.04.

Now, I have Windows 11 running in VirtualBox on the same host Ubuntu 22.04. But, I cannot install Ubuntu in WSL.

Notes:

[LIST]
[*]I have turned on the guest's VirtualBox Settings > System > Processor > Extended Features > Enable Nested VT-x/AMD-V.
[*]Some of the instructions come from [Ubuntu's instructions]("https://canonical-ubuntu-wsl.readthedocs-hosted.com/en/latest/guides/install-ubuntu-wsl2/").
[/LIST]
Here are the steps that I've tried (I've also tried variations on this). These are all in the guest Windows 11 machine.

[LIST=1]
[*]Control Panel > Programs > Programs & Features > Turn Windows features on or off > turn on:
[LIST]
[*]Virtual Machine Platform
[*]Windows Hypervisor Platform
[*]Windows Subsystem for Linux
[*]and then restart Windows.
[/LIST]

[*]In PowerShell as an Administrator, run [FONT=courier new]wsl --update[/FONT] and then restart Windows.
[*]In PowerShell as an Administrator, run [FONT=courier new]wsl --install --distribution Ubuntu[/FONT] . This gives the following error:
[/LIST]
```
Installing: Ubuntu
Ubuntu has been installed.
Launching Ubuntu...
Installing, this may take a few minutes...
WslRegisterDistribution failed with error: 0x80370102
Please enable the Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS.
For information please visit https://aka.ms/enablevirtualization
```
Unfortunately, the [given link]("https://aka.ms/enablevirtualization") doesn't help me. It says to use this command:
```
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
```
But, alas, [FONT=courier new]Set-VMProcessor[/FONT] is not recognised as a command.

I didn't have any of these problems when I installed Ubuntu on WSL in Windows 10, yet in Windows 11, I get problems.

What can I do to install it successfully, please?

**More information**

[LIST]
[*]Host: Ubuntu 22.04
[*]VirtualBox version 7.0.20 r163906 (Qt5.15.3)
[*]Guest: Windows 11 Home, installed with Guest Additions enabled
[*]The Windows 11 installation is fairly barebones, with nothing installed other than what came on the installation ISO directly from the Microsoft website. It's fully up-to-date.
[/LIST]
Thank you

---

