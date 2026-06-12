---
title: "missing kernel-headers?"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by onineko on 2006-09-22
Hello!

I was trying to set my double-head graphics card (an nvidia) to work with 2 monitors, one being the main, the other simply to enlarge my desktop. 
Now, poking the xorg.conf didn't do the trick, so i decided to install the nvidia-driver first and then try it again.

I used the howto I found on the ubuntu-forum (i don't know right now which thread it was) and then I came to the command 
sudo cp /usr/src/name of your source/arch/i386/Makefile.cpu /usr/src/kernel-headers-`uname -r`/arch/i386/

but there is not /usr/src/kernel-headers... on my machine.

So I went google and searched for kernel-headers.2.6.15-27-686 
And I found nothing at all.

By now, when I try to update my system or enter the synaptic-package manager I get the error 
"/usr/bin/update-manager konnte nicht ausgeführt werden /couldn't be run)

Die X Authorisierungsdatei konnte nicht kopiert werden.
(the x-authorisation file could not be copied)"

...What might I do now to get it running normal again, not to talk about both of my monitors? ^^;

many thanks in advance

---

### Post by whizbaby on 2006-09-22
Before compiling you should have installed the package *linux-kernel-headers*. As to your xauth problem you would have to look in the howto you followed to see what changes to undo.

---

