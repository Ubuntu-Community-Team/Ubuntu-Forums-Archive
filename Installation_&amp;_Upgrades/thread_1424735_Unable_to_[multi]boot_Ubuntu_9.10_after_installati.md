---
title: "Unable to [multi]boot Ubuntu 9.10 after installation"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by lewyssmith on 2010-03-08
I installed Ubuntu 9.10 from live CD into sda7:-
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      506016    6  FAT16
/dev/sda2              64        4865    38572065    5  Extended
/dev/sda5              64         960     7205121    7  HPFS/NTFS
/dev/sda6             961        1859     7221186   83  Linux
/dev/sda7            1860        2759     7229218+  83  Linux
/dev/sda8            2760        3026     2144646   82  Linux swap / Solaris
/dev/sda9            3027        3924     7213153+  83  Linux
/dev/sda10           3925        4865     7558551   83  Linux

FWIW I found the disk partition & bootloader parts of the installation a nightmare: never sure what it wanted to do.
I was peeved not to be offered the boot loader on a dedicated floppy - the surest & safest way to handle new installations without messing up the rest. Is this possible, please?

I multi-boot normally from NT Boot Loader chainloading partition boot sectors. (It is actually very easy to use; and is preserved during MS re-installations). Or similarly with an 'old' Grub shell boot floppy:-
root (hd0,x)
chainloader +1
boot

Having forced the installation to put *the boot sector in the root partition* (sda7), neither method works, and I cannot get into Ubuntu. I have an identical problem with OpenSuse 11.2, so suspect it is Grub2 related, and that the partition boot sector is not being correctly set up.

I can provide specific error msgs if required - just tedious! In the meantime, any suggestions?

Lewis Smith

---

### Post by von Stalhein on 2010-03-08
I found the info in [this thread]("http://ubuntuforums.org/showthread.php?t=1014708") to be pretty helpful.

Certainly the thread starter will be able to suggest the next step - good luck!!

---

### Post by ajgreeny on 2010-03-08
A multiboot system like yours would be best served by using ubuntu's grub2 on the MBR in my opinion.  ubuntu is very good at finding all other OSs at install time and if by chance it did not find everything, runing sudo update-grub afterwards certainly should do so.

I have a similar setup to yours in many ways, with my main Ubuntu OS on sda and three other linux OSs on sdb, but all booting from the Ubuntu grub2.  It has performed faultlessly for me and I think any other way of doing this would be completely un-neccesary.  Perhaps try re-installing grub2 on to the MBR using the info in von Stalhein's link, and I think it should work well.

---

### Post by lewyssmith on 2010-03-08
Thanks to both replies. The 'this thread' link "How to restore the Ubuntu grub bootloader (9.10 and beyond)" suggested by von Stalhein looks good, and I shall try it forthwith. grub-install onto /dev/sda7 and hope it flies. But please understand that nothing Ubuntu has been messed with, nor should need restoring. I'll report back.

I was wrong about the same problem with Suse (which I got bootable in the end); it does not use Grub2 apparently.

The NT boot loader could well be the most useful MS software - if you have any of their thingies. I never use mine!

Lewis Smith

---

### Post by lewyssmith on 2010-03-11
With Ubuntu on /dev/sda7, I tried to re-install its boot loader on its *root partition* as advised [ref] in this thread. Ran from live Ubuntu 9.10 CD, console. sda7 directoriy structure is /boot/grub/...
sudo mkdir /mnt/sda7
sudo mount /dev/sda7 /mnt/sda7
sudo grub-install --root-directory=/mnt/sda7 /dev/sda7

Yields:-
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea. [comment: why?]
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged.
grub-setp: error: canot read 'grub/core.img' correctly

I retried with --root-directory set to both /mnt/sda7/boot and ...boot/grub same result.

So what next?
a) Can I revert to 'old' Grub, which I understand better?
b) Aside: how to I find my own thread? I looked hard, searched long!

TIA               Lewis Smith

---

### Post by von Stalhein on 2010-03-11
Hello Lewis,
As for reverting - that's what I did in the end, it was easier in the short term. Nothing I tried worked on this machine.

I found a thread in here somewhere about going back to the original GRUB - since then it's been all good.

I hope that when Lucid is released I will be able to move along the timeline too :-;)

Edit - [here it is!!!!]("http://ubuntuforums.org/showpost.php?p=8341799&postcount=4")

---

### Post by kansasnoob on 2010-03-11
I wrote this about reverting to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Appendix #1 describes briefly how to use a chroot.

---

### Post by von Stalhein on 2010-03-11
> **kansasnoob said:**
> I wrote this about reverting to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Appendix #1 describes briefly how to use a chroot.

Oh well played sir.

I wish I'd found that when I was in extremis!!!

---

### Post by lewyssmith on 2010-03-11
Thanks to all for all the links indicated, which I have saved. I *shall* try to revert Grub; and report the outcome. I have yet to see my installed Ubuntu! It is clear from this forum that there are huge numbers of boot problems, so something is not right somewhere.

FWIW You may have noticed that I insist on putting the Grub boot on the [root] *partition* boot sector. That way, you can just boot it by
root (hdx,y)
chainloader +!
boot
without any knowledge at all of kernel, initrd, UUID etc. It also stops (or should, but alas not always) messing up any existing working multiboot system. So simple, why bother with anything else? Of course, the partition boot sector has got to be good...

Also FWIW with the NT loader, all you need to do is
1] copy the partition boot sector to somewhere where Windows can see it
2] and add a line to its boot.ini like
\path\to\boot\sect="Partition to boot"

What could be simpler?

Lewis Smith

---

### Post by von Stalhein on 2010-03-12
^^

Something that just works?

:D

---

### Post by TutAmongUs on 2010-03-12
> **ajgreeny said:**
> A multiboot system like yours would be best served by using ubuntu's grub2 on the MBR in my opinion.  ubuntu is very good at finding all other OSs at install time and if by chance it did not find everything, runing sudo update-grub afterwards certainly should do so.

I have a similar setup to yours in many ways, with my main Ubuntu OS on sda and three other linux OSs on sdb, but all booting from the Ubuntu grub2.  It has performed faultlessly for me and I think any other way of doing this would be completely un-neccesary.  Perhaps try re-installing grub2 on to the MBR using the info in von Stalhein's link, and I think it should work well.
  If someone could make a front end for grub that at least matches that of XOSL, THEN I would consider it.  Right now, it is an invasive dog that insists on being on the MBR even when it is told NOT to modify it.

---

### Post by lewyssmith on 2010-03-12
<<
If someone could make a front end for grub that at least matches that of XOSL, THEN I would consider it. Right now, it is an invasive dog that insists on being on the MBR even when it is told NOT to modify it.
>>
I agree with the sentiment, but feel it is down to the Linux distribution boot mechanisms rather than Grub itself, which used directly does what it is aked to in my experience. I am unsure of Grun2, though.

I am thoroughly fed up with Linux distributions destroying working multi-boot setups, insisting on trampling where you do not want, out of control. And repeat my plea for all of them to offer making a boot floppy (where possible), which seems to have disappeared.

Lewis Smith

---

### Post by matthew on 2010-03-28
I removed several posts from this thread after the discussion became unhelpful and argumentative. I would like to remind people to please treat other forum members as you would like to be treated--I presume that means with kindness and respect. If you can't contribute without insulting others, don't respond at all. Thank you.

---

### Post by lewyssmith on 2010-03-31
Sorry to have been so long in coming back. I knew it would be a battle, put it off, and it was... I re-installed Ubuntu from the LiveCD several times, curiously inconsistently. Despite my caution, Ubuntu won in the end, and put Grub2 on the MBR (rather than partition sector where I wanted it)... Which worked for most, but not all, other installed Linuxes.

I am hardened enough now to have backups of all boot sectors, MBR & partitons. Do likewise - & remember count=1 and bs=446 when restoring the MBR with dd! (512 for partiton boot sectors).

But at last I got into Ubuntu. While there, the first thing I did was use TexasNoob's excellent notes cited earlier on replacing Grub2 with old Grub. Many thanks for same. (I question the need to do both grub-install *and* grub setup, which I think are equivalent).

I then used old Grub (which I know) to install itself on the partition boot sector (for chainloading) and floppy disc (for direct booting). In fact I had to go round in circles endlessly, re-booting and re-installing Grub repeatedly, because there was always something that did not work, either chainloading or booting directly from floppy. At last it all does. Cross fingers.

I still suspect that the problem lay with Grub2 or its installation, particularly that whatever (if anything) it put on the *partition* boot sector was not useable by either old Grub nor NT Loader for chainloading. I may be wrong, but dare not try to find out!

Thanks to all who gave advice.

Lewis Smith

---

### Post by lewyssmith on 2010-04-07
(I thought I had already closed this thread; what follows may be a repeat).
I won in the end by re-installing Ubuntu from live CD (several times, inconsistent re the booting outcome). Despite my efforts to the contrary, Ubuntu won in the end and grabbed the MBR. Not all of the resulting menu entries worked...

Luckily I had all partition boot sectors & MBR backed up. Beware when restoring the MBR to cite bs=446 in the dd command.

I reverted to old Grub as cited earlier in this thread: many thanks for kansasnoob's precise instructions. (I query the need to do both Grub setup *and* install-grub). With this I installed the Ubuntu partition boot sector, *and* made a boot floppy. So at last I can get into Ubuntu!

Lewis Smith

---

### Post by oldfred on 2010-04-07
I liked chainbooting with old grub but find new grub works very well for me. I just added an entry in new grub to my old grub partition to chainboot the older systems and turned off new grub from finding them since it wanted to find all the versions.

I was able to get grub2 into the partition with the force command but it complained on every update.

You also can do a custom menu:
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I have given up on floppies. Herman has info on using grub partitions either old or new and using USB or CD's to boot.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

If you have lots of partitions and boot loaders the best way to know what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by lewyssmith on 2010-04-07
Thanks to 'oldfred' for his extra info. I will try the bootinfoscript for interest. Could not get the Herman link to respond.

I shall be happy to move to Grub2
- when I understand it (its documentation that I have seen is incomplete).
- when it is part of all the Linuxes I play with.
- when I am convinced that it 'chainloads' successfully as per old Grub, especially from the NT loader. (Neither old Grub shell nor the NT loader liked whatever Ubuntu Grub2 put on the partition boot sector - if anything).

Re flopppy discs, they do have their good points, not least simplicity. My machine is quite recent, but cannot boot from a USB flash drive. Making a series of boot CDs is rather heavy. (Can you in fact do this directly from Grub2?). Individual floppies (per installed system) are easy to make & great fallbacks; with an [old] Grub shell boot floppy as a further resource.

It would be nice if the thread itself had a 'solved' button!

Lewis Smith

---

