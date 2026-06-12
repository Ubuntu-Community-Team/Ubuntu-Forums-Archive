---
title: "How do I use the Vista/7 bootloader now?"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Secret Neo on 2009-12-26
So I installed Ubuntu on a new partition, its fine, but it used Grub. But I want to use Windows 7 as default and use it's bootloader. How do I add the entry for Ubuntu into EasyBCD and tell Grub to not load first?

OR, it might be easier but maybe use the Grub loader and make Windows 7 default?

But I'd rather want to use EasyBCD and go through the Windows bootloader.

---

### Post by phillw on 2009-12-26
> **Secret Neo said:**
> So I installed Ubuntu on a new partition, its fine, but it used Grub. But I want to use Windows 7 as default and use it's bootloader. How do I add the entry for Ubuntu into EasyBCD and tell Grub to not load first?

OR, it might be easier but maybe use the Grub loader and make Windows 7 default?

But I'd rather want to use EasyBCD and go through the Windows bootloader.

Hi,

Well make your mind up time ...

I can tell you how get Win to be in charge of your MBR
I can tell you how to put Grub2 in charge & set Win 7 as the default
You want to use EasyBDC --> google it, it's not a ubuntu supported boot loader

[http://www.sevenforums.com/installation-setup/2557-dual-win7-ubuntu.html](http://www.sevenforums.com/installation-setup/2557-dual-win7-ubuntu.html)

is the best i found.

Regards,

Phill.

---

### Post by Secret Neo on 2009-12-26
> **phillw said:**
> Hi,

Well make your mind up time ...

I can tell you how get Win to be in charge of your MBR
I can tell you how to put Grub2 in charge & set Win 7 as the default
You want to use EasyBDC --> google it, it's not a ubuntu supported boot loader

[http://www.sevenforums.com/installation-setup/2557-dual-win7-ubuntu.html](http://www.sevenforums.com/installation-setup/2557-dual-win7-ubuntu.html)

is the best i found.

Regards,

Phill.

thx. but ya I'd rather want the 7 bootloader in charge. 

actually i found this: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4), is that a good method or is there a better one?

---

### Post by phillw on 2009-12-26
To put Win in charge, or Grub for that matter, head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Dead easy, dead quick.

Regards,

Phill.

---

### Post by Secret Neo on 2009-12-27
> **phillw said:**
> To put Win in charge, or Grub for that matter, head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Dead easy, dead quick.

Regards,

Phill.

Thx but if I go that route, will Ubuntu be in the Boot List?

---

### Post by phillw on 2009-12-27
> **Secret Neo said:**
> Thx but if I go that route, will Ubuntu be in the Boot List?

Dunno about Win7. but. if you put it under Win control 1st, you can always then put it under Grub afterwards, if Ubuntu doesn't show up. That thread has both options.

If you want to alter the default boot order within Grub, then it's not too hard. Grub I know a bit about, Win boot-loader since the demise of boot.ini, i know nothing about !! :)

Regards,

Phill.

---

### Post by Secret Neo on 2009-12-27
> **phillw said:**
> Dunno about Win7. but. if you put it under Win control 1st, you can always then put it under Grub afterwards, if Ubuntu doesn't show up. That thread has both options.

If you want to alter the default boot order within Grub, then it's not too hard. Grub I know a bit about, Win boot-loader since the demise of boot.ini, i know nothing about !! :)

Regards,

Phill.

ya well, ok, how do you alter grub to make win7 the default? and the order of the list?

---

### Post by phillw on 2009-12-27
Choices.... the easiest is by GUI, (a little window), but you need to put it on your computer 1st.

> 
[LIST=1]
[*]**[COLOR=Navy][SIZE=3]Menu Default Entry[/SIZE][/COLOR] **
File: */etc/default/grub*
Line to edit (4):  *DEFAULT=0*
Example: *DEFAULT=1*   # (The second "menuentry" item).

There are several ways to update the default selection in GRUB 2. Below are choices for using a simple GUI app to make the change for you, a manual way via editing the GRUB 2 files. A third method, using the command "grub-set-default" does not appear to work in GRUB 2 with Ubuntu at this time.
[LIST=1]
[*] StartUp-Manager: For those who prefer a GUI app to change the default selection.
If you want a simple, GUI-based app that can change the default entry, you can install and run StartUp-Manager. This app was written for Grub legacy but still works for this option in Grub 2. Click on the "SUM" link in my signature line for instructions on how to install and an explanation of the various settings you can change with StartUp-Manager.
[/LIST]
[/LIST]


The SUM link is this one --> [http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

If you're happier to roll up your sleeves and use the terminal, then 

> 
[LIST=1]
[*] Edit the Files: Get to Know GRUB 2

If you prefer to change the GRUB 2 files manually:

You can see the current "menuentry" items listed in the */boot/grub/grub.cfg* by running this command:
 	Code:
 	grep "menuentry" /boot/grub/grub.cfg 
Counting starts with zero (0). The first "menuentry" item is "0", the second is "1", etc. The third visible "menuentry" would be 2. 

Determine the number you wish to make the default, and enter it in */etc/default/grub*. Make the change and save the file.
 	Code:
 	gksu gedit /etc/default/grub 
The user can also select "saved" as an option, which will use the last successfully booted kernel/OS as the default selection.
Example: DEFAULT="saved"

Save the file, then update the menu:
 	Code:
 	sudo update-grub 
[/LIST]


Your choice.

Regards,

Phill.

---

### Post by Secret Neo on 2009-12-27
thanks alot, thought im gettin pretty tired so i might head off to bed and give it a go tommorow, thanks for the input tho.

btw you wouldn't know any way to change the title of the systems in the list would you? is there a program that can do it or is it a terminal thing?

---

