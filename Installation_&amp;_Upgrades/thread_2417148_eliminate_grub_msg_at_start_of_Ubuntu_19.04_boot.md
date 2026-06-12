---
title: "eliminate grub msg at start of Ubuntu 19.04 boot"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2019-04-21
When i start 19.04 a several second boot choice msg comes up. I always want to go straight to normal Ubuntu. Can I get rid of the msg without using something like grub-customizer ?

Thanks

---

### Post by dino99 on 2019-04-22
is the grub setting have 'splash quiet' set ?

---

### Post by s9032g@comcast.net on 2019-04-24
I don't know

---

### Post by oldfred on 2019-04-24
I do this to change from default 10 sec to 3, if you change to 0 you never can get into grub and if you need recovery mode or boot older kernel after update and issues you are stuck and only chroot from live installer may work. Best to keep 3 sec or so:

sudo nano -B /etc/default/grub

#GRUB_TIMEOUT=10
GRUB_TIMEOUT=3

---

### Post by Rubi1200 on 2019-04-24
Others may disagree but I do not recommend Grub Customizer.

Oldfred has the best advice in the post above.

Good luck!

---

### Post by CatKiller on 2019-04-24
> **oldfred said:**
> I do this to change from default 10 sec to 3, if you change to 0 you never can get into grub and if you need recovery mode or boot older kernel after update and issues you are stuck and only chroot from live installer may work. Best to keep 3 sec or so:

For what it's worth, you can still enter the GRUB menu even with the timeout set to 0: spamming the button means that it's already in the keyboard buffer for the 0 seconds that GRUB looks for it. It's not pretty, but it does still work.

For the OP, you can set GRUB_TIMEOUT_STYLE to "hidden" as well as reducing the duration.

---

### Post by s9032g@comcast.net on 2019-04-25
I like oldfred's solution. I went to terminal and did the terminal command that shows me  "#GRUB_TIMEOUT=10
GRUB_TIMEOUT=3". On the bottom of the terminal screen there are keys to making the change. I am not sure how to go about this and I don't want to screw something up. Pls gic=ve me more detail about adding the # mark and then putting in the new line "GRUB_TIMEOUT=3". Thanks

---

### Post by CatKiller on 2019-04-25
/etc/default/grub is just a text file, and nano is just a text editor.

The shortcuts are listed at the bottom of the screen.

You use sudo nano -B /etc/default/grub to open the file in nano as root. The -B makes a backup. Edit it appropriately. Ctrl-X to exit.

Then run sudo update-grub to update your GRUB configuration using your new configuration file.

---

### Post by s9032g@comcast.net on 2019-04-25
" Edit it appropriately. Ctrl-X to exit."
 
How to do the actual edit is my question. I haven't done this before and don't want to mess it up

---

### Post by CatKiller on 2019-04-25
> **s9032g@comcast.net said:**
> " Edit it appropriately. Ctrl-X to exit."
 
How to do the actual edit is my question. I haven't done this before and don't want to mess it up

?

oldfred's already said: find the GRUB_TIMEOUT value and change it to something more to your liking. The value is in seconds.

---

### Post by oldfred on 2019-04-25
Nano is an old fashioned text editor. Entry is only where cursor is, so you have to use arrow keys to move around.
But it will also accept copy & paste. I often forget and paste something in wrong place, because that is where cursor was.
You can edit the 10 to 3, but I prefer to comment out the one line as it is original and add my own line. Helps me remember that it is something I changed.

---

### Post by Claus7 on 2019-04-25
Hello,

after my update to 19.04 gradually from 18.04 and 18.10, I noticed the same behavior of grub as the OP. I checked another configuration of grub of mine and I saw that the GRUB_TIMEOUT_STYLE=hidden was there, whereas in 19.04 was removed.

As a result the first 3 lines of grub were configured as:
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0

and the grub menu was removed from boot sequence. In-between I had to issue the command sudo upgrade-grub.
In order to change and add the configurations above I issued the command:
sudo gedit /etc/default/grub

which opened the grub menu with the gedit program. The configurations above can change according to one's needs.

Regards!

---

### Post by s9032g@comcast.net on 2019-04-27
Please explain how to do the edit. I understand what the edit is but I don't see just how to accomplish it on the terminal. There are a bunch of "keys" on the bottom of the terminal screen but they don't seem to react to anything I do.

---

### Post by jeremy31 on 2019-04-27
In terminal do ```
gedit admin:///etc/default/grub
```
Make the changes to the file, save and exit, then
```
sudo update-grub
```
Reboot

---

### Post by s9032g@comcast.net on 2019-04-28
Ok . Here is what I see after doing the first terminal entry. 

GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Now ,since this does not match up with the earlier instructions that I got, would you please tell me what to change to eliminate the boot delay?

Thanks a bunch. If I keep asking I always seem to get a more succinct solution.

---

### Post by CatKiller on 2019-04-28
Scroll down.

---

### Post by ajgreeny on 2019-04-28
I have a single boot machine running Xubuntu 18.04, and using UEFI.
I have always found it very difficult to press Esc at exactly the correct time to get the grub menu to appear; even continuous tapping at the key will often not work, potentially causing big problems getting to the menu in order to boot to recovery mode, should it be required.

As a result of this potential problem I have manually edited the /etc/default/grub file to make sure that the grub menu appears at each boot, which it normally would not, this being a single OS system.

Here is the content of my  /etc/default/grub file which you may find useful; note the short timeout of 2 seconds and the change to the "GRUB_DISTRIBUTOR" line which I like to show the actual name of my OS, ie, "Xubuntu-18.04-Bionic".
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
	
GRUB_DEFAULT=0
# next line will make countdown time show menu by default
GRUB_TIMEOUT_STYLE=MENU
# next line changed from 0 to 2 for 2 second delay
GRUB_HIDDEN_TIMEOUT=2
# next line changed from true to false to allow delay countdown to show
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR="Xubuntu-18.04-Bionic"
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

### Post by s9032g@comcast.net on 2019-05-01
Ok. Once again my output was different from yours;

GRUB_DEFAULT=0 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="quiet...

I just changed the timeout from 10 to 2, updated Grub, and now the delay is very short.

Thanks for the help.

---

