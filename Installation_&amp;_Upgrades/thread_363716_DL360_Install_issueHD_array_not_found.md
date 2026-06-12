---
title: "DL360 Install issue/HD array not found"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by moneymonk on 2007-02-17
I'm trying to install 6.06 Server on a Compaq (pre-HP) DL360 with a Compaq Smart Array SCSI controller.  The install appears to go fine, but on reboot I receive the error:

[I]cpqarray: Error sending ID Controller
Unable to find volume group 'Ubuntu'
Alert! /dev/mapper/ubuntu-root does not exist.  Dropping to a shell![/I]

I've done some research within this forum.  Apparently, the *cpqarray* driver is part of a module and not the kernel.  When the machine boots it uses the wrong driver before it has a chance to get to the module and use the correct one. I attempted two different fixes, which seemed pretty specific, but a bit over my head.

One of them was here: []("http://www.ubuntuforums.org/showthread.php?t=255335")
[http://www.ubuntuforums.org/showthread.php?t=255335](http://www.ubuntuforums.org/showthread.php?t=255335)

> **scubanator87 said:**
> I was having the same problem here at work. Tried Several different install settings and mess with the smartstart cd 

for hours and couldn't figure it out. i finally found this post and adjusted it for my Edgy install: Here is what i 

did:

Booted from Install cd and chose Repair.

Go through the same start of the set up till error. 

after error a list of options will be available, scroll down and select "Start a Shell"

Make a folder to mount your install
$ mkdir /target

Now mount it for access (my partition defaulted to c0d0p1)
$ mount /dev/ida/<your partition goes here> 

now chroot
$ chroot /target

Now us vi/vim to edit the modules file to have the array boot on start. first make a back up!
$ cp ./etc/initframsfs-tools/modules ./etc/initframsfs-tools/modules_backup
$ vi ./etc/initframsfs-tools/modules

Once in vi, unless you have the commands memorized, you'll need a cheat sheet like me. i had to print it out to keep 

from running back to my desk over and over.how ever, you'll only need a few commands and i can help with that.

after you open its in command mode so do the following
hit j till your at the bottom of the document. 
hit o to open a new line after the current. 
type "cpqarray" and hit enter. this is the module for raid array
hit ZZ to save and exit

If your read the comments in the modules file, you notice that to update the list you need to run update-initramfs 

to update the init file. you need to run the -u option to update the list. 
$ update-initramfs -u 

Now all you have to do is reboot! yay your system now works. :-)

I followed Scubanator's advice but was unable to *chroot.*  I receive the error:

*Chroot: Cannot run command '/bin/sh': No such file or directory.*

I also tried vjshah's fix (quoted by DavidRa) which is very similar, but works around the *chroot*. It is located here:  []("http://www.ubuntuforums.org/showthread.php?t=81817&highlight=82466")
[http://www.ubuntuforums.org/showthread.php?t=81817&highlight=82466](http://www.ubuntuforums.org/showthread.php?t=81817&highlight=82466)

> **DavidRa said:**
> A genius calling himself or herself "vjshah" posted a working fix in [http://www.ubuntuforums.org/showthread.php?t=82466](http://www.ubuntuforums.org/showthread.php?t=82466).

I have quoted his fix here:

Now, I should note that I did NOT follow the procedure blindly:

[LIST]
[*]My root partition was automatically mounted to /target during rescue boot; I think (hazy memory) that /boot was already available in /target/boot.
[*]I didn't bother with chroot;
[*]I modified the paths to account for the fact that I wasn't chroot'd;
[*]I used the command "echo cpqarray >> /target/etc/mkinitramfs/modules" instead of a text editor (nano).
[/LIST]Hope this helps!

However when I do *echo cpqarray >> /target/etc/mkinitramfs/modules* I get the error:
*sh: /target/etc/mkinitramfs/modules : No such file or directory*

I don't know what *DavidRa* means when he says: [I] I didn't bother with chroot;
I modified the paths to account for the fact that I wasn't chroot'd;[/I]

I'm a newbie, and I want to get this server rolling and learn something along the way about Linux.  A step by step walk thru with some explaination of what I'm trying to do would be awesome and very appreciated.  Please help.

Thanks-

The Monk

---

### Post by cfgtech on 2007-03-29
having the exact same issue with my Proliant 8500
the installation goes great by the looks of it and at boot up it bombs
I'm running a dual boot.Will have to look for answers..

---

### Post by madman1337 on 2007-07-19
I am having this same issueon a DL380. I will try out the fixes above and see if I can get it to work.

---

### Post by gstark on 2008-03-05
I was able to load 7.10 on a DL380 using this post:

[http://ubuntuforums.org/showthread.php?p=4459536#post4459536](http://ubuntuforums.org/showthread.php?p=4459536#post4459536)

---

