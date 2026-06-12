---
title: "Ubuntu 16.04 dual boot w/ windows 10 cannot install"
date: 2017-05-14
forum: Installation &amp; Upgrades
---

### Post by slowerphoton on 2017-05-14
I've tried to install Ubuntu on my new laptop with Windows 10 - I was aiming for a dual boot. On the first run everything seemed fine until it asked me to choose my language. It just stopped for more than 10 minutes loading something:


[SIZE=3][IMG]https://i.stack.imgur.com/VQDBD.jpg[/IMG][/SIZE]


I tried to shut it down but it had no effect (it asked me "Do you really want to close all running applications?" but didn't do anything). So I turned it off by force. When I attempted to do it again it surprisingly worked I went through the whole installation process and got into Ubuntu. I downloaded a few programs I needed, checked my emails and shut it down. 


When turning on again there was a just black screen with white text running for more than half an hour like this: 

[I]
** 19 printk messages dropped **
    [200.119021] nouveau <missing> fifo: sched_error 20[<missing>][/I]


I shut it down by force again and booted Ubuntu without problems. I logged in and spent a few minutes there then opting for restart and choosing to load windows instead. While being on Windows I also removed the USB stick. Then I restarted it again but it gave no options and booted to windows directly. My Ubuntu disappeared.


I decided to attempt the installation again but it always stops at choosing the language like the first time.


What should I do?


I am using Lenovo IdeaPad 510 15 (80SV00RBCK) with graphics cards (I guess): Intel(R) HD Graphics 620, NVIDIA GeForce 940MX. [This is my BIOS settings.]("http://imgur.com/a/xXdQk")


    
When I made a new USB stick (via Etcher) it gets worse. [This is what the installation looks like.]("http://imgur.com/a/0N3JM")


All I can see is the numbers and the `83.*******` number iterates by one about each second. I didn't even get to choosing the system language or anything.

[Here is a link to the same question on stackoverflow if you prefer.]("https://askubuntu.com/questions/914936/ubuntu-16-04-dual-boot-w-windows-10-cannot-install")

---

### Post by oldfred on 2017-05-14
Make sure fast start up is off in Windows. That keeps partition mounted and Linux NTFS driver then cannot see the NTFS partition to be able to work with it.
Best to use Windows to shrink NTFS partition and reboot so it can run chkdsk which is required after any resize of NTFS partitions.

If Secure Boot is on/enabled in UEFI, you may be able to install, but then cannot install proprietary drivers nor dual boot from grub.
You can use Intel video and directly boot using UEFI boot menu.
Something about not maintaining Secure Boot when proprietary driver is installed into kernel. It looses it signing.

 Grub only boots working Windows. That also means it cannot be hibernated, nor need chkdsk. And Windows updates often turn fast start up back on, so then you have to directly boot Windows from UEFI and turn it off again.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208) 

I assume the 500 is an older model, but may have some of same issues.
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[URL="http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358"]http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358

[/URL] One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
But only one ESP - efi system partition per device/drive.
      [http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358"]
[/URL]

---

