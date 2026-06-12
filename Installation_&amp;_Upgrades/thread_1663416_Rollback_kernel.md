---
title: "Rollback kernel"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by rflores2323 on 2011-01-09
I am on the below.
/Lucid/10.04/kernel/2.6.32-27-generic./

I want to rollback to 2.6.32-26 as I am having some troubles with the new kernel.

I am on an acer revo 3610.  when it boots up I cant get into the grub menu to pick previous menu. I try to press shiftand it just boots to splashscreen.

Any help pls.

---

### Post by davidmohammed on 2011-01-09
are you sure you are press shift early enough in the boot sequence - suggest hold down the shift key as soon as the bios splash screen is displayed.

Alternatively you can press and hold down the down arrow when booting.

---

### Post by rflores2323 on 2011-01-09
> **davidmohammed said:**
> are you sure you are press shift early enough in the boot sequence - suggest hold down the shift key as soon as the bios splash screen is displayed.

Alternatively you can press and hold down the down arrow when booting.

I hold down shift but I get I flashing dash symbol and then it starts to go to splash screen.  I dont have a bios splash that comes up just the ubuntu splash which I customized with a xbmc splashscreen.  I will try the down arrow to see if that works since shift doesnt seem to. 

 Can I revert via command line if I need to.

---

### Post by rflores2323 on 2011-01-09
Help.

---

### Post by rflores2323 on 2011-01-09
I tried to push tje down arrow key amd still doesnt boot to grub.

---

### Post by arpanaut on 2011-01-09
By any chance is this install an upgrade that has not been converted to grub2?

Just for grins, try hitting the "Esc" after post and see if you get to the grub menu.

If not at least this will bump you back up the board.

---

### Post by rflores2323 on 2011-01-09
> **arpanaut said:**
> By any chance is this install an upgrade that has not been converted to grub2?

Just for grins, try hitting the "Esc" after post and see if you get to the grub menu.

If not at least this will bump you back up the board.

I tried that and nothing.  this is the grub that I have installed when i ran the below command.  I did do upgrade from karmic to lucid.

```
xbmc@xbmc-desktop:~$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu9)
xbmc@xbmc-desktop:~$ 

```

Also tried to update it and got tbe below output

```
xbmc@xbmc-desktop:~$ sudo update-grub
[sudo] password for xbmc: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by rflores2323 on 2011-01-09
this is my grub file also

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by arpanaut on 2011-01-09
have you tried to reinstall Grub?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

  > I dont have a bios splash that comes up just the ubuntu splash which I customized with a xbmc splashscreen.
Maybe disable that until things get worked out with the kernel.

---

