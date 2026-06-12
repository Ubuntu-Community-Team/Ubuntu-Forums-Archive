---
title: "Broken dual boot config. Can't go back to windows"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Bisto on 2011-05-19
Hi,
I installed natty on top of my existing win7 install using the wubi.
After a few reboots and noticing that the windows loader appeared in grub, I decided to make kubuntu the default boot option. Now i realise that grub will not take me back to win7 as I'd hoped!

I looked for a boot.ini instinctively, and cannot find it!
Google searches have given me sudo gedit /boot/grub/menu.lst, which I have replaced for sudo kate /boot/grub/menu.lst but this info seems outdated as there is no menu.lst!

What do I have to edit to get my win7 back??

Help V much appreciated :) Seb

---

### Post by oldfred on 2011-05-19
Wubi uses the windows boot loader to boot. You should be booting with windows and then choosing win or Ubuntu. Then wubi starts and it uses the same grub2 menu as a standard install which will list both Ubuntu & windows.

Did you install grub2 to the MBR? menu.lst is from grub legacy and is not used unless you have upgraded from prior to 9.10 or installed grub 0.97.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you have win7 you do not have boot.ini which is from XP. You have to use bcdEdit to update the BCD which has replaced boot.ini in Vista/7.

---

### Post by Bisto on 2011-06-02
Hi, actually I didn't install it to the mbr or anything exciting like that! What I did was boot into windows, then use the 'default os' option as kubuntu, without showing me boot options.
What I was aiming for was to use GRUB to boot into either windows or kubuntu rather than having two boot loader screens asking me to select an o/s.
I now realise it would have been easier to tell grub not to ask!
Even using the /fixmbr and the other thing (which escapes me due to a lack of sleep as i'm now a daddy!) and the startup repair on the win7 disk didn't fix it as there was nothing technically 'wrong' with the bootloader!
What I had to do in the end was to boot a win7 recovery disk, command prompt, and use bcdedit to configure the timeout option back to 5 or more seconds, enabling me to select windows and configure the default o/s from there :)

Thanks for your help! I don't know if i'm the only retard who's managed this situation or not, so perhaps this may be of use to future like-minded retards :D

Bisto.

---

