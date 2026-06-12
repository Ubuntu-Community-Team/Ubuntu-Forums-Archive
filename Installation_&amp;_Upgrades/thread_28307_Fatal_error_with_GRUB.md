---
title: "Fatal error with GRUB"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by shaynaynay on 2005-04-19
you can refer to my post here: [http://ubuntuforums.org/showthread.php?t=28237](http://ubuntuforums.org/showthread.php?t=28237)
And I'm writing to this forum, 'cause I discovered I have the Hoary 5.04 version.

The GRUB gives me fatal error, saying it could not install to hd0.
LILO's installation is OK, but is installed into hdb. And after reboot, windows XP comes up, no boot menu.

I've downloaded this: [http://www.osloader.com/](http://www.osloader.com/) which does recognize the Linux installation, but when it try to load I get a "kernel panic" error, and some other errors (can't find "root=" or something like that), and freezes.

Do you familier with this?
Thank you very very very very much!!  ](*,)   ](*,)   ](*,)

---

### Post by alastair on 2005-04-19
I'm not sure you give enough detail here. 

I think something went wrong on the install basically. It might be best to install GRUB on "hda" i.e. primary master. If windows is also installed, it should put a windows menu in GRUB for you as well.

Try again - and come back if you get problems.

---

### Post by shaynaynay on 2005-04-20
[QUOTE=alastair]I'm not sure you give enough detail here. 

I think something went wrong on the install basically. It might be best to install GRUB on "hda" i.e. primary master. If windows is also installed, it should put a windows menu in GRUB for you as well.

Try again - and come back if you get problems.[/QUOTE]

hmmm... what else do you need in order to fix this?
The installation proccess went well...
I installed Ubuntu to the first partition of my second HD (hdb)..
In the partitioning part, I told it that this disc is bootable, and in the "mount point" I put "/", as I've been told to do.
Then he just continued, installed whatever he needs, and then when he tried to install GRUB, it gave me the fatal error ("unable to install GRUB in (hd0)")..

---

### Post by shaynaynay on 2005-04-20
I'm adding more information about my problem:
during boot, I get the following lines:

...strange... kswapd0 not stopped
...strange... kseriod not stopped

RAMDISK: couldn't find valid RAN disk image starting at 0.
VFS: cannot open root device "341" or unknown-block(3,65)
Please append a correct "root=" boot option
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block(3,65)

Thanks again.

---

### Post by mdkrokz on 2005-05-04
I have exactly the same problem. I've installed kubuntu on three computers. Everything works just fine on my desktop but I have this "grub fatal error" problem during grub installation on my toshiba laptop and the third computer. Lilo doesn't work on the third computer either. It only partially works on my laptop, as it boots the default OS specified in  lilo.conf but I have no way to select which OS to boot at startup.

---

### Post by alastair on 2005-05-04
Not sure.

But you said :

"I installed Ubuntu to the first partition of my second HD (hdb).."

/dev/hdb1 is device 3,65

But you also said that an error on GRUB install was :

"unable to install GRUB in (hd0)"

Now "(hd0)" is the first hard disk device - normally assumed primary master (hda), not slave (hdb). Maybe there is a BIOS vs OS discrepancy i.e. your BIOS boot order is not as expected or something?

Remember - if you get a GRUB menu you can ESC to stop there, then type commands to setup a boot i.e. figure out then where things are. It even does TAB completion.

See : 

[http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You](http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You)

---

