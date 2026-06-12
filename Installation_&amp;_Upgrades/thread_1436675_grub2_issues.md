---
title: "grub2 issues"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by loosescrew on 2010-03-23
I started a thread here .[http://ubuntuforums.org/showthread.php?t=1430322](http://ubuntuforums.org/showthread.php?t=1430322) That got me up and running but according to what i have read my grub setup is still not correct. My boot-up takes quiet awhile.
 Here is the content of /etc/default/grub       When GRUB_CMDLINE_LINUX DEFAULT="QUIET SPLASH" i'M NOT ABLE TO UPDATE GRUB. Or anything else for that matter.  
  ```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”by” 
GRUB_CMDLINE_LINUX=""


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Thanks,Joe

---

### Post by loosescrew on 2010-03-23
bump

---

### Post by andrewthomas on 2010-03-23
> **loosescrew said:**
> I started a thread here .[http://ubuntuforums.org/showthread.php?t=1430322](http://ubuntuforums.org/showthread.php?t=1430322) That got me up and running but according to what i have read my grub setup is still not correct. My boot-up takes quiet awhile.
 Here is the content of /etc/default/grub       When GRUB_CMDLINE_LINUX DEFAULT="QUIET SPLASH" i'M NOT ABLE TO UPDATE GRUB. Or anything else for that matter.  
  ```
 # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT**=**”by” 
GRUB_CMDLINE_LINUX=""


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```Thanks,Joe
When you edited /etc/default/grub you didn't replace 
```
GRUB_CMDLINE_LINUX_DEFAULT=”by” 


```with ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```now just 
```
gksudo gedit /etc/default/grub
``` cut out the first line and add the second, then ```
sudo update-grub
```

---

### Post by loosescrew on 2010-03-23
Thanks,andrewthomas. Evidently i wasn't typing correctly. copy/paste did the trick. Thanks joe

---

### Post by andrewthomas on 2010-03-23
Glad to be of help loosescrew.

---

### Post by leorolla on 2010-03-30
There is a problem with the text editor that you used.

In some other parts of this file, there also a ```
`
``` when there should be a ```
'
```.

To avoid problems in the future, better fix them.

But don't use the keyboard to write the `, copy and paste is safer.

---

