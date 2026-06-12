---
title: "How to prevent other software from upgrading with Ubuntu?"
date: 2022-07-05
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-07-05
I have been using Ubuntu is my scientific consulting since 2015.  I have encountered two "disasters" with updated applications software that were updated when I went from 21.10 to 22.04.

The first one concerned Shotwell and loss of functionality and imposition of the "Library."  Gthumb is a good substitute.

The second one concerns LibreOffice Writer 7.3.4.2 (1:7.3.4-0ububtu22.04.1).  Yesterday, I had carefully positioned and anchored (both position and wrap) two images on the second page of a report (saved as docx).  When I started the PC today and let Ubuntu do all sorts of upgrades, I then opened the document I was working on yesterday.  First, the settings on LibreOffice Writer had been changed to NOT VIEW IMAGES AND CHARTS.  Second, all the positioning and wrapping information had been destroyed.

If Ubuntu is to be successful, it must be well accepted in commercial environments.  That means the applications software that is bundled with each LTS must be free of serious bugs.  I have just replaced a couple of PCs in my business.  I buy refurbished PCs that come with Win 10 Pro and Office 365 preinstalled.  Why should I add Ubuntu?  Even with Ubuntu, I still need to purchase PDF Studio Pro to edit PDF documents, as well as use SpiderOak for off-site backup instead of Data Deposit Box.

I hope this post will generate some constructive discussion.

John

---

### Post by Holger_Gehrke on 2022-07-05
Within a version of Ubuntu you can put a hold on updates of packages with "apt-mark hold *package-name*". But when you upgrade from one version of Ubuntu to another this doesn't work. Also it is likely to have unintended consequences because a hold on one program will make updates to packages it depends on impossible too, which will probably have security implications.

The programs available through Ubuntu are mostly not developed  specifically for Ubuntu, and Canonical - the commercial entity behind  Ubuntu which makes it's money mostly from support contracts for servers, they don't make money from the desktop version - has almost no influence on the developers of these programs. So  don't blame Ubuntu for the problem with Shotwell, blame the devs.

The Writer problem has nothing to do with the update and everything with saving in a foreign format. 'docx' is the format of Microsoft Office. While this format is an ECMA-Standard (ECMA-376), it is extremely complex and the standard basically is: "The way MS-Office does it is the right way, if the documentation for the standard says one thing and the program does another then the program is right.". If you want repeatable results out of LibreOffice you should use it's native formats (odt for text, ods for spreadsheets,  ...). While support for Office Open XML has grown better, it is not a good idea to use it as anything other than as an export format for giving documents to users of MS Office or to import from when getting documents from them. Anything else is just asking for trouble.

And if you have to edit PDF files, you are doing it wrong. PDF is meant as the digital equivalent of a finished and printed document. It's basically a data stream for a virtual printer. You're not supposed to change a PDF file, you're supposed to edit the file you generated the PDF from and generate a new PDF. Much less trouble.

Holger

---

### Post by cigtoxdoc on 2022-07-05
Thank you for your reply.  My business is scientific consulting.  My clients as well as scientific societies and publishers I write for mandate that submissions by docx or pdf.  Since my business generates new content, we create pdf-documents.

John

---

### Post by monkeybrain20122 on 2022-07-05
Or you can set up your system with btrfs file system, it creates a snapshot whenever you install or upgrade some packages, you can restore from a snapshot very easily if something goes wrong (of course provided you can boot up. If a system update screws thing up reallu badly so you cannot even get into the system you need to have a full image to restore from)

---

### Post by mIk3_08 on 2022-07-07
> **cigtoxdoc said:**
> How to prevent other software from upgrading with Ubuntu?

John

You can just mark it as hold to prevent the app from updating. Regards and cheers.

---

### Post by Impavidus on 2022-07-07
Holger_Gehrke is spot on. I just want to add that issues are less likely when just installing bugfixes within one release of Ubuntu and more likely when moving from one version of an application to another, like when upgrading Ubuntu to a new release. So I suggest you stick to LTS releases, so you can minimize the number of release upgrades.

The scientific publishers I've dealt with all wanted LaTeX, but if your contacts want a Microsoft format, there's no reliable way other than using a Microsoft product.

> **Holger_Gehrke said:**
> PDF is meant  as the digital equivalent of a finished and printed document. It's  basically a data stream for a virtual printer.It's actually designed as a data stream for a real printer. And as printers aren't supposed to edit the page they are going to print and consumer-grade printers have limited processing power (in particular around 1992, when pdf was introduced), everything that would make it easier to edit the file was stripped away.

---

