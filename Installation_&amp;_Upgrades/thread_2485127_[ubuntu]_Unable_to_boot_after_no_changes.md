---
title: "[ubuntu] Unable to boot after no changes"
date: 2023-03-20
forum: Installation &amp; Upgrades
---

### Post by marhan on 2023-03-20
Can't boot after doing nothing

Hi everyone, I hope you're spending a happy day, I just ran into this problem at work today : I was working on Ubuntu 22.04 on a Python script among other things such as reading proprietary doc, but normally none of these actions changed anything for the system itself and I didn't update or upgrade anything. And after shutting down my machine with "sudo shutdown now" I wasn't able to boot, and where the logs normally display "unable to run on non-dell system" before showing the Ubuntu loading wheel, a new line appeared, saying "Failed to start: Set the console layout", after that the loading wheel and Ubuntu logo appears and it can't go further. The wheel is spinning indefinitely. Then I tried to boot in recovery mode, and the boot stops on "overlayfs : missing "lowerdir "
Usci_api USBC000:00: failed to reset PPM! 
Usci_api USBC000:00: PPM in it failed (-110)

I don't really understand since nothing is supposed to have changed in the system files... If someone has an idea, it would be really helpful since I need to boot my pc to work - _-'
Have a good day!

---

### Post by MAFoElffen on 2023-03-21
What version and Edition of Ubuntu is this? 

What may be in need is to mount and chroot into the system from a LiveCD and check the disk space. Saving that Python Script may had been the last straw if space was tight... That is what I am thinking. Usually that error is about low space in the filesystem.

---

