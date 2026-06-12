---
title: "no kernel loading on grub"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by hamedi on 2013-07-19
hi linux professionals =O 

I had ubuntu 12.04 3.5.0-23-generic dual boot with win7 .but there was a problem to use ati/radeon fglrx on my system so i decided to downgrade kernel (because that driver working with kernel <= 3.4 ) .

I installed linux-image.3.2.0-23-generic and linux-image.3.2.0-24-generic on my system , and i used sudo update-grub to add those kernels to grub boot loader ,and output showed all kernels added to boot loader.

after restart there was just 3.5.0-23 on boot loader so i thought if i uninstall 3.5.0-23 grub can load other kernels ( Im taking shame =[ ) .I uninstalled linux-image-3.5.0.23generic via synaptic and after restart there is just these options on grub boot loader :

memtest

win7

I used live usb to get this informations :

**/etc/default/grub** :

    > # If you change this file, run 'update-grub' afterwards to update
    > # /boot/grub/grub.cfg.
    > # For full documentation of the options in this file, see:
    > #   info -f grub -n 'Simple configuration'
    > 
    > GRUB_DEFAULT="0"
    > #GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true GRUB_TIMEOUT=10 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" GRUB_CMDLINE_LINUX=""
    > 
    > # Uncomment to enable BadRAM filtering, modify to suit your needs
    > # This works with Linux (no patch required) and with any kernel that obtains
    > # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
    > #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
    > 
    > # Uncomment to disable graphical terminal (grub-pc only)
    > #GRUB_TERMINAL=console
    > 
    > # The resolution used on graphical terminal
    > # note that you can use only modes which your graphic card supports via VBE
    > # you can see them in real GRUB with the command `vbeinfo'
    > #GRUB_GFXMODE=640x480
    > 
    > # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    > #GRUB_DISABLE_LINUX_UUID=true
    > 
    > # Uncomment to disable generation of recovery mode menu entries
    > #GRUB_DISABLE_RECOVERY="true"
    > 
    > # Uncomment to get a beep at grub start
    > #GRUB_INIT_TUNE="480 440 1"

**there is nothing in /boot** .

ubuntu@ubuntu:/$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
iF  linux-image-3. 3.2.0-23.36    Linux kernel image for version 3.2.0 on 64 b
ii  linux-image-3. 3.5.0-23.35~pr Linux kernel image for version 3.5.0 on 32 b
ii  linux-image-ge 3.5.0.23.30    Generic Linux kernel image

1-are those kernles(3.2.0.23 and 3.20.24 ) exists in my system ?

2_if they are in my system how can i add them to grub and use them ?

3-is there a way to get 3.5.0.23 kernel back ?


I read similar threads before but I dont want to re-install ubuntu .
please help me. **:**'**(**

---

### Post by dino99 on 2013-07-19
when you install a new kernel, there are 4 packages to install : 2 headers & 1 or 2 images (3.2 might have only one)
the headers are needed to compile the graphic driver by the system

note: install synaptic for ease, and you can also install the "linux-image" metapackage to be sure having a complete installation

---

### Post by hamedi on 2013-07-19
> **dino99 said:**
> when you install a new kernel, there are 4 packages to install : 2 headers & 1 or 2 images (3.2 might have only one)
the headers are needed to compile the graphic driver by the system

note: install synaptic for ease, and you can also install the "linux-image" metapackage to be sure having a complete installation

thanks dino99 for reply , u mean i need to install synaptic on live cd and install kernels throught that ?

---

