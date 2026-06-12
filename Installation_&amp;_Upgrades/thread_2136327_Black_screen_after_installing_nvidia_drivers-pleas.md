---
title: "Black screen after installing nvidia drivers-please read as I've researched this alot"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by razaz03 on 2013-04-17
Hi all,

I'm using Backtrack v5r3 64bit Gnome (please don't close the thread as I feel that this prevalent issue may be encountered by us vanilla ubuntu guys at one stage!).

I've reconfigured the xorg.conf file after trying to carry out instructions as per [http://www.n1tr0g3n.com/?p=2953](http://www.n1tr0g3n.com/?p=2953) thread.

That is, download the latest drivers from nvidia.com, editing nouveau update initramfs AND the second post:

That is, blacklist tonnes of unwanted drivers, purge remove nvidia add x-swat apt-get install nvidia-current etc.etc., nvidia-xconfig

Finally I've tried (amongst many other things) the changes to grub as per [http://insidetrust.blogspot.co.uk/2011/08/few-other-tips-for-backtrack-5-graphics.html](http://insidetrust.blogspot.co.uk/2011/08/few-other-tips-for-backtrack-5-graphics.html)

That is, added [FONT=Courier New][COLOR=#cc0000]i915.modeset=1 [/COLOR][/FONT]with no joy.

I used to get 'screens not found error', (before reconfiguring my xorg.conf since it didn't reflect the proper PCI bus ID), but now I simply get a black screen with a cursor whereupon it hangs for ever.

I can still ctrl-alt-f1 to get to the loading process (which I can terminate), or ctrl-alt-f8 which states something about read-only and making write only in recovery mode.

What I need is someone experienced to troubleshoot this as my system is responsive so I don't feel that it's a grave error, and not advice to "reinstall" or "not to use the OS" or "follow this guide!!!" because I've followed them all! (and read an entire book about ubuntu)

Thanks a lot!

razaz03

---

### Post by razaz03 on 2013-04-17
as an update I can remove the xorg.conf file and the system boots with no problems, but when I lsmod, there are no drivers for video (or any nvidia drivers at all it seems)!

---

### Post by midnightramen on 2013-04-18
you may want to run 'lspci | grep VGA instead. 

I got the black screen after login as well. I would be able to hit the lightdm login screen fine yesterday, but then after authenticating, I would get the black screen and cursor. I reinstalled the nvidia drivers, and such, but ultimately, I think I fixed it by deleting the /home/<user>/.Xauthority file. I had finally realized that it was something to do with my user home folder after stumbling across the /home/<user>/.xsession-errors file.

So, you might want to try that - deleting the /home/<user>/.Xauthority file and see if that fixes it. I had also cleaned out the  ~/.compiz/sessions directory contents as well, but I don't think that solved my issue.

**EDIT: better yet, run "dmesg | grep VGA" . You might actually be using the nouveau driver.

---

### Post by razaz03 on 2013-04-19
> **midnightramen said:**
> you may want to run 'lspci | grep VGA instead. 

I got the black screen after login as well. I would be able to hit the lightdm login screen fine yesterday, but then after authenticating, I would get the black screen and cursor. I reinstalled the nvidia drivers, and such, but ultimately, I think I fixed it by deleting the /home/<user>/.Xauthority file. I had finally realized that it was something to do with my user home folder after stumbling across the /home/<user>/.xsession-errors file.

So, you might want to try that - deleting the /home/<user>/.Xauthority file and see if that fixes it. I had also cleaned out the  ~/.compiz/sessions directory contents as well, but I don't think that solved my issue.

**EDIT: better yet, run "dmesg | grep VGA" . You might actually be using the nouveau driver.


I deleted the Xauthority file and dmesg grep vga returns VESA VGA frame buffer device, with no joy. Please help! (or tell me where to go to get some!)

---

