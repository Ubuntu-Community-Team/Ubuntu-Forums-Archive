---
title: "Vista Booted --&gt; Killed Grub. Complete Re-install of Grub?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by prepstyles on 2007-12-17
I've been looking around, my apologies if this has been asked before.

I installed Ubuntu 7.10 64 bit on my girlfriends new ASUS F3 Series Laptop: 
The machine came with: A restore partition, Vista's partition, A Data partition.
I used the 7.10 Live CD to resize the Data partition then carved out a partition for / and swap.

Grub auto configured and installed (like usual).

On first boot Gurb menu comes up and Ubuntu boots - no problem.

I got Ubuntu configured the way I wanted.

Then I reboot and ran Vista from Grub Menu ... Here it comes now ...

After the Vista intro screen with the progress bar I get a screen with HUGE off centered RED BOLD text that says ERROR the computer then restarts and then Grub menu comes up and says "error 22".

What I think happened was Vista started up and realized the partition sizes weren't what it expected and it wrote some garbage into the MBR and killed Grub.

So .... I Burned a Super Grub CD and tried to recover Grub... Almost nothing worked; not fix Linux MBR, not fix Windows MBR, not Boot Windows, not Boot Linux, everything said "partition not found", or "file not found" the only thing that looked like it did work was a removal of Grub.

Then I managed to get into the Vista recovery options and restore Vista's boot options ... so Vista works again....

So I would like to reinstall Grub (now that I figure Vista has reconciled the partition sizes) but everything I've seen tries to restore Grub hasn't worked because none of the files were found .. also like I said I think the uninstall of Grub went through.

If any other info would be useful don't' hesitate to let me know.

I'd greatly appreciate any help.

Cheers!

---

### Post by logos34 on 2007-12-17
I don't run vista (x64 ubuntu studio/x64 xp pro dual booter here) but my advice is don't push your luck--use the vista boot manager to boot linux instead.  EasyBCD is what you want to try next:
 
[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

You'll reinstall grub but to the ubuntu root partition.

---

### Post by prepstyles on 2007-12-18
> I don't run vista (x64 ubuntu studio/x64 xp pro dual booter here) but my advice is don't push your luck--use the vista boot manager to boot linux instead. EasyBCD is what you want to try next:

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

You'll reinstall grub but to the ubuntu root partition. 

I acutally stumbled across EBCD a few hours ago thanks for the advice ...

It looks like that did the trick ... although I had to reinstall Ubuntu 3 times before I placed Grub in the Linux partition correctly ... the UI for that in the installer needs to be a lot clearer :mad: .... talk about time consuming....

Everything looks good now.

Thanks for the reply logos34.

Cheers!

---

