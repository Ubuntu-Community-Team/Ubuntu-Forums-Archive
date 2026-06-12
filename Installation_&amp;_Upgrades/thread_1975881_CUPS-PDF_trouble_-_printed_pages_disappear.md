---
title: "CUPS-PDF trouble - printed pages disappear"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by paramax55 on 2012-05-08
I had been using CUPS-PDF just fine, but I got in the habit of exporting things to PDF instead of printing them. Then one day (and probably a couple upgrades later) I tried to print to PDF and I error that cups-pdf didn't exist. I re-installed cups-pdf, which didn't help. Then I deleted the pdf printer from system settings and added it back in. Now I can print test pages and they go to the /Home/PDF directory like they should. When I am printing from within an application, however, everything chugs along like it should, but the document is not in the folder. I even tried a search and any new pdfs don't exist. I just upgraded my system a couple days ago. I am running the latest Ubuntu Studio.

Any ideas?

---

### Post by upandacross on 2012-05-08
I am posting in this thread although cups-pdf has generated many other discussions elsewhere. Various suggestions have been made with respect to file permissions, SELinux, Apparmor, etc. As is usually the case, I tried several until finding "the main thing". I'm too tired to retrace my steps and see if any of the other suggestions are actually needed, but the problem I found was definitely a show-stopper.

As distributed, /etc/cups/cups-pdf.conf allows the path for gs to default to /usr/bin/gs and that is not correct on my 11.10 system. The following is a diff of the change that did the trick for me:

224c224
< GhostScript /usr/bin/gs
---
> GhostScript /usr/local/bin/gs

Clues that you may have this problem are found in /var/log/cups/cups-pdf_log after setting LogType to 7 in /etc/cups/cups-pdf.conf. Check your log file for the debug line showing how gs is invoked and confirm that the path is "/usr/bin/gs". If you, like me, have a system where the path should be "/usr/local/bin/gs", then the PDF print will fail full stop. Another clue is that the [DEBUG] line right after invoking gs looks something like this (I have made the important phrase bold):

{your date and time} **[DEBUG] output file unlinked** (/{whatever your home directory is}/PDF/{whatever the OutputFile name was for gs})

The output file is being deleted because the gs invocation failed (silently, as far as the cups-pdf_log file is concerned [-X).

Finally, you will see in the log file:

[ERROR] failed to set file mode for PDF file (non fatal) {your output file name}

I'm slightly amused that cups records this as non-fatal as in "IT DIDN'T WORK". While it is true that the file mode could not be set, this is not a permission problem as much as it's the problem of trying to set permissions on a non-existent file ](*,).

I spent a lot of time on this problem and never found another post that came to this conclusion. I hope this saves you some trouble.

---

### Post by paramax55 on 2012-05-17
@[upandacross]("http://ubuntuforums.org/member.php?u=1052299")  - Thanks for your help! At least I know where to look for things now.  This problem is fixed. I don't know why, but it is fixed. I had tried, I  thought, everything - including a reboot before. After seeing your  post, I went into the .conf file and enabled logging. Guess what? My  sample page printed. Who knows why, but now I can print and I am happy.

---

