---
title: "Re installation wipes all printer settings for specific documents"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by jb8824 on 2021-02-13
We assign certain documents to certain printers. We use a separate /home, so most of our settings survive new installations. Is there any way to permanently assigning a document to a printer? Normally, the installation is finished before printers are searched for. We thought this would be handled in the office app (we use LibreOffice) but those folks didn't seem to be able to help. Is there anything in the OS that will let us hardwire a particular document to a particular print and keep that setting through numerous installs?
Thanks.

---

### Post by TheFu on 2021-02-13
Not "hardwired", but you can script it using CUPS classes:
```
lp -d laser /path/to/file
lp -d inkjet /path/to/file
```
_laser_ and _inkjet_ are the names I told CUPS to use for the 2 printers here in the web interface on port 631/tcp. They have "official" names, but I don't remember those.

This assumes the files can be directly printed. Postscript and PDF files usually can. 

How you determine the different type of file and which printer it should be sent at is left to you. You could use part of the name or look inside the file for keywords.  There is a way to use inotify to watch an output directory, then have it do some processing for the files followed by printing. I know openoffice had a headless interface which could be used in batch programs to take a document and print it to PDF, for example.  Suspect LibreOffice has a headless interface too?  A quick web-search found this:
```
$ unoconv -f pdf mydocument.odt
```
Just tested it with a ODT that had 3 images inside (passport, immunization records, and something else) and it worked to create a PDF that looked fine. The unoconv manpage says this:
```
NAME
       unoconv - convert any document from and to any LibreOffice supported format

```
That seems really handy to me.

---

