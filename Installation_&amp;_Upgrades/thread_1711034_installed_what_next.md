---
title: "installed what next"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by johnnybevo on 2011-03-20
I installed 10.10, dual boot. (with xp pro)
Did reboot.
choose ubuntu from boot options.
Now only have progress bar no gui.
What next?

---

### Post by Hakunka-Matata on 2011-03-20
please provide a few more details

---

### Post by sikander3786 on 2011-03-21
Yes we need some details.

Everything we need to know, bootinfoscript will tell us. Please boot an Ubuntu Live CD/USB and post the output of the script as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes as this will be a long output.

In the meantime, you can try using the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

I couldn't understand what you mean by 'progress bar'. Is it the Ubuntu logo screen with flashing dots?

---

### Post by Rubi1200 on 2011-03-21
Did you install with Wubi inside Windows?

---

### Post by johnnybevo on 2011-03-21
> **Rubi1200 said:**
> Did you install with Wubi inside Windows?

yes it is installed inside windows

I have tried nomodeset that does not work.


"I couldn't understand what you mean by 'progress bar'. Is it the Ubuntu logo screen with flashing dots?" Yes

I dont know how to open a terminal the is all new to me.

---

### Post by Rubi1200 on 2011-03-21
Can you still boot Windows normally?

Did this happen after a new install of Wubi or after some updates perhaps?

I think you will find the answers in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Have a read and if you still have questions or would like me to explain in more detail, feel free to ask.

---

### Post by johnnybevo on 2011-03-21
> **Rubi1200 said:**
> Can you still boot Windows normally?

Did this happen after a new install of Wubi or after some updates perhaps?

I think you will find the answers in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Have a read and if you still have questions or would like me to explain in more detail, feel free to ask.

Yes windows is working fine.
I think maybe my mouse, as I was watching code fly by,
It said something about 
usb disconnect then address
new lowspeed usb device, then gave info. about my mouse.
  
  I will go read info you posted.
Thanks for the help

---

### Post by johnnybevo on 2011-03-21
about to give up. very frustrated now. aahhhh
Hearing much about Ubuntu, but if I cant get it too run, it is no good.

---

### Post by Rubi1200 on 2011-03-21
Let's take a step back.

Please confirm:

you installed Wubi inside Windows and it asked you to reboot.

after rebooting you got stuck at the point you described without ever actually booting into Ubuntu.

So far so good?

If so, the installation never completed.

Do you have another mouse you can try?

If you enter BIOS are there settings for legacy USB devices and how is it set?

---

### Post by johnnybevo on 2011-03-21
> **Rubi1200 said:**
> Let's take a step back.

Please confirm:

you installed Wubi inside Windows and it asked you to reboot.

after rebooting you got stuck at the point you described without ever actually booting into Ubuntu.

So far so good?

If so, the installation never completed.

Do you have another mouse you can try?

If you enter BIOS are there settings for legacy USB devices and how is it set?

Installed inside windows and it ask for a reboot. yes the install never completed you are correct. 
I do not have another mouse but I will check the BIOS.
What really stinks is I just uninstalled aahhh.
I do have the ISO burned to cd, the last time it would not work so I used wubi and downloaded.
I am going to take a look at the Bios before I do a reinstall.
Be back soon.

---

### Post by johnnybevo on 2011-03-21
USB legacy support is set to auto.
Should I try to install again?

I should mention I have to disable my card readers to avoid the windows no disk error. dont know if that means anything

I am going to try to install again from disk

---

### Post by johnnybevo on 2011-03-21
trying to install from cd I get an invalid argument.

03-20 15:48 INFO   root: === wubi 10.10 rev197 ===
03-20 15:48 DEBUG  root: Logfile is h:\docume~1\johnny\locals~1\temp\wubi-10.10-rev197.log
03-20 15:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
03-20 15:48 DEBUG  CommonBackend: data_dir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\data
03-20 15:48 DEBUG  WindowsBackend: 7z=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
03-20 15:48 DEBUG  CommonBackend: Fetching basic info...
03-20 15:48 DEBUG  CommonBackend: original_exe=H:\wubi.exe
03-20 15:48 DEBUG  CommonBackend: platform=win32
03-20 15:48 DEBUG  CommonBackend: osname=nt
03-20 15:48 DEBUG  CommonBackend: language=en_US
03-20 15:48 DEBUG  CommonBackend: encoding=cp1252
03-20 15:48 DEBUG  WindowsBackend: arch=i386
03-20 15:48 DEBUG  CommonBackend: Parsing isolist=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
03-20 15:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-20 15:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-20 15:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-20 15:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-20 15:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-20 15:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-20 15:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-20 15:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-20 15:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-20 15:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-20 15:48 DEBUG  WindowsBackend: Fetching host info...
03-20 15:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-20 15:48 DEBUG  WindowsBackend: windows version=xp
03-20 15:48 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-20 15:48 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-20 15:48 DEBUG  WindowsBackend: windows_build=2600
03-20 15:48 DEBUG  WindowsBackend: gmt=-6
03-20 15:48 DEBUG  WindowsBackend: country=US
03-20 15:48 DEBUG  WindowsBackend: timezone=America/Chicago
03-20 15:48 DEBUG  WindowsBackend: windows_username=johnny
03-20 15:48 DEBUG  WindowsBackend: user_full_name=johnny
03-20 15:48 DEBUG  WindowsBackend: user_directory=H:\Documents and Settings\johnny
03-20 15:48 DEBUG  WindowsBackend: windows_language_code=1033
03-20 15:48 DEBUG  WindowsBackend: windows_language=English
03-20 15:48 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.93GHz
03-20 15:48 DEBUG  WindowsBackend: bootloader=xp
03-20 15:48 DEBUG  WindowsBackend: system_drive=Drive(H: hd 48065.6054688 mb free ntfs)
03-20 15:48 DEBUG  WindowsBackend: drive=Drive(C: hd 1222.1328125 mb free fat32)
03-20 15:48 DEBUG  WindowsBackend: drive=Drive(H: hd 48065.6054688 mb free ntfs)
03-20 15:48 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-20 15:48 DEBUG  WindowsBackend: uninstaller_path=None
03-20 15:48 DEBUG  WindowsBackend: previous_target_dir=None
03-20 15:48 DEBUG  WindowsBackend: previous_distro_name=None
03-20 15:48 DEBUG  WindowsBackend: keyboard_id=67699721
03-20 15:48 DEBUG  WindowsBackend: keyboard_layout=us
03-20 15:48 DEBUG  WindowsBackend: keyboard_variant=
03-20 15:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-20 15:48 DEBUG  CommonBackend: locale=en_US.UTF-8
03-20 15:48 DEBUG  WindowsBackend: total_memory_mb=1527.484375
03-20 15:48 DEBUG  CommonBackend: Searching ISOs on USB devices
03-20 15:48 DEBUG  CommonBackend: Searching for local CDs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 INFO   root: Running the installer...
03-20 15:48 DEBUG  WindowsFrontend: __init__...
03-20 15:48 DEBUG  WindowsFrontend: on_init...
03-20 15:48 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
03-20 15:48 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
03-20 15:48 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=johnny
03-20 15:48 INFO   root: Received settings
03-20 15:48 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
03-20 15:48 DEBUG  TaskList: # Running tasklist...
03-20 15:48 DEBUG  TaskList: ## Running select_target_dir...
03-20 15:48 INFO   WindowsBackend: Installing into H:\ubuntu
03-20 15:48 DEBUG  TaskList: ## Finished select_target_dir
03-20 15:48 DEBUG  TaskList: ## Running create_dir_structure...
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
03-20 15:48 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
03-20 15:48 DEBUG  TaskList: ## Finished create_dir_structure
03-20 15:48 DEBUG  TaskList: ## Running uncompress_target_dir...
03-20 15:48 DEBUG  TaskList: ## Finished uncompress_target_dir
03-20 15:48 DEBUG  TaskList: ## Running create_uninstaller...
03-20 15:48 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-20 15:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-20 15:48 DEBUG  TaskList: ## Finished create_uninstaller
03-20 15:48 DEBUG  TaskList: ## Running copy_installation_files...
03-20 15:48 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
03-20 15:48 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\winboot -> H:\ubuntu\winboot
03-20 15:48 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
03-20 15:48 DEBUG  TaskList: ## Finished copy_installation_files
03-20 15:48 DEBUG  TaskList: ## Running get_iso...
03-20 15:48 DEBUG  CommonBackend: Searching for local CD
03-20 15:48 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-20 15:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-20 15:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-20 15:48 DEBUG  CommonBackend: Searching for local ISO
03-20 15:48 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-20 15:48 DEBUG  TaskList: New task get_metalink
03-20 15:48 DEBUG  TaskList: ### Running get_metalink...
03-20 15:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink) > H:\ubuntu\install
03-20 15:48 DEBUG  downloader: Download start filename=H:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
03-20 15:48 DEBUG  downloader: download finished (read 9071 bytes)
03-20 15:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > H:\ubuntu\install
03-20 15:48 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-20 15:48 DEBUG  downloader: download finished (read 488 bytes)
03-20 15:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > H:\ubuntu\install
03-20 15:48 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-20 15:48 DEBUG  downloader: download finished (read 198 bytes)
03-20 15:48 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-20 15:48 INFO   saplog: Checking block bindings..
03-20 15:48 INFO   saplog: Key verified successfully.
03-20 15:48 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

03-20 15:48 DEBUG  TaskList: ### Finished get_metalink
03-20 15:48 DEBUG  TaskList: New task download
03-20 15:48 DEBUG  TaskList: ### Running download...
03-20 15:48 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.iso.torrent) > H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  TaskList: ### Finished download
03-20 16:30 DEBUG  TaskList: New task check_iso
03-20 16:30 DEBUG  TaskList: ### Running check_iso...
03-20 16:30 DEBUG  CommonBackend: Checking H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-20 16:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-20 16:30 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  TaskList: New task get_file_md5
03-20 16:30 DEBUG  TaskList: #### Running get_file_md5...
03-20 16:30 DEBUG  TaskList: #### Finished get_file_md5
03-20 16:30 DEBUG  TaskList: ### Finished check_iso
03-20 16:30 DEBUG  TaskList: ## Finished get_iso
03-20 16:30 DEBUG  TaskList: ## Running extract_kernel...
03-20 16:30 DEBUG  CommonBackend: Extracting files from ISO H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  WindowsBackend:   extracting md5sum.txt from H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  WindowsBackend:   extracting casper\vmlinuz from H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  WindowsBackend:   extracting casper\initrd.lz from H:\ubuntu\install\ubuntu-10.10-desktop-i386.iso
03-20 16:30 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-20 16:30 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\vmlinuz
03-20 16:30 DEBUG  CommonBackend:   H:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
03-20 16:30 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\initrd.lz
03-20 16:30 DEBUG  CommonBackend:   H:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
03-20 16:30 DEBUG  TaskList: ## Finished extract_kernel
03-20 16:30 DEBUG  TaskList: ## Running choose_disk_sizes...
03-20 16:30 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
03-20 16:30 DEBUG  TaskList: ## Finished choose_disk_sizes
03-20 16:30 DEBUG  TaskList: ## Running create_preseed...
03-20 16:30 DEBUG  TaskList: ## Finished create_preseed
03-20 16:30 DEBUG  TaskList: ## Running modify_bootloader...
03-20 16:30 DEBUG  TaskList: New task modify_bootini
03-20 16:30 DEBUG  TaskList: ### Running modify_bootini...
03-20 16:30 DEBUG  WindowsBackend: modify_bootini C:
03-20 16:30 DEBUG  TaskList: ### Finished modify_bootini
03-20 16:30 DEBUG  TaskList: New task modify_bootini
03-20 16:30 DEBUG  TaskList: ### Running modify_bootini...
03-20 16:30 DEBUG  WindowsBackend: modify_bootini H:
03-20 16:30 DEBUG  WindowsBackend: Could not find boot.ini H:\boot.ini
03-20 16:30 DEBUG  TaskList: ### Finished modify_bootini
03-20 16:30 DEBUG  TaskList: ## Finished modify_bootloader
03-20 16:30 DEBUG  TaskList: ## Running modify_grub_configuration...
03-20 16:30 DEBUG  TaskList: ## Finished modify_grub_configuration
03-20 16:30 DEBUG  TaskList: ## Running create_virtual_disks...
03-20 16:30 DEBUG  Virtualdisk:  Creating virtual disk H:\ubuntu\disks\root.disk of 16744MB
03-20 16:30 DEBUG  Virtualdisk:  Creating virtual disk H:\ubuntu\disks\swap.disk of 256MB
03-20 16:30 DEBUG  TaskList: ## Finished create_virtual_disks
03-20 16:30 DEBUG  TaskList: ## Running uncompress_files...
03-20 16:30 DEBUG  WindowsBackend: compact H:\ubuntu\install\boot /U /A /F
03-20 16:30 DEBUG  WindowsBackend: compact H:\ubuntu\install\boot\*.* /U /A /F
03-20 16:30 DEBUG  TaskList: ## Finished uncompress_files
03-20 16:30 DEBUG  TaskList: ## Running eject_cd...
03-20 16:30 DEBUG  TaskList: ## Finished eject_cd
03-20 16:30 DEBUG  TaskList: # Finished tasklist
03-20 16:30 INFO   root: Almost finished installing
03-20 16:30 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
03-20 16:31 INFO   root: Finished installation
03-20 16:31 INFO   root: Rebooting
03-20 16:31 DEBUG  TaskList: # Running tasklist...
03-20 16:31 DEBUG  TaskList: ## Running reboot...
03-20 16:31 DEBUG  TaskList: ## Finished reboot
03-20 16:31 DEBUG  TaskList: # Finished tasklist
03-20 16:31 DEBUG  root: application.quit
03-20 16:31 DEBUG  WindowsFrontend: frontend.quit
03-20 16:31 DEBUG  WindowsFrontend: frontend.on_quit
03-20 16:31 DEBUG  root: application.on_quit
03-20 16:31 INFO   root: sys.exit
03-21 13:10 INFO   root: === wubi 10.10 rev197 ===
03-21 13:10 DEBUG  root: Logfile is h:\docume~1\johnny\locals~1\temp\wubi-10.10-rev197.log
03-21 13:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
03-21 13:10 DEBUG  CommonBackend: data_dir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl3D.tmp\data
03-21 13:10 DEBUG  WindowsBackend: 7z=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl3D.tmp\bin\7z.exe
03-21 13:10 DEBUG  CommonBackend: Fetching basic info...
03-21 13:10 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-21 13:10 DEBUG  CommonBackend: platform=win32
03-21 13:10 DEBUG  CommonBackend: osname=nt
03-21 13:10 DEBUG  CommonBackend: language=en_US
03-21 13:10 DEBUG  CommonBackend: encoding=cp1252
03-21 13:10 DEBUG  WindowsBackend: arch=i386
03-21 13:10 DEBUG  CommonBackend: Parsing isolist=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl3D.tmp\data\isolist.ini
03-21 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 13:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 13:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 13:10 DEBUG  WindowsBackend: Fetching host info...
03-21 13:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 13:10 DEBUG  WindowsBackend: windows version=xp
03-21 13:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 13:10 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-21 13:10 DEBUG  WindowsBackend: windows_build=2600
03-21 13:10 DEBUG  WindowsBackend: gmt=-6
03-21 13:10 DEBUG  WindowsBackend: country=US
03-21 13:10 DEBUG  WindowsBackend: timezone=America/Chicago
03-21 13:10 DEBUG  WindowsBackend: windows_username=johnny
03-21 13:10 DEBUG  WindowsBackend: user_full_name=johnny
03-21 13:10 DEBUG  WindowsBackend: user_directory=H:\Documents and Settings\johnny
03-21 13:10 DEBUG  WindowsBackend: windows_language_code=1033
03-21 13:10 DEBUG  WindowsBackend: windows_language=English
03-21 13:10 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.93GHz
03-21 13:10 DEBUG  WindowsBackend: bootloader=xp
03-21 13:10 DEBUG  WindowsBackend: system_drive=Drive(H: hd 30335.0585938 mb free ntfs)
03-21 13:10 DEBUG  WindowsBackend: drive=Drive(C: hd 1222.01953125 mb free fat32)
03-21 13:10 DEBUG  WindowsBackend: drive=Drive(D: removable 0.0 mb free )
03-21 13:10 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
03-21 14:33 INFO   root: === wubi 10.10 rev197 ===
03-21 14:33 DEBUG  root: Logfile is h:\docume~1\johnny\locals~1\temp\wubi-10.10-rev197.log
03-21 14:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\ubuntu\\uninstall-wubi.exe"']
03-21 14:33 DEBUG  CommonBackend: data_dir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\data
03-21 14:33 DEBUG  WindowsBackend: 7z=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\bin\7z.exe
03-21 14:33 DEBUG  CommonBackend: Fetching basic info...
03-21 14:33 DEBUG  CommonBackend: original_exe=H:\ubuntu\uninstall-wubi.exe
03-21 14:33 DEBUG  CommonBackend: platform=win32
03-21 14:33 DEBUG  CommonBackend: osname=nt
03-21 14:33 DEBUG  CommonBackend: language=en_US
03-21 14:33 DEBUG  CommonBackend: encoding=cp1252
03-21 14:33 DEBUG  WindowsBackend: arch=i386
03-21 14:33 DEBUG  CommonBackend: Parsing isolist=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\data\isolist.ini
03-21 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 14:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 14:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 14:33 DEBUG  WindowsBackend: Fetching host info...
03-21 14:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 14:33 DEBUG  WindowsBackend: windows version=xp
03-21 14:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 14:33 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-21 14:33 DEBUG  WindowsBackend: windows_build=2600
03-21 14:33 DEBUG  WindowsBackend: gmt=-6
03-21 14:33 DEBUG  WindowsBackend: country=US
03-21 14:33 DEBUG  WindowsBackend: timezone=America/Chicago
03-21 14:33 DEBUG  WindowsBackend: windows_username=johnny
03-21 14:33 DEBUG  WindowsBackend: user_full_name=johnny
03-21 14:33 DEBUG  WindowsBackend: user_directory=H:\Documents and Settings\johnny
03-21 14:33 DEBUG  WindowsBackend: windows_language_code=1033
03-21 14:33 DEBUG  WindowsBackend: windows_language=English
03-21 14:33 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.93GHz
03-21 14:33 DEBUG  WindowsBackend: bootloader=xp
03-21 14:33 DEBUG  WindowsBackend: system_drive=Drive(H: hd 30301.3945313 mb free ntfs)
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(C: hd 1222.015625 mb free fat32)
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(D: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(H: hd 30301.3945313 mb free ntfs)
03-21 14:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: uninstaller_path=H:\ubuntu\uninstall-wubi.exe
03-21 14:33 DEBUG  WindowsBackend: previous_target_dir=H:\ubuntu
03-21 14:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-21 14:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-21 14:33 DEBUG  WindowsBackend: keyboard_layout=us
03-21 14:33 DEBUG  WindowsBackend: keyboard_variant=
03-21 14:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-21 14:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-21 14:33 DEBUG  WindowsBackend: total_memory_mb=1527.484375
03-21 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-21 14:33 DEBUG  CommonBackend: Searching for local CDs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-21 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
03-21 14:33 INFO   root: Running the uninstaller...
03-21 14:33 INFO   CommonBackend: This is the uninstaller running
03-21 14:33 DEBUG  WindowsFrontend: __init__...
03-21 14:33 DEBUG  WindowsFrontend: on_init...
03-21 14:33 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_US', 'en']
03-21 14:33 INFO   root: Received settings
03-21 14:33 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_US', 'en']
03-21 14:33 DEBUG  TaskList: # Running tasklist...
03-21 14:33 DEBUG  TaskList: ## Running Backup ISO...
03-21 14:33 DEBUG  TaskList: ## Finished Backup ISO
03-21 14:33 DEBUG  TaskList: ## Running Remove bootloader entry...
03-21 14:33 ERROR  WindowsBackend: Cannot find bcdedit
03-21 14:33 DEBUG  WindowsBackend: undo_bootini C:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 1222.015625 mb free fat32)
03-21 14:33 DEBUG  WindowsBackend: undo_bootini D:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: undo_bootini E:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: undo_bootini F:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: undo_bootini G:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
03-21 14:33 DEBUG  WindowsBackend: undo_bootini H:
03-21 14:33 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 30301.3945313 mb free ntfs)
03-21 14:33 DEBUG  TaskList: ## Finished Remove bootloader entry
03-21 14:33 DEBUG  TaskList: ## Running Remove target dir...
03-21 14:33 DEBUG  CommonBackend: Deleting H:\ubuntu
03-21 14:33 DEBUG  TaskList: ## Finished Remove target dir
03-21 14:33 DEBUG  TaskList: ## Running Remove registry key...
03-21 14:33 DEBUG  TaskList: ## Finished Remove registry key
03-21 14:33 DEBUG  TaskList: # Finished tasklist
03-21 14:33 INFO   root: Almost finished uninstalling
03-21 14:33 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_US', 'en']
03-21 14:33 INFO   root: Finished uninstallation
03-21 14:33 DEBUG  root: application.quit
03-21 14:33 DEBUG  WindowsFrontend: frontend.quit
03-21 14:33 DEBUG  WindowsFrontend: frontend.on_quit
03-21 14:33 DEBUG  root: application.on_quit
03-21 14:33 INFO   root: sys.exit
03-21 14:56 INFO   root: === wubi 10.10 rev197 ===
03-21 14:56 DEBUG  root: Logfile is h:\docume~1\johnny\locals~1\temp\wubi-10.10-rev197.log
03-21 14:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
03-21 14:56 DEBUG  CommonBackend: data_dir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\data
03-21 14:56 DEBUG  WindowsBackend: 7z=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\bin\7z.exe
03-21 14:56 DEBUG  CommonBackend: Fetching basic info...
03-21 14:56 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-21 14:56 DEBUG  CommonBackend: platform=win32
03-21 14:56 DEBUG  CommonBackend: osname=nt
03-21 14:56 DEBUG  CommonBackend: language=en_US
03-21 14:56 DEBUG  CommonBackend: encoding=cp1252
03-21 14:56 DEBUG  WindowsBackend: arch=i386
03-21 14:56 DEBUG  CommonBackend: Parsing isolist=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\data\isolist.ini
03-21 14:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 14:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 14:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 14:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 14:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 14:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 14:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 14:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 14:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 14:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 14:56 DEBUG  WindowsBackend: Fetching host info...
03-21 14:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 14:56 DEBUG  WindowsBackend: windows version=xp
03-21 14:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 14:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-21 14:56 DEBUG  WindowsBackend: windows_build=2600
03-21 14:56 DEBUG  WindowsBackend: gmt=-6
03-21 14:56 DEBUG  WindowsBackend: country=US
03-21 14:56 DEBUG  WindowsBackend: timezone=America/Chicago
03-21 14:56 DEBUG  WindowsBackend: windows_username=johnny
03-21 14:56 DEBUG  WindowsBackend: user_full_name=johnny
03-21 14:56 DEBUG  WindowsBackend: user_directory=H:\Documents and Settings\johnny
03-21 14:56 DEBUG  WindowsBackend: windows_language_code=1033
03-21 14:56 DEBUG  WindowsBackend: windows_language=English
03-21 14:56 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.93GHz
03-21 14:56 DEBUG  WindowsBackend: bootloader=xp
03-21 14:56 DEBUG  WindowsBackend: system_drive=Drive(H: hd 48028.390625 mb free ntfs)
03-21 14:56 DEBUG  WindowsBackend: drive=Drive(C: hd 1222.12109375 mb free fat32)
03-21 14:56 DEBUG  WindowsBackend: drive=Drive(H: hd 48028.390625 mb free ntfs)
03-21 14:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-21 14:56 DEBUG  WindowsBackend: uninstaller_path=None
03-21 14:56 DEBUG  WindowsBackend: previous_target_dir=None
03-21 14:56 DEBUG  WindowsBackend: previous_distro_name=None
03-21 14:56 DEBUG  WindowsBackend: keyboard_id=67699721
03-21 14:56 DEBUG  WindowsBackend: keyboard_layout=us
03-21 14:56 DEBUG  WindowsBackend: keyboard_variant=
03-21 14:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-21 14:56 DEBUG  CommonBackend: locale=en_US.UTF-8
03-21 14:56 DEBUG  WindowsBackend: total_memory_mb=1527.484375
03-21 14:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-21 14:56 DEBUG  CommonBackend: Searching for local CDs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 14:56 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu Netbook CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu Netbook CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
03-21 14:56 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
03-21 14:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 14:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-21 14:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-21 14:56 DEBUG  Distro: wrong arch: i386 != amd64
03-21 14:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 14:56 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-21 14:56 INFO   root: Running the CD menu...
03-21 14:56 DEBUG  WindowsFrontend: __init__...
03-21 14:56 DEBUG  WindowsFrontend: on_init...
03-21 14:56 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\translations, languages=['en_US', 'en']
03-21 14:56 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl26.tmp\translations, languages=['en_US', 'en']
03-21 14:56 INFO   WindowsFrontend: Operation cancelled
03-21 14:56 DEBUG  WindowsFrontend: frontend.quit
03-21 14:56 DEBUG  WindowsFrontend: frontend.on_quit
03-21 14:56 DEBUG  root: application.on_quit
03-21 14:56 INFO   root: sys.exit
03-21 15:00 INFO   root: === wubi 10.10 rev197 ===
03-21 15:00 DEBUG  root: Logfile is h:\docume~1\johnny\locals~1\temp\wubi-10.10-rev197.log
03-21 15:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
03-21 15:00 DEBUG  CommonBackend: data_dir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\data
03-21 15:00 DEBUG  WindowsBackend: 7z=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\bin\7z.exe
03-21 15:00 DEBUG  CommonBackend: Fetching basic info...
03-21 15:00 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-21 15:00 DEBUG  CommonBackend: platform=win32
03-21 15:00 DEBUG  CommonBackend: osname=nt
03-21 15:00 DEBUG  CommonBackend: language=en_US
03-21 15:00 DEBUG  CommonBackend: encoding=cp1252
03-21 15:00 DEBUG  WindowsBackend: arch=i386
03-21 15:00 DEBUG  CommonBackend: Parsing isolist=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\data\isolist.ini
03-21 15:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-21 15:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-21 15:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-21 15:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-21 15:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-21 15:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-21 15:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-21 15:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-21 15:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-21 15:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-21 15:00 DEBUG  WindowsBackend: Fetching host info...
03-21 15:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-21 15:00 DEBUG  WindowsBackend: windows version=xp
03-21 15:00 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-21 15:00 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-21 15:00 DEBUG  WindowsBackend: windows_build=2600
03-21 15:00 DEBUG  WindowsBackend: gmt=-6
03-21 15:00 DEBUG  WindowsBackend: country=US
03-21 15:00 DEBUG  WindowsBackend: timezone=America/Chicago
03-21 15:00 DEBUG  WindowsBackend: windows_username=johnny
03-21 15:00 DEBUG  WindowsBackend: user_full_name=johnny
03-21 15:00 DEBUG  WindowsBackend: user_directory=H:\Documents and Settings\johnny
03-21 15:00 DEBUG  WindowsBackend: windows_language_code=1033
03-21 15:00 DEBUG  WindowsBackend: windows_language=English
03-21 15:00 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.93GHz
03-21 15:00 DEBUG  WindowsBackend: bootloader=xp
03-21 15:00 DEBUG  WindowsBackend: system_drive=Drive(H: hd 48028.234375 mb free ntfs)
03-21 15:00 DEBUG  WindowsBackend: drive=Drive(C: hd 1222.12109375 mb free fat32)
03-21 15:00 DEBUG  WindowsBackend: drive=Drive(H: hd 48028.234375 mb free ntfs)
03-21 15:00 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-21 15:00 DEBUG  WindowsBackend: uninstaller_path=None
03-21 15:00 DEBUG  WindowsBackend: previous_target_dir=None
03-21 15:00 DEBUG  WindowsBackend: previous_distro_name=None
03-21 15:00 DEBUG  WindowsBackend: keyboard_id=67699721
03-21 15:00 DEBUG  WindowsBackend: keyboard_layout=us
03-21 15:00 DEBUG  WindowsBackend: keyboard_variant=
03-21 15:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-21 15:00 DEBUG  CommonBackend: locale=en_US.UTF-8
03-21 15:00 DEBUG  WindowsBackend: total_memory_mb=1527.484375
03-21 15:00 DEBUG  CommonBackend: Searching ISOs on USB devices
03-21 15:00 DEBUG  CommonBackend: Searching for local CDs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
03-21 15:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Ubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Ubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Ubuntu Netbook CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Kubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Kubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Kubuntu Netbook CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Xubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Xubuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Mythbuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp is a valid Mythbuntu CD
03-21 15:00 DEBUG  Distro:     does not contain H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\casper\filesystem.squashfs
03-21 15:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 15:00 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-21 15:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-21 15:00 DEBUG  Distro: wrong arch: i386 != amd64
03-21 15:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-21 15:00 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-21 15:00 INFO   root: Running the CD menu...
03-21 15:00 DEBUG  WindowsFrontend: __init__...
03-21 15:00 DEBUG  WindowsFrontend: on_init...
03-21 15:00 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\translations, languages=['en_US', 'en']
03-21 15:00 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\translations, languages=['en_US', 'en']
03-21 15:02 INFO   root: CD menu finished
03-21 15:02 INFO   root: Running the installer...
03-21 15:02 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\translations, languages=['en_US', 'en']
03-21 15:02 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\translations, languages=['en_US', 'en']
03-21 15:03 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=johnny
03-21 15:03 INFO   root: Received settings
03-21 15:03 INFO   WinuiPage: appname=wubi, localedir=H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\translations, languages=['en_US', 'en']
03-21 15:03 DEBUG  TaskList: # Running tasklist...
03-21 15:03 DEBUG  TaskList: ## Running select_target_dir...
03-21 15:03 INFO   WindowsBackend: Installing into H:\ubuntu
03-21 15:03 DEBUG  TaskList: ## Finished select_target_dir
03-21 15:03 DEBUG  TaskList: ## Running create_dir_structure...
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
03-21 15:03 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
03-21 15:03 DEBUG  TaskList: ## Finished create_dir_structure
03-21 15:03 DEBUG  TaskList: ## Running uncompress_target_dir...
03-21 15:03 DEBUG  TaskList: ## Finished uncompress_target_dir
03-21 15:03 DEBUG  TaskList: ## Running create_uninstaller...
03-21 15:03 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-21 15:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-21 15:03 DEBUG  TaskList: ## Finished create_uninstaller
03-21 15:03 DEBUG  TaskList: ## Running copy_installation_files...
03-21 15:03 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
03-21 15:03 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\winboot -> H:\ubuntu\winboot
03-21 15:03 DEBUG  WindowsBackend: Copying H:\DOCUME~1\johnny\LOCALS~1\Temp\pyl43.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
03-21 15:03 DEBUG  TaskList: ## Finished copy_installation_files
03-21 15:03 DEBUG  TaskList: ## Running get_iso...
03-21 15:03 DEBUG  TaskList: New task copy_file
03-21 15:03 DEBUG  TaskList: ### Running copy_file...
03-21 15:04 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
03-21 15:04 DEBUG  TaskList: # Cancelling tasklist
03-21 15:04 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
03-21 15:04 DEBUG  TaskList: New task check_iso
03-21 15:04 DEBUG  CommonBackend: Searching for local ISO
03-21 15:04 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-21 15:04 DEBUG  TaskList: New task get_metalink
03-21 15:04 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-21 15:04 DEBUG  TaskList: # Cancelling tasklist
03-21 15:04 DEBUG  TaskList: # Finished tasklist

---

### Post by johnnybevo on 2011-03-21
I think after I reinstall, I will try to disable legacy support in the BIOS to see what happens.

---

