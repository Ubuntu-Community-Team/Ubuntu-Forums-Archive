---
title: "Ubuntu just won't install"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by Wim_Van_Loock on 2014-11-04
[COLOR=#333333]Hi,

[/COLOR]After trying Ubuntu for a while through Virtual Box I wanted to install it next to Windows 7.

I first made a primary partition to install on, downloaded the ISO-file [COLOR=#333333](14.04.1 desktop amd64)[/COLOR]
[COLOR=#333333]and unpacked it with WinArchiver. Then I started the installation with wubi.exe.[/COLOR]

[COLOR=#333333]At the end I get this "permission denied" error.
[/COLOR]When I boot the PC I can choose between Ubuntu and W7 but by
choosing Ubuntu I also get an error.

Anyone any idea what I'm doing wrong?
I put the installation log file beneath(sorry for the length)

Thanks in advance for any reaction!

****************************************************************************
```


[COLOR=#333333]11-04 12:02 INFO root: === wubi 14.04 rev286 ===[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG root: Logfile is c:\users\wimvan~1\appdata\local\temp\wubi-14.04-rev286.log[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\WIMVAN~1\\AppData\\Local\\Temp\\$WinArchiver$\\wubi.exe"'][/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: data_dir=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\data[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: 7z=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\bin\7z.exe[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Fetching basic info...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: original_exe=C:\Users\WIMVAN~1\AppData\Local\Temp\$WinArchiver$\wubi.exe[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: platform=win32[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: osname=nt[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: language=nl_BE[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: encoding=cp1252[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: arch=amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Parsing isolist=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\data\isolist.ini[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Edubuntu-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Edubuntu-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Ubuntu Studio-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Lubuntu-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Ubuntu Studio-i386[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Adding distro Lubuntu-amd64[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: Fetching host info...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows version=vista[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_version2=Windows 7 Home Premium[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_sp=None[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_build=7601[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: gmt=1[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: country=BE[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: timezone=Europe/Brussels[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_username=Wim Van Loock[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: user_full_name=Wim Van Loock[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: user_directory=C:\Users\Wim Van Loock[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_language_code=1043[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: windows_language=Dutch[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: processor_name=Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: bootloader=vista[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: system_drive=Drive(C: hd 250736.035156 mb free ntfs)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: drive=Drive(C: hd 250736.035156 mb free ntfs)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free )[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: drive=Drive(U: hd 101315.214844 mb free ntfs)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: previous_target_dir=U:\ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: keyboard_id=135464979[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: keyboard_layout=be[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: keyboard_variant=[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: python locale=('nl_BE', 'cp1252')[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: locale=nl_BE.UTF-8[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: total_memory_mb=4040.0[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking Ubuntu ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: extracting .disk\info from U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: parsing info from str=Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04.1', 'build': '20140722.2', 'codename': 'Trusty Tahr', 'arch': 'amd64'}[/COLOR]
[COLOR=#333333]11-04 12:02 INFO Distro: Found a valid iso for Ubuntu: U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Searching for local CDs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Kubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Mythbuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Edubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Lubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Ubuntu Studio CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 INFO root: Running the installer...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsFrontend: __init__...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsFrontend: on_init...[/COLOR]
[COLOR=#333333]11-04 12:02 INFO WinuiPage: appname=wubi, localedir=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\translations, languages=['nl_BE', 'nl'][/COLOR]
[COLOR=#333333]11-04 12:02 INFO WinuiPage: appname=wubi, localedir=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\translations, languages=['nl_BE', 'nl'][/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WinuiInstallationPage: target_drive=U:, installation_size=30000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=wimvanloock[/COLOR]
[COLOR=#333333]11-04 12:02 INFO root: Received settings[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Searching for local CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain E:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking whether U:\ is a valid Ubuntu CD[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: does not contain U:\casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:02 INFO WinuiPage: appname=wubi, localedir=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\translations, languages=['nl_NL', 'nl'][/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: # Running tasklist...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running select_target_dir...[/COLOR]
[COLOR=#333333]11-04 12:02 INFO WindowsBackend: Installing into U:\ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Finished select_target_dir[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running create_dir_structure...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\disks[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\install[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\install\boot[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\disks\boot[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\disks\boot\grub[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Creating dir U:\ubuntu\install\boot\grub[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Finished create_dir_structure[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running uncompress_target_dir...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Finished uncompress_target_dir[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running create_uninstaller...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: Copying uninstaller C:\Users\WIMVAN~1\AppData\Local\Temp\$WinArchiver$\wubi.exe -> U:\ubuntu\uninstall-wubi.exe[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [/COLOR][The leading OS for PC, tablet, phone and cloud | Ubuntu]("http://www.ubuntu.com/")
[COLOR=#333333]11-04 12:02 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [/COLOR][Support | Ubuntu]("http://www.ubuntu.com/support")
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Finished create_uninstaller[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running copy_installation_files...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: Copying C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: Copying C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\winboot -> U:\ubuntu\winboot[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG WindowsBackend: Copying C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Finished copy_installation_files[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ## Running get_iso...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Trying to use pre-specified ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: New task is_valid_iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ### Running is_valid_iso...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking Ubuntu ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 INFO Distro: Found a valid iso for Ubuntu: U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ### Finished is_valid_iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: New task check_iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: ### Running check_iso...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: Checking U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG Distro: checking Ubuntu ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 INFO Distro: Found a valid iso for Ubuntu: U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: New task get_metalink[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: #### Running get_metalink...[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: downloading [/COLOR][http://releases.ubuntu.com/14.04/ubu...amd64.metalink]("http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink")[COLOR=#333333] > U:\ubuntu\install[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: Download start filename=U:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: download finished (read 45848 bytes)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: downloading [/COLOR][http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink)[COLOR=#333333] > U:\ubuntu\install[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: download finished (read 560 bytes)[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: downloading [/COLOR][http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg)[COLOR=#333333] > U:\ubuntu\install[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG downloader: download finished (read 198 bytes)[/COLOR]
[COLOR=#333333]11-04 12:02 INFO saplog: Verified a signature from ID:'46181433FBB75451'.[/COLOR]
[COLOR=#333333]11-04 12:02 INFO saplog: Checking block bindings..[/COLOR]
[COLOR=#333333]11-04 12:02 INFO saplog: Key verified successfully.[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG CommonBackend: metalink md5sums:[/COLOR]
[COLOR=#333333]a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink[/COLOR]
[COLOR=#333333]d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink[/COLOR]
[COLOR=#333333]b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink[/COLOR]
[COLOR=#333333]63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink[/COLOR]
[COLOR=#333333]d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink[/COLOR]
[COLOR=#333333]3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink[/COLOR]
[COLOR=#333333]3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink[/COLOR]
[COLOR=#333333]38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink[/COLOR]


[COLOR=#333333]11-04 12:02 ERROR CommonBackend: The md5 of the metalink does match[/COLOR]
[COLOR=#333333]11-04 12:02 ERROR CommonBackend: Cannot authenticate the metalink file, it might be corrupt[/COLOR]
[COLOR=#333333]None[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: #### Finished get_metalink[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: New task get_file_md5[/COLOR]
[COLOR=#333333]11-04 12:02 DEBUG TaskList: #### Running get_file_md5...[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: #### Finished get_file_md5[/COLOR]
[COLOR=#333333]11-04 12:03 ERROR CommonBackend: Invalid md5 for ISO U:\ubuntu-14.04.1-desktop-amd64.iso (dccff28314d9ae4ed262cfc6f35e5153 != 119cb63b48c9a18f31f417f09655efbd)[/COLOR]
[COLOR=#333333]None[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Finished check_iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG CommonBackend: Trying to use ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: New task check_iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Running check_iso...[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG CommonBackend: Checking U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG Distro: checking Ubuntu ISO U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 INFO Distro: Found a valid iso for Ubuntu: U:\ubuntu-14.04.1-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 ERROR CommonBackend: Invalid md5 for ISO U:\ubuntu-14.04.1-desktop-amd64.iso (dccff28314d9ae4ed262cfc6f35e5153 != 119cb63b48c9a18f31f417f09655efbd)[/COLOR]
[COLOR=#333333]None[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Finished check_iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: New task download[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Running download...[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG btdownloader: downloading [/COLOR][http://releases.ubuntu.com/14.04.1/u...64.iso.torrent]("http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent")[COLOR=#333333] > U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 ERROR TaskList: Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 229, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 221, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 90, in add[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 105, in postrequest[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.[/COLOR]


[COLOR=#333333]Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 78, in download[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\download.py", line 303, in download[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 256, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 229, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 221, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 90, in add[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 105, in postrequest[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.[/COLOR]




[COLOR=#333333]11-04 12:03 ERROR TaskList: Non fatal error Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 229, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\RawServer.py", line 221, in listen_forever[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 90, in add[/COLOR]
[COLOR=#333333]File "\lib\bittorrent\Rerequester.py", line 105, in postrequest[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback[/COLOR]
[COLOR=#333333]DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.[/COLOR]


[COLOR=#333333]in task download[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Finished download[/COLOR]
[COLOR=#333333]11-04 12:03 ERROR root: Could not remove: U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\backend.py", line 426, in download_iso[/COLOR]
[COLOR=#333333]OSError: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: New task download[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG TaskList: ### Running download...[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG downloader: downloading [/COLOR][http://mirror.vutbr.cz/ubuntu/releas...ktop-amd64.iso]("http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso")[COLOR=#333333] > U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:03 DEBUG downloader: Download start filename=U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: ### Finished download[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG downloader: download finished (read 1010827264 bytes)[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: New task check_iso[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: ### Running check_iso...[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG CommonBackend: Checking U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG Distro: checking Ubuntu ISO U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:08 ERROR WindowsBackend: Error executing command[/COLOR]
[COLOR=#333333]>>command=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\bin\7z.exe l U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]>>retval=2[/COLOR]
[COLOR=#333333]>>stderr=[/COLOR]


[COLOR=#333333]7-Zip 9.20 Copyright (c) 1999-2010 Igor Pavlov 2010-11-18[/COLOR]






[COLOR=#333333]Error: U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: Het proces heeft geen toegang tot het bestand omdat het door een ander[/COLOR]




[COLOR=#333333]proces wordt gebruikt.[/COLOR]












[COLOR=#333333]Errors: 1[/COLOR]
[COLOR=#333333]>>stdout=[/COLOR]
[COLOR=#333333]Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\utils.py", line 66, in run_command[/COLOR]
[COLOR=#333333]Exception: Error executing command[/COLOR]
[COLOR=#333333]>>command=C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\bin\7z.exe l U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]>>retval=2[/COLOR]
[COLOR=#333333]>>stderr=[/COLOR]


[COLOR=#333333]7-Zip 9.20 Copyright (c) 1999-2010 Igor Pavlov 2010-11-18[/COLOR]






[COLOR=#333333]Error: U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: Het proces heeft geen toegang tot het bestand omdat het door een ander[/COLOR]




[COLOR=#333333]proces wordt gebruikt.[/COLOR]












[COLOR=#333333]Errors: 1[/COLOR]
[COLOR=#333333]>>stdout=[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG WindowsBackend: command >>C:\Users\WIMVAN~1\AppData\Local\Temp\pyl6CE5.tmp\bin\7z.exe l U:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG Distro: does not contain casper\filesystem.squashfs[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: ### Finished check_iso[/COLOR]
[COLOR=#333333]11-04 12:08 ERROR TaskList: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'[/COLOR]
[COLOR=#333333]Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\backend.py", line 595, in get_iso[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\backend.py", line 441, in download_iso[/COLOR]
[COLOR=#333333]OSError: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: # Cancelling tasklist[/COLOR]
[COLOR=#333333]11-04 12:08 DEBUG TaskList: # Finished tasklist[/COLOR]
[COLOR=#333333]11-04 12:08 ERROR root: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'[/COLOR]
[COLOR=#333333]Traceback (most recent call last):[/COLOR]
[COLOR=#333333]File "\lib\wubi\application.py", line 58, in run[/COLOR]
[COLOR=#333333]File "\lib\wubi\application.py", line 132, in select_task[/COLOR]
[COLOR=#333333]File "\lib\wubi\application.py", line 158, in run_installer[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\backend.py", line 595, in get_iso[/COLOR]
[COLOR=#333333]File "\lib\wubi\backends\common\backend.py", line 441, in download_iso[/COLOR]
[COLOR=#333333]OSError: [Errno 13] Permission denied: u'U:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'[/COLOR]
```

---

### Post by sudodus on 2014-11-04
Welcome to the Ubuntu Forums :-)

Please do not use wubi. It is an old tool for trying Ubuntu, but you have already tried in in VBox, so you are ready for a real dual boot installation. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

Do not unpack the iso file using the file archiver. Instead copy/flash/clone it to a USB pendrive according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

or burn an iso image to a DVD disk (do not make a data DVD with one file).

Finally, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

and you can get help for the installing steps later on ...

---

### Post by Wim_Van_Loock on 2014-11-04
It may sound rather stupid but I can't burn CD-DVD's anymore(the drive won't recognize any disk, so in fact, it's broke) and
I don't have a USB-stick available.

I also tried putting the ISO-file on an external hard drive but I couldn't get the
BIOS to boot from it.

There must be a way to install from the ISO-file on your hard-disk, no?

---

### Post by sudodus on 2014-11-04
It is possible to boot from an external hard disk drive (USB or eSATA), but if you have other data there, data that you want to keep, it will be risky. There are cheap USB pendrives, that are slower than more expensive ones, but still very reliable, for example Sandisk Cruzer Blade 4 GB. It is also possible to boot from the internal drive, but more advanced, maybe not the first thing to try.

You run Windows 7, so I assume the computer is not too old. It should be able to boot from USB. You find several tips about booting in this link

[https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

It will help giving relevant advice if you specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by Wim_Van_Loock on 2014-11-04
eMachines EL1870
Intel core i3 4 X 2100CPU 3.10GHz
4GB DDR3 Ram
Intel HD Graphics

WiFi chip card, I don't know. I just know I'm on a LAN cable network.... :-)

---

### Post by Wim_Van_Loock on 2014-11-04
This should give you a better idea of my computer's specs :

[http://speccy.piriform.com/results/YrirSDXPBejKcRArDuA4pFv](http://speccy.piriform.com/results/YrirSDXPBejKcRArDuA4pFv)

---

### Post by Wim_Van_Loock on 2014-11-04
> **sudodus said:**
>  It is also possible to boot from the internal drive, but more advanced, maybe not the first thing to try.



Is there a tutorial to do this? I'm willing to learn and take the risk.... ;)

---

### Post by sudodus on 2014-11-04
Then you should start by taking a ***backup*** of your internal drive,

1 - everything

2 - or at least
a. all your personal files (documents, pictures, mail files ...)
b. Windows - at least a recovery system

because installing an operating system is risky.

-o-

You can create a partition, install grub into it, and point grub to the iso file. You can find tutorials via the internet, for example

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27)

and you can extract files from the iso file (this is old, uses 'old grub', and more complicated than necessary)

 [https://help.ubuntu.com/community/Installation/FromUSBStick#Create_Bootable_USB_Manually](https://help.ubuntu.com/community/Installation/FromUSBStick#Create_Bootable_USB_Manually)

-o-

But if Windows is installed in ***UEFI*** mode, things are much more complicated, and I would definitely advice only the standard method via a USB boot drive, and you may need [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to get a dual boot system working.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sudodus on 2014-11-04
> **Wim_Van_Loock said:**
> Is there a tutorial to do this? I'm willing to learn and take the risk.... ;)

Please think again, if you can get (buy or borrow) a USB pendrive!

---

### Post by sudodus on 2014-11-04
> **Wim_Van_Loock said:**
> eMachines EL1870
Intel core i3 4 X 2100CPU 3.10GHz
4GB DDR3 Ram
Intel HD Graphics

WiFi chip card, I don't know. I just know I'm on a LAN cable network.... :-)

It is powerful enough and new enough to boot from USB. Maybe you can also find out, if Windows is installed in UEFI or old style BIOS mode (alias CSM).

---

### Post by phidia on 2014-11-04
Take a look at this official [installation guide]("https://help.ubuntu.com/community/Installation"). Under Server and network installation you'll see guides on how to do a netboot install. You could follow that and install that way, but do make backups of everything as was previously suggested.

---

