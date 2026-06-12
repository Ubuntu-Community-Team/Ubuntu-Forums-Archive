---
title: "What kernel packages do i need?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by 12345 on 2007-06-23
Hi,

I am using Feisty with its default kernel. Now i would like to replace it completely with the new kernel b/c hardware problem.
What are the all kernel packages do i need? (I just need the name of them to download). Thanks

(PS. I have problem with the automatic security-update, that is why i have to install the packages manually.)

---

### Post by 5-HT on 2007-06-24
Which kernel are you currently using for Feisty (uname -r)? Apart from some backported security updates and bug fixes, Ubuntu kernels for a release will not be updated.

The current Feisty kernel is 2.6.20-16.29
If you are using the 'generic' kernel, the package is called linux-image-2.6.20-16-generic.
You could also install the linux-generic metapackage which depends on the most recent kernel.

If you want a newer kernel, you could try using the 2.6.22 release canadidate in Gutsy, but to avoid breakage it really would be best to just compile Gutsy's kernel sources for your system (or just grab the newest 22rc or stable kernel from kernel.org.)

NOTE: If you are using the restricted modules package, that will need to be updated as well (linux-restricted-modules-2.6.20-16-generic for the generic kernel. linux-restricted-modules-generic is a metapackage that will depend on the most recent restricted modules of the generic flavour).

cheers,

---

### Post by 12345 on 2007-06-24
I am using this one here:

~$ uname -r
2.6.20-15-generic

and based on your info i picked some packages:

linux-image-2.6.20-16-generic
linux-restricted-modules-2.6.20-16-generic
linux-restricted-modules-common
linux-headers-2.6.20-16
linux-headers-2.6.20-16-generic

Am i missing something? Thanks again!

best regards,

---

### Post by 5-HT on 2007-06-24
Nope :), you've got everything covered for the kernel & restricted modules.
You won't need the headers packages unless you'll be compiling stuff requiring the kernel C headers.


You can always install linux-image-generic & restricted-modules-generic if you want to pull in the newest kernel and restricted modules when they're released. You did mention something was up with your automatic updates though.

---

### Post by 12345 on 2007-06-24
Thank you 5-HT !
Everything works well now, my DVD has been correct recognized again :D
Last time i clicked on the orange icon for update, then it installed automatic something i dont know whatever i deleted them all later b/c it caused problem with the DVD. Later the orange icon does not show kernel update anymore and i dont know what to download #-o 
I will lock all these 5 new packages in synaptic. No more kernel updates for now. :p Thanks again for the usefull infos!

best regards,

---

