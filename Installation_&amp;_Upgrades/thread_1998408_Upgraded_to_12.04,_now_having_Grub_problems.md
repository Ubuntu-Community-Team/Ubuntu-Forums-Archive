---
title: "Upgraded to 12.04, now having Grub problems"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by amira-uk on 2012-06-06
Hi,
I upgraded from 11.10 to 12.04. At first grub2 said there were no partitions so I used Supergrub2 Rescue Disk to fix it and can now boot Kubuntu.
When I try to boot Vista I just get a flashing cursor (I left it for an hour).
I tried to update grub2 manually but it obviously didn't work and I get and error message when running update-grub.

Here is my grub splash screen [http://imgur.com/fAsdH](http://imgur.com/fAsdH)

Please see error and my grub below:

 beki@beki-desktop:~$ sudo os-prober;sudo update-grub
    [sudo] password for beki: 
    /dev/sda1:Windows Vista (loader):Windows:chain
    /usr/sbin/grub-mkconfig: 14: /etc/default/grub: title: not found
    beki@beki-desktop:~$ 



            # If you change this file, run 'update-grub' afterwards to update
    # /boot/grub/grub.cfg.
    # For full documentation of the options in this file, see:
    #   info -f grub -n 'Simple configuration'
        GRUB_DEFAULT=0
    #GRUB_HIDDEN_TIMEOUT=0
    GRUB_HIDDEN_TIMEOUT_QUIET=true
    GRUB_TIMEOUT=10
    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    GRUB_CMDLINE_LINUX=" vga=792 splash"
        title Microsoft Windows Vista
    root (hd0,0)
    savedefault
    makeactive
    chainloader +1
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
   
    
I've also tried the boot-repair app.
So I'm really confused, if anyone has any ideas please let me know.

---

### Post by darkod on 2012-06-06
Supergrub can sometimes do thing in a different way. That's why I avoid using it. You have all you need in your kubuntu cd.

First, burn a cd of kubuntu 12.04 if you already don't have one.

Run the boot-repair again but not to do any repair, just to create the boot info summary and post here the link it gives you with the results. That will show more details.

---

### Post by amira-uk on 2012-06-06
> **darkod said:**
> Supergrub can sometimes do thing in a different way. That's why I avoid using it. You have all you need in your kubuntu cd.

First, burn a cd of kubuntu 12.04 if you already don't have one.

Run the boot-repair again but not to do any repair, just to create the boot info summary and post here the link it gives you with the results. That will show more details.

Thanks, I am downloading it now but my internet is terrible so I won't be looking at it tonight. I'll get back to you when I've looked into it, its not urgent so it might be a couple of days.

---

### Post by oldfred on 2012-06-06
It looks like you added this into the middle of /etc/default/grub. That will corrupt grub and may prevent the entire update from running. Entry is an old style grub legacy entry and would not be valid for grub2 anyway. It looks like your menu already has a Windows entry.

title Microsoft Windows Vista
    root (hd0,0)
    savedefault
    makeactive
    chainloader +1

Did you resize Vista using Vista's MMC or partition tools? If not Vista needs chkdsk from a Windows repairCD.

---

### Post by amira-uk on 2012-06-10
Yes I did add it in, but it didn't seem to change anything either way.
I've now decided, seen as KDE is now broken after it tried to update that now would be the perfect time to invest in an SSD so I'm not going to worry about trying to fix it as that will be arriving during the week.
Thanks for the help though, much appreciated, I'm sure I'll be back with more questions!

---

