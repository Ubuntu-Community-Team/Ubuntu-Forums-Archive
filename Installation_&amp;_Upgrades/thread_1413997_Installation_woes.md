---
title: "Installation woes"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by santi_ on 2010-02-23
I have a box with a number of different distros and some spare disk, so I decided to give 9.10 a try. Part of having different distros is a backup system, hoping that not all disks/partitions can crash simultaneously(I do have external backups too)
Also, I mostly use Slack 13, so I want to add Ubuntu to  LILO manually.  I do ***not** want GRUB to overwrite the mbr, because I am not sure how to add the Slack vmlinuzes to grub(I have no experience with grub)

The problems: First, even when specifying the damn time zone, I get error messages and keep doing so for the next 5 screens. When it comes to checking existing partitions, it reverts back to the time zone screen, I fill all info info, next screen until last, shows a waitbox checking existing partitions, then back again, like an infinite loop. I should note, I did install Ubuntu with no problems from THE SAME CD on a friend's PC running Windows, no problem. It's embarassing to have problems in my case, where there is no Windows installation.

So, the issues are: a) what is wrong with these errors and b) can I tell the installer NOT to install grub?

---

### Post by darkod on 2010-02-23
I'm not sure about the errors but you can easily tell it not to install grub on the last screen of the installer. Before clicking Install, click on the Advanced button and you can deselect the bootloader.

For your information, I haven't tried it, but with the new grub2 that comes with 9.10 you don't need to know how to add kernels of other distros. In most cases it picks them up automatically, like it can pick up windows, and puts them in the grub menu.

---

### Post by tommcd on 2010-02-23
Sorry, but I am not sure about those time zone errors. You may want to try the Ubuntu alternate install CD to install Ubuntu. This is a text based installer that you may prefer (I do) since you are a Slacker. If you have ever installed Debian, the Ubuntu alternate install CD is almost the same as installing Debian:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
I don't know if this will fix the time zone difficulties, but it can't hurt to try it. 
For grub vs lilo:
I boot Slackware 13 64bit from grub2 in Ubuntu 9.10. Grub2 would not add an entry for Slackware 13 64bit simply by running:
```
sudo update-grub
```
Even with 32bit Slackware 13, the update-grub command does not manage to add the initrd line for Slackware so you can boot the generic kernel. The solution was to add a custom entry file for Slackware in the /etc/grub.d directory like this:
[https://wiki.ubuntu.com/Grub2#User-defined%20Entries](https://wiki.ubuntu.com/Grub2#User-defined%20Entries)
That whole tutorial if very good for getting to know grub2: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
And then run: "sudo update-grub".
I am not very familiar with lilo, as I have always booted Slack from grub. If you want to use lilo, then I would think that the best option would be to install Ubuntu's grub to the Ubuntu partition instead of the MBR, then chainload Ubuntu from lilo. For example, see post #4 in this thread:
[http://www.linuxquestions.org/questions/slackware-14/advice-for-lilo-setup-dual-boot-slackware-ubuntu-613632/](http://www.linuxquestions.org/questions/slackware-14/advice-for-lilo-setup-dual-boot-slackware-ubuntu-613632/)

---

