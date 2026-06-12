---
title: "[SOLVED] Reverting back to 2.6.22-14.38-rt kernel"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Nerdriot on 2008-02-04
Hello,

Today, after going through with the kernel update, several things just aren't functioning well anymore. There's just too many to list, so rather than whine about it, I'd like to ask for some help. :)

Can someone tell me how to go from the new kernel installed today (2.6.22-14.51) to the 2.6.22-14.38?

It updated both generics, and both rt kernels.

Thanks in advance for any help... this is getting frustrating... :(

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Enable the option *howmany=all* in grub's menu.lst and you should be able to boot from any kernel image you just have there on your hd :)

---

### Post by Nerdriot on 2008-02-04
Thank you one thousand times. If this works, then I owe you a kidney (or another thank you, whichever.)

:D

---

### Post by Nerdriot on 2008-02-04
Well, it worked for what it was supposed to do, but the reason it didn't fix my problem was because I was too vague, heh...

The update changed the headers and images to 2.6.22-14.51. When the headers and images were 2.6.22-14.38, they were working flawlessly. Now, I'm having random crashes, Audacity no longer plays back what I record into it, Jack no longer stays connected, Ardour no longer plays anything back, etc..

Is there a command I can use that will install the 2.6.22-14.38 headers and images?

Thanks in advance (again) :D

---

### Post by Odrodzona-Sarmacja on 2008-02-04
I think you could apt-get install it all... linux headers, images and restricted modules. Just not from synaptic. Try in terminal  "sudo apt-get install <linux-*>" every of these older files.

Also I think you should try enabling some of these unlocking old boot option or alternative boot options in menu.lst, if you didn't have yet.

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

Try enabling them all and see if it has any effect. If still you can boot your old .38 then go about installing the old images files in terminal.

---

### Post by Nerdriot on 2008-02-04
Thank you all for your help! I really appreciate you guys taking the time to respond.

I figured out the problem, however. After the kernel updates, my menu.list was updated, too. So it removed the small change I added into it, which was "noapic".

Once I added that back in, and rebooted, the problem was solved.

Thank you guys again, though. I really appreciate it. :)

---

