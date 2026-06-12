---
title: "no bootable device"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by quiquednst on 2014-02-21
I have seen some posts with similar title but no one seems to apply to my case. So I'm writing this new post.
I'm working for a nonprofit organization which recycles personal computers.

 For the last years we have provided hundreds of computers based on Ubuntu (mainly xubuntu).
 Recently we got a set of computers with W7 installed and running. They are using BIOS and msdos partitioning.
 As we install xubuntu-12.04 it isn't possible to get access to grub, getting always the 'no bootable device' message. Even I tested with an old 10.04 but with the same result.

 From CD/DVD you may boot and chrooting you may work with the installed system (xubuntu 12.04) without any problem.
 From this point (my xubuntu system) I reinstalled grub (grub-install) without errors but … the same problem.

 I run Boot-Repair ([http://paste.ubuntu.com/6964514/](http://paste.ubuntu.com/6964514/)) but … the same problem.
 It seems BIOS doesn't like to look at MBR or MBR is wrong and I (grub-install) can't change it.

 Any help?
 Thanks in advance

---

### Post by sudodus on 2014-02-21
Maybe there are already four primary partitions, which fill the MSDOS partition table. This problem is typical for HP computers, and a solution is to remove the HP_TOOLS partition to get 'logical space' and then to shrink the main Windows partition to get disk space.

After that you can create an extended partition, and inside that create an ext4 partition for Xubuntu's root file system and a swap partition.

Please post the output of the following commands to get more specific advice

```
sudo fdisk -lu
```

```
sudo parted -l
```

try to mount all partitions and then

```
df
```

---

### Post by mörgæs on 2014-02-21
First of all it would be good if you mentioned what you are trying to achieve. Do you want dual boot or a Xubuntu only system?

---

### Post by oldfred on 2014-02-21
You have an unusual instal as the only primary partition is the extended partition.

Some BIOS will not let you boot without a boot flag on a primary partition. 

Grub does not use boot flag, so you boot flag on sda6 is not required. Since sda1, the extended partition is a primary partition, I think you can add a boot flag to it and BIOS may then work. But that also is unusual.

---

### Post by quiquednst on 2014-02-21
sudodus:
I hope the info you are asking for is on the Boot-Repair report ([http://paste.ubuntu.com/6964514/](http://paste.ubuntu.com/6964514/)).
Now I don't get access to the computers and therefore I can't add new data.

---

### Post by quiquednst on 2014-02-21
Well, I will try to explain the context.
At the very beginning we built several OS on he same HD and therefore we decided to build sda1 for MS and an extended partition for others. Later on we abandoned MS and we took all the space for Linux partitions. As we maintained an sda6 image we keep the same structure, only one extended partition with several logical partition (swap, OS). And this solutions has been working with different computers.
 Right now we just have a swap logical partition and an OS (xubuntu 12.4) logical partition under an extended partition (sda1).
I tried also putting xu on sda1 as Primary Part. but I'm afraid I forgot to activate the boot flag. May it be relevant?
Thanks for your help

---

### Post by sudodus on 2014-02-21
> **quiquednst said:**
> sudodus:
I hope the info you are asking for is on the Boot-Repair report ([http://paste.ubuntu.com/6964514/](http://paste.ubuntu.com/6964514/)).
Now I don't get access to the computers and therefore I can't add new data.

Sorry, that I overlooked the pastebin. It is OK, and the problem is *not* that the partition table is crowded. Honestly, I don't know what is the problem. I know that *oldfred* has more experience than most of us, so I suggest that you read very carefully his posts.

Otherwise I can only suggest that you ***test a fresh installation*** of Xubuntu (using a CD/DVD/USB drive made with a desktop iso) to find out if your problem depends on the partition structure, or if it is something else, for example problems with the BIOS or motherboard or some driver (graphics or wifi).

It would also make it easier to give relevant advice if you specify for this batch of computers

- Brand name and model
- graphics chip/card
- wifi chip/card

***Edit***: Are you 100% sure that the computers are set in BIOS mode, not UEFI?

---

### Post by quiquednst on 2014-02-21
They are custom computers, 4 or 5 years old, with an Intel mothercard and an Intel BIOS (MQ96510J.86A).
About UEFI, I get access to the BIOS and I don't see anything related with EFI. Moreover pastebin seems to say that this is not an EFI compatible computer.
I run a Boot-Repair with a similar computer before changing anything and the report is in [http://paste.ubuntu.com/6964667/]("http://paste.ubuntu.com/6964514/").
It seems it isn't a UEFI and it works with msdos partitions.
Regards

---

### Post by sudodus on 2014-02-21
OK, we are sure it is not UEFI :-)

And as far as I know, Intel mobos and BIOS are usually easy to manage with linux drivers.

Do the computers run 'live' when booted from  a CD/DVD/USB install drive made with Xubuntu? If this is the case, they should also boot from grub. But there are exceptions, computers that boot only from certain grub versions (I have found such problems with some HP computers when booting via USB). Grub of Ubuntu (and Xubuntu) ***13.04*** was better (than grub of 12.04 and 13.10) for these computers.

One possibility might be to try to run one of those computers with the 'Chainloader' described in the following link. It can be installed in a USB drive or an internal drive and my experience is that it is a very good booter (using grub of Ubuntu 13.04).

 [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by oldfred on 2014-02-21
Intel motherboards are one of those that has to have a boot flag on a primary partition. 

If with newer gpt partitioned drives where gpt partitioning should only have a boot flag on an efi partition for UEFI boot, we have had to add a dummy efi partition just to have a boot flag.
And Intel is one of those involved or even promoting UEFI, but left hand on setting software standards and right hand on designing motherboards must not talk.

---

### Post by quiquednst on 2014-02-22
*[COLOR=#0000cd][SIZE=4]**It works!**[/SIZE][/COLOR]*
We have built a new partition structure with 2 *PRIMARY* partitions: sda1 for the OS with **boot** flag on, and sda2 as Swap.
We have restored on sda1 the image we had and it works! (we had to make a few changes on the saved image before restoring it and on fstab later on, but this is another story)
That's all!
Thanks for your help, your very fast and successful help!

---

### Post by sudodus on 2014-02-22
> **quiquednst said:**
> I'm working for a nonprofit organization which recycles personal computers.

 For the last years we have provided hundreds of computers based on Ubuntu (mainly xubuntu).
 

Good luck with your valuable work to make old computers work with systems based on Ubuntu (mainly xubuntu) :-)
> **quiquednst said:**
> *[COLOR=#0000cd][SIZE=4]**It works!**[/SIZE][/COLOR]*
We have built a new partition structure with 2 *PRIMARY* partitions: sda1 for the OS with **boot** flag on, and sda2 as Swap.
We have restored on sda1 the image we had and it works! (we had to make a few changes on the saved image before restoring it and on fstab later on, but this is another story)
That's all!
Thanks for your help, your very fast and successful help!

Thanks for sharing your solution :KS

-o-

Finally: I suggest that you try to use the One Button Installer. OBI, and make a tarball from your installed system, and use the OBI to install it in new (recycled) computers. See this link

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

