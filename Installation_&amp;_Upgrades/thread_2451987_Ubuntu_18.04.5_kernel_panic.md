---
title: "Ubuntu 18.04.5 kernel panic"
date: 2020-10-14
forum: Installation &amp; Upgrades
---

### Post by nunosempere on 2020-10-14
Hi,

My Ubuntu installation goes to a purple screen, perhaps after I upgraded some packages yesterday. I get a "kernel panic not syncing no init found try passing init option to kernel" error, and boot-repair doesn't work; the pastebin it produces is here: [URL="http://paste.ubuntu.com/p/WJPp7npqKR/"]http://paste.ubuntu.com/p/WJPp7npqKR/
[/URL] 
I've googled around and tried various things. I've tried adding the nomodeset option to the kernel boot options, but this didn't work, so I reverted the change. I found the utility testdisk: [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix), but it hasn't proved useful, it tries to create an image.dd file which is too big for the USB I'm booting from.

It's also not clear to me how I should "pass the init option to the kernel; when I google the error I get the following pages, which don't solve my confusion: [https://stackoverflow.com/questions/50349253/kernel-panic-no-working-init-found-try-passing-init-option-to-kernel](https://stackoverflow.com/questions/50349253/kernel-panic-no-working-init-found-try-passing-init-option-to-kernel), [https://askubuntu.com/questions/362437/kernel-panic-not-syncing-no-init-found-try-passing-init-option-to-kernel](https://askubuntu.com/questions/362437/kernel-panic-not-syncing-no-init-found-try-passing-init-option-to-kernel), [https://www.linuxquestions.org/questions/linux-general-1/what-does-try-passing-init%3D%5C-option-to-kernel-mean-180473/](https://www.linuxquestions.org/questions/linux-general-1/what-does-try-passing-init%3D%5C-option-to-kernel-mean-180473/)

Any thoughts as to what I can do next? I have a good backup system with everything up to yesterday, so I'm also ok, but would be mildly inconvenienced by "nuke it from orbit" solution.

Note: My computer also has a Windows installation which doesn't work but which I don't care much about.

---

### Post by CelticWarrior on 2020-10-14
> [COLOR=#000000][INDENT]Note: My computer also has a Windows installation which doesn't work but which I don't care much about.[/INDENT]


[/COLOR]

I would say thatb alone is a very good reason to reinstall and use Ubuntu only. ;)


Regarding your problem please do not complicate things. Boot Repair and the other tool are NOT intended for this.
Simply try booting from an older kernel using the advance options in Grub menu, post results. We troubleshoot from there.

---

### Post by ajgreeny on 2020-10-14
I'm inclined to agree with CW but if that is unacceptable  to you try booting to a live ubuntu system then run terminal command ```
sudo e2fsck /dev/sdx#
```where sdx# is the root paertition of your failing ubuntu system.

---

### Post by hexform on 2020-10-15
I'm having the same issue right now. I can't even boot in via bootable USB. It just goes to Kernel Panic after displaying the purple screen for a few seconds.

---

### Post by CelticWarrior on 2020-10-15
@hexform

Not the same issue. Please open your own thread.

---

