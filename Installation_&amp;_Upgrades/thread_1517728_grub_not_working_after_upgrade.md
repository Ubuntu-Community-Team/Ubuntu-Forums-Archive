---
title: "grub not working after upgrade"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by ebohatch on 2010-06-25
I have been running a dual boot system Win 7 and Ubuntu 9.10 for months on 2 different systems. I just upgraded 1 system to 10.04. I had it set so that the grub boot will boot to the last selected OS. With 10.04 this no longer works. I went in and edited the /etc/default/grub   reset GRUB_DEFAULT=saved
then ran update-grub

all seemed to work properly.


but all boots always boot the top line (ubuntu) I must always manually select Windows 7 everytime.  

Is there something new I am missing.

---

### Post by Don Barzini on 2010-06-25
This link has all the info you need regarding your issue.....

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

This section is of interest to you....

> 
[SIZE="4"]**/etc/default/grub** (file)[/SIZE]

The main configuration file for changing default settings. Upon installation, the following lines are available for alteration by the user:
    
      **GRUB_DEFAULT** - Sets the default menu entry. Entries may be numeric, a complete menuentry quotation, or "saved"

      **GRUB_DEFAULT=0** Sets the default menu entry by menu position. As in GRUB, the first "menuentry" in grub.cfg is 0, the second is 1, etc.

      **GRUB_DEFAULT="xxxx"** An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"

      **GRUB_DEFAULT=saved**
                - The information in this section applies to GRUB 1.98 and later.

                - Enables the "grub-reboot" and "grub-set-default" commands to set the default OS.
                
                - The default OS will not be set by an interactive selection of an OS from the menu.
                
                - **grub-set-default** Sets the default boot entry until changed.
                      -The format is **sudo grub-set-default X**, with X being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic"

                      -To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run grep menuentry /boot/grub/grub.cfg 

                      -**grub-reboot** This command sets the default boot entry for the next boot only. The format of the command is the same as for grub-set-default (see above). 
    *

      **GRUB_SAVEDEFAULT=** If set to **true** this setting will automatically set the last selected OS from the menu as the default OS on the next boot.
          - No commands need be run to set the default OS.
          - Any time a menuentry is manually selected from the GRUB 2 menu, it becomes the default OS.


---

### Post by ebohatch on 2010-06-25
Thanks  it does the trick, the following seems to be new

GRUB_SAVEDEFAULT= If set to true this setting will automatically set the last selected OS from the menu as the default OS on the next boot.
- No commands need be run to set the default OS.
- Any time a menuentry is manually selected from the GRUB 2 menu, it becomes the default OS. 


I put it in and it now works like it used to.

---

