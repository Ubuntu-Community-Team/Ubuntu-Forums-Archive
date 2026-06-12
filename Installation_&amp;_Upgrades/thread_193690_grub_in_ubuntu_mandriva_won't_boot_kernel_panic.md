---
title: "grub in ubuntu mandriva won't boot: kernel panic"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by skaramanger on 2006-06-10
Greetings,

I have been puzzling over this problem for several days. After installing kubuntu dapper 6.06, I could no long access my mandriva system.  I have searched these forums and the grub docs and need some assistance.

I managed to setup a menu item in grub for mandriva, but its not complete.  I think I'm close, but need some input here.

Below is my menu.lst:

### END DEBIAN AUTOMAGIC KERNELS LIST  
title Other
root

title	Mandriva 2006 kernel 2.6.12-22mdk-i586-up-1GB
root	(hd0,9)
# splashimage (hd0,9)/boot/grub/mdv-grub_splash.xpm.gz 
kernel	(hd0,9)/vmlinuz-2.6.12-22mdk-i586-up-1GB root=/dev/hda10 ro quiet 
initrd	(hd0,9)/initrd
savedefault
boot

### END MANDRIVA MANUAL KERNELS LIST


The mandriva boot errors are approximately:

no resume device specified  ## where should I put that
error opening /dev/console: 2
warning can't access null
exec of init failed 14
kernel panic not syncing

How I got to this point may be of some help:  I booted the kubuntu dvd and clicked on install when kde started.  Then I went away for a short constitution that well turned out to be not! oops hate when that happens!!   I came back to a completed install (grub install to mbr right?) and no way to boot mandriva.](*,) 

Mandriva has a /boot partition at /dev/hda10 hence (hd0,9). I was using lilo in Mandriva, but I don't care about that anymore.  I just want to use it.  I know enough to be dangerous so go easy on me.:mrgreen: .

I have seen several ways to set up grub, but need a more complete picture.

Thanx

Terry

---

### Post by louis_nichols on 2006-06-10
Just a couple of guesses:

I don't think the line with root (hd0,9) is need there. I don't know if it does any harm, either, but it's worth trying without. Can't harm.

Second thing is that usually the initrd bears the version name of the kernel, so on that line youshould have something like:

initrd (hd0,9)/initrd-2.6.12-22mdk-i586-up-1GB

It may not be so in mandriva, but you should make sure. This does seem like the likely culprit, judging from your error message.

---

### Post by skaramanger on 2006-06-10
Greetings Louis,


[QUOTE=louis_nichols]Just a couple of guesses:

I don't think the line with root (hd0,9) is need there. I don't know if it does any harm, either, but it's worth trying without. Can't harm.

Second thing is that usually the initrd bears the version name of the kernel, so on that line youshould have something like:

initrd (hd0,9)/initrd-2.6.12-22mdk-i586-up-1GB  

It may not be so in mandriva, but you should make sure. This does seem like the likely culprit, judging from your error message.[/QUOTE]

True but Mandriva/lilo creates a soft link for default vmlinuz/initrd. Also Could you be a little more detailed about the error messages.  I'll make the change anyway. See what happens. How does one specfiy a resume partition in grub?

Thanks

terry

---

### Post by skaramanger on 2006-06-10
[QUOTE=skaramanger]Greetings Louis,




True but Mandriva/lilo creates a soft link for default vmlinuz/initrd. Also Could you be a little more detailed about the error messages.  I'll make the change anyway. See what happens. How does one specfiy a resume partition in grub?

Thanks

terry[/QUOTE]
I just made the changes you mentioned.  Same errors.

My fix was to boot using mandriva install cd 1 go through the motions. The installer didn't change any files except I had it install grub into the MBR.  I rebooted, edited menu.lst to add  my ubuntu kernel and wahla!! Appears that trying to setup grub from ubuntu to boot mdrva is more complicated I was missing something, but now set!  :-) 

Thanks,

Terry

---

