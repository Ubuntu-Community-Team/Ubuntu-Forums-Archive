---
title: "GRUB in primary partition instead of MBR"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Francesc Oller on 2007-10-20
I'd like to install GRUB in a primary partition. Setup is:

/dev/hda1   WinMe
/dev/hda2   Linux
/dev/hda3   extended
/dev/hda5   swap

Reason is clear. Not to mess up with MBR GRUB reinstalls in case of a WinMe reinstall.

When telling Gutsy installer to install GRUB in hda2 and activate it, Ubuntu won't load

I don't know why, this works flawlessly with LILO. Docs say that in this case another (capable) bootloader should be used in MBR. Why?

Any ideas?

Thanks,

Francesc Oller

---

### Post by confused57 on 2007-10-20
You might want to try a GAG boot floppy or cd:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

If it works well to boot WinME and Ubuntu, GAG bootloader can be installed to the mbr.

---

### Post by Francesc Oller on 2007-10-20
I know this, but doesn't solve the problem. If WinMe is reinstalled, GAG (or GRUB) MBR is gone and have to be reinstalled, which is why I'd like to have WinMe bootloader installed in the MBR (and GRUB  in a primary partition).

Regards

Francesc

---

### Post by Francesc Oller on 2007-10-20
Also keep in mind that GAG is useful for booting Linux from a floppy or CD without touching Win MBR.
I definitely want to boot Ubuntu in a primary partition, the active one, chainloading form WinMe bootloader in the MBR.

Is this possible? Does somebody have this setup?

Francesc

---

### Post by Herman on 2007-10-20
GAG would be perfect for what you want to do. GAG installs to MBR and the first track of the hard disk if you want it to, because most people find that more convenient than using a floppy disk or CD all the time.
Because it's in the first track of the hard disk, GAG Boot Manager is 'operating system independent', meaning you can delete either of your operating systems if you like, and GAG will still be there.

Regards, Herman :)

---

### Post by Francesc Oller on 2007-10-20
Then if I understand, GAG can be istalled to the 1st track, WITHOUT TOUCHING the MBR. When Win MBR takes control, jumps to the active partition which has GAG at the beginning. Thank-you for all who answered, I'll give GAG a try

regards, Francesc

---

### Post by Herman on 2007-10-20
No, GAG installs to the MBR *and* the first track.

---

### Post by Herman on 2007-10-20
Many people don't understand that the size of the space reserved for the boot loader in the MBR is less than 446 bytes, so an entire bool loader hasn't a hope of fitting into the MBR any easier than you can fit an elephant into a volkswagon.

When we say we are installing a boot loader to MBR, what we really mean is we are installing a small pointer in the MBR to help the BIOS to find the real part of the boot loader which is actually located somewhere else like in an operating system partition somewhere. In the case of GAG it can be in the first track of the hard disk, where it won't get deleted when we change operating systems.
>  Reason is clear. Not to mess up with MBR GRUB reinstalls in case of a WinMe reinstall.
Grub installs in three places, the MBR, the first fifteen sectors of the first track, as well as the operating system partition.

Regards, Herman :)

---

### Post by Francesc Oller on 2007-10-21
Herman, but then GAG isn't useful for the purpose we're talking about, say:

     "not to reistall GAG (or GRUB or whatever) in the MBR in case WinMe is reistalled"
     (since at least GAG MBR must be restored)

Please, take note that this isn't a feature I can't live without. In fact, I'm running GRUB in the MBR as everybody seems to be doing, but then ... there is the little reinstall annoyance. It's just a technical curiosity. I remember in the old LILO days when this was made a point in a docs chapter titled: "choosing the right boot concept".

Clearly it's WinMe's bootloader's fault (I can boot Ubuntu primary partition from a GRUB floppy disk) but then how do we explain that:

  - WinMe bootloader can chainload LILO in an extended partition. (I've verified this, was my old setup)
  - WinMe bootloader CANNOT chainload GRUB in a primary partition. Please try this by telling Gutsy's installer not to install GRUB in the MBR, computer won't boot

  - I've to try yet putting GRUB in a extended partition instead of a primary.

Regards

Francesc Oller

---

### Post by Herman on 2007-10-21
:) Francesc,
I don't know how you can set up a dual boot computer without having to do at least a little bit of fiddling around with boot loaders.

There are ways of setting up a dual boot while leaving the IPL for the Windows boot loader in the MBR.
An old fashioned way is to install LiLo or GRUB to the first sector of the Linux partition, then use a Linux 'dd' command to copy that sector and make it into a file with a .bin extension. You move that file to the root of the Windows partition and then configure boot.ini to chain load it. There are quite a few websites that advise doing it that way. You can try that if you want, and see if you think that will be less work than changing your MBR. Here is a link to a very good and well known website about that, 
[Matthew J. Miller's HOWTOs: Dual Booting Ubuntu Linux and Windows  ...]("http://www.google.com.au/url?sa=t&ct=res&cd=22&url=http%3A%2F%2Fwww.matthewjmiller.net%2Fhowtos%2Fdual-boot-linux-and-windows%2F&ei=PJsbR-ijOZGggAPZoqXuBw&usg=AFQjCNHig8N2cD5twwEkyIBdwYI7GkPaKg&sig2=E3VsbkDnM4PLgmj7U-Un_w")

Another way is to install WinGRUB in Windows, you don't have to change your MBR to use WinGRUB. WinGRUB is very good because then when you use any disc partitioning software and resize your partitions (if a partition is getting a bit too full), and move the Ubuntu partition, it will still boot.
I have my own page already about WinGRUB, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").

Originally designed for Windows Vista users, but also suitable for Windows XP i believe, is EasyBCD, but I don't think it will work for WinMe, Easy BCD is very good, [EasyBCD]("http://neosmart.net/dl.php?id=1").

The rest of the ways I know all involve changing the MBR.

[GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

[LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")

[GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

The MBR is an important sector on the hard disk, but it is still made of the same kind of material as the rest of the hard disk and can be written to and re-written as many times as we like, it will never wear out. :)

Now you can go ahead if you want and try out for yourself all those way to dual boot and see which ones are a lot of work, which ones are able to still work if you move or resize a partition, and which ones you can configure the most to suit your needs, and which ones are the easiest if you have to re-install Windows.

Then come back here and tell me which one is the easiest, which one is the most fun (customizable), which is easiest to maintain, (when there is a kernel update), and which one you like the best. :)

> WinMe boot loader CANNOT chainload GRUB in a primary partition. Please try this by telling Gutsy's installer not to install GRUB in the MBR, computer won't boot.
    I've to try yet putting GRUB in a extended partition instead of a primary.Oh, so you are trying out the old fashioned method?
You must be doing something wrong because I think it doesn't matter if GRUB is in a primary partition or a logical partition, it will still boot the same.
I already tried all those things a long time ago.
I know LiLo likes primary partitions more. If LiLo is in MBR it can boot in a primary or logical partition, but if you are booting it from Windows I'm not sure. Probably you are right about that.
I never heard of installing a boot loader in an extended partition, I think you mean in a logical partition, probably.

Well, have fun, that is the most important thing! :)

Regards, Herman :)

---

### Post by meierfra on 2007-10-21
> never heard of installing a boot loader in an extended partition, I think you mean in a logical partition, probably.


Reading this I just  had to  try to install grub to an extended partition. It actually  works!  Here  is what I did:

0) I reinstalled the Windows MBR with Super Grub.

1) I used fdisk to set the  boot flag for my extended partition sda3 and to remove the boot flag from my windows partition. (fdisk warned me that sda3 is an extended partition, but I ignored the warning)

2) I  removed the "makeactive" from the Windows item in menu.lst.

3 ) I  installed  grub to  sda3 via "root (hd0,7),  setup (hd0,2)"  at a grub prompt. Among other things, this stores the location of my "menu.lst" in the first sector of "sda3"

So now then I boot the computer the following happens:

The  windows MBR calls  the first sector of  the active partition. The active partition is sda3 and  grub  is installed on the first sector.  Grub now  uses the information in "menu.lst" to   create the grub menu. 

This all worked  fine and I can boot into windows and ubuntu from the grub menu.
So  it seems to be an easy method to keep the Window MBR intact. Just as easy as the regular way : Instead of installing Grub to the MBR,  install it to   the extended or primary partition containing ubuntu, set the boot flag to that partition  and don't use  "makeactive"  in  "menu.lst"-item for Windows.

But there seem to be at least a couple of  problems:

Windows is no longer on an active partition (i.e it does not have a boot flag)  Sometimes this will prevent windows from booting (I think).  Also Windows seems to be unable to hibernate since it  looks for the pagefile on the active partition:
[http://ubuntuforums.org/showthread.php?t=582849#8]("http://ubuntuforums.org/showthread.php?t=582849#8")

Grub is unable to install the stage1.5 files on an extended or logical partition.  This produces  a warning during grub set-up, but I'm not sure under what circumstances it  causes real problems.

And maybe somebody with more knowledge lets us know why this is  really a bad idea.

Actually it it is clear why Ubuntu chooses to install grub on the MBR:  
 Windows not being  an active partition  at least sometimes has real  disadvantages.
 Reinstalling the MBR on the other hand is so easy to do in some many different ways that one really should not worry about it.

---

### Post by Herman on 2007-10-22
Well!... I'll be!

Thanks for sharing that information, meierfra, that is really interesting! :)
I'll have to try it too, now.

Regards, Herman. :)

---

### Post by envoy on 2007-10-22
I followed the guide at 
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx")
Works for me. I have a Dell E1505 and this way I can still use MediaDirect too.

---

### Post by Francesc Oller on 2007-10-22
:)Herman,
AFAIK, boot.ini only exists in WinXP, useless for WinMe, nonetheless I find the method more involved.

I'm not using the old fashoned method. To clarify:

old setup:

/dev/hda1 primary                 WinMe
/dev/hda2 extended active                <--- LILO bootloader
/dev/hda5                                 Linux
/dev/hda6                                 swap
/dev/hda7                                 Linux    <--- root partition

/dev/hda <--- MBR, WinMe IPL

This works well

new setup:

/dev/hda1 primary                 WinMe
/dev/hda2 primary active     Linux     <--- root partition GRUB bootloader
/dev/hda3 extended
/dev/hda5                                 swap

/dev/hda <--- MBR, WinMe IPL

GRUB doesn't take control

I'll post my findings, thanks for your detailed explanations

Francesc Oller

---

### Post by meierfra on 2007-10-22
> GRUB doesn't take control

Could you give us some more details?  Are you booting directly into windows? Or does grub try to load the grub menu and fails? Or do you get to the grub menu, but then grub  fails to load ubuntu? Any error messages?

---

### Post by Francesc Oller on 2007-10-26
meierfra, WinMe-MBR refuses to chainload GRUB boot sector in primary partition. The message is:

"no se encuentra sistema operativo" (operating system not found -in english-)

My tests say that:

  - WinMe-MBR refuses to chinload anything but Win95 FAT32 partitions (id type = c). I haven't been able to make it chainload to either a Linux-type primary or an extended partition boot sector. (It looks the id partition).
  - Win98-MBR (and perhaps DOS-MBR) happily chainloads to an extended partition (was your test?). Which kind of Win-MBR did you test?

Not all Windows bootloaders are equal!

After testing this I agree with you that this isn't worth the trouble.

Regards

Francesc Oller

---

### Post by meierfra on 2007-10-26
> - WinMe-MBR refuses to chinload anything but Win95 FAT32 partitions (id type = c). I haven't been able to make it chainload to either a Linux-type primary or an extended partition boot sector. (It looks the id partition).
- Win98-MBR (and perhaps DOS-MBR) happily chainloads to an extended partition (was your test?). Which kind of Win-MBR did you test? 

Very interesting.  I used the XP-MBR . Or  more precisely whatever Super Grub installed for my Windows XP.

---

