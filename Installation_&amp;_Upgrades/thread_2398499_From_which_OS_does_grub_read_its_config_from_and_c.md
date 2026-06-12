---
title: "From which OS does grub read its config from and can I safely change that?"
date: 2018-08-13
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2018-08-13
I have a multi boot/EFI system. I started with Windows 10, installed mint 18, later Ubuntu 18, next Ubuntu 16 over Mint 18. All os's reside on a single SDD. This change in Linux systems because I have a multi video card setup which causes Mint 18 (also 19) to crash. Ubuntu 18 works fine but I had some issues. So I tried Ubuntu 16 and installed it over Mint. Ubuntu 16 installed a graphic grub and I do not want that. 

When I wanted to remove the grub boot screen  I realized that each Linux has its own configuration grub files. Each installation seems to mange to trick grub into booting from its own configuration. Changing the files of another os will not help. Anyhow, that's my explanation of why changing the grub of Linux 18 had no effect on the boot screen.

in [this article]("https://unix.stackexchange.com/questions/305345/where-is-grub-installed-and-do-i-need-a-new-one-for-a-separate-linux-installatio") I understood that I should use `grub-install /dev/partition where os is installed` to tell grub to fetch its configuration files from that device. But it also states that "On a single disk you shall always run grub-install from a single OS only!  That's important, otherwise you will keep overwriting your config." Does that mean I have to run it from the Ubuntu 16 system, it being the last one installed? That will be a problem as I want to clear this system. So I wonder If my understanding is correct.

Next I looked into the [grub manual]("https://www.gnu.org/software/grub/manual/grub/html_node/Installing-GRUB-using-grub_002dinstall.html") where it said that grub-install only has to point to the EFI partition in which case I wonder where grub reads its configuration from.

So I want grub to read its config from Ubuntu 18. How can I safely do that?

Thanks very much for your time.

---

### Post by kc1di on 2018-08-13
Hello nocom2  and Welcome to Ubuntu,

Grub is normally controlled by the last Linux installation that you installed , in your case that would seem to be ubuntu 16.x so any changes made in others will not affect grub. 
If you do run grub install from one of the other installs that one will then control grub.  If you want an easy way to control grub install grub-customizer from[ this ppa]("https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer") But be careful you can mess grub up if your not sure what your doing.
in order to get rid of the grub splash screen you delete the term quiet splash.  under the general tab boot parameters box.  
good luck.

---

### Post by Dennis N on 2018-08-13
grub boot loader files are installed to a folder named ubuntu in your EFI system partition. You have 3 OS that use ubuntu's installer and each one installs grub to the same folder, overwriting what what previously there. That's why the most recent install is the one that displays the grub menu.

If you plan to do another Ubuntu type installation (any Ubuntu or main Mint varieties) and want to keep the previous grub worikng, one way is to copy the previous ubuntu folder to a safe place, then restore it after doing the new installation. Then you will continue to use the previous grub.

If the grub of the OS you want has already been overwritten and you have no backup, it's possible to restore it with some editing of one of the grub files in the ubuntu folder. If you're interested in that, and have some terminal skills, someone here can help.

---

### Post by nocom2 on 2018-08-14
The grub-install worked, thank you very much! The installation is now read from the correct os: ubuntu 18 as you correctly assumed. And thanks for the tip of grub-customize, that helped me to order all the different entries correctly.

@kc1di, I still have an issue though. I deleted "quiet splash" from  GRUB_CMDLINE_LINUX_DEFAULT. Compiled /etc/default/grub and I don't see some graphics screen but still a dull grey background so that I cannot see the boot messages. Any idea how to solve that? I listed the /etc/default/grub below

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

---

### Post by kc1di on 2018-08-14
Hi,
try changing your /etc/default/grub file to look something like this:
```
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT='10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
```

see if you can then see the boot messages.
you'll need to run ```
sudo update-grub
``` in order for the changes to take effect.

---

### Post by nocom2 on 2018-08-15
Hi,
Thanks for your reply! I did as you asked but still got the dark grey background. Next I deleted the Ubuntu 16 partition as this trouble was introduced with the installation of Ubuntu 16. That did not work either. In grub-customizer>Appearance settings no theme is installed, the backgrounds are transparent and there is no background image. Are there any options left :-)?

**Update**
I looked more careful at the dark grey screen and it seems some kind of graphics background. When the boot options are shown it shows GNU GRUB version 2.02 at top in a graphics font type. When selecting a system to boot that text disappears but the same dull grey background remains. I experimented with a background picture and that shows when the boot options are shown but is replaced by the grey background when an option is selected. I thought to be clever and add GRUB_TERMINAL="console" to /etc/default/grub. That had the effect of removing the graphics background, but now the background was black instead of grey and still without the boot messages.

---

### Post by kc1di on 2018-08-15
try commenting out this line:```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and uncommenting this one: ```
GRUB_TERMINAL=console
```
if not already done.

---

### Post by nocom2 on 2018-08-15
I do not have the graphics screen anymore but a black screen. After choosing an os to boot the screen remains black until the login screen appears. I put the complete /etc/default/grub below as a kind of sanity check. Thanks a lot for all your time!

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
#GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
#GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#export GRUB_MENU_PICTURE="/home/arnold/images/andromeda_2560x1440.png"

---

### Post by nocom2 on 2018-08-22
I mark this thread as solved because my original question was solved, thanks guys!. I'll open another thread for the absence of boor messages.

---

