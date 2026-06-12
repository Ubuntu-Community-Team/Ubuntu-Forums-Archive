---
title: "Errer while installing Ubuntu Server 10.10"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by jamlamin on 2011-01-29
Hello,
I'm trying to install server 10.10.
I shose my language, than i give the command to install the server.

At that moment my screens gets black.
A couple of minutes later i get te following screen....


Can someone tell me whats this error, and how i can solve this.

Sorry for bad English!

---

### Post by mörgæs on 2011-01-30
Hi, welcome to the fora.

Does the machine work in a live boot on 10.10? 10.04? 

A good first step is experimenting with boot options, if problems appear:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by jamlamin on 2011-02-01
Can't find a good solution...

---

### Post by Carson5696 on 2011-02-01
Hey Ubuntu just said sorry the had problems with their sever..... Please use this web site [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
The iso that you have might have been corrupted

Have a great Day!!! ;)

P.S. this is 10.04.1 but it still has everything that ubuntu 10.10 has

---

### Post by mörgæs on 2011-02-01
> **Carson5696 said:**
> Hey Ubuntu just said sorry the had problems with their sever..... Please use this web site [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
The iso that you have might have been corrupted


What do you mean by that? 

If you are saying that there was a problem with the ISOs found on [www.ubuntu.com](www.ubuntu.com) please provide some documentation. It is quite a statement.

---

### Post by Carson5696 on 2011-02-01
Bad ISO Image - ubuntu-8.10-desktop-i386.iso

Chris Bidwell cjbidwell at qwest.net 
Fri Nov 14 21:07:53 GMT 2008
Previous message: testing updates (was Re: Dell Mini 9 update testing)
Next message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
I've burned this iso from several mirrors and I get an error each time I 
check the disk.

Is anyone else getting issues with this?

Thanks,
Chris

Previous message: testing updates (was Re: Dell Mini 9 update testing)
Next message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
More information about the Ubuntu-qa mailing list


Website:[https://lists.ubuntu.com/archives/ubuntu-qa/2008-November/000337.html](https://lists.ubuntu.com/archives/ubuntu-qa/2008-November/000337.html)

---

### Post by Carson5696 on 2011-02-01
Bad ISO Image - ubuntu-8.10-desktop-i386.iso

Mike Rooney mrooney at gmail.com 
Fri Nov 14 23:25:18 GMT 2008
Previous message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Next message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
On Fri, Nov 14, 2008 at 4:07 PM, Chris Bidwell <cjbidwell at qwest.net> wrote:

> I've burned this iso from several mirrors and I get an error each time I
> check the disk.
>
> Is anyone else getting issues with this?
>
> Thanks,
> Chris
>


I just downloaded the torrent yesterday and burned it. It passed the
integrity check and installed fine. While this isn't a direct ISO I would
imagine it comes from the same place.

I would suspect your issue is a bad set of discs, a bad burner, or a bad
reader. However it wouldn't hurt to hear a confirmation of a successful ISO
download, I suppose!

-- 
Michael Rooney
mrooney at gmail.com
-------------- next part --------------
An HTML attachment was scrubbed...
URL: [https://lists.ubuntu.com/archives/ubuntu-qa/attachments/20081114/c4e1f5a8/attachment-0001.htm](https://lists.ubuntu.com/archives/ubuntu-qa/attachments/20081114/c4e1f5a8/attachment-0001.htm) 
Previous message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Next message: Bad ISO Image - ubuntu-8.10-desktop-i386.iso
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
More information about the Ubuntu-qa mailing list



Website:[https://lists.ubuntu.com/archives/ubuntu-qa/2008-November/000338.html](https://lists.ubuntu.com/archives/ubuntu-qa/2008-November/000338.html)

---

### Post by Carson5696 on 2011-02-01
[Bug 187459] [NEW] genisoimage creates bad iso images if joliet is	used - error: "Unexpected joliet directory length" appears

Mantas Kriau&#269;i&#363;nas mantas at akl.lt 
Wed Jan 30 23:51:30 GMT 2008
Previous message: [Bug 23046] Re: mkisofs aborts on malformed joliet filenames
Next message: [Bug 187459] Re: genisoimage creates bad iso images if joliet is used	- error: "Unexpected joliet directory length" appears
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
Public bug reported:

Since Ubuntu 7.04 (Feisty, genisoimage version 1.1.6) CD burning causes
a lots of problems for me and my friends - in lots of cases genisoimage
creates bad iso images if joliet is used - error: "Unexpected joliet
directory length" appears:

ubuntu at baltix:/mnt/SVARBU-Manto$ sudo genisoimage -r -V "Baltix-Linux-3.1bm 2008-01" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o Baltix.iso Baltix-3-CD/CD/
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using MANO_NUMERIS_LOGO000.GIF;1 for  Baltix-3-CD/CD/pics/remejai/mano_numeris-logo.gif (mano_numeris_logo.gif)
Using MANO_NUMERIS_LOGO000.GIF;1 for  Baltix-3-CD/CD/pics/remejai/thumbs/mano_numeris-logo.gif (mano_numeris_logo.gif)
Using UBUNTU_LT_INSTALLATION_S000.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_6_-_sukurti-naudotoja.png (Ubuntu_LT_installation_step_7_-_santrauka-patvirtinimas.png)
Using UBUNTU_LT_INSTALLATION_S001.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_7_-_santrauka-patvirtinimas.png (Ubuntu_LT_installation_step_1_-_pasirinkti-kalba.png)
Using UBUNTU_LT_INSTALLATION_S002.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_1_-_pasirinkti-kalba.png (Ubuntu_LT_installation_step_3_-_klaviaturos-isdestymas.png)
Using UBUNTU_LT_INSTALLATION_S003.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_3_-_klaviaturos-isdestymas.png (Ubuntu_LT_installation_step_4_-_paruosti-vieta-diske.png)
Using UBUNTU_LT_INSTALLATION_S004.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_4_-_paruosti-vieta-diske.png (Ubuntu_LT_installation_step_5_-_importuoti-esamus-naudotojus.png)
Using LINUX_WINDOWS_NAUDOJIMAS000.PNG;1 for  Baltix-3-CD/CD/doc/Linux-Windows-naudojimas-tinkle/Linux_Windows_naudojimas_tinkle-SAMBA_html_m74e24fb4.png (Linux_Windows_naudojimas_tinkle-SAMBA_html_64b2cbe6.png)
Using LINUX_WINDOWS_NAUDOJIMAS001.PNG;1 for  Baltix-3-CD/CD/doc/Linux-Windows-naudojimas-tinkle/Linux_Windows_naudojimas_tinkle-SAMBA_html_64b2cbe6.png (Linux_Windows_naudojimas_tinkle-SAMBA_html_m397604df.png)
Size of boot image is 4 sectors -> No emulation
genisoimage: Unexpected joliet directory length 1112 expected: 1116 ''
  1.40% done, estimate finish Thu Jan 31 03:34:32 2008
  2.78% done, estimate finish Thu Jan 31 03:34:32 2008
[..]

This bug is not 100% reproducible, but it appears very often for me and
others - it seems Joerg Schilling (original author of cdrecord software)
is right - "the debian/ubuntu program (genisoimage) is a bad hack on a 2
year old version of mkisofs":

From: Joerg.Schilling at fokus.fraunhofer.de (Joerg Schilling)
> To: 429244 at bugs.debian.org
> Subject: invalid Joliet table (was: genisoimage creates invalid iso images)
> Date: Sat, 14 Jul 2007 22:13:49 +0200
> 
> do not expect to get any useful answer/help for your Debian bugreport. The projct is dead.
> 
> BTW: I cannot see any problems with your data using a recent original software:
> 
> [http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)
> [ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)
> 
> The debian program is a bad hack on a 2 year old version of mkisofs.

When I downgraded to genisoimage 1.1.2-1 then this problem dissapears,
like in other cases, described in debian bugs.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558) :

Subject: genisoimage: Unexpected joliet directory length - this
important bug is a duplicate of bug #429244

I also several times meet with the same problem in Ubuntu 7.04 and 7.10, 
which uses the same version of genisoimage package - 1.1.6. The same error 
message during genisoimage run:
"Unexpected joliet directory length" and the same problems, like 
described in Debian bugs #429244 and #430558 :

From: Julian Andres Klode <jak at jak-linux.org>
>To: 429244 at bugs.debian.org
>Subject: invalid Joliet table (was: genisoimage creates invalid iso images)
>Date: Sun, 08 Jul 2007 15:03:43 +0200
> 
> It seems to me that the Joliet table is invalid.
> 
> $ isoinfo -Jf -debug -i image.iso
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> /..
> /
> isoinfo: Short read on old image
> 
> But "$ isoinfo -Rf -debug -i image.iso" works (Rock Ridge)
> 
> $ isoinfo -J -d  -debug -i image.iso
> CD-ROM is in ISO 9660 format
> System id: LINUX
> Volume id: Debian unstable i386
> [..]
> Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993 
> E.YOUNGDALE (C) 1997-2006
> J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT TEAM
> [..]
> Volume set size is: 1
> Volume set sequence number is: 1
> Logical block size is: 2048
> Volume size is: 376104
> Root directory extent:  57 size: 2048
> Path table size is:     11702
> L Path table start:     21
> L Path opt table start: 0
> M Path table start:     27
> M Path opt table start: 0
> Creation Date:     2007 07 07 20:51:50.00
> Modification Date: 2007 07 07 20:51:50.00
> Expiration Date:   0000 00 00 00:00:00.00
> Effective Date:    2007 07 07 20:51:50.00
> File structure version: 1
> El Torito VD version 1 found, boot catalog is in sector 1671
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> Joliet with UCS level 3 found
> Rock Ridge signatures version 1 found
> Eltorito validation header:
>    Hid 1
>    Arch 0 (x86)
>    ID ''
>    Key 55 AA
>    Eltorito defaultboot header:
>        Bootid 88 (bootable)
>        Boot media 0 (No Emulation Boot)
>        Load segment 0
>        Sys type 0
>        Nsect 4
>        Bootoff 688 1672

When I downgraded to version 1.1.2-1 then this problem dissapears, like
in other cases, described in debian bugs.

Btw, it seems this important bug is a duplicate of bug #429244 :

From: Richard Kralovic <Richard.Kralovic at dcs.fmph.uniba.sk> wrote:
>To: 430558 at bugs.debian.org
>Subject: genisoimage: Unexpected joliet directory length
>Date: Tue, 18 Sep 2007 14:04:09 +0200
>
> I can confirm this bug [..] (I was able to reproduce it only on one 
> machine out of several almost identical ones).
>
> I was able to track down the bug to the diff between svn revisions  
> 743 and 744 (The svn diff is attached). Indeed, after reverting this
> change, everything works.

I think it would be wise to stop creating bad and unmaintained forks of
cdrecord and work together with Joerg Schilling (original author of
cdrecord software) - it seems cdrecord is really free and really
working, OSI approved software and there are no restrictions for
patching and improving it - look here for more info:

[http://cdrecord.berlios.de/private/cdr-faq.html](http://cdrecord.berlios.de/private/cdr-faq.html)

** Affects: cdrkit (Ubuntu)
     Importance: Undecided
         Status: New

** Affects: cdrkit (Baltix)
     Importance: Undecided
         Status: New

** Affects: cdrkit (Debian)
     Importance: Unknown
         Status: Unknown

** Also affects: cdrkit (Baltix)
   Importance: Undecided
       Status: New

** Bug watch added: Debian Bug tracker #429244
   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244)

** Also affects: cdrkit (Debian) via
   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244)
   Importance: Unknown
       Status: Unknown

-- 
genisoimage creates bad iso images if joliet is used - error: "Unexpected joliet directory length" appears
[https://bugs.launchpad.net/bugs/187459](https://bugs.launchpad.net/bugs/187459)
You received this bug notification because you are a member of Ubuntu
Burning Team, which is a bug contact for cdrkit in ubuntu.

Previous message: [Bug 23046] Re: mkisofs aborts on malformed joliet filenames
Next message: [Bug 187459] Re: genisoimage creates bad iso images if joliet is used	- error: "Unexpected joliet directory length" appears
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
More information about the Ubuntu-burning mailing list



Website:[https://lists.ubuntu.com/archives/ubuntu-burning/2008-January/002919.html](https://lists.ubuntu.com/archives/ubuntu-burning/2008-January/002919.html)

---

### Post by Carson5696 on 2011-02-01
[Bug 187459] [NEW] genisoimage creates bad iso images if joliet is	used - error: "Unexpected joliet directory length" appears

Mantas Kriau&#269;i&#363;nas mantas at akl.lt 
Wed Jan 30 23:51:30 GMT 2008
Previous message: [Bug 23046] Re: mkisofs aborts on malformed joliet filenames
Next message: [Bug 187459] Re: genisoimage creates bad iso images if joliet is used	- error: "Unexpected joliet directory length" appears
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
Public bug reported:

Since Ubuntu 7.04 (Feisty, genisoimage version 1.1.6) CD burning causes
a lots of problems for me and my friends - in lots of cases genisoimage
creates bad iso images if joliet is used - error: "Unexpected joliet
directory length" appears:

ubuntu at baltix:/mnt/SVARBU-Manto$ sudo genisoimage -r -V "Baltix-Linux-3.1bm 2008-01" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o Baltix.iso Baltix-3-CD/CD/
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using MANO_NUMERIS_LOGO000.GIF;1 for  Baltix-3-CD/CD/pics/remejai/mano_numeris-logo.gif (mano_numeris_logo.gif)
Using MANO_NUMERIS_LOGO000.GIF;1 for  Baltix-3-CD/CD/pics/remejai/thumbs/mano_numeris-logo.gif (mano_numeris_logo.gif)
Using UBUNTU_LT_INSTALLATION_S000.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_6_-_sukurti-naudotoja.png (Ubuntu_LT_installation_step_7_-_santrauka-patvirtinimas.png)
Using UBUNTU_LT_INSTALLATION_S001.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_7_-_santrauka-patvirtinimas.png (Ubuntu_LT_installation_step_1_-_pasirinkti-kalba.png)
Using UBUNTU_LT_INSTALLATION_S002.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_1_-_pasirinkti-kalba.png (Ubuntu_LT_installation_step_3_-_klaviaturos-isdestymas.png)
Using UBUNTU_LT_INSTALLATION_S003.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_3_-_klaviaturos-isdestymas.png (Ubuntu_LT_installation_step_4_-_paruosti-vieta-diske.png)
Using UBUNTU_LT_INSTALLATION_S004.PNG;1 for  Baltix-3-CD/CD/doc/Baltix-Ubuntu-Linux-diegimas_failai/Ubuntu_LT_installation_step_4_-_paruosti-vieta-diske.png (Ubuntu_LT_installation_step_5_-_importuoti-esamus-naudotojus.png)
Using LINUX_WINDOWS_NAUDOJIMAS000.PNG;1 for  Baltix-3-CD/CD/doc/Linux-Windows-naudojimas-tinkle/Linux_Windows_naudojimas_tinkle-SAMBA_html_m74e24fb4.png (Linux_Windows_naudojimas_tinkle-SAMBA_html_64b2cbe6.png)
Using LINUX_WINDOWS_NAUDOJIMAS001.PNG;1 for  Baltix-3-CD/CD/doc/Linux-Windows-naudojimas-tinkle/Linux_Windows_naudojimas_tinkle-SAMBA_html_64b2cbe6.png (Linux_Windows_naudojimas_tinkle-SAMBA_html_m397604df.png)
Size of boot image is 4 sectors -> No emulation
genisoimage: Unexpected joliet directory length 1112 expected: 1116 ''
  1.40% done, estimate finish Thu Jan 31 03:34:32 2008
  2.78% done, estimate finish Thu Jan 31 03:34:32 2008
[..]

This bug is not 100% reproducible, but it appears very often for me and
others - it seems Joerg Schilling (original author of cdrecord software)
is right - "the debian/ubuntu program (genisoimage) is a bad hack on a 2
year old version of mkisofs":

From: Joerg.Schilling at fokus.fraunhofer.de (Joerg Schilling)
> To: 429244 at bugs.debian.org
> Subject: invalid Joliet table (was: genisoimage creates invalid iso images)
> Date: Sat, 14 Jul 2007 22:13:49 +0200
> 
> do not expect to get any useful answer/help for your Debian bugreport. The projct is dead.
> 
> BTW: I cannot see any problems with your data using a recent original software:
> 
> [http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)
> [ftp://ftp.berlios.de/pub/cdrecord/alpha/](ftp://ftp.berlios.de/pub/cdrecord/alpha/)
> 
> The debian program is a bad hack on a 2 year old version of mkisofs.

When I downgraded to genisoimage 1.1.2-1 then this problem dissapears,
like in other cases, described in debian bugs.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558) :

Subject: genisoimage: Unexpected joliet directory length - this
important bug is a duplicate of bug #429244

I also several times meet with the same problem in Ubuntu 7.04 and 7.10, 
which uses the same version of genisoimage package - 1.1.6. The same error 
message during genisoimage run:
"Unexpected joliet directory length" and the same problems, like 
described in Debian bugs #429244 and #430558 :

From: Julian Andres Klode <jak at jak-linux.org>
>To: 429244 at bugs.debian.org
>Subject: invalid Joliet table (was: genisoimage creates invalid iso images)
>Date: Sun, 08 Jul 2007 15:03:43 +0200
> 
> It seems to me that the Joliet table is invalid.
> 
> $ isoinfo -Jf -debug -i image.iso
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> /..
> /
> isoinfo: Short read on old image
> 
> But "$ isoinfo -Rf -debug -i image.iso" works (Rock Ridge)
> 
> $ isoinfo -J -d  -debug -i image.iso
> CD-ROM is in ISO 9660 format
> System id: LINUX
> Volume id: Debian unstable i386
> [..]
> Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993 
> E.YOUNGDALE (C) 1997-2006
> J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT TEAM
> [..]
> Volume set size is: 1
> Volume set sequence number is: 1
> Logical block size is: 2048
> Volume size is: 376104
> Root directory extent:  57 size: 2048
> Path table size is:     11702
> L Path table start:     21
> L Path opt table start: 0
> M Path table start:     27
> M Path opt table start: 0
> Creation Date:     2007 07 07 20:51:50.00
> Modification Date: 2007 07 07 20:51:50.00
> Expiration Date:   0000 00 00 00:00:00.00
> Effective Date:    2007 07 07 20:51:50.00
> File structure version: 1
> El Torito VD version 1 found, boot catalog is in sector 1671
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> Joliet escape sequence 0: '%' 1: '/' 2: 'E' 3: ''
> Joliet with UCS level 3 found
> Rock Ridge signatures version 1 found
> Eltorito validation header:
>    Hid 1
>    Arch 0 (x86)
>    ID ''
>    Key 55 AA
>    Eltorito defaultboot header:
>        Bootid 88 (bootable)
>        Boot media 0 (No Emulation Boot)
>        Load segment 0
>        Sys type 0
>        Nsect 4
>        Bootoff 688 1672

When I downgraded to version 1.1.2-1 then this problem dissapears, like
in other cases, described in debian bugs.

Btw, it seems this important bug is a duplicate of bug #429244 :

From: Richard Kralovic <Richard.Kralovic at dcs.fmph.uniba.sk> wrote:
>To: 430558 at bugs.debian.org
>Subject: genisoimage: Unexpected joliet directory length
>Date: Tue, 18 Sep 2007 14:04:09 +0200
>
> I can confirm this bug [..] (I was able to reproduce it only on one 
> machine out of several almost identical ones).
>
> I was able to track down the bug to the diff between svn revisions  
> 743 and 744 (The svn diff is attached). Indeed, after reverting this
> change, everything works.

I think it would be wise to stop creating bad and unmaintained forks of
cdrecord and work together with Joerg Schilling (original author of
cdrecord software) - it seems cdrecord is really free and really
working, OSI approved software and there are no restrictions for
patching and improving it - look here for more info:

[http://cdrecord.berlios.de/private/cdr-faq.html](http://cdrecord.berlios.de/private/cdr-faq.html)

** Affects: cdrkit (Ubuntu)
     Importance: Undecided
         Status: New

** Affects: cdrkit (Baltix)
     Importance: Undecided
         Status: New

** Affects: cdrkit (Debian)
     Importance: Unknown
         Status: Unknown

** Also affects: cdrkit (Baltix)
   Importance: Undecided
       Status: New

** Bug watch added: Debian Bug tracker #429244
   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244)

** Also affects: cdrkit (Debian) via
   [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429244)
   Importance: Unknown
       Status: Unknown

-- 
genisoimage creates bad iso images if joliet is used - error: "Unexpected joliet directory length" appears
[https://bugs.launchpad.net/bugs/187459](https://bugs.launchpad.net/bugs/187459)
You received this bug notification because you are a member of Ubuntu
Burning Team, which is a bug contact for cdrkit in ubuntu.

Previous message: [Bug 23046] Re: mkisofs aborts on malformed joliet filenames
Next message: [Bug 187459] Re: genisoimage creates bad iso images if joliet is used	- error: "Unexpected joliet directory length" appears
Messages sorted by: [ date ] [ thread ] [ subject ] [ author ]
More information about the Ubuntu-burning mailing list



Website:[https://lists.ubuntu.com/archives/ubuntu-burning/2008-January/002919.html](https://lists.ubuntu.com/archives/ubuntu-burning/2008-January/002919.html)

---

### Post by mörgæs on 2011-02-01
What you posted is several years old and concerns obsolete versions of Ubuntu. 

While we appreciate that you are trying to help in the forum, please judge carefully the quality of the material you are providing.


For people following this: There is no reason to believe that the available ISO's have errors.

---

### Post by Carson5696 on 2011-02-01
Sorry

---

### Post by Elfy on 2011-02-01
Posts of old information removed.

---

### Post by jamlamin on 2011-02-01
Someone sad it's becaus i have a Raid controler... not supported by the OS?

---

### Post by mörgæs on 2011-02-01
I have never used raid myself, so I can not help you here, but yes: My guess is that this should be the first to investigate. Raid is supported, but it might take some manual settings to get to work.

Maybe this forum has something of use:
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

