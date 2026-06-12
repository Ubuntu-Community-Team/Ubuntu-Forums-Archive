---
title: "Dual Window/Ubuntu boot wants windows recovery key (bitlocker key)"
date: 2024-09-05
forum: Installation &amp; Upgrades
---

### Post by willabeer on 2024-09-05
I had a dual boot setup working nicely with Windows 11 Pro and Jammy Jelly (22.04.4).  I got a upgrade notice that I could upgrade to Royal Numbat (24.04.4).  I gladly updated to Royal Numbat.  On the Ubuntu side everything works as expected, but if I select the Windows Boot option in Grub, then Windows asks for the BitLocker Key.  It is not fun fat fingering in 48 numbers on a display that is minimal.  But Windows accepts the key and works.  

If I change the Boot options to place Windows as first priority, Windows will start without the BitLocker Key and will work as expected.

I tried to fix grub by doing a simple Grub Update, but that didn't work.  I next ran Boot-Repair and the Paste is at [https://paste.ubuntu.com/p/BzNcwkBJvt/](https://paste.ubuntu.com/p/BzNcwkBJvt/) .

Boot-Repair didn't fix the problem.  I haven't found anything on the internet to fix this problem. Not sure what to do next and some help would be appreciated.

---

### Post by oldfred on 2024-09-05
Not sure it is possible.
Can you not directly boot Windows from UEFI one time boot key. Not really different than booting from grub menu.

I have seen posts on mounting bitlocker once in Ubuntu.
But if using any encryption, you must have good backups, so if encryption breaks you still have your data.

Some discussion of bitlocker:
[https://ubuntuforums.org/showthread.php?t=2456222&page=2&p=14013210#post14013210](https://ubuntuforums.org/showthread.php?t=2456222&page=2&p=14013210#post14013210)

---

### Post by willabeer on 2024-09-05
Not sure if I understand your comment.  I can directly boot Windows if I set it's boot priority in BIOS to first.  I don't need the recovery key if I do this.  It works.  It doesn't work when Ubuntu's BIOS boot priority is first, and I try to switch to Windows with Grub.  Did you have in mind something I could do in the BIOS?

---

### Post by oldfred on 2024-09-05
It should not matter what is default in UEFI boot.
But you always should be able to select an alternative from UEFI boot.

Select system you use the most as default in UEFI settings.
And boot other system from F12 or whatever key your system uses for UEFI one time boot.

---

### Post by tea for one on 2024-09-05
Booting Windows via grub = Bitlocker active
Booting Windows via PC boot menu = Bitlocker inactive

Assuming that you shut down Windows 11 completely and Windows is then encrypted, it would indicate that the encryption is not working consistently.
Just a guess, no real evidence.

---

### Post by willabeer on 2024-09-07
oldfred:  I have thought about what you proposed, and I could do my boots like that.  However, it will cause a little inconvenience, and I just like using the Grub menu to determine which operation system to use.  I like the Grub approach for its simplicity and  exposure to basic Ubuntu start items.  How unlike the Windows approach where you need to open settings and hunt for what you need.

---

### Post by willabeer on 2024-09-07
tea for one:  From my observations, I would say that BitLocker and Windows are operating as designed.  It appears that something is amiss with the handoff between Grub and the boot.  I would have thought that Boot-Repair would have repaired the problem.  I might need to uninstall and then reinstall Ubuntu.  I would like to fix the problem instead of uninstalling approach.

---

### Post by oldfred on 2024-09-07
I do not think grub can boot Windows if bitlocker is on.
It cannot pass the correct security info.

---

### Post by tea for one on 2024-09-07
```
nvme0n1p1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, BitLocker
nvme0n1p4	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, BitLocker
sda2	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot, BitLocker
```
There are three partitions labelled BitLocker, which one has the (encryption) key when you boot Windows via Grub?

---

### Post by willabeer on 2024-09-08
nvme0n1p4 is the Windows OS, drive C:

the others are just files.

---

### Post by tea for one on 2024-09-09
> **willabeer said:**
> IIf I change the Boot options to place Windows as first priority, Windows will start without the BitLocker Key and will work as expected.
Do you still have to enter the BitLocker password rather than the BitLocker 48 digit recovery key?

---

### Post by yancek on 2024-09-09
The link below explains how to use bitlocker on windows and boot from Grub.  Haven't used it so have no idea if it will work but you might read through the page.

[https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/](https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/)

---

### Post by pspathis2 on 2024-09-09
Hi all,


I am facing exactely the same issue mentionned by Willaber. I have the exact same configuration, that is a dual boot with windows 11 pro and Jammy Jelly (22.04.4). Windows was encrypted with BitLocker and I used to boot on it using grub. Auto-unlock was also working fine thanks to the TPM.
Besides, I was using dislocker to read the windows partition from ubuntu and all was working like a charm.

Got the upgrade notice and fell for it :( Since then, I have to enter the mighty recovery key to please bitlocker whenever I select windows from grub.
Seems indeed that upgrading to Royal Numbat modified grub sufficiently enough so that BitLocker automatic unlocking stops working. 

- I tried to suspend BitLocker and reboot, no luck.
- I tried to decrypt the C: drive and to re-encrypt it from windows. When doing so, I can check the "Run BitLocker system check" and after restarting, BitLocker warns me that "The data drive specified is not set to automatically unlock" and as a result won't encrypt: "C: was not encrypted".
- I tried to encrypt unchecking the "Run BitLocker system check" and then, encryption works but auto-unlock won't work and I have to enter the recovery key each time I start windows.
- I tried to decrypt, then clear the TPM, and the encrypt again, no luck either.

Seems to be an old issue since there are many posts about BitLocker suddenly not offering to auto-unlock after an update, but I did not find a solution up to now :(
Thanks for your help!

---

### Post by willabeer on 2024-09-09
Tea for One:  When Windows is the Boot's first priority, then Windows opens without asking for any passwords or without entering 48 digit encryption key.

---

### Post by tea for one on 2024-09-10
> **willabeer said:**
> When Windows is the Boot's first priority, then Windows opens without asking for any passwords or without entering 48 digit encryption key.
How is Windows 11 decrypted?

---

### Post by willabeer on 2024-09-10
tea for one:  When Windows 11 is first boot priority, I would say that Windows 11 is using the Bitlocker key that is stored on the system.  When Ubuntu is first boot priority, then when I try to boot windows from Grub, it then appears windows 11 wants me to enter the recovery key; It didn't require this before I updated from Jammy Jelly.

---

### Post by willabeer on 2024-09-10
pspathis2:  Have you tried the method in the link that Yancek provided?  I haven't as yet.

---

### Post by tea for one on 2024-09-10
> **willabeer said:**
> tea for one:  When Windows 11 is first boot priority, I would say that Windows 11 is using the Bitlocker key that is stored on the system.
When you enabled BitLocker, did you select [COLOR="#0000FF"]Let BitLocker automatically unlock my drive[/COLOR]?

---

### Post by willabeer on 2024-09-10
I am unaware of any such option, nor do I remember see this option anywhere.

---

### Post by tea for one on 2024-09-10
Do you have TPM and Secure Boot enabled in your UEFI settings?

---

### Post by 1fallen on 2024-09-10
BitLocker stores a key in the system's TPM, which will fail to verify if it detects tampering (this includes BIOS setting changes, and other changes to software and hardware).

If it is the Home edition, please right-click Start->Setting->Privacy and security->Device encryption. Turn "Device encryption" off, and wait for the decryption to complete.

If the option is still available after decrypting, you can turn it on again if you still need to encrypt the computer. Please note that it may create another recovery key and upload it to the Microsoft account, so please check whether there is another key saved on the account. You can also check the currently used recovery key locally by right-clicking Start->Terminal/PowerShell/Command prompt, and enter the following command:
```

manage-bde.exe -protectors -get C:
```

The recovery key is listed under "numeric password".

This Advice was offered to me by "Johann - MSFT | Microsoft Community Support Specialist" (Note this was virgin Ubuntu install and not a upgrade)

And it worked for Win11 Pro as well, I did it for a friend, as I'm not A MS customer...

---

### Post by tea for one on 2024-09-10
> **1fallen2 said:**
> BitLocker stores a key in the system's TPM
Yes, if TPM is enabled (Windows 11 pro)
With TPM enabled, you can also change [COLOR="#0000FF"]How the drive is unlocked at startup[/COLOR]
If you always boot via Grub then the change (Pin or USB Flashdrive) will stick
If you decide to boot Windows 11 via the UEFI menu, you'll have to go through the laborious process of entering the 48 digit recovery key.
Then, if you change your mind again and boot via Grub,  more onerous 48 digit recovery procedure.

However, you can also use BitLocker encryption with both TPM and Secure Boot disabled.
Choose to enable BitLocker with either a password or USB key and Grub can be used to boot Windows 11.
Grub will require the password or have the USB key attached.

I don't know where the key is stored but, because TPM chip is not involved, Grub manages to boot Windows 11.

---

### Post by 1fallen on 2024-09-10
> **tea for one said:**
> Do you have TPM and Secure Boot enabled in your UEFI settings?
One good way to check is:
```
[ -d $(ls -d /sys/kernel/security/tpm* 2>/dev/null | head -1) ] && \
    echo "TPM available" || echo "TPM missing"
```
Mine shows it "TPM available"
> **tea for one said:**
> 
I don't know where the key is stored but, because TPM chip is not involved, Grub manages to boot Windows 11.

this might help us or you :P
```
sudo cat /proc/keys 
```

BTW Why dual boot?? If you really need windows and ubuntu, then a second drive would be Ideal, Or a virtual install from Windows to Ubuntru, or Ubuntu host with Windows as a Guest.

Dual Booting is at best a hit or miss>>>>YUCK not for me anymore....

Any-who Good Luck to the OP

---

### Post by tea for one on 2024-09-10
> **1fallen2 said:**
> ```
[ -d $(ls -d /sys/kernel/security/tpm* 2>/dev/null | head -1) ] && \
    echo "TPM available" || echo "TPM missing"
```
Mine shows it "TPM available"
Mine too, but it does not indicate [COLOR="#0000FF"]enabled [/COLOR]or [COLOR="#0000FF"]disabled[/COLOR].
My TPM is disabled
> this might help us or you :P
```
sudo cat /proc/keys 
```

I doubt if a BitLocker key is stored in an Ubuntu folder ;)
> BTW Why dual boot?? If you really need windows and ubuntu, then a second drive would be Ideal, Or a virtual install from Windows to Ubuntru, or Ubuntu host with Windows as a Guest.
Dual Booting is at best a hit or miss>>>>YUCK not for me anymore....

Yes, dual booting adds an undesireable complexity.
The following truncated text is good advice.
> If you can possibly manage it, have one OS per computer. 
If you absolutely must have more than one OS per computer, at least have one OS per disk. 
If you absolutely insist on having more than one OS per disk, understand everything written on this page
From Recommendations here [https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

---

### Post by 1fallen on 2024-09-10
> **tea for one said:**
> Mine too, but it does not indicate [COLOR=#0000FF]enabled [/COLOR]or [COLOR=#0000FF]disabled[/COLOR].
My TPM is disabled
It will in the Bios under Patform
> **tea for one said:**
> 
I doubt if a BitLocker key is stored in an Ubuntu folder ;)
True but you can see them from a Linux Machine:Or, You can access the BitLocker partition under Linux using Dislocker, an open-source driver that is using FUSE (or not).

Note: You need the file on a USB key (the one with the .bek extension) or the recovery password.

More on Dislocker:
```
dislocker
dislocker by Romain Coltel, v0.7.2 (compiled for Linux/x86_64)
Compiled version: master:8d42bdd

Usage: dislocker [-hqrsv] [-l LOG_FILE] [-O OFFSET] [-V VOLUME DECRYPTMETHOD -F[N]] [-- ARGS...]
    with DECRYPTMETHOD = -p[RECOVERY_PASSWORD]|-f BEK_FILE|-u[USER_PASSWORD]|-k FVEK_FILE|-K VMK_FILE|-c

Options:
    -c, --clearkey        decrypt volume using a clear key (default)
    -f, --bekfile BEKFILE
                          decrypt volume using the bek file (on USB key)
    -F, --force-block=[N] force use of metadata block number N (1, 2 or 3)
    -h, --help            print this help and exit
    -k, --fvek FVEK_FILE  decrypt volume using the FVEK directly
    -K, --vmk VMK_FILE    decrypt volume using the VMK directly
    -l, --logfile LOG_FILE
                          put messages into this file (stdout by default)
    -O, --offset OFFSET   BitLocker partition offset, in bytes (default is 0)
    -p, --recovery-password=[RECOVERY_PASSWORD]
                          decrypt volume using the recovery password method
    -q, --quiet           do NOT display anything
    -r, --readonly        do not allow to write on the BitLocker volume
    -s, --stateok         do not check the volume's state, assume it's ok to mount it
    -u, --user-password=[USER_PASSWORD]
                          decrypt volume using the user password method
    -v, --verbosity       increase verbosity (CRITICAL errors are displayed by default)
    -V, --volume VOLUME   volume to get metadata and keys from

    --                    end of program options, beginning of FUSE's ones

  ARGS are any arguments you want to pass to FUSE. You need to pass at least
the mount-point.

```
Or the Man Page:
```
DISLOCKER-FUSE(1)                          DISLOCKER-FUSE                         DISLOCKER-FUSE(1)

NAME
       Dislocker fuse - Read/write BitLocker encrypted volumes under Linux, OSX and FreeBSD.

SYNOPSIS
       dislocker-fuse  [-hqrsv]  [-l  LOG_FILE]  [-O  OFFSET]  [-V  VOLUME DECRYPTMETHOD -F[N]] [--
       ARGS...]

       Where DECRYPTMETHOD  =  {-p[RECOVERY_PASSWORD]  |  -f  BEK_FILE  |  -u[USER_PASSWORD]  |  -k
       FVEK_FILE | -K VMK_FILE | -c}

DESCRIPTION
       Given  a  decryption mean, the program is used to read or write BitLocker encrypted volumes.
       Technically, the program will create a virtual NTFS partition that  you  can  mount  as  any
       other NTFS partition.

       The  virtual  partition  is  linked to the underlying BitLocker volume, so any write to this
       volume is put on the BitLocker volume as well. However, you can use dd(1) to get rid of this
       limitation -- if it's a limitation for you. An example is provided in the  EXAMPLES  section
       of this man page.

OPTIONS
       Program's options are described below:

       -c, --clearkey
              decrypt volume using a clear key which is searched on the volume (default)

       -f, --bekfile BEK_FILE
              decrypt volume using the bek file (present on a USB key)

       -F, --force-block=[N]
              force  use  of  metadata  block  number N (1, 2 or 3).  Without N, the first block is
              forced.  Without this option, the program will try each block until a  valid  one  is
              found

       -h     print the help and exit

       -k, --fvek FVEK_FILE
              decrypt  volume  using  the FVEK directly.  See the FVEK FILE section below to under&#8208;
              stand what is to be put into this FVEK_FILE

       -K, --vmk VMK_FILE
              decrypt volume using the VMK directly.  See the VMK FILE section below to  understand
              what is to be put into this VMK_FILE

       -l, --logfile LOG_FILE
              put messages into this file (stdout by default)

       -O, --offset OFFSET
              BitLocker  partition  offset,  in  bytes, in base 10 (default is 0).  Protip: in your
              shell, you probably can pass -O $((0xdeadbeef)) if you have a 16-based number and are
              too lazy to convert it in another way.

       -p, --recovery-password=[RECOVERY_PASSWORD]
              decrypt volume using the recovery password method.  If no recovery-password  is  pro&#8208;
              vided, it will be asked afterward; this has the advantage that the program will vali&#8208;
              date  each  block one by one, on the fly, as you type it and not to leak the password
              on the commandline

       -q, --quiet
              do NOT display any information.  This option has priority on any previous  &#8216;-v'.  One
              probably wants to check the return value of the program when using this option

       -r, --readonly
              do not allow to write on the BitLocker volume (read only mode)

       -s, --stateok
              do  not check the volume's state, assume it's ok to mount it.  Do not use this if you
              don't know what you're doing

       -u, --user-password=[USER_PASSWORD]
              decrypt the volume using the user password method.  If no user-password is  provided,
              it  will  be  asked afterward; this has the advantage not to leak the password on the
              commandline

       -v, --verbosity
              increase verbosity (CRITICAL level by default), see also &#8216;-q'

       -V, --volume VOLUME
              volume to get metadata and encrypted keys from

       --     mark the end of program's options and the beginning of FUSE's  ones  (useful  if  you
              want to pass something like -d to FUSE)

       ARGS  are  any  arguments  you want to pass to FUSE. Note that you need to pass at least the
       mount-point.

FVEK FILE
       The FVEK file option expects a specific format from the file. The file is split into two ma&#8208;
       jor parts:
              - 2 bytes describing the encryption in use, from 0x8000 to 0x8003 for AES 128 or  256
              bits, with or without diffuser.

              - 64 bytes (512 bits) which are the FVEK as in the FVEK key protector once decrypted.

       The file is therefore 66 bytes long, not more nor less.  Note that you may have to deal with
       endianness.

EXAMPLES
       These are examples you can run directly.  First, you may want to copy the BitLocker volume:

              % dd if=/dev/sda2 of=encrypted.bitlocker

              This  will  copy  the  entire  volume  located into /dev/sda2 to encrypted.bitlocker.
              You're not forced to do this step, but this will ensure no write whatsoever  is  per&#8208;
              formed on the BitLocker volume.

       Then dislock it:

              % dislocker -V encrypted.bitlocker -f /path/to/usb/file.BEK -- /mnt/ntfs

              This will create a file into /mnt/ntfs named dislocker-file.

       To mount partitions once decrypted, use this sort of line:
              % mount -o loop /mnt/ntfs/dislocker-file /mnt/clear

       --

       It seems that you have to unmount the NTFS partition and the dislocker one before halting
       the system, or you will run into unexpected behaviour. In order to do so, you may run these
       commands (replacing your mount points):
              % umount /mnt/clear && umount /mnt/ntfs/dislocker-file

       --

       Note  that  these  are examples and, as such, may need to be modified. For instance, you may
       want to change the decryption method used in them.

AUTHOR
       This tool is developed by Romain Coltel on behalf of HSC (http://www.hsc.fr/)

       Feel free to send bugs report to <dislocker __AT__ hsc __DOT__ fr>

Linux                                        2011-09-07                           DISLOCKER-FUSE(1)
```

[COLOR=#FF0000]**Please Note:**[/COLOR]
```

It seems that you have to unmount the NTFS partition and the dislocker one before halting
       the system, or you will run into unexpected behaviour. In order to do so, you may run these
       commands (replacing your mount points):
              % umount /mnt/clear && umount /mnt/ntfs/dislocker-file

``` > **tea for one said:**
> 
Yes, dual booting adds an undesireable complexity.
The following truncated text is good advice.

From Recommendations here [https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

+1 To all the above

---

### Post by willabeer on 2024-09-10
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYgAAAAVCAYAAABczHkPAAAHyklEQVR4Xu1cTYhcRRB Cy7oQnY1P7BJWA2RKCRCQFH0ELyISARRQS8iBvUgiod48qAS1IMncxB/DioRbx5UBHPwaA6Kf6CYgAZDcJO4sJtINrCKK0RroIZvvqnq7jfzxjcba067 /p1V3/181VV9 zENw9svljFJxAIBAKBQOCSR CaN7 utceJIIhaeMXgQCAQCATWLAKXJEFse btamru urY/j1rVjFtCb7jwMedpY8fuLctEWJdB4GbPjhT/frei9Xip2/1jdh09xPV1Y 8UH374Jba K278c7qumcPVT /sq 68N1nPe/vPHikWj1/NuyhNqrNvSB6Xzj8bnX60HPNTVo4U22CuPjvR a2jKlwzZEPa4sgJLhO77zF3J8oWD6zex/teX72y8PVyVcf7/5NjMHDNvWsKVBTBLH7naPVZeuu6i7Fsjclw7DzbN33ch/Oy8e aizISdBcmf pR2/DylzyfhBEGiXR 8Y991XfP7arZyAGWMs2MJ6xjcsztR15tnTko0YCtRWjPJIfJUGIHBtu3dvFixOQ2gQhLSYFeVwDRFsEgVZpBRHLgMXoVuaPd4KXZHJzDz9vZmyqSC DLAkwJWM8gpC/T85sWBNVmYWzOFlTJPF/IogSmxmXMaUEYZGI7iFFAm0RxH Fr8SYmV239RDsQAQhAitJYLaLGfTfF37vY3J5zypZMTNmhsf5OYPyHJVZkWWR967Yem0XdynLlb15P6vLS91MEbOLHDmWEoTuV2W48ua7OnItfPJGT7mvRLJy8kczgxFs9PPH6V 6gZyxkDHchsB3MWNCw5T1zx/9ws2aWW 4hrYwdD6ppv5aPNXXEkH9so5UL2hjuE U1QoUFsGhPpk8LJm1xLfsh53Yw0PtDMcj6acyupSerOwzhZVlF16LSaulElsapY/z tx2aYsgWKeoT08Hlp4FO2kT6kdjTMov2AfYbmUulYfX5Dgg M3svr0nCRyYIGRhLH0EiKm5HV1S8DJODIgyh4C76Y6HOkIx6fDYOgSBZxCptgkSFmcI8vuJ1/d3AjUHyFS5r07CbQjLgHGP8vPUths65DB7z5PdlogodvXcQjW5frZjO9iS4sDEeuFqivXC /KwEpwmp9ebpM964jUtrKyAxo7A LHsXoLgVRBI6li5CWaIgzqZBiD9XR0tV0Gk8OB981jUJ2d0jCPKzPOmsOI1c2cQSBDsV1ZVOSofz3UG2iIIr7JI6aBui8mzvZTdaiyQd//87YR7ziTjPBsYmiAslkstiELLYZsGP8nOLMdD8AclCM9wRBZUFCpUANv 1MFOQLSqi1yQKK0gsPWhBCHtJnlfD9kFA5FDZC0hCFybDVH2suX p3v2hZlEnTMINFo8yMRg5Tn1IATBvVhvbqvPjJmWtTbaiDUv4lKiew8Pb99W9s5j2f5RZmssZti4J5Z/UIJAW JEBWVtysebIgg B8Tq0TqDUN14ROAd5KfstSmCkHkmpzd2kkmrRYR6SJ1leOebQxOEGOHyD5932In7416Wjc6mwY zODU4NOamCIIPkzV4cGDTYGy1BeRZqs3kEUTKOFHZ4vxSMWjlIFUDPmeH9A6QLYLQ2y5W9lp6iwkrCm65qGxCPE0TBO/bajNZCYGW1yKTtW/UvVX9pgIsy5TCI0eMFrkpgbP941wWQXhYcdU4DEF4N6dG4eNNEcQoziBU5xgTuCUo lB7bZIgtKqz5mSbUZkwVovtSGvburk4MEFwO4gFSRmdGrMIiYLlKggx7DMfvta95pc6g8BSGANGrh2iWYIYkbaXBrlCWFpBcEtBswElzNXlc9X8 y912lweQdQpZa2gwucusnbumivimMqoPadW 8DqJddiyrX1FEuLINAeL9 8ve/8o04FIXjj2ZRFEN4tpxRBaBtAnXfYCsK70MAZ7ygIYhQ niOI1C0gxSLVTVCf824qlRxSI/mm7NXq91s wR0X9jXEpIQgsLtTcuFlIILQ4IBsWXoGgZWBHBSjkLkzCHbMQQkCMwgGVTNNzkxLjAMDxSAEwdm7JZv1/Q5 L9diwqyPe/GlFQSSUsrpuH PGDHh5wiiVDZLHq0alZCGOYPI3ehK4VFCEErYOYIQvNQHOcinsGI/GwVBiJ41q27Kx3MEoQFebwXK7xyXRk0QiHuJDqzLHKlOTIog OyMyYV9T4mQ7QHH1SaI1PcgsHXj3WLSxb3 JZfY3Jvlss1q87AhsVFwC4DJwGN buOkvpTUBEFwZppyEA XVItJ5 d9WddBeX7WL sN9cI3K/SZ1brLHQRze9DKgqw2jeyV9TXoLSZ1PMWvRAbes1c5aYKCuscWE/6dbZ8vEqSwsjAqucWECUqusm7ax0sIgnWTs1PFU7FMJYLeM/YNPtPD70ahrWAc0vVR/xqXUomTFeu4jS161apZ94sxr1GCaOpfbYjxelc2OTDG74FAILD2EAgfb1dnOQIvka52BTEsQWjWlvseQYnwMSYQCATGD4Hw8XZ0Yn0HYtj/eFGbIBaXTsV/c21H/7FqIBAIBAJjjcBEEMRY6yeECwQCgUCgNQSCIFqDPhYOBAKBQGC8EQiCGG/9hHSBQCAQCLSGQBBEa9DHwoFAIBAIjDcCQRDjrZ QLhAIBAKB1hAIgmgN lg4EAgEAoHxRuAf7aW87tjzUGMAAAAASUVORK5CYII=[/IMG]

tea for one: Secure Boot was disabled before I started this.  I started trying 	 yancek's solution which required turning off Bitlocker, which I did.  Before proceding further, I did a Ubuntu Boot-Repair to see if that would repair problem.   I then went back to Windows and turned on bitlocker, which then bitlocker wouldn't do auto-unlock nor encrypt.  This seems to be the problem pspathis2 has.  I then turned on secure boot which allowed bitlocker to work.  I wonder if the simplest solution would be to uninstall Ubuntu and reload a dual boot or just rely on the booter to select the OS.   Are there any good instruction on how someone would do this?  I'm fairly new a Ubuntu and need some hand holding.

---

### Post by willabeer on 2024-09-10
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAmUAAAAwCAYAAABQUw1KAAAek0lEQVR4Xu1dXciuWVn NrglJ9yj8wPjz4QoNqChUI3kgT8HEWIQKehJSFIdROKBHXWQ4VQHHeVBJB5UTEQnHlQIIyEdZB4YZYKhgmniNKMOzE/NFnbiDnZer1yv13ft 77Xet7veX/23vd78n3v zzPWve61v1zrXutZ61L1578 o2vfOgtZ/1ZhsAr3v HZw 889fO/uOP3n/23S98 uyNf/7ls2/86Yc2//unuras1lvnbsUHUr/6Ax89  Kvv36qAa/67T/b3PfNP/6NqftvtZte 5G/O7vyujdtxX72nz91rq0v/ulfOPvJ33n0XLP 6y9// zpxz5 qzV1NXmhT3e96qfOvvaRX16lzJ/5xLdXKacLaQQagUZgTQQuPf7oIzfuZGe/BpgIohnpqK6tUfetUMbSgPq6j3727Ol/ OvbkoSADPzvt/7zTAdC I3EjIRMSRjwuNMHTiCy1775pbNvPfq7q6h8k7JVYOxCGoFGYGUELt34wQdl mgdTuvf3vvybXWavfCRvAYQzwpVzhT3vuDFL93UcfUr/7IdBSMIvegVr9nWTTnckWbZA3/ qU/9xTlnrvVqu9HGe3/undt6mQXTeimn4sGsEB/8v / 9zYrpIQkygA5zijD5UA77//5X9li4u2O7gfRdhy8j //xd88 4lf/b0wY Nt0v7RTI8TDBambfXMkOpVpM/ez wHLVv7CXi88P5XnsukOBmekRnlz qGt3umfPTH9eefvSnbA6zuevChDfEC7ve95V3DrKL3neoc2uH9R8wzHdd iOyysvnIXrUPtb rvq18h8qk2Gf9FdmstrFJ2cqRpItrBBqBVRC49Pn3vGxDyvzjZAHOD9NPDAZ0tPj 8nd/cHMtygplU3eaHWAQufrv/7SZtiEBQNkgIwhW j/uRxC8fPe9YQZBZfdpRlxTUoPvCPr4oG4nAKgHH5820WyOE0 0 fkvf24zJYVr168 s/nfSRlku3zPAzdN02nZlJ/EUgM4SQT cmpQ2x7hwH4jiWB7tU78f/nKPdsytX1OLBxP6pGXN5v5Un2K hnYRu11/VCsZ2XOdANT0toez2bNlE 7cf1CWyDr3a9/8wZv19fMyl2XgMu1J7620VMtD89DvmtPfHWjZ6MsZGSX33/6yQ15j2we5aueRXrFuiMbvuvB1075jmjwgt9oF qXvJ7Mv63iQbuQRqARaARWRCAlZXDeT/zVH2zWSGm2Rx085FBn6NNU2dRdRqg8uGngiQjN3W98202kzB0yAyiC4b1vf 82I0EMGYjxHYHHg2aW3dAgEY3wScQ0CEK2lzz8ji3BqwirBkANiJpJ8eBbkVjigHIjgsD2RJkayvljL3v1loADLxKIKPOVkcOR7roO4Tv7eUl7dRDBQUMls5Ndkg0S GiQ8u2/ ZNNc3Ytn1h43Zp1y7KKTq508MCBBmzXCWREbihHZZckVm7zERlm1g/3qlyRDTMrWPmOiGShrMtX7tvakso syaxM2UjS zrjUAjcAwEUlKm2REGZQiIbJJmmjSIa1aIATBanIvynvns356bUlTyxMXyKO9//vXvN2uLPAhl65TcISsBwbovZrAgn9fJqR2fCqID11E5M3gR8VTiqkFQ783k9wBUkRTHUTNvjoPW7dk/XHvwfR/eEFzvQ5ITkAOfhnScqMAVORwpuWcdtf1Vex1bZiBnZdbspusGyCj7m/LTJh74pd86t2g/w6TK7HrdrIPTgiPSi/s5eMC6K7yAoh8ONEYZpMouM5t3PfP U31yG1aSXfmOiGTptCXa6ssfRpnZJmUjS zrjUAjcAwEUlLGYAgnzwCXEScIjmkTON3nv/iZLdny7xrQMlKmAUgzST7Cz9aqRRkETnNGQT1avxMFJ89QoS2YDnLSpCTQM0t4hm3KXgwYBTm9jrKQreGLGj7NqIFJ5awCoBM2DeQRYYuU1jOcmtEYKfloXVHWXmKLKUBmyfDbrMyVbowILrOiVduiTBzur7KNkb3hmSwbzLV1UQYZz40ySEsGS2rzqmfef2qPUbaRg6TKd0R xHVfsa ygbyvSdnIEvt6I9AIHAOBlJQx8wChuF7Jg4ROieE zRD5WihtXDQl6NMszFqBpC1dq5atm/Kgkzn2ESnL1pORkHFBva /I0nAOhonpcQnWp mW21o3ZphYV3MaFTkxrM2uo4o2o6B7fHpw0xhVUafZqqUfNTPVXtJyrCuSt/Sm5W50o0qezdbPvtHXzqhjrPPdMmA6opvJaLkiv2l6zCjaXiWV73BWNkls21u86pnUf RIDmRxHPqWyrfEZGybFmBy B20aTsGGGm62wEGoFZBFJSRpLFdWUskIGE3zWzpW EYRoHo2B8ov2mdKSqQZ9v1SHIYC8nBIMrb3hr WYdZfE30vwNOb/OYJi9aehTJPo2Jtud3UOZcP361ee2a998XZl3lAc5TBf722u 3gxloK1YnA yhxcmPBPnJE3xB9b4RHtARSSRb8zimdHUmpM8ToNGL2mM1iRq/2l7uU1CNkXofRTJnOkGyZ4S410wQTleh091upzZVCinNak7/jauT9lmRD1yEiO71D53AqTr/9heTvu636jeBHbfofZJm3a94u/RdL/uJ9ikbDY09H2NQCNwDASm1pQdQ7Bd6hxNz xS5prPZC8 rFnHmmVVU2sXqSd7Y/MiZd5Jz85Mz50aHqO3Pg8tb09fHhrxrq8RaARmEDhHynRE6nt7zRR27HtOzfETD2ZAsszHsXFj/Z7NwO/RFg4XkXd2jddF6ridnx0t1j/Vtp8akWxSdqqa0nI1Anc2AtvNY 9sGLr1jUAj0Ag0Ao1AI9AIHBeBck3ZcUXr2huBRqARaAQagUZgLQQ6Q7wWkvsrp0nZ/rDtkhuBRqARaAQagZNBoEnZyXRFKsilZz732A2 8ZidY3iMZqy5BmWfC z9rcZjYLWkzlNdd7ekDWveu6aerSlXl3VnIpBtKn0INE79RalDYHAqdSyNWbN916TsVHo4l PStSe/fgM7uZ/SZ6lCjmRf4uiWkKy15Ry1Y3R9Rp47lYREOnCrLpp3PYj2lvNtP3ybjFMagI30el/Xl9j6WjJkm16z/NH1i8gxau/tPmDzLWd8KxnfGglYZ8ecXaQfZp5Vf0W5qpeuZvuuSdkM se959Ljjz5ygzvCH1eUH9W hETNyDzr6GZIjda3tpwzbanuGclzu5CQXXCKdGB2dLlLfYd6xjegRb268TK  /5t0IMff hnw/0DDyX3setZautryTsiRqPru8ox097bdcDmm3oDQ99UONr B0TnWAmL2ZhFfdDzbisdaVK2qwUd7rnt25e maMbaLSLOMXUEUe1k7w3y7dgYDk qtdz7fwZ32l8JFO1QamPlLLNZfXEAO6Q7iOVjAD5xp8oSw2FZY92t/fNX7Hxq PmozzHTnFV4 b/zKZUfepZGh99qgNkudA1fDht7rqn7dCMjm  ym1bsvtV33SUzDK9L3wbGK8v2uQYdVRZJ9cp3whYZVTsluAajaB1L7johIrIxbjD9nIVQ 2zSBe1fMeA5c72c6UvlU5XJzEstfXM72SuOrJz71PX 8jmK93O/KfWzW14svZS/tHGxrgvalOFMZ7JdEZxq3Td63TMZsqHfkZbPOkpEn68XNavIx a9VfUJ16Ht5V24sfW0W/iedzjx/n5aRlaT5Oyw5GrXWtKF/pH59ThuBc/OgjfX/7uD26OYhoRCQ S M4jZLS aFd7BKzvfecbmwPRPViMZNJd8UdH5kAmPYHAj9FRQ9ZjmqIzN3mYuhtFdgyUHzWjh7krtpkDGaWw9bgaP9bKj8VSR Dl6tE5eqRPdr7jzLFAxEQxYCDgeapRZsuP28k2po2yADq69JEynSt1TTHQ/x1H7WvHQ4 cctKu2Sw9P/W7X/j0JvN114MP3TRqz44aggwaiKCnOH4qOrFBg7Ieug55cByY2icDm9rbKPvqWTvgjBMYZvs5O0ZK9YVnb/JeylkNJiJdqmx9ZFvEMZKXuI6w8hMRKt32wEv91jN6XRfdt/l1PaNWjzSr2uQ4Kk6qg9GRc6i/8t3UY/a12 hM d6n2mbF1/U9C6iR7VPfqv4aZSFxnYNkj6OsM4t/6le036I2NCnblSod7rmUlEEReMSSZpfcmapRjY7JYbPcUNRZZcQOB1HjE53rV8kUnbmXHZkTOV4N3B6A1dDQpuvPPbUJONlUgcviwVbJVkUes2A8MnwPUkoqfTSZkRD0MQ oV5KHvskcQkTqmBUiphzxoX81m6R96 XogAD1ZycQRMHQ 4hyoG4nRR4cogGLHpROPXeCqP3twUwD8iyuGQGlvI4xfvdMg9qkBm0N7ur0cY8SyGoKOCOsUYCu lnbqfoCwhr1xcxRYxex9co9u216lmNEjHi90u3Kf2YkZEQq3d/oJs zbULfPPi D28GD5XOODG69sRXtwPhivCrje5aflU3s25V5jvTt 8//eQ2OeG aETGHV Po9kgmG1h3933lnelZyqrTzocveiadkFg6pglBnNUgKyTTrOo8/bd2rM1Tj6dooE ekadMkfeTMtHjt8DCh2dGjXBUqLiBhct/GTmxA1N5c7WA3gAqxyhEiYGQj1MmiMezV5opsOVocpi4mxRGLQefI36 V3l5O/R4vLsFAjFtSJDvvaJRI Ht3v/ HRtdmJCRByqAYRnIjXYRA42WgcUEUQt14Mk5Xnqkx/b2Jh IlyrDF1FTkF6I2Lm8mhw9wXSOu1dBfssa7Okn0fk2XWegwvgd/cb37bNLno5F7H1zNE6YaTdMmM IkZ6vdLtyn iTpTzole8Zpt5wW9LB2y0eZyj67MTuMY2ud/j75XOEL8lvhvPaB/OlE//gTOY/fzlyn6AVUTMItunvmFWA2c186O aGbgorM/6m jgTymL7V8YjFzYkxnynahSYd9JiVlNDYQAWZGMqcDkTE14iN8/65ESDMLqoROVLKRHx1T5jQimXz0qd/9Gp736QTtGh p0WEgC8fRonelO2UP5p76V0PVjB3LrbIZXndFQrydHsCYBUSZrgujt5Mq8ory9HpEhhgQsG7CA7APAjLTifSwykRWgwt3sFlWNCIkGkwjgglboz6PcGWgjdbwVVMY2dR3lAFgMPMBguJcBfuKlNE GWyzfna9VX2Jso04fBzYuX361DGXXKgtKYlzW8d3D yubzODvuoNOrXxSrdHA7YIU2 vyl4N2HCfLv/Ad/Vb6I XPPyOMwwm1O9VOsO6Z IJp6bpj7mkY6Z8POOzKKw7GhhEfrXSAx38VP1VkfGRzmSETuPfqz/w0c0AWqdAM1/YpCxD5nR T0kZDRWiMmPiRuQKpQZAhY1G Ro0mK5mcFGDZ1YsCzycptCRXCWTT5vouoyIlEXTWOw6n3qks8JfnR7Vrta2RY5QA5xmBzlqdoe hJRVJMQzK hHfPjmEQOjrjHCdZ/yjNTag2pEuhnwnDCoo4syqNV6EZUlImVOiH1gcPnue7ftRzuZXapw1DqdkCjxrYIgp Rmzp5Fuy5fuedchlNH QyYXEtG24heaFDCq3bBwHb9 WdvWpOWEVLikNnPkn6u9EWDnfsbtU 2mxm pbaeZb5d3z37Qv9Fgh0NrLQMnxG4 /VvPte3vLfynxHh8YXgLnc1YBu1iTpw/epz2 Uulc5o3aN4UtlotoTD28Y UN/JTCL7RWcF6MejNZgjfav6K4sJI3wzQkdSBnlJVL0s9VvEpUnZ6ZCvTJJyR38oBNeVKRnRtz90RE8njHuRSsVImwFXBdD7kCZGYFGCxXs1HetTidUbmSoTnyOxo0GiDgQnjqxpjC948Us31Wdvgvo6HZ0K0nVlkcPmiAbXPDuVpalxL9oKkoBRI0a8lBHXsrdPPdNSOTg6UUx5sD4lYFmq3/skmhbzgOYjXHc66jS0vCww jRGlGFSOaFv0GntC/a9Ok6VA/jjA3IzwlH7XXVNp0OqIEjdgF7yk60D836jTmNdY1SOX2f5DFxZfex/XmdbIqLseu9lK0GJ6luiLx5gvO/1OmxdM2GqNyNbj/pcSbu2WdsLvcGUVvS2aWYruF/Jgto6f8/8p0 hKfmO2ku5RwONqk20HZ8izHRmVj9GA5fZ8lGf66DGDhJ0xTl6Kx3ljPQt8kWjgYvLh5iHD30RB pZ/MtmlvA8khU AGtS5hp4et n1pSdntinJ9FMgDo9qVuiRuCHUzw6TXQrYDJaPL3PNmhGa5/1dNmng8Ax9W1NFJqUrYnmfso6R8qUjc9Mn xHpFunVB2tZaOrW6c1LemdisBoEfgp4lItnt6nvLPrGPcpQ5d9eASOpW9rt7RJ2dqIrl/edvPY9YvuEhuBRqARaAQagUagEWgEZhEo15TNFtL3NQKNQCPQCDQCjUAjcLshcOjsYpOy202Duj2NQCPQCDQCjUAjsAoCBydlz3zusRt8m7LayXiV1i0oZM11LjNvwCwQ7dyt/mbWruXcas/dLgtfj4H7rbiw/hg4rVnnUh9wzDVES2VdE6ddyrpVfOCaMWUXnO7kZ45pTxfF/eCk7NqTX7/B/aguKvxaz6/tlJa8GbnEwewiJ1 mqDaRrHDEQmPfL0zv30WmXfptbSPL9tDaRbZTeSbri9slOPgWAL6foL/Gj36Z2RR3H/2nPmDGBo9JnJf4qxmsZvdZmynL7zmUv1kiW4RfNYg8Nd jPj5qy9r6sQTbmXujGFrZE 4fnc07U   7jk4KXv80UduPP3Yx/fVnp3KXVvpZp3SUgeztpw7gWUPHUqmYwatNXA6RBlLg8MhZFqjDu6TpXtt SbQviEx6oXOHGsAOOsDiM9oo9c1cMzKWCrrSJYlA81RWX79UP5miVwRfmsPIpfIc5F7o7asrR8XkW WpN/KA9GDk7IbP/gAWN/M0EFUpfaN 3SEvGRzTd/UL9vEsdooNts8NZOp2rjTR/Ysw3/naF Nw0lKNjJTHL39On3s19hOrUc3J VGu9z9n8YSZSb0Hq1TN6Wsnsc1V1TP/EV9 8L7X7ndfRplKAlWvEZyuP5lZ76pjGgn9uLC2Y/4 FR91sfeVupidT xi/qi2shSCQH/p5wjTNQ5VvapOhPZvWa/sk1rs5Mc9EQP37U/c/wjPDJdjXTf6/C2UkcrG8Q9vgO n3AQtaXyKzN9l8ma9aWXiS2McCg29Rsy4jce20WZtU 9zmhjXzznGVDvs2z7pEiXRhvVZvrnmzlzM20mFNR/aBm0H2 ryry273EC6Nuo6JFfkR6rj4/aEv2GfprBLupP1eesjCpW6fNRDMV11Uv318o1vJ95GgnrGPkLtwvV92oD ln/n/mxNX9PF/o7KeNRFH5UkR5ZMtqF2Tsf33mEk9anxE53k//ed75x0 G4KGMkk57dVjmFaDTlR/lo4NHd6Z2UoR4ezqvtdlLFTTtn2kmCAOcJJfJDxHF9lMFS Xn/81/8zBl2gff263Eu2gY/pgZt1R3OPYixb6NTC1AuzhT0QMnf6Wy4Y7gfm5KN1L2uSCYGG5R514MPbbM46jQjcl3pRNbX/B34E28/KYGOgQFjFhPvGzhA3f1dzz1UO/NslpIttyl1itlxMnr0zWiaXfFwG2D7tTzqPvtsNPLGdRJo90u0kcyfaP9nNuBOeIlf8TIzWf2YKtXTyFehXJyMwhMd6Bv9zFjqnR47xXtc3922gZ0e7ZVl4TJdcrnVX2XPRDZY dtINzTz6Xo/a2ezvsfbiLqVHChmmaxKkKOTKqLfaDdqu6P VD2GLErAFTPFOzvhBWVlMfTylfu2x7Sp/qt8MwO5SA62mwO4LIGheqv2OvLnB8 Uff49L9tkyvyDxvOIJQ18HtRVAarRopbvIGjHZMQOB5jjg4DjWZlKpig463E6VbaLgcCzcVFgQJuuP/fUxiFW06A KlDjIsnL2qltcQyJbxWsokCr2EWO7vrVZ246iNn7Gd95hE3Vt1FfkJRnZBXt4kjz2X/8xE2kPEvlR87/2hNf3bZFA5g7o1HwU2dVOaioLzyIKbH3DNQMJn5I9hJboOzRAd4ejJVEKY5OQh1jHF9TvUAUDf5ALJD1UTKpgTTLQquMelan66sOEiJ/Qp3CoMdJTuQrOXCY9SuaOXHi6b6WBN4HJ9HgK8pgRkHS66xISWXbmZ9TUkv75aBN68LzPMR89hkdHET NtINl1P1HuXN2NkS36N9SH/INVOelXPCvOS6YqGkR23X 1/702OyDkxHgyD1W 4D/HQQ99Gq/yqf62Vka5W/cFvmvVECw4lxFuOJQ2b3 /h96pglNgACIOukbFob7GnaLIvhIzrcd/meBzYBM3pGgyZHK0yBRkFRZXInoFkzd6be4Z7SxP3sPDd lTsjCiODU0XxdqLuiGjgvMpoxBspSxRonZwoSczaUWUFqr5V56h9TsXPRoesD/fp YXuUCvnkJEhTKnq acMIviL1LkHv0ontP6Z4KD6d UNb70p88nstONDGa9980vnsiJLbAFlaH/otAWuZSdUZJmjETmNiFmEEYmFn OoUx4R0SD2lEMHbqqvUbYWb59r cQimxZ32/IgP/IrlIdTi5GsPu2IMnXKLSL8OnUTZQvY5/CBXiez pG 88DryLZ5TTGpdMn9JOutnokIaOZvI90YJQuqgfIuvkfroz7Tb2lbsqwSsPTZA KbZUizszur/vQ 0/NL1Y4wne/kscqQLjl32eVjViqaEh/5C/ps6jkJv/MS9acz/vxkMmVULDh EqbM4WkA05GdTtW4AiDzxfUA6jQ94GcZITqIzLFFMvm0m373a3g G1Xgmo/sGOAwWqYyuPOuRqTZqFMdYeSctE/ufft7fzC18KM0sdfv6eFdDc8NUvvMR1DenyQaSjhmyWpEXLLMoP4eYTsaRTFDEhF1J4aOc6Qf1CcNYk5StVy9FjmjyCnO2KeOYjV4ZCNfb5tn4ng9y6yx3dFUezSKJ0GOHCnriuzASZlnoJnFygid hMeVo  nzk beRXsoAGmbNBYnSNbRxlCtXONaurpCzDx/V9iW1TvkqXIPtLHn7H2VOf/Ng5P1k9E9l45m jmFMNIvfhe9hGzDLAH6Ot0Cn4FLX/SI89a6fxFPhG7VuCXTbQjgg3bdZtJotVUQzNZr78wHX1M1Fmiz4Vfzk7oNnzKiHkcU/7vIrxlOlkSBnBhGCcYnKnH6WBOX1BwCLGq6Ntju6YfYuyRb7QFDJlpKySyafvUAbbFykU74 2r9ApLnVG F nMVTZ1OAqR6HPVJksdbKQcSkpU0UejSY16DFoabvZ5qpv2W9I5WuWR41 JIePqKMMjDsCL9ONUgmDGmnkUCqd0H5z0o5rVZ rg6HzxV 8rTjCRPtGsyBuCxWZnpk6oGNEZkltAs8iY8tAr4Rb 9wX7ao9uL/IBmMsL7Mxz9gx40zZMkJHO0P5DJxV9k/7uvIrVd NZI2mI1FvNgNBmWZIma6nRH8Cn1EAHdk26690iXVcv/rcdnkM9V2nnCt/U/nbjLRkU8tr x76ZPhIZK/85YmMDLNNSkCjtmS/zWKXZbiclCnRm41VWWIjG4hmg4uMlFX wgeFwJHr GhnarO8NuPPT4aU0VC4rowNopPjd1UyTZ8j9Y90KD6 7kXvQ1DFAjyMIjxlr9MHnmas3shUmfgcnRADCOQCYdSpKw342Zug/J0drQs4gQ3XOagCRAaXBUjcC5n4iaYmoYBXXvem7T0kvq580ZuXqmAq 6zhjQhC1rdcfBxlVHYhq1Vwchl9FJVNA6NMJXlZ8HP8o0FD1BcVKaK9gdzgg37nfnSzfYPnMvscBVyXt1oH5nWoLdIxZ9Mpahfu7KJpDy0nIw5uayoffAg PjLP/EmVqVdS4nVmfmXUd5WsLiPt1cv0vlO/qbrK57VO9B18CUg2MtFZAEV71bZpK57Jwe8jXYpwzJ6pCGjkbxUz6DDiVzWIXNv3qK/XhISTnmzAp1lVbwsHaIwPtNFZ7LIMV9S3u 6o4DEUWVEdgGt/qh/2wXaUCBn5C70OvcbHB4L4ze1n5M9PhpRlaU53Rv39hwiMRq N07oIzGYx1q21S1sLgdEU3Fr1rFWOZ8PWKrfL2Q2BY/rb9j279dlFnlrLX/iMxIxMRyVlysyzvWdmGnGn3KMjlJm1J3cKLvtop4/SUUfr6D6QPkyZ1WL9w0iwrJbZNXfLSu27lyBwLH/bvmdJL 3n3l39hWf1Id3S03QOTsq4eex oOxSG4FGoBFoBBqBRqARaARmELjUpGwGpr6nEWgEGoFGoBFoBBqB/SLQpGy/ HbpjUAj0Ag0Ao1AI9AITCHQpGwKpr6pEWgEGoFGoBFoBBqB/SLQpGy/ HbpjUAj0Ag0Ao1AI9AITCHQpGwKpr6pEWgEGoFGoBFoBBqB/SLQpGy/ HbpjUAj0Ag0Ao1AI9AITCHw/7kHP8mRTxesAAAAAElFTkSuQmCC[/IMG]
tea for one:  Do you mean one OS per disk, or is it one OS per partition?

---

### Post by tea for one on 2024-09-10
Clearly, you want to use two systems and learn about Ubuntu.
Also, I get the impression that Windows is your principal system.

The best solution is:-
Each OS on a separate disk
Each OS installed in UEFI mode with GPT and its own ESP
Encryption is available for each disk - user choice?
Boot via PC UEFI boot menu
Possible third disk for data sharing (ntfs)

The distinct advantage is that corruption on one OS will not affect the other OS
Boot problems can be fixed by the correct tools for each system
e.g. Ubuntu utilities for Ubuntu and Windows tools for Windows

What do you think?

---

### Post by willabeer on 2024-09-11
tea for one:  

Your impression that Windows is my principal system is correct and I am a Ubuntu Newbie.  However, I find that I like Linux because is seems so down to earth, and not oriented toward the next great idea.

I like your solution and I will be moving to implement your solution.  I find that trying to fix my issue is not straight forward.

ONE MORE QUESTION:   
You stated-  [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAPwAAAANCAYAAACNZQPbAAAFUElEQVRoQ 1aO2gVQRSdFBENmEASwUSjoqigYEBBtPBTWUQLFUyrGAUbC60sRIIoWGlhoYWKthZqYworJYXiD1IkoKKIfzBBEkEFBfUu3MfJeXc  94u HlbJbuzM/ecuWfuZ1/Tw11dP13J15qr79yHoUvu7eWjbsWZYffl9RP38vS qlXnbD3gFuw 5h71dxdikaz76spx9/Hm ar5xI7vkxPu2eD2pLVmr97ilh257J6e2uM P74VfGfenhOuc8MONzKwMhuH H0vhmzFd2TuuX17s1s/Pn qrJEEImFQHpwJ0 UaUsb q9/lMiRhcO/FUffu2lnTt2KvK8c6zudT4qOTI3cy3ci18NyD2NTR500/f186qiih8aplC97nKP i4FMPhujOewbkEXzRtvwtgl90 IJrbu1MChYWR6Ggh9vCfBQieI3wGjlSIlitziTvlRHhaxF8Xgx5hMARPmWtFPGoDWUdzGJnHpwpNqdg1zFFCz7P2nnGCu5UnVgc5ckOUC FCl4AiyGTo3ezdJvTDkyN5ITrWNdX4UgdUIybNW9Jdv/r2 du7NCG7G8EjWPkGaal1oZjCivjLWfX99SgiXtDGQZZFy/EgEQyHh3H92WuUPql2BkX4vdxZ43hcoRxTo3dz6JMnr2yUtwQTt4v5B/51f3muUIlFfsK42O Q3OjLepTIb9D/8SDDv3Fsl38sa13U8W3Le5iHFm2 vwCg0dpgp 4fTWrV9U51KGEgG/vX5i1bCiqMfFYwy8dvOGa2zoyAlnwKnYlUEhp6VleITsWGXBdjlwseJ6X1w5FPsQgNlk1fIg7PBRnzJmf1eihgw2fqV3WXknvwseZcpcHJ/c9YhFe1m5bub6qz DzFWv/sReCYuS5LVtCfmcFNzwMfdhkr79PjVd6UMwv 0LMLjxsrGCCfte /2SeRMQc26QpvZ4wsmjH5v4qYQkQuSSiWE0o3SzL6BDxCGhm1 JpTTt2MF/Kl5rSyyaPD1 vah5aouDSIyR43lSf4EWAvgae3JfMRDInXxZh4bRsx72KCT4PTp4rJvjYfjFOHh/inMfGhMU4sQ63DiYfNmseDBZiV/fOg9Matpwp Gz1NRh1fMu2gfoFj0073QA pWQVa7PlPoLBlIzTGh1n1fAKSObDLj2nk4qWo18ZgscIEDqFMfvRrwEhwWs0Z 40zQt13i2csb2KCT6GU ZvXbG24mi Uo0zBvTMWBmmz2OC5/JO1tB3axG8CtXiqB7Bow/H7EKe1Ad8B0Qhgrc y8WihhppObumtJiW1hPhfZ/wkChfM4vJzhvh8bNdLMLj6RwTPB4gurlqq0QHufSTHuIsK8L7cLau2jitvGC/4OYT 0NKEw5LipDghQcpM5WvIiJ8LYKPpfRsl9WgC2VGzGFpKb0lIF9diGNRRHwQaMYQErxEcbmkhmdRpXa7fQdPPYLnrxaxGr6lZ2lFpCmCF8zIHdoq97 8flb12ccSUFE1vO4V4hTBYw1tCV6bvFYWlCL4UEmHz1TwameRgmcONQtLbdpxSo8RnjOo0NyqH/SLUpt2luj1noqfO6m 7qx2yhkgp ncLZXnza3t08SjPzSRuXBetBe7nDpnPYLHTAXX8dXXnPpias4li87nS4/VARmrT0CxLr3V6ERMVqqsOEP7xb4g6XWsay3r8hjFGUvpQ3PHUudY7R3iALlSf1Z  BBkDBZHbKtPU7JWqZ/lGFjj/wYD/yMDscwEG35l8sN2FP5ZrkzjG3M3GPhTGeAMSeyM/bAmz49nasVdyk9rP46/Kf239LUCbrzXYKDBQLEM/ALVtXHp iQ5VgAAAABJRU5ErkJggg==[/IMG]
Can the Ubuntu and Windows systems share a encrypted data drive, or does the drive need to be unencrypted?

---

### Post by 1fallen on 2024-09-11
I "think" tea for one and i both Agree this is the safest:
> [COLOR=#E8E6E3]The best solution is:-[/COLOR]
[COLOR=#E8E6E3]Each OS on a separate disk[/COLOR]
[COLOR=#E8E6E3]Each OS installed in UEFI mode with GPT and its own ESP[/COLOR]

And "[COLOR=#E8E6E3]share a encrypted data drive,[/COLOR]" is doable but with a lot of learning.

LUKS (Linux Unified Key Setup) and BitLocker: LUKS is the standard encryption method for Ubuntu, while BitLocker is used in Windows. While both systems can encrypt drives, they use different formats and key management systems. This might lead to compatibility issues when trying to access the encrypted drive from both operating systems.

LUKS is superior in my humble opinion.

---

### Post by tea for one on 2024-09-11
> **willabeer said:**
> Can the Ubuntu and Windows systems share a encrypted data drive, or does the drive need to be unencrypted?
I have tested a shared encrypted external usb disk but only for 30 minutes.
BitLocker for Windows and dislocker for Ubuntu.
dislocker is in the universe repository.
I hadn't known about dislocker until it was mentioned by 1fallen2 in post 25.
I simply used an 8 letter password to lock and unlock - seemed OK in my very limited test.

Also, have a look at other ideas here [https://askubuntu.com/questions/1359587/encrypt-partition-for-use-in-ubuntu-windows](https://askubuntu.com/questions/1359587/encrypt-partition-for-use-in-ubuntu-windows)
I would also encourage you to conduct your own research into shared OS encryption, there may be more robust alternatives.

When using encryption, it is essential that you always have restorable backups of your personal data.

---

### Post by 1fallen on 2024-09-11
> **tea for one said:**
> 

When using encryption, it is essential that you always have restorable backups of your personal data.
+100 I can't believe I left that un-said....I'm getting Old and tired.....LOL

---

