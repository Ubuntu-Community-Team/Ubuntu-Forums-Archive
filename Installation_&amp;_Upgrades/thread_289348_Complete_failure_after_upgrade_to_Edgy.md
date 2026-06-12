---
title: "Complete failure after upgrade to Edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Trurl on 2006-10-30
Hey everyone,

   I just upgraded Dapper to Edgy using the recommended method. Update seemed to be fine, prompted restart, so I restarted to find a completely changed grub boot list (my windows dual-boot option no longer appears). No matter which Ubuntu kernel I try to boot, I get the following error message (only dif. being kernel name): 

root (hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda6 ro quiet
 splash
Error 17: Cannot mount selected partition
____________________

Two questions: How do I restore Linux and how do I get back into windows? 

Thanks,

Trurl

---

### Post by ciscosurfer on 2006-10-30
This page should help you out: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Trurl on 2006-10-30
I figured it out, and this should help anyone getting a similar message:

When the update to Edgy takes place, menu.lst is updated to reflect the new kernel. The update essentially removes any previous mention of windows as well as changing the # in root(0,#). Ultimately, I think it was trying to boot ubuntu from my windows partition. Going in with the LiveCD and changing the root(0,#) statements to the linux root partition value and re-entering the windows boot option data fixed that problem.

Now all I have to do is fix the X error I get whenever I load ubuntu. Still, at least my computer works again!

-Trurl

Thanks Cisco, fortunately I didn't need to actually re-install anything.

---

### Post by ciscosurfer on 2006-10-30
Glad to here you got yourself up and running again.  

As for the X error, when your computer boots up, before everything has loaded, drop to a command prompt by hitting CTRL-ALT-F2 and you will be presented with a login and password prompt.  Enter you login and password, then enter the following and follow the prompts: **sudo dpkg-reconfigure -phigh xserver-xorg** (you can leave off -phigh, which tells dpkg to only go through 'high priority' changes...just remember you can enter it like this ( -phigh ) later on when you get things running again and have only made a few manual changes to your **/etc/X11/xorg.conf** file) 
So, you can issue```
sudo dpkg-reconfigure xserver-xorg
``` Go through the entire setup and when you're done, you should be golden again.  Remember, you'll need to re-download any graphics drivers (like Nvidia or ATI, for example) that had on before...remember to grab the restricted-modules as well.  Over and out.

---

### Post by Turin Turambar on 2006-10-31
I had the same issue. For some reason Grub installed the wrong parametres.

It said hda1 instead of hda3

and

Root (0,0) instead of (0,2)

Anyone now why?
And, by the way, you didn't need to use the live CD... If something is wrong in the menu, you can just edit the line, typing "e".

---

