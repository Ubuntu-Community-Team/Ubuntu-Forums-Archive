---
title: "Boot issue after updating GLIBC"
date: 2024-02-14
forum: Installation &amp; Upgrades
---

### Post by sean940128 on 2024-02-14
[COLOR=#000000]So i was installing some packages and a message popped up: "version `GLIBC_2.32' not found". After troubleshooting a while, i found that it's due to my Ubuntu20.04 LTS's highest version of GLIBC is 2.30. Then i tried following 2 methods:[/COLOR]

[COLOR=#000000]# first method (update the version)[/COLOR]
[COLOR=#000000]$ tar xzvf glibc-2.32.tar.gz[/COLOR]
[COLOR=#000000]$ cd glibc-2.32/[/COLOR]
[COLOR=#000000]$ mkdir build[/COLOR]
[COLOR=#000000]$ cd build[/COLOR]
[COLOR=#000000]$ ../configure -prefix=/usr -disable-profile -enable-add-ons -with-headers=/usr/include -with-binutils=/usr/bin[/COLOR]
[COLOR=#000000]$ tar xvzf gawk-4.1.4.tar.gz[/COLOR]
[COLOR=#000000]$ cd gawk-4.1.4/[/COLOR]
[COLOR=#000000]$ ./configure[/COLOR]
[COLOR=#000000]$ make[/COLOR]
[COLOR=#000000]$ sudo make install[/COLOR]
[COLOR=#000000]$ export LD_LIBRARY_PATH=[/COLOR]
[COLOR=#000000]$ sudo rm /lib64/libm.so.6[/COLOR]
[COLOR=#000000]$ sudo ln -s $HOME/download/glibc-2.27/build/math/libm.so.6 /lib64/libm.so.6[/COLOR]


[COLOR=#000000]# second method (first one didn't resolve the problem so i tried this one)[/COLOR]
[COLOR=#000000]$ sudo vi /etc/apt/sources.list[/COLOR]
[COLOR=#000000]deb [/COLOR][http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu)[COLOR=#000000] jammy main[/COLOR]
[COLOR=#000000]$ sudo apt update[/COLOR]
[COLOR=#000000]$ sudo apt install libc6[/COLOR]

[COLOR=#000000]Half way of the installation the system crashed, so i had to force reboot my pc. Ever since no matter which kernel i boot with i have following error message as shown in the figure.[/COLOR]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293413&stc=1[/IMG]

[COLOR=#000000]It indicates that [end Kernel panic - not syncing: Attemped to kill init! exitcode=0x00000100]. Right now im trying to repair this by using boot-repair on a live-usb. The suggested repair is as following:[/COLOR]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293414&stc=1[/IMG]

[COLOR=#000000]Is this the correct way to repair it? Please help. Thank you very much.[/COLOR]

---

### Post by MAFoElffen on 2024-02-17
Did you have a backup done before trying something risky? Which, besides doing a backup routinely... Doing a backup rior to doing something that is not recommended, and will probably break your system would be one those times that it would be almost a requirement to have a fallback point to.

The glibc library is tied into so many things... that when got got that message in the first version error, I would have stopped and evaluated whether you needed that application you installed that threw that error, or evaluated whether you needed to upgrade your Ubuntu release to Jammy 22.04. Mxing the glib version on that foundation (Focal 20.04) is what broke it.

Too late now.

I feel that you have two options:

Option #1) Do a non-destructive re-install of 20.04 over your current install. I can post a link to a good explanation of how to do that.

Option #2) Boot from an Installer LiveUSB, chroot into the existing installed OS, and while using the Jammy sources.list still active, do a manual Debian Release Upgrade to finish converting it to 22.04.3.

Each comes with it's risks. Before either option, "NOW" would be a good time to do a backup, so that this time you do have a fall-back point to go back to.

---

### Post by sean940128 on 2024-02-19
Thank you for your kind reply, @MAFoElffen. I've tried so many possible methods to fix this but none worked. I should have just installed any previous version of that package which brings up the error message. And sadly I have no any fallback points I can restore with after the system is messed up. Yeah I learned this the hard way lol. Now I'll just reinstall my whole system i guess. And I'll surely do backups routinely. Thank you very much sir!

---

### Post by ActionParsnip on 2024-02-19
Could try a chroot from Live USB / CD to see if you can revive the boot

---

### Post by MAFoElffen on 2024-02-19
> **ActionParsnip said:**
> Could try a chroot from Live USB / CD to see if you can revive the boot
You could try, though (I know) the kernel series depends on the version of the glibc versions. It provides the core libraries for the GNU system and GNU/Linux systems, as well as many other systems that use Linux as the kernel.

He built glibc from the source package, which means he would have to successfully rebuild the source package again with the version it had or maybe a bit higher... From a chroot. With no garrantees that it would work. 

For example, this person with 18.04:
[https://stackoverflow.com/questions/72513993/how-to-install-glibc-2-29-or-higher-in-ubuntu-18-04](https://stackoverflow.com/questions/72513993/how-to-install-glibc-2-29-or-higher-in-ubuntu-18-04)

---

### Post by sean940128 on 2024-02-20
Thanks for the advice, I tried "chroot", "sudo chroot" but I got error messages. After playing around for a while, now I cannot even boot with the live usb...(unable to find a medium containing a live file system). I'm just an os killer or what. So frustrated lol... Fortunately, all my files are saved on another usb so i can proceed to re-install the system. Thank you guys for the help. Really appreciate it.

---

### Post by guiverc on 2024-02-20
> **sean940128 said:**
> After playing around for a while, now I cannot even boot with the live usb...(unable to find a medium containing a live file system). 

If you boot a 20.04 or newer system, the install media will be checked; and the message *unable to find a medium containing *just indicates it cannot find the media to check, meaning your media is corrupted, and it may have offered to download an ISO for you to attempt install from what is downloaded.

I'll suggest you return to validating the ISO you downloaded is correct ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) or writing it again (*in my experience its the write that is faulty most of the time; USB thumb-drives are cheap consumables and low price matters more than quality*)

To me, that message is only evidence of a faulty ISO or bad write of ISO to flash media.

As to your actual problem...  My 2c opinion.

In your case I'd do a *non-destructive* re-install which is one option MAFoElffen suggests, esp. if you're using a Desktop system (*its less ideal for Server installs; but ensure you have backups first regardless*).

if using a desktop, I've written an answer on another site, and I'll provide a link [here]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533").

Whilst I don't know what actual damage you've done, I'd probably explore what appears in /var/log/apt/history.log and review what it said was being upgraded.. and it maybe fixable.. and I may actually try correcting that first if it was my system; the non-destructive install (*assuming desktop install*) is what I'd expect to bail me out.

I'd avoid changing core package/libraries where you can... and if you need to try, attempt the change(s) first on a test or virtual machine and not an install you value.

*FYI:  the link I provided says up to 22.10 because that was the latest stable release at the time I wrote that answer..  If I wrote it today it would say 23.10.*

---

### Post by ActionParsnip on 2024-02-20
Simply running
```

sudo chroot

```
is not how you chroot, in case you thought it was that simple. You need to mount file systems and so on, then chroot into the mount point. You didn't expand your reply to more than "I ran sudo chroot" and I assume nothing

---

