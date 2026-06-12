---
title: "What after boot-repair?"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by maccagnano on 2014-03-29
Hi all. I've a problem with grub,(won't start after some error i make) so i make a live usb with boot-repair. All is fine but when finished and restarted i have a bash-like with "grub>". What i can do now? 
Here is the pastebin:
[http://paste.ubuntu.com/7174496/](http://paste.ubuntu.com/7174496/)

In the meanwhile i'm tryng to download a iso of ubuntu to make a cd....

Thanks to who can help me.

---

### Post by Ubi_one_2014 on 2014-03-29
pls download the iso of 13.10, and install

---

### Post by steeldriver on 2014-03-29
> **maccagnano said:**
> (won't start after some error i make)

Can you give us some details about what you did? I don't see anything out of the ordinary in your boot-repair pastebin (based on a very quick look...)

---

### Post by maccagnano on 2014-03-29
Thanks for the quick reply.....I was doing a live of an operating system, but wrong (I know ... I'm a fool) instead of writing on usb ... I shot everything on /.
After.... i delete some file...but sure i was wrong on deleting

---

### Post by steeldriver on 2014-03-29
OK in that case it's probably going to best to recover whatever data you can from the partition (after mounting it from a live CD/usb system) and then reinstall

---

### Post by maccagnano on 2014-03-29
i can't do anything from the command line? i don't know.....something like a recovery or ....

---

### Post by maccagnano on 2014-03-29
what about the line 318 in the pastebin?? "[COLOR=#000000]Unknown BootLoader on sda2"[/COLOR]

---

### Post by maccagnano on 2014-03-29
news......booting from usb, i'm trying the "check for errors" (something like this) and it found 1 error in ./casper/filesystem.squashfs

any idea?

---

### Post by steeldriver on 2014-03-29
Which partition are you checking? there shouldn't even be a ./casper/filesystem.squashfs on your original HDD, it probably indicates that the aborted installation  got quite far along (i.e. overwrote a bunch of stuff on your HDD)

---

### Post by oldfred on 2014-03-31
You have what looked like a normal 12.04.4 install in sda1 on your 250GB drive except kernels?
Grub is in MBR and looks to sda1 to continue to boot.
But now grub.cfg shows no Ubuntu boot stanza and it does not look like you have any kernels?? 

Not sure how kernels would have been deleted. While you could chroot into your install and add kernels & update grub to use them, it probably is just easier to reinstall since it is a new install.

With a 250GB drive I would suggest a / (root) of 20 to 25GB and use rest of drive for /home. Keep existing swap. You do have to use Something else and manually partition and choose / & /home partition mounts & formats. 

If you do just want / then the auto install should just overinstall.

---

### Post by maccagnano on 2014-03-31
Meanwhile, thanks to everyone for your concern. I proceeded to reinstall without formatting right to recover files, documents, and virtual machines. Today I will install from the scratch following the advice of oldfred. So I learn to do **** .... ;)
Thank you all.

---

