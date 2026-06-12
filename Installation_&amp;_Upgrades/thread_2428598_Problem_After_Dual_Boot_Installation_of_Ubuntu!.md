---
title: "Problem After Dual Boot Installation of Ubuntu!"
date: 2019-10-06
forum: Installation &amp; Upgrades
---

### Post by peter1512 on 2019-10-06
Hello everyone,

I'm undergoing a crisis right now.
I'm supposed to be working on my Thesis research paper but in the process of doing so, I tried to install Ubuntu on my Lenovo ideapad 330s-15arr. After going back and forth with several attempts I finally managed to get to the install screen of Ubuntu and go through installation, but when I finished I realized that there was some major screw up.

Here's what I did:

[LIST]
[*]First I went to Disk Management on Windows 10 and created some space (35gb) for Ubuntu, using "shrink" option on my C drive (an SSD I installed myself a month ago)
[*]Then I created a USB with Ubuntu 19.04 ISO using Rufus
[*]I disabled Secure Boot, booted from USB, and edited the code (pressing "e") before pressing "Install Ubuntu" after reading some workarounds for my specific Lenovo model
[*]I  then followed the steps of the Ubuntu installer and selected the option "Install alongside another OS", which started an installation without asking me for a specific partition to which it would install Ubuntu
[*]The installation was complete and I restarted the computer only to be greeted with the GNU Grub menu that did not contain Windows 10, and furthermore would not load Ubuntu
[/LIST]

So right now I am on a state where I can't access Windows 10, I can't access Ubuntu, and whenever I insert a USB it refuses to boot from it.

Here are the options I get:
[https://i.imgur.com/zM3pIg8.jpg](https://i.imgur.com/zM3pIg8.jpg)
[https://imgur.com/zM3pIg8](https://imgur.com/zM3pIg8)

1. Ubuntu: It just takes me to a blank purple screen and nothing happens
2. Advanced options for Ubuntu: It takes me to another menu with the options 'Ubuntu with Linux 5.0.0-13-generic' and 'Ubuntu with Linux 5.0.0-13-generic (recovery mode)', both of which take me to a loading screen that never loads.
3. Windows Boot Manager (on /dev/nvme0n1p2) and Windows Boot Manager (on /dev/sda1):Take me to this screen:

[https://i.imgur.com/ySWMeN6.jpg](https://i.imgur.com/ySWMeN6.jpg)

None of the above options of this screen seem to work. 'Enter' does nothing, 'F1' takes me to the GNU GRUB loader, 'F8' does nothing, 'Esc' takes me to BIOS, and 'F9' takes me to GNU GRUB loader.


4. System Setup: takes me to BIOS.

I've tried connecting a USB with Ubuntu, a Live Linux USB, a Windows USB made with the Media Creation tool, and all failed! It wouldn't boot from USB even if I set it first in the priority list via the BIOS.

Did I just brick my computer??? Please help me, I have no idea what else to do... :(

Thank you in advance.

---

### Post by oldfred on 2019-10-06
Did you backup Windows before making major changes to system?

You should be able to directly boot Windows from UEFI boot menu, same key you used to select to boot USB installer, often f10 or f12.

Grub only boots working Windows or Windows that is not hibernated. And Windows default shutdown mode is fast start up which sets hibernation flag. You need to have fast start up off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Most brands have similar issues across many models. Lenovo seems to have many models and issues are often not the same. Also it looks like yours is AMD based and that is just supposed to work.

Have you updated UEFI from Lenovo for your system? That should be done whether installing Ubuntu or not as many virus issues.
And if SSD also update firmware.

---

### Post by dino99 on 2019-10-06
Check that howto; maybe you will find yourself what was not done well with the install
[https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)

---

### Post by peter1512 on 2019-10-06
> **oldfred said:**
> Did you backup Windows before making major changes to system?

You should be able to directly boot Windows from UEFI boot menu, same key you used to select to boot USB installer, often f10 or f12.

Grub only boots working Windows or Windows that is not hibernated. And Windows default shutdown mode is fast start up which sets hibernation flag. You need to have fast start up off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Most brands have similar issues across many models. Lenovo seems to have many models and issues are often not the same. Also it looks like yours is AMD based and that is just supposed to work.

Have you updated UEFI from Lenovo for your system? That should be done whether installing Ubuntu or not as many virus issues.
And if SSD also update firmware.

Thank you for your response oldfred!

I did not backup Windows before making major changes because it was not my primary computer and had no files.

When I start the computer the F buttons do not seem to work even when I use the Fn button.
I turned fast start up off before I started my Ubuntu installation.

At the moment I cannot access any OS. I am completely stuck and I don't know what to do.


> **dino99 said:**
> Check that howto; maybe you will find yourself what was not done well with the install
[https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/](https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/)

Thank you for your response dino99. 

I did everything this howto says except from the "Installation Type" part where I selected "Install Ubuntu alongside another OS".

Should I go on panic mode yet?? :-&

---

### Post by peter1512 on 2019-10-06
No one can help? :'(

---

### Post by oldfred on 2019-10-06
If you cannot access any buttons at beginning it may be you have fast boot on in UEFI. Fast boot is a separate setting in UEFI from fast start up in Windows.
Fast Boot assumes no system change and immediately starts boot. Normal boot scans system and  writes system data, so operating system knows what hardware you have. Since it assumes no changes, it immediately starts boot, and usually you have no time to even press a key. 

You need to force the full start-up which normally you can do as a cold boot, not a warm reboot.
Cold boot is full system shutdown, remove battery if laptop and hold power switch fo r10 sec or so to drain any remaining power. Then on boot immediately press key to get into UEFI or one time boot key to boot Windows.

---

### Post by peter1512 on 2019-10-07
> **oldfred said:**
> If you cannot access any buttons at beginning it may be you have fast boot on in UEFI. Fast boot is a separate setting in UEFI from fast start up in Windows.
Fast Boot assumes no system change and immediately starts boot. Normal boot scans system and  writes system data, so operating system knows what hardware you have. Since it assumes no changes, it immediately starts boot, and usually you have no time to even press a key. 

You need to force the full start-up which normally you can do as a cold boot, not a warm reboot.
Cold boot is full system shutdown, remove battery if laptop and hold power switch fo r10 sec or so to drain any remaining power. Then on boot immediately press key to get into UEFI or one time boot key to boot Windows.

I did a cold boot just like you described it. I even took the BIOS battery off. I opened it and tried F2, Fn+F2, F12, and Fn+F12. I also tried Lenovo's Novo button. No luck there either. Every single time it would take me to the Grub menu.

What is happening? My Linux experience. :icon_frown:

---

### Post by oldfred on 2019-10-07
At very bottom of grub menu is this entry, you only see the menuentry part or System Setup. It should take you into UEFI.

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

---

### Post by peter1512 on 2019-10-07
Thank you for your reply Oldfred but I actually managed to get into Windows 10!
I just removed the HDD from the laptop and when it took me to the GRUB menu I selected the Windows Boot Manager it loaded Windows 10 exactly how I left it last time.

My question would now be _how do I clear the linux bootloader that takes me to the GRUB menu?_
I assume that if I plug my HDD back in to the laptop I'll get the same shenanigans.

---

### Post by oldfred on 2019-10-07
In UEFI (often f2) you should have UEFI boot entries that show in your UEFI boot menu (Often f10 or f12). And from UEFI configuration you can set boot order.

Usually UEFI forgets boot entries or resets them when a drive is removed. But it also usually finds Windows even if drive removed & restored.
You often have to use efibootmgr or reinstall grub (which uses efibootmgr) to restore the Ubuntu boot entry.

Grub only boots working Windows. 
And since Windows updates often turn fast start up on, you need to be able to directly boot Windows from UEFI to turn fast start up back off. Also if Windows gets corrupted and needs chkdsk grub will not boot it. You then may be able to boot into repair console  or need a Windows repair flash drive.

---

