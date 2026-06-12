---
title: "newbie unbutu server"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by nsa4ever on 2008-05-22
Hello Hello,
im trying to understand the Ubuntu server, but first i would like to used it with the virtualbox machine.

so ive downloaded the sun xVm Virtual Box 1.6
and Ubuntu 8.04 LTS Server Edition - Supported to 2013 for Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM).

im geeting all the time this problem ([ http://site.nsaprofile.net/help/help_me.jpg]( http://site.nsaprofile.net/help/help_me.jpg))
[IMG]http://site.nsaprofile.net/help/help_me.jpg[/IMG]

my machine have a intel processor pentium 4.

can anyone help me please.

---

### Post by Peter09 on 2008-05-22
I would suggest that you have the wrong binary of Virtual Box. Go back to the website and download the 386 version.

pC

---

### Post by nsa4ever on 2008-05-22
huns, ive downloaded from a local server in Portugal, 

[ftp://ftp.rnl.ist.utl.pt/ubuntu-releases/hardy/ubuntu-8.04-server-i386.iso](ftp://ftp.rnl.ist.utl.pt/ubuntu-releases/hardy/ubuntu-8.04-server-i386.iso)
Ubuntu Edition: Ubuntu 8.04 server
Computer Platform: i386
Download Location: [ftp://ftp.rnl.ist.utl.pt/ubuntu-releases/](ftp://ftp.rnl.ist.utl.pt/ubuntu-releases/)

and all look like the same to me

and the virtual box was the:
x86 windows version

---

### Post by dstew on 2008-05-22
Your Pentium 4 may be a 32-bit or 64-bit processor, depending on the model number. Is it possible you downloaded a 64-bit kernel, and your processor is 32-bit? Check your processor specs, either from your computer documentation, or your BIOS setup display. What is the exact name of the downloaded Ubuntu .iso? The generic kernel is usually the best, since it automatically detects 32- or 64-bit processors, and activates the correct software.

EDIT: After I posted I see the other posts. That .iso should work with either 32- or 64-bit processors, so I think something else must be wrong...

---

### Post by Peter09 on 2008-05-22
Looking back at your screen, thats appears to be an error from the virtual machine. You need to point it to a bootable CD or ISO. A virtual machine is just like a normal computer (except the most obvious bit is missing ... H/W). If it does not have an operating system it will not boot.

You build a virtual machine just like a normal one, following the same step. 1st install your O/S....

PC

---

### Post by nsa4ever on 2008-05-22
ive used virtual machine many times, and this is the first time that i have a problem, here a picture of my processor:
[http://site.nsaprofile.net/help/help_cpu.jpg](http://site.nsaprofile.net/help/help_cpu.jpg)

[IMG]http://site.nsaprofile.net/help/help_cpu.jpg[/IMG]

i think ive done all right haven't i?

---

### Post by Peter09 on 2008-05-22
OK,
are you getting this problem on the virtualbox GUI?

PC

---

### Post by nsa4ever on 2008-05-22
im downloading again from other source the ubuntu-8.04-server-i386.iso , but in the tree installations that ive made went well, the problem is when virtualbox reboot the machine.

i think the problem is really with the virtual machine, but ive tried first with a older version of virtualbox and the problem was the same, and then i updated and i get the same error message.

i suspect is the Unbutu. baaaaaaaaah or my hardware?

---

### Post by Peter09 on 2008-05-22
Looks like it,
just a thought, make sure that VirtualBox is not attaching the bootable CD to the virtual machine again, or something like that. It does appear to be trying to boot from somewhere again.

PC

---

### Post by nsa4ever on 2008-05-22
i have another virtual machine with windows xp. This was made with an older version of virtual box  and that works fine with the new virtual box 1.6.

---

### Post by nsa4ever on 2008-05-22
ive changed the boot sequence from virtual box and the problem is the same.

---

### Post by nsa4ever on 2008-05-23
anyone?

---

### Post by dstew on 2008-05-23
I have no experience at all with virtualbox. You might be better off posting on a virtualbox forum. If you want to try Ubuntu without installing, I suggest you create an Ubuntu Live CD, and boot that to try out Ubuntu. If you open the Live CD instead of boot it, you can also try it out or install it inside Windows if that is what you want.

---

### Post by nsa4ever on 2008-05-23
thank you! im going to do that right know. ;) ill post the answers i get form them here.

---

### Post by nsa4ever on 2008-05-23
problem solved!!
just go to the virtual box, settings, general -> advanced and turn on the enable PAE/NX :P

this topic can be closed. thank you to all.

---

### Post by dstew on 2008-05-23
Excellent. Thanks for updating this thread, it will be a good reference for others.

---

