---
title: "Updated Feisty -&gt; Gutsy and got stuck  with  kernel 2.6.20-16 (instead of 2.6.22-14)"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by guido_damico on 2008-01-03
Hello,
on one system of mine I upgraded to Gutsy from Fiesty and noticed that the kernel was left at the old 2.6.20-16-generic.

I do not understand how that was possible, but since I saw on the update-manager that the new kernel was available I thought to install it.

The update failed with an error similar to [_this one_]("http://www.linuxquestions.org/questions/linux-software-2/failed-to-symbolic-link-bootinitrd.img-2.6.18-4-486-to-initrd.img-556239/") ("[FONT="Courier New"]Failed to symbolic-link boot/initrd.img-2.6.18-4-486 to initrd.img[/FONT]" and some symlinks created in / instead of in [FONT="Courier New"]/boot[/FONT]), the only difference was the version number. I removed the symlinks from / and checked from SUM (Start-Up Manager) that the new kernel is listed in GRUB's options, hoping that would get the new kernel in.

Unfortunately this procedure left me with a setup that does not have any [FONT="Courier New"]initrd.img-2.6.22-14-generic[/FONT] file anywhere in my FS.

So now I can run a sort of *dumbed-down* version of Gutsy with the old kernel: it works, but is not where I'd like to be.

Re-installing the [FONT=Courier New"]linux-image*[/FONT] or [FONT=Courier New"]linux-generic[/FONT] packages did not lead to a valid configuration: I either get nothing changed, or just few more symlinks created in the root directory (among which one pointing to the infamous non-existing [FONT="Courier New"]initrd.img-2.6.22-14-generic[/FONT] file).

Any suggestion on how to get to 2.6.22?

Thank you,
Guido

---

