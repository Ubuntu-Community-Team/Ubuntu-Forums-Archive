---
title: "An error (1) occured while executing syslinux. Your USB won't be bootable"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by Zer0- on 2011-01-03
Ok so I've searched for a solution to this problem everywhere and couldn't seem to find any, so I decided to post here.
Recently I came across a new modified version of Ubuntu which was made for pentesters, called "blackbuntu".
Now I know everything is the same as linux, except a little tweaked. So, I am trying to setup my bootable USB drive, and get this error (I chose Try an unlisted OS -- Then picked New Syslinux).

And I keep getting this error:
[IMG]http://img339.imageshack.us/img339/5113/linx.png[/IMG]^



I hope somebody can help me,
Zer0-

---

### Post by Zer0- on 2011-01-03
Come on, anybody? Bumping this to get a reply :(

---

### Post by Zer0- on 2011-01-03
Searched everywhere, still no solution. Still need help here :(

---

### Post by zeating on 2011-01-18
bump..same problem, Ubuntu really doesn't want me to install it. Can't get it to run off CD OR USB

---

### Post by natedogs911 on 2011-01-19
I had the same problem on win 7 with macafee installed.
i disabled all firewall and virus scan software and then it worked

---

### Post by thesilentx on 2011-02-19
I reformatted the usb stick to FAT 32 from NTFS, and it worked.

---

### Post by macdewar on 2011-03-09
Did both of the above; still getting same error.

---

### Post by mörgæs on 2011-03-09
Have you tried Unetbootin?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by JB-HIFI on 2011-04-18
Hi, just wanted to add that disabling real time scanning on the free Microsoft Security Essentials virus scanner did the trick for me.

Thanks.

---

### Post by hosami on 2011-04-28
I had the same problem. Try to reformat your pendrive as FAT32 and the problem will be fixed (hopefully).

---

### Post by ZK_EviL on 2011-05-19
I am working with windwos 7 x64 and had the same problem. I managed to solve this:
-->Control Panel-->System and security-->Windows Firewall-->allow a program or feature through windwos firewall-->add the universal usb installer to the list
and simsala bim
it works:D

---

### Post by ranu_don on 2011-05-25
Yes ti works. If you got this error 1 then just formate your pendrive according to the default file formate which it whatever FAT32 or FAT.

---

### Post by Joeking1986 on 2011-07-12
Getting same error. Tried disabling firewall got the same error. using win vista. also, I was trying to download it onto my external hard drive not a usb stick or cd. does that matter?

---

### Post by Gianco on 2011-08-03
I had this very same error, so I tried to do the formatting by myself using Windows own format tool (FAT32 format) before installing the Ubuntu image, after that I just bypassed the formatting step built in the Universal USB installer app and the installation went through like a breeze without errors.

---

### Post by Vorac on 2011-09-10
Thanks thesilentx, re-formating from NTFS to FAT32 did the trick with me!

---

### Post by wickeed on 2011-09-12
It worked well for me, format my USB flash that was in NTFS to FAT32.
Thanks

---

### Post by armanke13 on 2011-09-30
> **natedogs911 said:**
> I had the same problem on win 7 with macafee installed.
i disabled all firewall and virus scan software and then it worked

deactivating Avira for a while, it works!

thanks... :)

---

### Post by jeden_Jedi on 2011-10-05
got rid of Kaspersky and it worked fine

---

### Post by uelkfr on 2011-10-09
Thank you, formating to FAT32 helped. Universal USB Installer does not do formating for you! (even if you check erase data box).

---

### Post by rbosaz on 2012-04-28
Having the same prob.  Formatted as fat32 and disabled AV.

---

### Post by KrisKustomPaint on 2012-07-01
Having the same problem tried formatting to fat32 and turning off firewall/ anti virus, tried uninstalling AV, adding exception in firewall. Nothing seems to work.

---

### Post by critin on 2012-07-01
Use unetbootin.  No problems.

---

### Post by steeven on 2013-06-18
My card reader of Dell laptop never works for me, even I mannuall run syslinux d: cannot read sector 0

After changing to a external USB card reader, everything OK.

---

