---
title: "Update 14.04 LTS (is it possible)"
date: 2024-04-03
forum: Installation &amp; Upgrades
---

### Post by Aggienator on 2024-04-03
Hi,

I'm returning to Ubuntu after a long absence and trying to install on a 2002 white MacBook. The latest CD I can boot from is the 14.04 server CD. When I try to update or install using apt-get it can't find any of the repositories. Is this because they have now been taken off line, and is there a way round it?

Many Thanks for any advice,

Aggie

---

### Post by guiverc on 2024-04-03
Ubuntu 14.04 LTS or the 2014-April release of Ubuntu reached *End of Standard Suppor**t *back in 2019-April when it completed the five years.

After a release reaches EOSS or EOL, mirrors/third-party sources are free to *drop* support for the release.

The main archive however was not dropped; as can be see at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

The packages available there have not been updated since EOSS was reached back in April 2019 though, however if you enable ESM you can get updates until the end of this month.

You weren't specific as to where you were trying to get packages; from the main archive (*which is still available*), an official ESM mirror, or possibly from a source that only supported fully-supported (non-ESM) release of Ubuntu.

ESM can extend support for a further five years, ie. April 2019 - April 2024 (*ie. this month only now*).  There is also a new option available to get a further two years of additional support (ie. from May 2024) which was recently announced.


> [h=3]Canonical expands Long Term Support to 12 years starting with Ubuntu 14.04 LTS[/h] Whilst most readers will be aware that this was going to happen,  Canonical has made it official that Ubuntu LTS releases can get  additional legacy support (two years), beyond Pro support already  available. This will mean users of Ubuntu 14.04 LTS, with Ubuntu Pro  support that would end in April 2024, there now is a further two year  option of legacy support.



 [https://ubuntu.com/blog/canonical-expands-long-term-support-to-12-years-starting-with-ubuntu-14-04-lts 2]("https://ubuntu.com/blog/canonical-expands-long-term-support-to-12-years-starting-with-ubuntu-14-04-lts")



I'm quoting from the recent UWN with link found [URL="https://discourse.ubuntu.com/t/ubuntu-weekly-newsletter-issue-833/43631"]here
[/URL]

---

### Post by Holger_Gehrke on 2024-04-03
A Mac from 2002 ? That's probably not an Intel Mac but one with a PowerPC processor. In that case you're better off using Debian instead of Ubuntu because that AFAIK still supports PPC .

Holger

---

### Post by readableauthor on 2024-04-03
> **Aggienator said:**
> Hi,
When I try to update or install using apt-get it can't find any of the repositories. Is this because they have now been taken off line, and is there a way round it?
Aggie
You should switch to this repo: [https://old-releases.ubuntu.com/ubuntu/](https://old-releases.ubuntu.com/ubuntu/)

---

### Post by MAFoElffen on 2024-04-03
Th big problem is that you cannot install Ubuntu with anything that is currently support because of your CPU. The Mac PowerBook from 2002 had a PowerPC 7455 "G4" CPu, which is only 32bit. Ubuntu stopped supporting 32bot CPUs back (for LTS'es) with 16.04 LTS. The last 32bit flavor was Lubuntu 18.04. Both are End Of Service long ago.

My recommendation would be to install Debian, which does have a 32bit option. And thier i386 NetInstall ISO will fill on a CD.

---

### Post by gezzer2 on 2024-04-04
if the macbook is an intel core2duo which will be 32 bit CPU then have a look at MX Linux.
MX Linux is based on Debian but they have done a marvellous job of making it a lot easier then full blown Debian.

here is the download link for MX Linux i386 32 bit ISO
[https://sourceforge.net/projects/mx-linux/files/Final/Xfce/MX-23.2_386.iso/download](https://sourceforge.net/projects/mx-linux/files/Final/Xfce/MX-23.2_386.iso/download)

---

### Post by Aggienator on 2024-04-05
Thanks all for your help!

After a bit of digging I realised the MacBook wasn't quite as old, a 2007 Intel core2Duo.

After editing the sources.list to [https://old-releases.ubuntu.com/ubuntu/](https://old-releases.ubuntu.com/ubuntu/) I still got the same errors, however I did manage to get an 18.04 desktop to install and everything is now going great!

Thanks to everyone for you help.

I love the Ubuntu community and am glad to be back!

Cheers, Aggie

---

### Post by gezzer2 on 2024-04-05
the 2007 MacBook had a intel L7200 core2duo cpu which is 64 bit so you could try an updated version of Ubuntu using live install USB to see if it works.
just a thought. but am glad you got it working ..

---

### Post by oldfred on 2024-04-05
I have this link in my notes on old Macs. Do not have a Mac, so never used it, but he also explains many of the issues of installing.

[https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

---

### Post by MAFoElffen on 2024-04-05
If 2007... I have  an old MacBook A1181 w/ Intel Core 2 Duo (2007). Even though the Intel CPU is 64bit, the EFI BIOS in mine is 32bit. A trick to get that working. I was got that to test my 'system-info' script's compatibility on MAC hardware. There was also a trick for the WiFi card in it. I also have it dual booted with Mountain Lion, and Lion.

It is currently running Ubuntu 22.04 LTS. Is a bit slow, but works great. Would run faster if you run a lighter flavor of Ubuntu.

---

### Post by MAFoElffen on 2024-04-05
18.04 has also reached end of support...

This is posted from my MacBook A1181...

'system-info' Report: [https://termbin.com/lkoi](https://termbin.com/lkoi)
```

mafoelffen@Mikes-MacBook:~/Scripts$ lsb_release -d
Description:    Ubuntu 22.04.4 LTS
mafoelffen@Mikes-MacBook:~/Scripts$ uname -r
6.5.0-26-generic

```
You can get to a supported version.

---

