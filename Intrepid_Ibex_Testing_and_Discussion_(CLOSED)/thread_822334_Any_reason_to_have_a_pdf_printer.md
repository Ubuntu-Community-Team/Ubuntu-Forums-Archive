---
title: "Any reason to have a pdf printer?"
date: 2008-06-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-06-08
Quick, possibly dumb question: since pdf is available as a "print to file" format, is there really a use now for the pdf printer that doesn't let you choose the destination folder or the file name?

[IMG]http://img204.imageshack.us/img204/130/pantallazoju7.png[/IMG]

---

### Post by abhiroopb on 2008-06-08
I'm sure there a number of programs where print to pdf is not an option. I know its there in openoffice, but it may not be there in other programs. I mean its not really a hindarance. Best is to keep it, in the off chance there is a program that doesn't have a print to pdf option.

---

### Post by Bou on 2008-06-08
> **abhiroopb said:**
> I'm sure there a number of programs where print to pdf is not an option.

Does that depend on the program itself, or the gnome printing dialogue?

---

### Post by abhiroopb on 2008-06-08
The program

---

### Post by Bou on 2008-06-08
Oh, it's OK then.

---

### Post by bruce89 on 2008-06-08
You can remove this by removing the *cups-pdf* package.

---

### Post by CREEPING DEATH on 2008-06-08
> **Bou said:**
> Quick, possibly dumb question: since pdf is available as a "print to file" format, is there really a use now for the pdf printer that doesn't let you choose the destination folder or the file name?

Yes!  You can print whatever to a .pdf, it goes into the PDF folder in your Home directory.  You then have a copy that can be emailed or taken with you anywhere for printing somewhere else, this came in very useful for me when I had no printer and had to get documents to enroll in some college courses recently.

CD

---

### Post by bruce89 on 2008-06-08
> **CREEPING DEATH said:**
> Yes!  You can print whatever to a .pdf, it goes into the PDF folder in your Home directory.  You then have a copy that can be emailed or taken with you anywhere for printing somewhere else, this came in very useful for me when I had no printer and had to get documents to enroll in some college courses recently.

It was more a case of every program that uses GtkPrint* doesn't need to have the *cups-pdf* PDF option as GtkPrint* already has a PDF option. In fact, cups-pdf was only installed because of Firefox's old crappy printing capability.

---

### Post by Bou on 2008-06-08
> **bruce89 said:**
> In fact, cups-pdf was only installed because of Firefox's old crappy printing capability.

That's exactly what I meant. But Firefox uses gtkprint now, doesn't it? Is there still a problem with it? I see you get the usual print dialogue when you press ctrl + p, complete with the "print to file" option.

---

### Post by bruce89 on 2008-06-08
> **Bou said:**
> That's exactly what I meant. But Firefox uses gtkprint now, doesn't it? Is there still a problem with it? I see you get the usual print dialogue when you press ctrl + p, complete with the "print to file" option.

Yes, indeed it does, which is why I advocate the removal of *cups-pdf* (I always have done anyway).

---

### Post by Bou on 2008-06-08
> **bruce89 said:**
> Yes, indeed it does, which is why I advocate the removal of *cups-pdf* (I always have done anyway).

If I wanted to file a bug asking for it to be removed from default installs, should I file it against a specific package? cups-pdf maybe?

---

### Post by cariboo on 2008-06-08
Print to file creates a postscript file. So print to file is not the same as the pdf printer.

Jim

---

### Post by 23meg on 2008-06-08
The plan is to switch to PDF as the default print job format in Intrepid.

[https://blueprints.launchpad.net/ubuntu/+spec/pdf-as-standard-print-job-format](https://blueprints.launchpad.net/ubuntu/+spec/pdf-as-standard-print-job-format)

[QUOTE=Bou]If I wanted to file a bug asking for it to be removed from default installs, should I file it against a specific package? cups-pdf maybe?[/QUOTE]

That would go to [ubuntu-meta]("bugs.launchpad.net/ubuntu/+source/ubuntu-meta").

---

### Post by Bou on 2008-06-08
> **cariboo907 said:**
> Print to file creates a postscript file. So print to file is not the same as the pdf printer.

As far as I know it gives you the choice, PS or PDF.

---

### Post by bruce89 on 2008-06-08
> **Bou said:**
> If I wanted to file a bug asking for it to be removed from default installs, should I file it against a specific package? cups-pdf maybe?

*ubuntu-meta* would be better.

---

### Post by Bou on 2008-06-08
Just filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/238387](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/238387)

---

### Post by bruce89 on 2008-06-08
> **Bou said:**
> Just filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/238387](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/238387)

I like my grumpy quote.

---

### Post by syxbit on 2008-06-08
i agree, that the package cups-pdf should be removed, but only after OOo starts using gtkprint (i really wish they'd push to include the necessary patch for 3.0 with intrepid!)
[EDIT] nevermind, i forgot that OOo includes a print to PDF function anyway (though it's still hideous, and needs to be patched to use gtkprint)

---

### Post by _oOMOo_ on 2008-06-08
> **syxbit said:**
> i agree, that the package cups-pdf should be removed, but only after OOo starts using gtkprint (i really wish they'd push to include the necessary patch for 3.0 with intrepid!)
[EDIT] nevermind, i forgot that OOo includes a print to PDF function anyway (though it's still hideous, and needs to be patched to use gtkprint)

Yes wholeheartedly agree. Until OO starts using gtkprint I'd be happier if cups-pdf was left alone. The Export to PDF function is a nice idea, but what's up with the quality of text? Is it just a setting I'm missing?

---

### Post by Arathorn on 2008-06-08
> **syxbit said:**
> [EDIT] nevermind, i forgot that OOo includes a print to PDF function anyway (though it's still hideous, and needs to be patched to use gtkprint)
You can forget about that if you're using [OpenType]("http://www.openoffice.org/issues/show_bug.cgi?id=43029") fonts, which is what most modern fonts are. There is also an advantage of PDF export to printing to PDF. As far as I know, only the export embeds links you have throughout the document (like links to chapters in your index) into the pdf file.

---

### Post by mdurham on 2008-06-08
Hi, Can you please help me out here? I've never been able to print to PDF. When I try the cpu does a lot of work for a few seconds (depending on length of document of course) and the hdd light flashes but I never end up with a PDF file anywhere, the PDF directory is always empty. What do you do to get this to work?
Any help appreciated.
Cheers, Mike

---

### Post by scorpion-kde on 2008-06-10
I thought I'd weigh in briefly here.  I'm working on the Common Printing Dialog for Google Summer of Code.  Since we're switching to PDF as the print job submission format, I may be able to add something to the dialog to dump out a PDF instead of submitting it to CUPS.  We haven't nailed down all of the details yet, so I don't know how feasible that is, but I will keep it in mind.  Also, I'm working on the KDE 4 implementation of the dialog, since I don't really know GTK+.  If I have time, I may take a crack at a GTK+ dialog.  I may make an announcement of some sort once the specification is finalized and I've done enough work on the KDE 4 dialog to know of any caveats.

---

### Post by bruce89 on 2008-06-11
> **scorpion-kde said:**
> I thought I'd weigh in briefly here.  I'm working on the Common Printing Dialog for Google Summer of Code.  Since we're switching to PDF as the print job submission format, I may be able to add something to the dialog to dump out a PDF instead of submitting it to CUPS.  We haven't nailed down all of the details yet, so I don't know how feasible that is, but I will keep it in mind.  Also, I'm working on the KDE 4 implementation of the dialog, since I don't really know GTK+.  If I have time, I may take a crack at a GTK+ dialog.  I may make an announcement of some sort once the specification is finalized and I've done enough work on the KDE 4 dialog to know of any caveats.

GTK+ already has [GtkPrintSetupUnixDialog]("http://library.gnome.org/devel/gtk/stable/GtkPageSetupUnixDialog.html").

---

### Post by scorpion-kde on 2008-06-12
> **bruce89 said:**
> GTK+ already has [GtkPrintSetupUnixDialog]("http://library.gnome.org/devel/gtk/stable/GtkPageSetupUnixDialog.html").

That dialog doesn't support the Common Printing Dialog DBUS API.  I know that because the API hasn't been written yet.  Also, the Common Printing Dialog specification is very exact about what the layout should be.  It may be possible to use that dialog as the starting point, though.

---

### Post by Jim March on 2008-06-16
In my experience in Hardy, depending on the font some characters may not print if you use the OpenOffice 2.4 PDF output system, yet if you use CUPS-PDF you get a much cleaner version.

Now OpenOffice may get sorted some time before Intrepid but...then again, we can't predict whether or not OO will ever break again.  Having the CUPS system around as a backup can't hurt.

Plus there's God knows how many other apps out there that don't have PDF natively.

As one screwball example: I just fired up IE6 out of Wine, and was able to print to PDF through Wine and CUPS-PDF.  Does anybody think IE6 is going to get native Linux PDF generation?  Right.

No messin' with CUPS-PDF thanks!

---

### Post by Gina on 2008-06-16
Yes, I think having a system-wide PDF printing facility is definitely a good idea.  I see no reason why individual apps should need to "reinvent the wheel" to provide PDF printing.

---

### Post by Arathorn on 2008-06-16
> **Jim March said:**
> In my experience in Hardy, depending on the font some characters may not print if you use the OpenOffice 2.4 PDF output system, yet if you use CUPS-PDF you get a much cleaner version.

Now OpenOffice may get sorted some time before Intrepid but...then again, we can't predict whether or not OO will ever break again.  Having the CUPS system around as a backup can't hurt.
Don't count on it. [This bug](http://www.openoffice.org/issues/show_bug.cgi?id=43029) has been open for years without any work done on it. If you (like me) want it solved (pdf export does have advantages over pdf printing), please vote for the bug.

---

