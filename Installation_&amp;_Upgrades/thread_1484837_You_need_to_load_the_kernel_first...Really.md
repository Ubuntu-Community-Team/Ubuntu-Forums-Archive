---
title: "You need to load the kernel first...Really?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by zimbandrew on 2010-05-16
I have just updated my version of Ubuntu from Ubuntu 9.10 to  Ubuntu 10.04 LTS

There is a measure of unhappiness as the poor machine struggles to boot using the updated kernel.  Simply, it will not boot, thus we get: 

error: you need to load the kernel first
Failed to boot default entries

The system then goes back to GNU GRUB version 1.97~beta4.

So we try Ubuntu, Linux 2.6.32-22-generic (recovery mode)...hmmm same thing

So, we press button 'e' and we get and Emacs-like screen:

insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c4e42608e425fd74
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks\
/root.disk ro single
initrd /boot/initrd.img-2.6.32-22-generic

Its certainly unhappy...so we pop to the next option 2.6.31-20-generic and we get:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
Deep Freeze...except for a blinging cursor.

Perhaps the recovert mode will work?  Runs a whole load of commands...it eventually freezes.  So back to the on/off switch.

Next call down the GRUB menu - Ubuntu, Linux 2.6.31-17 and now we are crossing fingers, becuase that is the last option apart from going back to Windows XP Professional.

It boots!  Whoopee - no hold on a second its crashed...a psycadelic screen and then a flashing screen like a load of medals...something wrong, I guess.

So to recovery mode on 2.6.31-17 we go.  Lots happens...and we get through to a Recovery Menu... been here before...
Option dpkg - repair broken packages looks attractive...click on it.  It gets busy online reading building calculating...then 'please press ENTER....phew...back to recover menu.

So lets update the grub bootloader...can't do any harm, surely..done

So lets run it in failsafeX mode...see what happens - compatible NVIDIA X driver not found...strange I did download and install one.

We seem to be able to log in now.  So how come the kernel is missing in the later editions at boot up and just how do we fix this so it has the kernel available at boot and the latest version of Linux?

I tried a few things:
sudo apt-get update
sudo apt-get install linux-image-2.6.32-22-generic

Says I should run apt-get autoremove....so I do
sudo apt-get autoremove
sudo apt-get install linux-backports-modules-2.6.32-22-generic .... package not found
sudo apt-get install linux-headers-2.6.32-22-generic ..... already installed

The machine still crashes so we return to the good old recovery mode and try resume normal boot...it freezes up after
rc-sysint start/running, process 3399
.
.
. 
* Check battery state...

Ctrl...Alt...Delete works!

---

### Post by drs305 on 2010-05-16
First, it appears this is a Wubi install, which is important for troubleshooters to know.

There was a very common bug in the Karmic wubi which caused similar problems. I don't know if it carried over to Lucid or not but the symptoms indicate it might have. 

Check out this link by meierfra and see if it helps:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by zimbandrew on 2010-05-16
Well...DRS305...you whacked the problem first time...my grateful appreciation for this :)

On advice... taken to [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Follow the instruction and download wubildr file and replace the existing file on the C: drive (in Windows)

It worked!

Thank you ever so much....and sorry for not telling your it is a Wubi set up...so obvious that I should have mentioned it.

Andrew

---

### Post by drs305 on 2010-05-16
Glad it worked but sorry to see the bug is still a problem ...

Would you please mark this thread "Solved". You do this via the Thread Tools link at the top right of the original post. (You can also remove it from there if necessary.)

Marking a thread 'Solved' allows helpers to concentrate on unresolved issues and also lets those looking for answers know that a solution to their problem may be contained in a thread.

zimbandrew, I forgot to welcome you to the Ubuntu forums. :-)
You will find this one of the friendliest forums on the web.

---

### Post by zimbandrew on 2010-05-16
Thank you for the welcome...stuck here in darkest Africa...home of Ubuntu, and just a Linux hobbyist.  Will comply with the solved issue marker.

Thanks once again.

Andrew

---

