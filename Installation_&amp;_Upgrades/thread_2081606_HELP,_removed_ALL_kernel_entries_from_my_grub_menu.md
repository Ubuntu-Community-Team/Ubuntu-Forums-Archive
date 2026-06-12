---
title: "HELP, removed ALL kernel entries from my grub menu..."
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by prshah on 2012-11-07
Hi,

I was running low on space, so used ```
sudo apt-get remove linux-image-3.2.0-2*
```

It remove all the older 3.2.0-2* kernels, but it also removed all entries for 3.2.0-3* kernels from the GRUB menu!

Now, I have no selection in the GRUB menu to boot into my linux installation! (Please see included screenshot).

I now understand that I should have used update-grub BEFORE rebooting; how do I get back into my installation so that I can install / update GRUB?

I have access to live session (CD/USB). My skill set is intermediate-high. Comfortable with terminal. Information / pointers much appreciated.

Regards,

---

### Post by 2F4U on 2012-11-07
Are there any kernels left on the system or did your remove them all, so that there are no kernels installed?

---

### Post by darkod on 2012-11-07
As the previous poster mentioned, it is very important whether all kernels are removed from ubuntu, or they are only missing from the boot menu (I would think it's the former).

Boot into live mode, open the root partition on the hdd and look into the /boot folder. Are there any vmlinuz files there?

---

### Post by grahammechanical on 2012-11-07
At the Grub menu we can press C and that will get us to a command line. What you do with it is dependant on at least two things,

a) the existence of at least one Linux kernel

b) our understanding of the Grub manual.

[http://www.gnu.org/software/grub/manual/]("http://www.gnu.org/software/grub/manual/")

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

According to that manual it is possible to boot a Linux image from the Grub command line. That boot menu would not have been changed unless update-grub was run, either as part of the removal of the Linux kernels or by you. Otherwise you would have a menu that listed options that did not work because the kernels were removed. I do not think that simply running update-grub will solve your problem. If there was a Linux kernel present then it would have appeared in the Grub menu.

You might want to give a lot of thought to re-installing.

Regards.

---

### Post by prshah on 2012-11-07
Hello, 

Thank you for your replies. Will check /boot tomorrow. 

I am aware of using the grub command line, but do not know the syntax. 

Can someone post the entire command: at the grub menu, select the kernel option, but press "e' instead of enter. Now please copy/paste/screen shot /photo the commands. 

Much thanks in advance.

---

### Post by prshah on 2012-11-08
Hello,

Problem solved, thank you for all your help and suggestions.

Will post details shortly, but, just in case, here is the summary:

a) Booted into live USB
b) Mounted "/" (root) file system from HDD
c) Checked "/boot"; no kernels present
d) chrooted into the installation
e) installed linux-image-current-generic using apt-get
f) the above installation did not complete totally, was not able to create required GRUB entries
g) Rebooted safely, entered grub menu, opened GRUB command line
h) typed in (manually) GRUB commands required to boot existing installation
i) that's it. it booted normally into my installation, but wifi modules (broadcom) not installed 
j) again (re) installed linux-image-current-generic
k) Ran 'dpkg --configure -a', which created the required GRUB entries
l) Rebooted, everything was normal, except wifi modules still not loaded
m) ran dkms with relevant parms to re-create broadcom wifi modules, then rebooted
n) system back to fully working status.

Detailed analysis, commands and outputs to follow shortly; for future reference for anyone else in the same position.

---

