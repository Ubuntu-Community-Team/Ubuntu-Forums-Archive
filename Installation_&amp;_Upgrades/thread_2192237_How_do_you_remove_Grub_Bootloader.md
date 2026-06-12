---
title: "How do you remove Grub Bootloader?"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by estods76 on 2013-12-06
I installed Ubuntu 12.04 a while back and i love it. so much in fact that it is the only OS on my pc. sadly, my computer doesn't seem to realize this because it shows Grub menu every time i turn on the machine. It shows options for ubuntu with linux ######, ubuntu with linux #####(recovery mode), and about 5 other options. It doesn't affect the computer, but it adds another 10 seconds to the boot time and its annoying. Can i remove it? should i remove it?

here is a picture of what it looks like. IT IS NOT MINE. I FOUND IT ON GOOGLE IMAGES. but it looks the same without the windows 7 option.
[http://4.bp.blogspot.com/-TQRtemX3J1A/Tsb5MM5YTLI/AAAAAAAAA0U/jSlNqk4zPFc/s1600/Ubuntu_11_dual_boot_menu.jpg](http://4.bp.blogspot.com/-TQRtemX3J1A/Tsb5MM5YTLI/AAAAAAAAA0U/jSlNqk4zPFc/s1600/Ubuntu_11_dual_boot_menu.jpg)

---

### Post by nothingspecial on 2013-12-06
Well you need a bootloader otherwise your computer will not boot. There are alternatives to grub but you do need a bootloader.

---

### Post by ajgreeny on 2013-12-06
Run the command ```
sudo update-grub
``` and it should make sure that the grub configuration is updated to take account of the removal of your other OS.

If that does not work show us the output of ```
cat /etc/default/grub
```

---

### Post by estods76 on 2013-12-07
sudo update-grub didn't work, in fact, id added more options to the list. Oh well, they should probably be there anyway, i guess. Thank you both of you for the fast responses!

anyway, here is the output you asked for, hope it helps:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by estods76 on 2013-12-07
I may have failed to mention, I had 12.04 and i had no problem with GRUB and then update manager told me to upgrade to 12.10. after doing so, i rebooted and it wouldn't boot to the lock screen! So I put 12.04 on a flash drive and started over. Could that be why there are so many options GRUB is finding and listing? It seems like the most logical explanation.

Also, I checked out this page [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html). it said that #GRUB_HIDDEN_TIMEOUT = 0 will show the GRUB menu and removing the # will not show it. But mine is has no #! Strange. Any thoughts?

---

### Post by Dennis N on 2013-12-07
> **estods76 said:**
>  Also, I checked out this page [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html). it said that #GRUB_HIDDEN_TIMEOUT = 0 will show the GRUB menu and removing the # will not show it. But mine is has no #! Strange. Any thoughts?

Setting GRUB_TIMEOUT=0 will supress the menu, not GRUB_HIDDEN_TIMEOUT=0.

If you do that, grub menu will not appear. But if you have a boot problem later on, you may never get the menu to boot another choice like recovery mode. Maybe you could still get the menu by holding down shift during startup - I am not sure in this situation. You could set it to 2 or 3, and it would pause for that many seconds, or you could just hit Enter when the menu appears, and the first entry will start booting immediately.

---

### Post by Dennis N on 2013-12-07
I got curious and subsequently found this:

From: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/978994](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/978994) 

making reference to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> "The default behavior is to hide the menu if only one operating system is present. If a user with only Ubuntu wishes to display the menu, place a # symbol at the start of this line [GRUB_HIDDEN_TIMEOUT] to disable the hidden menu feature."

Same as your information in post #5. However, this claim is no longer part of that referenced help page as far as I can see. Apparently it was removed. The reason?

If true, this would explain your menu showing up. Removing the # should **enable** the hidden menu option [no grub menu appears] if you have only one OS. Try it and let us know if it works. I cannot test this, since I have no system with only one OS.

The information in the previous post is still correct on GRUB_TIMEOUT.  

Also, to have #GRUB_HIDDEN_TIMEOUT=0 is apparently now the default - mine is the same (12.10).

---

### Post by estods76 on 2013-12-07
Ya I added a #, and tried it then I removed it and tried it. It didn't work either time. 

I'm thinking I will make it stay for 2-3 seconds instead of removing it. Cause if there is a problem I would be in trouble. Thanks for the answers!

---

### Post by heir4c on 2013-12-08
Have you run sudo update-grub after changing the settings?

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

---

### Post by Dennis N on 2013-12-08
> **estods76 said:**
> Ya I added a #, and tried it then I removed it and tried it. It didn't work either time. 


I confirmed your experience by using a flash drive I remembered I had with one OS installed (13.04). The flash drive grub menu also showed the OS on the hard drive (detected when installed), so I got rid of that by disabling the grub OS Prober on the flash drive installation, ran update-grub on the flash drive, and the grub menu now showed:

> Ubuntu
Advanced Options for Ubuntu
memory test (memtest86+)
memory test (memtest86+, serial console 115200)

So, as far as the grub on the flash drive knows, Ubuntu is the only OS in sight. 

I uncommented #GRUB_HIDDEN_TIMEOUT=0 and ran update-grub again. Will this hide the grub menu?
Rebooted again.
Result: Nope. Grub menu still appeared.

Granted, this is different than a new install when no other OS is detected by grub-install. In that case, the grub menu IS hidden by default as we know. Unable to explore that situation at this time since no system like that is available.

---

### Post by estods76 on 2013-12-09
> [COLOR=#000000]Have you run sudo update-grub after changing the settings?[/COLOR]

[COLOR=#000000][I]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg
[/I]
[/COLOR]


Yes, I did update after the changes were made.

> [COLOR=#000000]So, as far as the grub on the flash drive knows, Ubuntu is the only OS in sight. [/COLOR]

[COLOR=#000000]I uncommented #GRUB_HIDDEN_TIMEOUT=0 and ran update-grub again. Will this hide the grub menu?[/COLOR]
[COLOR=#000000]Rebooted again.[/COLOR]
[COLOR=#000000]Result: Nope. Grub menu still appeared.[/COLOR]

[COLOR=#000000]Granted, this is different than a new install when no other OS is detected by grub-install. In that case, the grub menu IS hidden by default as we know. Unable to explore that situation at this time since no system like that is available.[/COLOR]

interesting, the same happened to me. I guess GRUB shows whether or not you have multiple OS's. Well at least we know my PC is functioning normally(I hope!).

---

