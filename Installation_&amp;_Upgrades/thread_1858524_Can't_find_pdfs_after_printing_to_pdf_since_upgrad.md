---
title: "Can't find pdfs after printing to pdf since upgrade"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by jedchase on 2011-10-12
When I go to print and select pdf as the printer, I cannot find the finished product in my PDF folder inside my home folder.  It acts like it creates the pdf and is completed, but I cannot find the document.  I tried using the sudo apt command to get and reinstall the cups pdf printer to no avail which I found somewhere in these forums.  I can print to pdf using the print to file option.  I was wondering if I can at least make pdf instead of ps the default option in that.  I don't know what happened to the cups pdf printer.  Any suggestions.  Ubuntu and Gnome versions below.  Thanks!!!


Ubuntu 10.04 LTS 
Gnome 2.30.2

---

### Post by raja.genupula on 2011-10-13
are you sure about the directory where you are storing ?

well make a look at temp dir in filesystem , hope you can get there if printer wents fine.

---

### Post by jedchase on 2011-10-14
I'm not exactly sure what I did, but as of yesterday, it is working again. I reinstalled the cups PDF driver a few times and went through all of the various system printer menus and tabs, and voila, it started showing up in the home folder. I don't know what happened to the previous docs I printed, but at least it's working. The print to file as PDF produces a much smaller file, but I can't find a way to change the default for it as I don't use postscript files. Thanks for your interest.

---

### Post by jiex on 2011-10-16
I have the same problem, since upgrading to 11.10. 
I have tried to fix it by completely removing and reinstalling Cups pdf - but still it will not print pdf to the pdf folder. I can get pdf via the print to file option.
The print queue has nothing in it, and it looks like it is printing but there is no output. 
I would be most obliged for advice and / or assistance

---

### Post by neiljansons on 2011-10-16
Yep this seems to happen to me after every upgrade.
It seems that CUPS-PDF is not supported and is removed in the upgrade

But this time simply reinstalling it doesn't seem to have worked.

Any ideas?

Is there a better solution for printing to a .pdf file?

---

### Post by kisgeszi on 2012-01-04
I had the same problem and if I am correct it is caused by the following bug:

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/879172](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/879172)

It basically means that cups-pdf can currently only print to its default directory
/var/spool/cups-pdf/${USER}/

If you have a line in your /etc/cups/cups-pdf.conf such as
Out ${HOME}/Documents
then you have to comment it out. At least this is what worked for me.

---

### Post by terry_n_brown on 2012-03-25
+1 for kisgeszi msg. #6, thanks, I had to comment out that line too, otherwise no output.

you can always do

```
ln -s /var/spool/cups-pdf/{username} ~/PDF
```

to get an easier path to the outputs.

---

