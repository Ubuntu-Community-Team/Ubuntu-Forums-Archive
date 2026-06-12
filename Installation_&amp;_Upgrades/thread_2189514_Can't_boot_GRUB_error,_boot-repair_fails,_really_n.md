---
title: "Can't boot GRUB error, boot-repair fails, really need help"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by n.rjlawrance on 2013-11-22
I am an Ubuntu noob. I have had a problem trying to restore a dual-boot Windows 7 / Ubuntu 30.04 installation. The computer had Windows 7 installed for about a year. Three days ago I installed the secure-remix of Ubuntu 13.04 (successfully). Yesterday When I rebooted (no significant changes that I know of) grub said it couldn't access normal.mod (as in: [http://askubuntu.com/questions/325839/file-error-boot-grub-i386-pc-normal-mod-trying-to-repair-boot-live-dvd-install](http://askubuntu.com/questions/325839/file-error-boot-grub-i386-pc-normal-mod-trying-to-repair-boot-live-dvd-install))

I booted from a live CD and attempted to use boot-repair. It fails with the error "Please enable a repository containing the [linux] packages in the software sources of Linux-Secure-Remix-64bit 20may2013 (sda5). Then try again." (record here [http://paste.ubuntu.com/6457960/](http://paste.ubuntu.com/6457960/))
I tried to add all the repository sources but boot-repair still seems to fail. I would like to know, is it just that it can't access a required repository or is something else wrong? Do I need to reinstall Ubuntu? I think that the secure remix includes clean-ubiquity which backs up my MBR, but not sure what I can do with that.

Thanks for the help, it is really appreciated as this is my work computer and I have work I really need to do :)

---

### Post by oldfred on 2013-11-22
All your secure remix is, is Standard Ubuntu with Boot-Repair built in.

Not sure if either your install never was correct, or if software sources has a line or two that are corrupted so it does not process or if you did not have Internet so it could not run.

But you do not now have grub.cfg, kernels and maybe not a good sources.list, All could be fixed with a good chroot and updates to reinstall kernel & grub if sources.list works and Internet works.

Boot-Repair can help you chroot into your system.
It shows your sources.list starting at line 753, but at end line 808, I cannot tell if the errors are in file or after it. The end also looks correct, otherwise, so I am not sure why the errors?

your sources list is here
/etc/apt/sources.list

If in a working install, but if chrooted you many have added mount path in front of /etc. Not sure how Boot-Repair does it.
gksudo gedit  /etc/apt/sources.list

---

### Post by n.rjlawrance on 2013-11-23
Thanks for the help, I have tried to follow instructions such as those  listed here  ([http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)).  However, when I tried to issue this command "sudo chroot /mnt", I get the  error 'chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or  directory'[URL="http://opensource-sidh.blogspot.com.au/2011/06/recover-grub-live-ubuntu-cd-pendrive.html"]
[/URL]In the end I decided to uninstall and reinstall. It worked, but not exactly as I'd hoped. Thanks very much [IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]for the help though, it was genuinely appreciated.

---

