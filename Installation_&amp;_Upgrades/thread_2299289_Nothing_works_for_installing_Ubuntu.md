---
title: "Nothing works for installing Ubuntu"
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by arendvanderkolk on 2015-10-17
Hi,

For 2 weeks i have tried installing Ubuntu (and other distros) on my new Acer R11 laptop and nothing works. I have included system info file in the attachment.

After running from live usb or live DVD I always get to the point where you are asked to install Ubuntu in the black screen. But after pressing "install" it never starts installing from there and the system stalls.

The main requirements i have done but still no luck. I am clueless.

- make sure you are installing 64-bit version (DONE)
- Go to your UEFI settings and disable SecureBoot (DONE)
- in Windows, disable Fast Startup (DONE)
- Make sure the computer is booting in UEFI mode (DONE)

Does anybody have an idea? I am getting completely frustrated (but never give up ofcourse, ;-))

At this point i dont care if i loose my Windows 8 OS i just want to install Ubuntu so i can continue my Python training.

Please Help!

---

### Post by Skaperen on 2015-10-17
i have, in the past, seen this happen when any disk has a large number of partitions.  i don't know if the installer still has that issue.  if you want to WIPE your hard drive you can try this command in a terminal on the live cd:

[B]WARNING TO OTHER READERS:  THIS IS A DANGEROUS COMMAND, YOU WILL LOSE ALL YOUR DATA IF YOU TRY IT!
[/B]

[COLOR="#FF0000"]dd if=/dev/zero ibs=1048576 obs=1048576 oflag=direct of=/dev/sda
[/COLOR]
type "sudo" in front of this command to actually run it like:

sudo dd ...

**WARNING TO OTHER READERS:  THIS IS A DANGEROUS COMMAND, YOU WILL LOSE ALL YOUR DATA IF YOU TRY IT!**

i don't know if this will solve your issue.  i can say that if i have nothing on the drive that needs to be saved (already did 2 final backups) i would try this.

this means you will need to partition the drive again (even if your real problem is different).  the installer will go through this.  you could partition it yourself before installing, if you wish.

i wonder if UEFI is an issue in this case.

---

### Post by arendvanderkolk on 2015-10-17
Hi Skaperen,

thx for your response but i have found my solution :p in the following thread as it was related to graphics:

[http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) (see the answer of Sudodus)

I added **acpi=off **and **nomod[B]eset **[/B]. So, one of the two helped to solve this. And since my Acer Aspire R11 is a touchpad screen i think it is the nomodeset option.

also read this thread:

======
[http://ubuntuforums.org/showthread.php?t=2298832](http://ubuntuforums.org/showthread.php?t=2298832)
Welcome to the Ubuntu Forums :smile:
I think you have problems with the nvidia graphics. Try the boot option **nomodeset**, and when it works (to bring you into a simpler graphics), you can install a proprietary driver for your nvidia card.
See this link: [Boot options]("http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808")
======

Moving on now finally, thx again for your input.

Arend

---

### Post by ajgreeny on 2015-10-17
Have you tried using the "Try Ubuntu before installing" option which will get you to a live desktop?

I have always done that to test hardware, and it may give you some clues to problems that may be stopping the installation.

EDIT:
I see you have now solved this problem.  Please use the **thread tools** menu above to mark as SOLVED.

---

