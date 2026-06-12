---
title: "Acer C720, Dual Boot Chrubuntu"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by aaron63 on 2014-12-19
I have an Acer C720 and I'm trying to install a dual boot chrubuntu, but when I'm in developer mode, I type [FONT=courier new]curl -L -O [http://goo.gl/9sgchs;](http://goo.gl/9sgchs;) sudo bash sgchs 
[FONT=arial]but when I use this line of code it says
[FONT=courier new][COLOR=#ff0000]Error: this Chrome device does not seem to support CTR+L Legacy SeaBIOS booting. Use the old ChrUbuntu script please ...
[/COLOR][FONT=arial]Anyone got a solution please I'm a BTEC Level 3 IT student but in software not hardware so I'm out of my comfort zone slightly. [/FONT][/FONT][/FONT][/FONT]

---

### Post by TheFu on 2014-12-19
I have a C720, but don't have chrubuntu, just Ubuntu Server with openbox.
My notes from getting this working: [http://blog.jdpfu.com/2014/03/12/ubuntu-on-acer-c720-chromebooks](http://blog.jdpfu.com/2014/03/12/ubuntu-on-acer-c720-chromebooks)

Sorry - don't have a clue what BTEC is, so that doesn't help understand your knowledge level. Ah - a British thing.

---

### Post by aaron63 on 2014-12-21
Ill have a look at your notes thanks I'm now not sure whether or not is a C710 or a C720

---

### Post by durkla18 on 2015-02-22
try:

 wget [http://goo.gl/tnyga;](http://goo.gl/tnyga;) sudo bash tnyga

it worked for me on my acer c7 chromebook, manufactured in 2012.

---

### Post by durkla18 on 2015-02-22
please ignore the underlined part of it. It should *not* be underlined.

---

### Post by rick_tobin on 2015-03-16
i successfully installed 14.04LTS on my acer c720 chromebook using hugh Greenbugs dual boot method. he uses www://goo.gl/s9yrd. It worked perfectly for me, but i had to use a wireless mouse and then discover that ubuntu wont start while the usb dongle is inserted, easy solution is- not to insert wireless mouse dongle until ubuntu has already started up. hope this helps as i spent 9 days trying every other method and failed.

[https://www.distroshare.com/distros/get/14/](https://www.distroshare.com/distros/get/14/)
[COLOR=#3E423A][FONT=Lato]How to install:[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- Follow the "First things first" and "Boot into developer mode" sections as explained here: [http://www.linux.com/learn/tutorials/764181-how-to-install-linux-on-an-acer-c720-chromebook](http://www.linux.com/learn/tutorials/764181-how-to-install-linux-on-an-acer-c720-chromebook). After you follow those sections and while in the crosh shell, run this command: sudo crossystem dev_boot_usb=1 dev_boot_legacy=1. Don't follow the rest of the sections.[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- Put the ISO on a USB stick as explained below.[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- If you want to erase ChromeOS, reboot into legacy mode by rebooting and pressing Ctll-L at the white screen. The USB stick should boot. Install as a typical Ubuntu based distro.[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- If you want to dual boot, see this post: [https://www.distroshare.com/distros/get/14/#comment-1803627619](https://www.distroshare.com/distros/get/14/#comment-1803627619)[/FONT][/COLOR]

[COLOR=#3E423A][FONT=Lato]How to put on a USB stick:[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- Use the dd command[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- On Linux: sudo dd if=file.iso of=/dev/usb_device bs=1M (where usb_device is the usb drive)[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- On Mac OS X: [https://wiki.archlinux.org/index.php/USB_flash_installation_media#In_Mac_OS_X](https://wiki.archlinux.org/index.php/USB_flash_installation_media#In_Mac_OS_X)[/FONT][/COLOR]
[COLOR=#3E423A][FONT=Lato]- On Windows: Use Win32 Disk Imager - [http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)[/FONT][/COLOR]


[hugegreenbug]("https://disqus.com/by/hugegreenbug/") [COLOR=#FFFFFF]Mod[/COLOR] [* burningriverman*]("https://www.distroshare.com/distros/get/14/#comment-1777045597")*[COLOR=#CCCCCC]•[/COLOR] [2 months ago]("https://www.distroshare.com/distros/get/14/#comment-1803627619")*[COLOR=#3F4549][FONT=Helvetica Neue][FONT=inherit]*I found a solution on how to dual boot. I don't know if the problem is related to parted being removed from ChromeOS, but the Ubuntu installer tries to resize the partition by a MB, which messes everything up. Here are the steps I took to get a working dual boot:*[/FONT]
[FONT=inherit][I]1. Download and run the Chrubuntu script to partition the disk: curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd
2. Format the filesystem on /dev/sda7 while you are in the ChromeOS shell, which is where Linux is going to. Here is how did that:
sudo mkfs.ext4 /dev/sda7
3. After the script reboots ChromeOS and finishes repairing it, you can reboot and boot into legacy mode (Ctl-L) with the usb stick with this distro on it.
4. Run the installer continue on until you reach the "Installation Type" section.
5. Choose: "Something else"
6. Select /dev/sda7
7. Select Change. 
In the popup window, configure it so the filesystem matches what you formated it as in step #3 and the mount point is "/". Do NOT select the format checkbox. Then press ok.
8. A new popup will show up with the title: "Write previous changes to disk and continue?" Select "Go Back".
9. Select "Install Now"
10. A new pop up will show up with the title "Do you want to return to the partitioning menu?" Select "Continue"
11. Another popup: "Do you want to return to the partitioner?" Select "Continue"
12. Another popup: "Continue with installation? No partition table changes ..." Select "Continue"[/I][/FONT]
[FONT=inherit]*After the install, you should have a working dual boot.*[/FONT]



[/FONT][/COLOR]

---

