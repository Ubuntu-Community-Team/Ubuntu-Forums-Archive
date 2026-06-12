---
title: "Acrobat Reader not working"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sam81 on 2009-09-01
Hi,

since yesterday updates, acrobat reader does not open anymore. I have version 9 installed from the medibuntu repository. I also installed version 7 manually, but nothing, even that doesn't work. I guess it must be related to some update in the gtk libraries, although I can't really remember what was in the update. Anyone having the same problem?

---

### Post by Paddy Landau on 2009-09-01
Version 7 is really old.

If the official repository doesn't work for you, then uninstall both version 7 and 9. Download the [latest version]("http://get.adobe.com/reader/otherversions/") from the Adobe website. Choose the Linux x86 deb version.

---

### Post by sam81 on 2009-09-01
> **Paddy Landau said:**
> Version 7 is really old.

If the official repository doesn't work for you, then uninstall both version 7 and 9. Download the [latest version]("http://get.adobe.com/reader/otherversions/") from the Adobe website. Choose the Linux x86 deb version.

Thanks for the help. I had the latest version already installed (from medibuntu repo) and working... till yesterday, when it stopped working. Then I tried installing version 7 in a separate directory as a last resort with no luck (installs fine, but doesn't open). So, is the latest version working for you?

---

### Post by ayates on 2009-09-01
Happens here also - same version. If you "bug" it,  I'll confirm.

---

### Post by lsrg on 2009-09-01
Hi all,
I'm using the jaunty package from the ubuntu partner repository and it works flawlesly.. 

You can add the repository to your /etc/apt/sources.list
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

or download the package
[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.3-1jaunty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.3-1jaunty1_i386.deb)

Lsrg

---

### Post by lsrg on 2009-09-01
Hi all,
I'm using the jaunty package from the ubuntu partner repository and it works flawlesly.. 

You can add the repository to your /etc/apt/sources.list
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

or download the package
[http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.3-1jaunty1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.1.3-1jaunty1_i386.deb)

Lsrg

---

### Post by laharrin on 2009-09-01
I have this problem too --  as Sam81 and ayates.  Have tried the karmic partner archive which gives me 9.1.0-7jaunty2, not the 9.1.3-1jaunty1 package from the link lsrg provides.  This package doesn't work for me either.  Have also tried the .deb provided by the Adobe website.

Can't find a bug for this on launchpad...

---

### Post by sam81 on 2009-09-01
latest updates (I guess libgtk) fixed the problem

---

