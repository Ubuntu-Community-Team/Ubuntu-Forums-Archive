---
title: "Startup manager corrupted grub, how to fix ?"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by kubunut on 2011-03-02
Hey everyone,

Been distro hopping for a while and thought I would swap to gnome instead of kde4. Gave Ubuntu LTS a shot and so far almost everything is working great.

The only thing left is fixing that damn ugly boot splash screen...but now I made it worse. I can't even see the recovery mode text command prompt. I installed the nvidia driver almost blind :D

There is a duplicate of the same command prompt on either side of my monitor, only a few colours it seems and the text is unreadable.

This all happened after I tried using startup manager. It worked in Mint 10 fine. but messed everything up on ubuntu. I had the 640x480 ugly splash before this.

1. Now how do I get the command prompt to be readable again ?
2. How do I fix the res for the boot splash screen ?

Grub Entry
> ### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=1280x1024
        insmod ext2
        set root='(hd0,8)'
        search --no-floppy --fs-uuid --set 61b1cfb0-c481-4714-9c87-519c40d9d55b
        linux   /boot/vmlinuz-2.6.32-29-generic root=UUID=61b1cfb0-c481-4714-9c87-519c40d9d55b ro vga=794  quiet splash
        initrd  /boot/initrd.img-2.6.32-29-generic


sudo nano /etc/default/grub

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="vga=794"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024
GRUB_GFXPAYLOAD_LINUX=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


I am trying to set the res to 1280x1024 that's what worked before in Mint 10.


Any ideas ?

---

### Post by grahammechanical on 2011-03-02
If you are using Gnome go to System>Preferences>Monitors

If you have installed an additional driver for your video card then go to System>Administration and select the settings utility for the make of video card. In my case it is NVIDIA X Server Settings.

You should have an option to detect monitors.

Regards.

---

### Post by kubunut on 2011-03-02
> **grahammechanical said:**
> If you are using Gnome go to System>Preferences>Monitors

If you have installed an additional driver for your video card then go to System>Administration and select the settings utility for the make of video card. In my case it is NVIDIA X Server Settings.

You should have an option to detect monitors.

Regards.


Thanks for the reply,

I have been researching the problem. It seems startup manager plays with grub and which frame buffer the nvidia binary driver uses. Something is configured wrong, I don't know what it is.
I am thinking the easiest way to fix is to reinstall the entire system and just change the res to the one I want in that grub config and update-grub  :D

Just tried one of the solutions...and it worked !

sudo -i
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u

Thanks for the advice peoples !

---

