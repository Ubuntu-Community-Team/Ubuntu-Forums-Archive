---
title: "[SOLVED] How to install a new kernel?"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by L337_K3y5 on 2008-06-30
The kernel I'm about to install is the 2.6.25.9 version on [http://www.kernel.org/]("http://www.kernel.org/").  How do I install a new kernel?  Also, how do I revert back to my old version if I mess it up, or it doesn't work?  Also, one more thing, what does updating the kernel do to my files and programs on my distro.?

---

### Post by sdennie on 2008-06-30
Try this guide for a basic walkthrough of how to build/install a kernel for Ubuntu: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).  Installing a new custom kernel won't remove your old kernels and shouldn't effect your system in any other way.  If your custom kernel doesn't work right, your default Ubuntu kernels will still be available in grub when you boot.

---

### Post by L337_K3y5 on 2008-06-30
> **vor said:**
> If your custom kernel doesn't work right, your default Ubuntu kernels will still be available in grub when you boot.
Heh...heh...oh man, dang I've got my grub to where it shows only the recent versions of kernels and other operating systems, but thanks on the guide :).

---

### Post by L337_K3y5 on 2008-06-30
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-4.png[/IMG]
Ummm...I got to the part in the guide that showed how to install the kernel patch, and I get to the part above and it asks me if I want to overwrite the old patch?  What do I do now?  I want to keep the old patch for the old kernel, and keep it, but I also want to have the new patch for the new kernel.  I hope installing the new kernel won't mess up my wireless again...:(  Well, I'll just get on tomorrow and check the answers to see if it'll work.  Thanks!:D

---

### Post by L337_K3y5 on 2008-07-01
Well...does someone know how to help me in this situation? ^

---

### Post by sdennie on 2008-07-01
If you've got 2.6.25.9, you don't need to patch the kernel at all.  That's the latest stable kernel I believe.  You can skip the part about patching the kernel in the guide.

---

### Post by L337_K3y5 on 2008-07-01
Post here is unneeded.  *Just this one*

---

### Post by L337_K3y5 on 2008-07-01
Hey, I got this message after I got finished building the kernel and such.  What do I do now???:(:(:(

---

### Post by sdennie on 2008-07-01
That just means you closed vim uncleanly the last time you edited menu.lst.  Hit enter and then d.

---

### Post by L337_K3y5 on 2008-07-01
Ummm...am I supposed to still get the same message after I do what you said, cause I did it, exited out, and now every time I go into it using the same command line code, gives me the same error.:confused:

---

### Post by L337_K3y5 on 2008-07-01
Ummm...bad news, whenever I go into the new kernel, it brings up a list of things starting up, then after that, it goes to my login screen.  When I log in then, to either root or admin, it brings up a white screen, with the cursor, stays for about 10 seconds, then fails.  Also when I choose any kernel now, I have to click spacebar to continue cause it says my video something is 318 and it shows a list of res. to pick from...none of mine are on there, mine is 1280x800 32 bit.  This is crap, how do I do a reinstall of the new kernel, and if I have to remove it, how do I do that, this new kernel is a pain in the @$$, and its starting to get on my nerves.  Also btw, I can safely enter into any other kernels listed, but they too have the same unknown video 318 something, and I have to either choose a res. which btw makes it fail to load, or click spacebar to continue on, which works only on the older ones.

---

### Post by sdennie on 2008-07-01
For the older kernels, this is almost certainly related to the changes you were trying to make /boot/grub/menu.lst.  For the newer kernel, I'm not sure what the problem is.  

Building a new kernel is not really for the faint of heart and, the first few times you do it, you are likely to fail.  Eventually it becomes easy but, it's not something you are likely to get 100% right on the first try.

---

### Post by L337_K3y5 on 2008-07-01
K, well good to know I'm not the only one.  I'll just remove it from the grub list, but how do I do that so that I can make it back to just the others, basically how to I do a "uninstall" of the new kernel to indefinitely get rid of it?  I could remove it from the list myself, but if I set it back to show only the newest kernel, it would pop up the new one still, I want the one before it.

---

