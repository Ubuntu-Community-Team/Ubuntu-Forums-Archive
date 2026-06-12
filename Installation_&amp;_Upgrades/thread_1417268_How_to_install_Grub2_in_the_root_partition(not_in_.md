---
title: "How to install Grub2 in the root partition(not in MBR)"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by codemaniac on 2010-02-27
Hi friends,
I am having a problem while installing GRUB2 on my root partition on Ubuntu(sda9)..not in the MBR..
How can i install grub2 in Ubuntu's root partition without touching th MBR...????
In MBR there is a Grub of a another operating system...

---

### Post by coffeecat on 2010-02-27
I presume you're wanting to chainload from a legacy grub. This could be frustrating - or not as the case may be. :?

Attempting to install grub2 stage 1 to the partition boot record may or may not succeed. I've been successful with both my laptops, but I get an error with my main desktop. I don't know why - perhaps some hardware issue. Anyway....

You have to be running the version of Ubuntu (presumably Karmic) with grub2, or chroot into it. To install grub2 stage 1 to the PBR of sda9 you do:

```
sudo grub-install /dev/sda9
```Whether or not this succeeds, you'll probably get an error something like:

> grub-setup: warn: Attempting to install GRUB to a partition instead of  the MBR.  This is a BAD idea. 
grub-setup: warn: Embedding is not possible.  GRUB can only be installed  in this setup by using blocklists.  However, blocklists are UNRELIABLE  and its use is discouraged. 
Installation finished. No error reported.I got this from my desktop and despite the "Installation finished. No error reported" it had failed. But, as I said, in my laptop it did succeed and I was able to chainload from a legacy grub.

If you get a failure, you have two options:

**Either**: Use this stanza in your legacy grub menu.lst. It has the same effect as chainloading. I have absolutely no idea how it works, but it does.

```
title Karmic grub2 menu 
root (hd0,8) 
kernel /boot/grub/core.img
```**Or:** Chainload from your grub2 menu to your legacy grub partition. You'll have to install grub stage 1 of your legacy grub to its root partition (the one presently in your mbr), and configure grub2 by editing /etc/grub.d/40_custom,  running update-grub and installing grub2 stage 1 to the mbr. I can give you more details if you need.

Good luck!

---

### Post by ronnielsen1 on 2010-02-27
A little off the subject, more on the line of a complaint. Why grub2? I had grub all figured out. Grub2 has me ](*,)

---

### Post by louieb on 2010-02-27
[How To Install GRUB to a Partition Boot Sector]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition") - with grub-setup

@ronnielsen1- The developers of GRUB legacy stop working on it several years ago. The code was hard to maintain. They wanted to make something better. 

In order to have a boot loader with upstream support - bug fixes - improvements - Ubuntu switched to GRUB2.

---

### Post by codemaniac on 2010-02-27
@coffeecat : Thanks pal for your reply.. you almost read my mind..Except I have Linux Mint 8's [Grub2] on the MBR...
I tried to install ubuntu's GRUB2 at sda9 by....
grub-setup --force /dev/sda9 and
grub-install /dev/sda9 [Both in vain]
I got the "BAD IDEA" message....

i can chainload suse 11.2 & fedora 12 with no problem at all....both uses old grub...
But i cant chainload ubuntu ...

---

### Post by codemaniac on 2010-02-27
i have no grudge against grub2 ...But it has really complicated the simple chainloading process..
specially chainloading grub2 from grub2..

---

### Post by louieb on 2010-02-27
> **codemaniac said:**
> @coffeecat : I got the "BAD IDEA" message....

That message was a bad idea. We all get it.  I just ignore it and it does it anyway.

To know for sure if it did it or not run the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")

You will just have to create a custom entry - on my PC running Hardy right now so don't have an example handy.

Or you can just run update-grub and it should create boot entries for your other linux install

---

### Post by coffeecat on 2010-02-28
> **codemaniac said:**
> I tried to install ubuntu's GRUB2 at sda9 by....
grub-setup --force /dev/sda9 and
grub-install /dev/sda9 [Both in vain]
I got the "BAD IDEA" message....

I've now installed Lucid Alpha to my two laptops and to my desktop. On the laptops, where the Karmic grub2 stage1 installed just fine to their respective partition boot sectors, the Lucid grub2 stage 1 installed without a murmur ditto.

But on my desktop, where the Karmic grub2 stage1 won't install to the PBR, I get a problem with Lucid also. Since the Lucid grub2 is a slightly later version, I was hoping for better things. No such luck. "sudo grub-install /dev/sda9" gives me:

> /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.... and "sudo grub-install --force /dev/sda9 gives me:

> /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.Except that it didn't work. :(

All I can suggest is that you try one of the alternatives I suggested. There is a third, though. If you look in the root of your Mint8/Karmic (Mint8 is only Karmic with a pretty face, some restricted stuff, and some Mint-orientated package managing) partition, you'll see two symlinks, vmlinuz and initrd.img, linking to the latest kernel and initrd.img in /boot. You can add a stanza to your legacy grub menu, using /vmlinuz and /initrd.img for the kernel and initrd lines. That way you'll boot straight into your latest Mint/Karmic kernel without chainloading.

> **louieb said:**
> That message was a bad idea. We all get it.  I just ignore it and it does it anyway.

Unfortunately, not always. It seems to be hardware dependent. I wish I knew why. :(

---

### Post by codemaniac on 2010-02-28
[QUOTE]title Karmic grub2 menu 
root (hd0,8) 
kernel /boot/grub/core.img/QUOTE]

works..Now i can chainload ubuntu/mint, from suse's grub1..
still cant chainload a grub2 from another grub2..

Gave up on grub2 ...

---

### Post by codemaniac on 2010-02-28
> Or you can just run update-grub and it should create boot entries for your other linux install

No problem with that friend..I can do that..i just wanted a more fine grip @ grub2 while chainloading other distros{grub1/2}..
Which grub2 failed to provide...grub1 is MBR is the safest bet i found..i can now chainload grub2 also with coffecats help..thanks all..

---

