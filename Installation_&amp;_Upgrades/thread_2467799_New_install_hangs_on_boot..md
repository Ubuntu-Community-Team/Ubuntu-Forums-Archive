---
title: "New install hangs on boot."
date: 2021-10-08
forum: Installation &amp; Upgrades
---

### Post by nan123721 on 2021-10-08
I just installed kubuntu, the first boot is fine, but after I apt update, upgrade and reboot, my system infinitely sits on my MB boot logo

I've tried using different USB's, methods of writing. I've had distros on this drive before.

I have a TP Link AC1300, an RTX 2070, Ryzen 2600X and 16GB of RAM. I don't have any more info to give since there is no log to share.If I go into grub and select an older version, the boot goes fine. 

I wanna use Kubuntu, please help. 
Thanks

---

### Post by tea for one on 2021-10-08
> **nan123721 said:**
> If I go into grub and select an older version, the boot goes fine. 
I wanna use Kubuntu, please help. Thanks

When you select a previous kernel, the OS boots.
So far, so good - any other problems?

There are innumerable reports where one kernel is fine and another kernel is problematic.

I would continue to boot into a working kernel and then wait for a newer kernel to be available.
When a newer kernel is installed, try it and see what happens.
Your difficulty may well be corrected in the future.

Always keep a working kernel installed.

---

### Post by nan123721 on 2021-10-08
Im not sure if its a kernel issue. Its just an older version of kubuntu. How would I configure my GRUB for that?

---

### Post by tea for one on 2021-10-08
I cannot give precise instructions because I do not know how many systems and kernels you have.

You have to edit **/etc/default/grub** (with elevated privileges).
```
sudo nano /etc/default/grub
```

```

GRUB_DEFAULT=0 [COLOR="#0000FF"]This is the default - 0 means the first line in the Grub menu[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_DISABLE_OS_PROBER=true
```
Example below with an alternative default
```
GRUB_DEFAULT=[COLOR="#0000FF"]"1>2[/COLOR]"
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
#GRUB_DISABLE_OS_PROBER=true
```

[COLOR="#0000FF"]1[/COLOR] in "1>2" indicates the second entry of the main menu (Advanced Options)
[COLOR="#0000FF"]2[/COLOR] in "1>2" indicates the third entry of the submenu.

When you are happy with your choice, run in the terminal
```
sudo update-grub
```

Back up your existing /etc/default/grub so that you can go back to the beginning in the event of an error.
Remember - Grub counts from 0

---

### Post by MAFoElffen on 2021-10-09
Yes, that s a work-around, but doesn't answer his other questions.

Back to diagnostics of, to answer the OP... Because you can boot to the old, you have that fall-back to help with the diagnostics of the new, where it hangs.

You said you had an update, which suspect is that there was a kernel update, because you found that you can  with an older kernel... But to see what did get updated recently, you can look at the apt logs to see exactly what packages where updated in that update process. 

Next, the question to ask would be, where in the boot process "does it hang"? If you can't tell, while booted in the older kernel, either edit your boot line in the grub menu or edit your default Grub File to change "quiet splash" to "nosplash --verbose-text". That will turn off the blank screen panels while trying to boot, and you while see what (previously in the background) the system messages actually are during that process.

If it is hanging,oit will stop a point, but still might not give enough of a clue... Where you can proceed by turning on kernel debugging in five progressive levels of depth/detail.
1. Light Debug (added boot parameter, additional to above base)
```
rootwait verbose
```
3. Medium Debug (added boot parameter, additional to above base)
```
rootdelay=5 panic=10 debug
```
3. Heavy Debug (added boot parameter, additional to above base)
```
rootdelay=5 panic=10 debug ignore_loglevel
```
4. Extreme Debug (added boot parameter, additional to above base)
```
debug ignore_loglevel log_buf_len=10M print_fatal_signals=1 LOGLEVEL=8
```
5. Insane debugging (added boot parameter, additional to above base)
[code]rootwait pause_on_oops=5 panic=60 i915.modeset=1 no_console_suspend ipv6.disable=1 TERM=xterm-256color quiet 5[code]

Then reboot in the earlier kernel and view with dmesg to look at their system logs, at the last failed boot, and look for clues at why that newer kernel is having problems.

---

