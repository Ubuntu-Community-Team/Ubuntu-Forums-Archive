---
title: "Kernel upgrade 12.04"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by pycoed on 2013-09-09
[SIZE=2]I am having problems with a failing kernel upgrade &  I can't find a previous answered post that matches my symptoms, so please could someone help?
Update manager returns the following details:[/SIZE]

```
installArchives() failed: Setting up linux-image-3.2.0-53-generic (3.2.0-53.81) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
[COLOR=#ff0000]Generating grub.cfg ...[/COLOR]
[COLOR=#ff0000]Found background: /etc/apt/sources.list[/COLOR]
[COLOR=#ff0000]Unsupported image format[/COLOR]
[COLOR=#ff0000]run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1[/COLOR]
[COLOR=#ff0000]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-53-generic.postinst line 1010.[/COLOR]
[COLOR=#ff0000]dpkg: error processing linux-image-3.2.0-53-generic (--configure):[/COLOR]
[COLOR=#ff0000] subprocess installed post-installation script returned error exit status 2[/COLOR]
[SIZE=3][COLOR=#ff0000]<REPEATS FOR 3.2.0-53 up to 3.5.0-40>[/COLOR][/SIZE]
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-3.2.0-53-generic
 linux-image-3.5.0-39-generic
 linux-image-3.5.0-40-generic
 linux-image-generic-lts-quantal
 linux-generic-lts-quantal
 linux-image-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB


Total disk space freed by localepurge: 0 KiB


localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB


Total disk space freed by localepurge: 0 KiB


localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB


Total disk space freed by localepurge: 0 KiB


localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB


Total disk space freed by localepurge: 0 KiB


Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up linux-image-3.5.0-39-generic (3.5.0-39.60~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-39-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-39-generic /boot/vmlinuz-3.5.0-39-generic
Generating grub.cfg ...
Found background: /etc/apt/sources.list
Unsupported image format
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-53-generic (3.2.0-53.81) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-53-generic /boot/vmlinuz-3.2.0-53-generic
Generating grub.cfg ...
Found background: /etc/apt/sources.list
Unsupported image format
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-53-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-39-generic; however:
  Package linux-image-3.5.0-39-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.5.0-40-generic (3.5.0-40.62~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-40-generic /boot/vmlinuz-3.5.0-40-generic
Generating grub.cfg ...
Found background: /etc/apt/sources.list
Unsupported image format
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-40-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-53-generic; however:
  Package linux-image-3.2.0-53-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
```

[SIZE=2]
Could someone please explain the meaning of the red highlighted lines above & what I can do to remedy the situation?

[/SIZE]

---

### Post by MrAli on 2013-09-10
maybe following command will solve your problem:
```

sudo apt-get install --install-recommends xserver-xorg-lts-raring
sudo dpkg-reconfigure xserver-xorg-lts-raring

```

---

### Post by pycoed on 2013-09-10
Tried that but problem still remains. Any idea what the error reports mean?

---

### Post by pycoed on 2013-09-10
[SIZE=2]Still don't know what the problem was, but the following from askubuntu forums seems to have fixed it:-[/SIZE]


[COLOR=#333333][FONT=UbuntuRegular][TABLE]
[TR="bgcolor: transparent"]
[TD="class: answercell, bgcolor: transparent"]The packages causing all this trouble are initramfs-tools and initramfs-tools-bin. Their versions are 0.99ubuntu13 in [precise]("http://packages.ubuntu.com/precise/initramfs-tools") repository and 0.99ubuntu13.1 in [precise-updates]("http://packages.ubuntu.com/precise-updates/initramfs-tools") repository. Somehow the package lists are in a inconsistent state making apt trying to install one version from each repository.
Remove the package lists:
sudo rm /var/cache/apt/*.bin /var/lib/apt/lists/* /var/lib/apt/lists/partial/*
Then run apt-get update to download new package lists, then try apt-get -f install again.

[TABLE="class: fw, width: 656"]
[TR="bgcolor: transparent"]
[TD="class: vt, bgcolor: transparent"][share]("http://askubuntu.com/a/264341")[COLOR=#1B4072][/COLOR][improve this answer]("http://askubuntu.com/posts/264341/edit")
[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"]answered Mar 5 at 16:20
[URL="http://askubuntu.com/users/65926/eric-carvalho"][CENTER][IMG]http://i.stack.imgur.com/cxbjN.png?s=32&g=1[/IMG][/CENTER]
[/URL]
[COLOR=#888888][Eric Carvalho]("http://askubuntu.com/users/65926/eric-carvalho")
[COLOR=#444444]**10.3k**[/COLOR][COLOR=#444444]10[/COLOR][COLOR=#444444]22[/COLOR][COLOR=#444444]41[/COLOR][/COLOR]

[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][/TD]
[TD="bgcolor: transparent"][COLOR=#444444][TABLE="width: 660"]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]It seems to be hanging a bit on: Found memtest86+ image: /boot/memtest86+.bin. How long is it supposed to stay on that message? &#8211; [Simianspaceman]("http://askubuntu.com/users/137800/simianspaceman") [COLOR=#999999][Mar 5 at 18:20]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment330899_264341")[/COLOR]
[/TD]
[/TR]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]It shold be fast. What's the output of apt-get -f install? &#8211; [Eric Carvalho]("http://askubuntu.com/users/65926/eric-carvalho") [COLOR=#999999][Mar 5 at 19:43]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment330938_264341")[/COLOR]
[/TD]
[/TR]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]it would hang at at all messages that contained boot/memtest86+.bin. In this case it was solved by repeated purging and updating. But removing the lists directory seemed to help. It was ultimately a mix of the two methods. &#8211; [Simianspaceman]("http://askubuntu.com/users/137800/simianspaceman") [COLOR=#999999][Mar 15 at 21:46]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment336203_264341")[/COLOR]
[/TD]
[/TR]
[/TABLE]
[/COLOR]
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular][TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER]up vote[COLOR=#777777]0[/COLOR]down vote[/CENTER]
[/TD]
[TD="class: answercell, bgcolor: transparent"]This helped me in solving the issue:
sudo apt-get remove grub*
followed by
sudo apt-get update && sudo apt-get upgrade
Hope this helps you too.
Automatic translation from [the original answer in Spanish]("http://askubuntu.com/revisions/318198/1").

[TABLE="class: fw, width: 656"]
[TR="bgcolor: transparent"]
[TD="class: vt, bgcolor: transparent"][share]("http://askubuntu.com/a/318198")[COLOR=#1B4072][/COLOR][improve this answer]("http://askubuntu.com/posts/318198/edit")
[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"][edited Jul 9 at 16:03]("http://askubuntu.com/posts/318198/revisions")
[URL="http://askubuntu.com/users/88802/gertvdijk"][IMG]https://www.gravatar.com/avatar/64f1a286bd174de3b0b3d2d056a7793e?s=32&d=identicon&r=PG[/IMG]
[/URL]
[COLOR=#888888][gertvdijk]("http://askubuntu.com/users/88802/gertvdijk")
[COLOR=#444444]**16.8k**[/COLOR][COLOR=#444444]5[/COLOR][COLOR=#444444]32[/COLOR][COLOR=#444444]74[/COLOR][/COLOR]

[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"]answered Jul 9 at 15:59
[URL="http://askubuntu.com/users/173834/olive-valpo"][IMG]https://www.gravatar.com/avatar/290d9decea4d1735a0a973a67d309b7e?s=32&d=identicon&r=PG[/IMG]
[/URL]
[COLOR=#888888][olive valpo]("http://askubuntu.com/users/173834/olive-valpo")
[COLOR=#444444]**1**[/COLOR][/COLOR]

[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by pycoed on 2013-09-10
[SIZE=2]Still don't know what the problem was, but the following from askubuntu forums seems to have fixed it:-[/SIZE]


[COLOR=#333333][FONT=UbuntuRegular][TABLE]
[TR="bgcolor: transparent"]
[TD="class: answercell, bgcolor: transparent"]The packages causing all this trouble are initramfs-tools and initramfs-tools-bin. Their versions are 0.99ubuntu13 in [precise]("http://packages.ubuntu.com/precise/initramfs-tools") repository and 0.99ubuntu13.1 in [precise-updates]("http://packages.ubuntu.com/precise-updates/initramfs-tools") repository. Somehow the package lists are in a inconsistent state making apt trying to install one version from each repository.
Remove the package lists:
[COLOR=#ff0000]sudo rm /var/cache/apt/*.bin /var/lib/apt/lists/* /var/lib/apt/lists/partial/*[/COLOR]
Then run [COLOR=#ff0000]apt-get update[/COLOR] to download new package lists, then try [COLOR=#ff0000]apt-get -f install[/COLOR] again.

[TABLE="class: fw, width: 656"]
[TR="bgcolor: transparent"]
[TD="class: vt, bgcolor: transparent"][share]("http://askubuntu.com/a/264341")[improve this answer]("http://askubuntu.com/posts/264341/edit")[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"]answered Mar 5 at 16:20
[URL="http://askubuntu.com/users/65926/eric-carvalho"][CENTER][IMG]http://i.stack.imgur.com/cxbjN.png?s=32&g=1[/IMG][/CENTER]
[/URL]
[COLOR=#888888][Eric Carvalho]("http://askubuntu.com/users/65926/eric-carvalho")
[COLOR=#444444]**10.3k**[/COLOR][COLOR=#444444]10[/COLOR][COLOR=#444444]22[/COLOR][COLOR=#444444]41[/COLOR][/COLOR]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][/TD]
[TD="bgcolor: transparent"][COLOR=#444444][TABLE="width: 660"]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]It seems to be hanging a bit on: Found memtest86+ image: /boot/memtest86+.bin. How long is it supposed to stay on that message? – [Simianspaceman]("http://askubuntu.com/users/137800/simianspaceman") [COLOR=#999999][Mar 5 at 18:20]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment330899_264341")[/COLOR][/TD]
[/TR]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]It shold be fast. What's the output of apt-get -f install? – [Eric Carvalho]("http://askubuntu.com/users/65926/eric-carvalho") [COLOR=#999999][Mar 5 at 19:43]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment330938_264341")[/COLOR][/TD]
[/TR]
[TR="class: comment, bgcolor: transparent"]
[TD="bgcolor: transparent"][/TD]
[TD="class: comment-text, bgcolor: transparent"]it would hang at at all messages that contained boot/memtest86+.bin. In this case it was solved by repeated purging and updating. But removing the lists directory seemed to help. It was ultimately a mix of the two methods. – [Simianspaceman]("http://askubuntu.com/users/137800/simianspaceman") [COLOR=#999999][Mar 15 at 21:46]("http://askubuntu.com/questions/264331/failed-kernel-install-results-in-apt-and-dpkg-failure-due-to-dependencies-and-co#comment336203_264341")[/COLOR][/TD]
[/TR]
[/TABLE]
[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER]up vote[COLOR=#777777]0[/COLOR]down vote[/CENTER]
[/TD]
[TD="class: answercell, bgcolor: transparent"]This helped me in solving the issue:
[COLOR=#ff0000]sudo apt-get remove grub*[/COLOR]
followed by
[COLOR=#ff0000]sudo apt-get update && sudo apt-get upgrade[/COLOR]
Hope this helps you too.
Automatic translation from [the original answer in Spanish]("http://askubuntu.com/revisions/318198/1").

[TABLE="class: fw, width: 656"]
[TR="bgcolor: transparent"]
[TD="class: vt, bgcolor: transparent"][share]("http://askubuntu.com/a/318198")[improve this answer]("http://askubuntu.com/posts/318198/edit")[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"][edited Jul 9 at 16:03]("http://askubuntu.com/posts/318198/revisions")
[URL="http://askubuntu.com/users/88802/gertvdijk"][IMG]https://www.gravatar.com/avatar/64f1a286bd174de3b0b3d2d056a7793e?s=32&d=identicon&r=PG[/IMG]
[/URL]
[COLOR=#888888][gertvdijk]("http://askubuntu.com/users/88802/gertvdijk")
[COLOR=#444444]**16.8k**[/COLOR][COLOR=#444444]5[/COLOR][COLOR=#444444]32[/COLOR][COLOR=#444444]74[/COLOR][/COLOR]
[/TD]
[TD="class: post-signature, bgcolor: transparent, align: right"]answered Jul 9 at 15:59
[URL="http://askubuntu.com/users/173834/olive-valpo"][IMG]https://www.gravatar.com/avatar/290d9decea4d1735a0a973a67d309b7e?s=32&d=identicon&r=PG[/IMG]
[/URL]
[COLOR=#888888][olive valpo]("http://askubuntu.com/users/173834/olive-valpo")
[COLOR=#444444]**1**[/COLOR][/COLOR]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-09-11
The answer posted on Jul 9 at 15.59 seems a bit weird to me. How can removing Grub solve the problem? True you will not see the error messages because they appeared as the Grub configuration files were being updated. But would the system still boot? The two commands that followed would not have reinstalled Grub.

Regards.

---

### Post by pycoed on 2013-09-11
[SIZE=2]System boots OK, & reports upgrades as current?? Everything seems OK but I now have a Grub screen appearing on boot that I didn't before (12.04 is the only OS on this disk). 
So... I installed Grub Customizer  to try to suppress the view & that now reports :-

[/SIZE][SIZE=2][COLOR=#ff0000][SIZE=1]
grub-mkconfig couldn't be executed successfully. error message[/SIZE]:
[/COLOR][/SIZE][SIZE=1][COLOR=#FF0000] [SIZE=1]Generating grub.cfg ...[/SIZE][/COLOR][/SIZE]
[SIZE=1][COLOR=#ff0000]Found background: /etc/apt/sources.list[/COLOR][/SIZE]
[COLOR=#ff0000][SIZE=1]Unsupported image format[/SIZE]

[/COLOR][COLOR=#000000][SIZE=2]Which was also one of the errors shown in my original post, so it seems the problem IS with Grub & it's still there! Knowing nothing of Grub, this seems to suggest to me that it is finding my list of repositories where it expects to find a background image? Hence the "unsupported image format" report.
[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]Any idea how I might fix that?[/SIZE][/COLOR][COLOR=#ff0000]
[SIZE=2][/SIZE]

[/COLOR][COLOR=#000000][/COLOR]

---

### Post by antiplex on 2013-09-16
the OP's error-log indeed seems weird as grub seems to try to use the repository list (/etc/apt/sources.list) as a background image which makes absolutely no sense to me.
pycoed, do you recall ever having tampered with /boot/grub/grub.cfg or /etc/default/grub? could you share those files contents with us?
a listing of all files present in /boot/grub might also help.

note that i'm by no means an expert in grub issues, i've just come across this thread while experiencing problems (probably of a very different sort) after upgrading to kernel 3.2.0-53.81, but in my case something went berserk with my boot-partition which became unmountable.

---

### Post by bapoumba on 2013-09-16
So I'm going to have maybe two dumb questions :
- would you be using any splash image for grub ? From the error message, the wrong image format may relate to a real image and not a kernel image (i said dumb question :))
- I see some precise and some quantal references in the OP error message. What is your sources.list : **cat /etc/apt/sources.list**

---

### Post by antiplex on 2013-09-17
> **bapoumba said:**
> ... - I see some precise and some quantal references in the OP error message.
my guess is that the OP installed a newer kerner (from quantal -> 3.5.0-40) that is available in the default 12.04 repos for LTS-reasons.
by the way, since end of august there are also the 3.8 kernel-backports of raring available for 12.04 in the packages *linux-image-generic-lts-raring* and *linux-headers-generic-lts-raring* but that would probably not solve the grub issue he has ;)
to find out if the quantal kernel package is installed issue ```
dpkg -l | grep linux-image-generic-lts
``` in your terminal. if the output (if any) starts with ```
ii  linux-image-generic-lts-quantal
``` this would be the case but shouldn't matter imho.

still, the file-contents of **/boot/grub/grub.cfg** and/or **/etc/default/grub** as well as a listing of all files in **/boot/grub** could shed some light on the reasons behind the error messages i guess.

---

### Post by bapoumba on 2013-09-18
Thanks antiplex :)

---

