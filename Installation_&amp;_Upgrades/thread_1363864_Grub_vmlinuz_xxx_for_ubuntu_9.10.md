---
title: "Grub vmlinuz_xxx for ubuntu 9.10"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by ic2 on 2009-12-25
[FONT="Arial"]Hello everybody,

I need to use the simple sequence that ubuntu 9.10 use that will works with GRUB - The GNU Grand Unified bootloader that came with Arch Linux.  I worry about GRUB-2 upgrade latter if it's not the same.  I really don't know.

No need to tell you the h*ll I went through as one boot-loader over-write the next.  Arch was my last install, so I let Arch GRUB version be the main boot-loader until I got more free time to do it all over again.

Please don't get off track of my original question above ... but the main problem was; I could not find /boot/Grub/menu.lst no where in ubuntu 9.10 install.  That was a trip for me, looking all night long for it.  So I said forget it and installed ARCH linux to see if it would pick up the other installs and I'm soooo glad I made it last thing on the list to be installed.

The docs said "you'll find menu.lst in" /boot/Grub/menu.lst and it was there for Arch, un-like ubuntu 9.10 where it could not be found anywhere on it installed partition.  I could have missed something but this is what I saw, all night long before going back to my 9-5 boring job that morning.

This is something I would like to understand because ubuntu will end-up being one of my main OS of study, but this has not much to do with the main question I asked above, All I need is the simple sequence that resemble what others LINUX installs use, as below:

title Arch Linux
root (hd0,19)
kernel /boot/vmlinuz26=root=/dev/sda20 ro
initrd /boot/kernel26.img

title ubuntu 9.10
root (hd0,16)
kernel /boot/vmlinuz_xxxxx=root=/dev/sda17 xxxx ... Need to know
initrd /boot/kernel_xxxxx.img ... Need to know

title WindowsXP
root (hd0,0)
makeactive
chainloader --force +1boot

title FreeBSD
root (hd0,3,a)
kernel /boot/loader


**THIS IS THE ORDER OF MY INSTALL**..:

It was tricky to make sda2 Primary because Windows being the first to install did not accept it and would not intall.  So I  gave sda1 extra BYTES and made the Extended Partition right behind it and one more Primary Partition at the end of the disk. So I got the idea to resize Primary-1 with Partition Commander after all Windows were installed.  Now I got Primary-3, or is it Primary-2 as it should be called ... I'm not sure but it worked  :)

Lets ask that MicroSoft don't walk over that tooooo in a service pack or the next version or that any other OS don't do the same to make thing difficult by design  :( [/FONT]

(edit -- correction for a better clue)

[FONT="Courier New"]sda1 Win-Vista - Primary-1
sda2 BSDI - Primary-2 created after I installed all MS Windows "RESIZING" the extra bytes.
sda3 Now we get the NEW Extended-Partition for MS-Windows AFTER all has been installed.
sda4 FreeBSD - Primary-4
sda5	Win-7 -- 32bit
sda6	Win-7 -- 64bit
sda7	waiting for Win-8
sda8	G
sda9	H
sda10	I
sda11	J
sda12	K
sda13	L
sda14	M
sda15	N
sda16	0		200,000 GB

sda17	Linux-1		Ubuntu 9.10-ext3	25004.84	used 2.46GB

sda18	Linux-2		waiting			20003.89

sda19	Linux-3		waiting			15002.92

sda20	Linux-4		Arch			10001.95	used  814MB

sda21	Linux-5		SWAP			4087.97

sda22	Linux-6		future SWAP growth	67570.18[/FONT]


Thanks in advance

---

### Post by ic2 on 2009-12-25
I re-installed Ubuntu 9.10 and GRUB picked up Arch Linux but it did not pick up FreeBSD.  I click Ubuntu, Linux.  It booted to the window showing the name I gave it during installation time which was my name.  It asked me for my password.  I typed my password and Ubuntu opened.

The good thing is I founded grub.cfg and included these line at the bottom of the comment as instructed.

title FreeBSD 8.0
root (hd0,3,a)
kernel /boot/loader

Then I went to save the file ... under File, "save" is grayed out and I only get "Save As", so I clicked "Save As".  Then I get this:

**Could not save the file /boot/grub/grub.cfg.**
[COLOR="Red"]You do not have the permission necessary to save the file.
Please check that you typed the location correctly and try again.[/COLOR]


So I check 10000 times, and it still did not save the file.  I could not even save the file under a difference filename.

Could someone tell me what I need to do to solve this additional problem?  It make no since.  I followed Ubuntu install instructions to the letter.

This push me back to a week ago when I first asked about password and being the administrator.

[http://ubuntuforums.org/showthread.php?t=1355603&highlight=ic2](http://ubuntuforums.org/showthread.php?t=1355603&highlight=ic2)

PS: sorry if fonts were to large.  I use Opera and when I set to 22 it look perfect for viewing on personal machine.  No glasses needed.  Now with this post I reduced it back down to standard 9, now my fonts are tiny but better viewed by the forum i guest.

---

### Post by ic2 on 2009-12-26
I hand-copied what ubuntu 9.10 menu.lst had, than I re-installed Arch with it Gurb version and sorted out the ubuntu info and now it works.  It seems that GRUB-2 only made things more complicated.  Just use kernel, not linux for older version.

One Down, One to Go :)

# (4) Ubuntu 9.10 ; ........ *works perfectly*
title Ubuntu 9.10, kernel 2.6.31-14-generic on 17
root (hd0,[COLOR="Red"]16[/COLOR])
[COLOR="Red"]kernel[/COLOR] /boot/vmlinuz-2.6.31-14-generic root=/dev/sda[COLOR="Red"]17[/COLOR] ro   quiet slash
initrd /boot/initrd.img-2.6.31-14-generic

# (5) Ubuntu 9.10 Recovery Mode; ........ *works perfectly*
title Ubuntu 9.10 Recovery Mode on 17
root (hd0,[COLOR="Red"]16[/COLOR])
[COLOR="Red"]kernel[/COLOR] /boot/vmlinuz-2.6.31-14-generic root=/dev/sda[COLOR="Red"]17[/COLOR] ro single
initrd /boot/initrd.img-2.6.31-14-generic

# (6) Ubuntu Memtest86+ ; ........ *works perfectly*
title Ubuntu Memtest86+ -- it use SWAP
root (hd0,[COLOR="Red"]16[/COLOR])
[COLOR="Red"]kernel[/COLOR] /boot/memtest86+.bin

# (7) Memory Test Console; ........ ***Not Working***
title Memory Test Console
root (hd0,16)
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
# root=/etc/grub.d/memtest86+


I guest no one never had the password administrator problem.  I'm using ubuntu 9.10 -- 64 on a 64 bit quad core AMD machine, maybe that's the problem or I got a bad download, who knows.

---

### Post by ic2 on 2009-12-26
PS:

I think I need glasses.  Things are coming to light.

Have a great day

---

