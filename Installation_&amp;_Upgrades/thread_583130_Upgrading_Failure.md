---
title: "Upgrading Failure"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Pusteblume on 2007-10-20
](*,) Help,
during upgrading from ubuntu 6.06-LTS to 6.10 ther was an error so I was forced to reset. 
At that moment the upgrading ( by updatemanager) was setting up all the downloaded files.
Now the upgrade ist incomplete. Booting the system shows me the following lines:

1. BusyBox v1.1.3 (Debian 1:1.1.3-2Ubuntu3) Built-in shell (ash)
2. Enter "help" for a list of built-in commands.
3. /bin/sh:can´t access tty; job control turned off
4. (initram ss) after that line the cursor flashes.

When I now type help (as told) , all built-in commands are listed. 

The upgrading was done via internet.


Who can help me PLEASE?

---

### Post by dimeotane on 2007-10-20
do a search on here for "/bin/sh:can´t access tty; job control turned off"

you will find that it's a common error with a variety of reasons and solutions.

I often encounter it after a kernel upgrade, I think because I've often changed my partitions around.   My solution is to press 'e' in grub to edit the locations of my HD to the correct setting.
ie. from (5,0) to (1,0) and to set my kernel root=/dev/sda2   because the UUID has changed.

---

### Post by Pusteblume on 2007-10-20
thank you for your information. I will try it out and let you know later.

---

### Post by Pusteblume on 2007-10-21
hi dimeotane 
I tried to look for "/bin/sh:can´t access tty; job control turned off". There were to many possibilities.  
Where exactliy do I look. The problem ist, that I only have a limited amount of  commands.

(initramfs) help

When I type after the word (initramfs)** help** then ubuntu shows me the built-in commands as follows

Built-in commands:


. : alias bg break cd chdir command continue echo eval exec exit 
    export false fg gtopts hash help jobs kill let local pwd read 
    readonly return set shift time trap true type unlimit umask unalias 
    unset wait [ [[ash basename busybox cat chmode chroot chvt clear 
    cmp cp cut deallocvt dumpcmap echo egrep env expr false fbset
    fdf lush fgrep grep hostname ifconfig ip kill ln loadfont loadkmap
    lsmkdir mkfifo mknod mkswap mktemp more mount mv openvt printf
    ps pwd readlink reset rm rmdir sed setkeycodes sh sleep sort 
    stat sync tail tee test touch tr true tty umount uname unic yes

(initramfs)

this is what I see

when I type after the words (initramfs) **ls**...... then ubuntu shows me
dev bin etc modules scripts es usr prok var
root conf lib sbin init sys tmp 

when I opened the dir **etc**, I found the following:
modprobe.d evms.conf udev 


Would you please be so kind to give a step by step instruction to complete the setup to the version 6.10 (Edgy Eft)

---

