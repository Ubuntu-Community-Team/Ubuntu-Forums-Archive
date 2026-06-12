---
title: "Installing Ubuntu 11.10 Shows Black Screen with Blinking Cursor"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by myfootsmells on 2011-11-18
Ubuntu 11.10 32bit
Hyper-V on Windows Server 2008 R2

I see the purple screen, then Ubuntu 11.10 and the four dots, Welcome to Ubuntu 11.10 and shows the ubuntu@ubuntu CLI.  After a few seconds, black screen w/ blinking cursor.  I can then press alt+f1 to show the cli again.

I tried rebooting and holding down shift but Grub doesn't appear.

I also tried pushing a key during the purple screen which gives me the option of picking my language but nothing there seemed to help.

Any ideas why it's not showing the installation screen?  Thanks.

Michael

---

### Post by MAFoElffen on 2011-11-18
> **myfootsmells said:**
> Ubuntu 11.10 32bit
Hyper-V on Windows Server 2008 R2

I see the purple screen, then Ubuntu 11.10 and the four dots, Welcome to Ubuntu 11.10 and shows the ubuntu@ubuntu CLI.  After a few seconds, black screen w/ blinking cursor.  I can then press alt+f1 to show the cli again.

I tried rebooting and holding down shift but Grub doesn't appear.

I also tried pushing a key during the purple screen which gives me the option of picking my language but nothing there seemed to help.

Any ideas why it's not showing the installation screen?  Thanks.

Michael
First have a good 11.10 32bit LiveCD, then follow the instructions in this post:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Forcing Grub to Show Menu**]("http://ubuntuforums.org/showpost.php?p=11469860&postcount=800")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

After it updates the grub file... Look at /boot/grub/grub.cfg and see if there is a menu item for your Windows Server.

Then, stay chroot'ed to your system... do this command:
```

lspci -vnn | grep VGA

```Please post the results... It ill show what Linux see's as the the Video GPU... This info is needed to fix your lockup, which does happen at that point sometimes with NVidia and ATI.  Hanging at this point is rare... But it happens. 

If it says you have NVidia, then follow this link to "fix" your problem and install your drivers. The "fix" is the code at the bottom of the post.
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

If it says you have ATI, then follow this link to "fix" your problem  and install your drivers. The "fix" is the code at the bottom of the  post.
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

Note- You won't have to use "sudo" while you are chroot'ed / you are root at the point.

When finsished exit out the chroot and unmount the mounted drive. Reboot.

I'm not familiar with Hyper-V, but it is Visualization... As you worded the description, I'm not sure if you have Ubuntu running alongside or within a VM. If VM, then the lspci may give different results than your actual box.  If it is alongside... Then I see a problem in grub not seeing Ubuntu or the Windows Manager not seeing Ubuntu... 

The grub instructions will work if grub exists (not booted from the windows boot manager). The others instructions will work either way.

Tell me how it goes and what you find.  Still curious on your hardware info...-

---

### Post by ptr727 on 2011-12-18
Hi, I have a similar problem.

I tried installing Mythbuntu 11.10 to run Myth backend on Hyper-V.
OS boots, 4 dots, then black screen and blinking cursor.
I tried Ubuntu 11.10 desktop, same thing.

11.10 server installs without issues, (using text UI installer).

I found walkthroughs to install 10.04 desktop on Hyper-V, but have not found any success posts for 11.10?

Any ideas?

P.

---

