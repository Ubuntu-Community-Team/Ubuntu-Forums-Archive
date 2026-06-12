---
title: "An understandable, complete Solution for GRUB Error 15 after Install or Upgrade"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Jim-BobH on 2008-07-13
Subject: An understandable, complete Solution for GRUB Error 15 after Install or Upgrade

NOTE: I have seen some indications that 8.04.1 fixes most if not all of these problems, but the problem will recur many times before the word gets out to everyone if it _is_ truly fixed, so here is my attempt to help until then:

I'm somewhat a Linux newbie but I think I see a lot of problems with the descriptions of this error and its solutions, so I am trying to help (and point out to help authors that newbies need all these details) by starting here a single spot where everything needed can be found. I hope some real experts will jump in and correct/clarify anything I say in a less-than helpful way. I just went through this exact error and resolution myself, and this is what I think would have been a "complete solution":

There are apparently many ways to get to the point where we try to (re)boot and get GRUB Error 15: File not found. Regardless of the reason (assuming the installation actually did do everything _else_ correctly), the "last cause" is that the wrong boot partition is specified (in at least two places) in

/boot/grub/menu.lst   (and that is lst as in LIST, not 1st as in FIRST)

and there are several things we need to know/do to fix it. See farther below (and hopefully follow-up posts) for how-to help. In these examples, (hd1,0) is the WRONG (drive,partition) set:

1. In the section that looks like

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

make sure the last line correctly specifies your desired grub root device.

IF you just did a fresh install on your "first" hard drive or you otherwise know you want to boot on that partition (and the one that your system treats as the "first" may depend on whether you have IDE (PATA) and SATA drives, and whether your BIOS can change Hard Drive Boot Priority, and who knows what else)

THEN # groot=(hd0,0) is correct. Yes, that is a comment line. Apparently some part of Ubuntu reads it and uses it to re-write the real specifications under certain conditions. The file menu.lst itself has some comments about how this works, but I don't completely understand it. Doesn't matter; just fix it. Thanks to Hangfire for pointing this out.

ELSE you will have to figure out that answer, or just try different drive numbers (the first value) and partition numbers (the second value) until you hit it. There are several posts about how to find all your partitions and figure out which one you want to boot on by default. I found dozens with Google; I presume you will too, and tailor your searching to your particular situation.

====> Once you know the correct (drive,partition) numbers e.g. (sd1,2) use those in place of (hd0,0) in all the fix instructions in this post!

2. In all the other places that have the wrong partition specified,

after 

### BEGIN AUTOMAGIC KERNELS LIST

after

## ## End Default Options ##

but before

### END DEBIAN AUTOMAGIC KERNELS LIST

for example:

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=29f74e7d-0b13-4495-abfd-2ebdc568d29b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

fix in the same way, i.e. make that root line be

root		(hd0,0)

---------------

How to do all the above: Here is one way:

After a power-up or otherwise a re-boot, hit Esc (Escape) to get the boot menu. The top line is the default and (unless you are choosing something else during boot) clearly the culprit. Make sure it is highlighted and hit e (edit). Follow the on-screen instructions to highlight (select) and edit the root (hd1,0) line to be root (hd0,0) then boot.

Once you boot successfully, you now know the wrong and right (drive,partition) numbers, so fix them permanently:

Start a Terminal: Choose Applications >> Accessories >> Terminal. In the Terminal, type:

sudo nano /boot/grub/menu.lst

This switches to SuperUser (root) priviledges (it will ask for _your_ _User_ password, at least the first time) and starts a very simple, very small (nano) text editor and you should see the contents of menu.lst

(NOTE: You can edit all you want, but you can't save your work on this file if you don't have root rights!)

Follow the on-screen instructions to move to the spots and edit them as described above. In my file, "## default grub root device" is line 72, and there are many more lines after that.

(If you make an unrecoverable error, e.g. you trash something and can't remember for sure how to fix it (there is no Undo) then just Exit WITHOUT WriteOut, and re-enter the command to start over editing.)

Once you have made all the corrections described above, be sure to WriteOut the file before exiting.

Choose Restart to test the fix. If it doesn't work, go back to "How to ...", reboot and see if you missed something. If _I've_ missed something, hopefully the Community will catch it soon and fix it; in that case I apologize; this is about the best I can do at this point.

====> Speaking of the Community: Can someone please notify the Developers that the Installer needs to be a little smarter? Apparently it is choosing the wrong boot partition for menu.lst if there are multiple drives / partitions, especially with Wubi / multi-boot or with both PATA and SATA drives in the same machine.

IHTH

Jim

- end -

---

### Post by PeteBraven on 2008-07-13
Ah,. this seems to be somewhat similar to the problem I was thinking of posting myself after my head/wall-banging session yesterday!
When I can get my head out of the toilet long enough, (I ate something that doesn't like me much) I will try getting it round why the install ran fine up to where it hung with a 'fatal error' trying to load Grub.
Yes I did go for the Lilo option but that just screwed up the MBR instead and then the IDE became unreadable.
Ok,.. re-inserted original microslop rescue floppy and 'fdisk /mbr' to get back here with original system still intact!
Now I can try your suggestions and see if it wakes up my install!

---

