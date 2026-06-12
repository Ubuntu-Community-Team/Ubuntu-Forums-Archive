---
title: "How Do I Move Grub2 Without Altering the MBR?"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by linux4me on 2011-10-27
I have a dual boot installation of Vista and Ubuntu 11.10 that I set up as follows:
[LIST]
[*]Vista on the primary partition.
[*]Ubuntu on an extended partition.
[*]Truecrypt set up to encrypt the Vista system partition.
[*]Truecrypt as the bootloader.
[/LIST]

Truecrypt overwrote Grub2 in the MBR. What I need to do now is move Grub2 to the /root partition of Ubuntu so I can boot Ubuntu, and *not* alter the MBR, which would destroy Truecrypt's bootloader.

I've done a bunch of searching, and found methods of [moving Grub2]("https://help.ubuntu.com/community/Grub2#Changing_or_Moving_GRUB_2"), but to my noob's eyes it looks like that would alter the MBR, too.

I have a recovery disk for Truecrypt, so theoretically I could follow the steps above, let Grub2 damage the Truecrypt bootloader, and then recover it using the recovery disk. I actually found one web site that suggested that approach, but it seems kind of kludgy.

What would the procedure be to move Grub2 to my Ubuntu partition without altering the MBR so that Truecrypt remains the bootloader on the primary (Vista) partition and I can still boot both OSs?

TIA

---

### Post by drs305 on 2011-10-27
There was an option to use the '--force' option with 'grub-install' in earlier versions of Grub 2 but this appears to have been removed in Grub 2 - at least it doesn't show in the man page any longer. 

You may be give the option of where to install Grub 2 if you run:
```
sudo dpkg-reconfigure grub-pc
```

You can can get to the same screens by purging Grub 2 (sudo apt-get purge grub-common) and then reinstalling (sudo apt-get install grub-pc).

By either method you should be prompted for where you want to put Grub. You use the SPACEBAR to designate the location. In your case, you would select only the Ubuntu partition (for example sda5) and make sure the drive has no asterisk next to it.

You will probably get a warning about using Blocklists, but you have your reasons for trying it this way and hopefully it will permit you to install it to the partition.

---

### Post by oldfred on 2011-10-27
Understand it is a bit less reliable installed to a partition as it has to use blocklists or hard coded addresses. You may have to reinstall on updates to grub if the files get moved from current address.

Instructions then always say to install to sda, the MBR of the drive, but you want to install to sda5 or whatever partition it is. Your will also have to add a --force option. Not sure if that is at end or right after grub-install.

#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda5
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda5 --force

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by linux4me on 2011-10-27
Thank you both for your replies.

I went with oldfred's procedure because it seemed like it gave me a little more control over the process.

I used the
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda5 --force
```
option because I am using 11.10.

I can now just enter my Truecrypt password to run Winblow$ or hit Esc to boot Ubuntu. All is good until the next Grub update.

---

### Post by drs305 on 2011-10-27
> **linux4me said:**
> Thank you both for your replies.

I went with oldfred's procedure because it seemed like it gave me a little more control over the process.

I used the
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda5 --force
```
option because I am using 11.10.

I can now just enter my Truecrypt password to run Winblow$ or hit Esc to boot Ubuntu. All is good until the next Grub update.

Glad it worked. And I just checked and the "force" option is listed in the man page, although I swear for a time it wasn't there...
> All is good until the next Grub update.
If you are worried about Grub updates, you can always 'pin' Grub to it's current version. You should do it in Synaptic (if you install it) as well as via the command line. Unless you always do it the same way, you would need to do both - locking in Synaptic doesn't prevent an upgrade in the terminal, and vice versa.



Here is the Ubuntu Community Doc on it - check the 'Hold' section:
[https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")

---

### Post by WeFY-KVQqr on 2012-01-18
Do not try this because this advise is incomplete.

This will work only if the extended partition of ubuntu is on sda2.
If it is on sda3 or whatsoever you're screwed anyway because Truecrypt can't find the bootloader then.
It is all over the truecrypt forums: system encryption and linux is not compatible (and probably will never be compatible).
I've tried this literally a dozen times and I´ve never succeeded in cases where the extended partition is not sda2.

If someone has other observations please let us know.

---

