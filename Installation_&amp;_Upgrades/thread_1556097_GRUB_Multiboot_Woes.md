---
title: "GRUB Multiboot Woes"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by Phillip Bromley on 2010-08-18
I'm having an issue with GRUB, I have four OSes on my hard drive. Here they are in the order I installed them:

Windows 7 (Windows bootloader)
Ubuntu (GRUB 1.97)
YLMF OS (GRUB 2)
Debian (Some ancient bootloader)

(For those of you unfamiliar with it, YLMF OS is an Ubuntu-based distro re-skinned to look like Windows XP. Other than the theme and branding it's exactly the same as Ubuntu)

Each time I installed another operating system, it replaced my original bootloader with its own. I made the mistake of installing Debian last, thus leaving me "stranded" with an old version of GRUB. Since at the time I was relatively inexperienced with Linux, I solved the problem by reinstalling Ubuntu, which then replaced the bootloader with GRUB 1.97.

I mainly use YLMF OS, and so when I wanted to change some GRUB menu settings (the default entry, timeout, etc.) I naturally changed the /etc/default/grub file in the YLMF OS partition, not the one in Ubuntu. Once I rebooted I realized that my changes weren't being applied for that reason. Thus my problem is that my computer is using the GRUB that Ubuntu installed, not the one YLMF OS came with. How do I change which version of GRUB is used when I boot up? Yes, I could just change the settings in the Ubuntu partition, but YLMF OS came with the newer/est version of GRUB, so I want to use that instead.

Thanks in advance.

---

### Post by oldfred on 2010-08-19
Do not know about YLMF OS (GRUB 2).

But grub2 should be the same. They are making continous fixes so each version has changes/improvements and sometimes regressions.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you boot into YLMF, you should just be able to install grub from there:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

I believe anyone with multiple systems or multiple drives should run this before or after any changes to system just to know & document what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Phillip Bromley on 2010-08-19
I tried the commands you showed me:
[quote="oldfred"]sudo fdisk -l
if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub[/quote]
I rebooted to test it out, and it works! But for some reason Memtest86+ isn't an option any more, and ideas on how to get that back?

Thanks a lot!

---

### Post by oldfred on 2010-08-19
I see memtest in the repositories. You then would have to add an entry to grub. If grub2 in YLMF does not have you can add it to 40_custom. But look in /etc/grub.d and see if memtest was made non executable to not have it in the menu.

sudo chmod +x /etc/grub.d/filename

You can of course use the copy in your Ubuntu.

---

### Post by Phillip Bromley on 2010-08-19
I installed Memtest86+ from the repositories, and it now appears on the GRUB boot menu. Thanks a ton!

---

