---
title: "boot loader and general issues"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by jmike1 on 2004-12-29
I have been planning to install linux as a second OS on my machine. Frankly, now that I am getting into it, I am having second thoughts as the process looks to be really difficult and risky. It is the information I am getting from the linux websites that lead me to this conclusion. A big problem is that you may need instruction that you can print out if to refer to if something goes wrong and most of the tutorials are in HTML on multiple pages making the whole tutorial a pain to print.
What makes it worse is that each tutorial refers to other documentation and most of the Linux documentation I am seeing is quite confusing. 
My big concern is with making sure the boot loader goes where I want it to and does not wipe out my MBR. I've heard that this can be a big problem with ubantu and that the ubantu installation insists on trying to put it on the MBR. Both the Lilo and grub manuals, not to mention the tutorial on this site don't give much direction for how to make sure the boot loader goes in the right place. In my case, I have 2 hard disks and want to put Linux on the second, which currently has nothing but trash on it. If I end up doing this at all. I also have Partition Magic and Boot Magic installed and want to use that, not a Linux program, to select the OS I boot to. I don't mind if Linux doesn't work 100%, I am actually pretty happy with Windows XP and have access to multiple linux and solaris systems for any Unix work. I'm just installing linux as an exercise. 
So basically I have my ubantu CD burned. Before I start I want to know for sure how to avoid wiping out my main boot record and make sure every thing goes on the 2nd disk. 
Also is there any where to get the installation manual in text or PDF or something besides HTML? There are links on the ubantu home site, but they are dead links.
Also, the second disk is currently formatted in FAT 32. From what I have read, it has been suggested although not actually stated, that I need to reformat it to the linux or FAT file systems. Am I understanding this correctly?

Thanks,
Mike

---

### Post by jmike1 on 2004-12-29
So does anybody have answers to my questions or should I just give up on linux for the time being?

---

### Post by eldrich_rebello on 2004-12-30
if you dont want to wipe out your mbr you'll have to boot into ubuntu with a floppy.
grub/lilo should be fine if you do install it to your MBR.detecting windows etc should be fine.
doing so will replace your 3rd party boot loader.i'd go with a linux loader/ie lilo/grub
make/resize your partition on your 2nd HDD.to make room for ubuntu and install the os there.the partition manager will do the rest for you.(from the ubuntu installer,not partition magic)

---

### Post by jmike1 on 2004-12-30
eldrich_rebello

Thanks for the response, but I really don't like the idea of using grub as my main bootloader. From what others on this forum area have written, that can be really dangerous and make it impossible to boot to Windows XP. I've read the grub manual and it looks pretty difficult to use. I have a very stable system right now that does everything I need it to do perfectly and don't want to risk screwing it up just for an experiment.
But thanks again for at least trying to help and please accept my condolences on the recent tragedy to hit your part of the world. I hope that you and your loved ones are making it through OK.

Mike

---

### Post by alpha on 2004-12-30
Just a little note here, I think you should be a little more patient when waiting for answers, patience is a virtue.

---

### Post by eldrich_rebello on 2004-12-31
hi.the tsunami did'nt hit bombay(west coast of india).no probs there.
about not detecting windows,i think that's what grub does best.detecting existing windows partitions.should work fine.if you're apprehensive,give it a go on a test pc,someone who's willing to risk it,though i think it'll go fine

---

