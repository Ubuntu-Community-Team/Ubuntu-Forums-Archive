---
title: "Karmic PDF"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shadowlands on 2009-10-23
error message when trying to open a PDF " unable to open document failed to read the catalogue
Anyone else have this problem and if so how did you correct it?

---

### Post by shadowlands on 2009-10-24
in karmic. Any time I try and open a pdf file evince gives the error

File type unknown (application/octet-stream) is not supported

If I try and open a postscript (ps) file, evince gives the error

File type plain text document (text/plain) is not supported

I can confirm

---

### Post by bennachie on 2009-10-24
There's something odd going on with the latest version of Evince. See the bug report at [https://bugs.launchpad.net/bugs/459569](https://bugs.launchpad.net/bugs/459569). However, the failure to render certain documents properly is a lot less all-encompassing than the problems you appear to be experiencing.

---

### Post by HotShotDJ on 2009-10-24
Odd.  I've tested the default PDF reader on several PDF files that I have on hand and they have all worked.  I even tried a W9 form and was able to fill out the form and save it without a problem.

Let's check a few things.  Browse to the file(s) that you are having trouble with using Nautilus and right click -> Properties.  In the "Basic" tab, what is it (what are they) showing for "type"?  It (they) should say "PDF document (application/pdf)"

If it says that, then go to the "Open With" tab and tick off the "Document Viewer" radio button. If that button is not there, click on "Add" and find it in the list, click to highlight and then click the "Add" button.

Hopefully, this will get things fixed up for you.  If not, post back and we can dig deeper.

EDIT:  I've just noticed that your file type isn't coming up correctly.  Is this with all PDF files?  Could you try to download a few?  Here is a link to one that I can confirm works fine on my system: [http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf) -- also one with fillable fields: [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fwww.irs.gov%2Fpub%2Firs-pdf%2Ffw9.pdf&ei=N2TjSszbKIGe8Abv7Lz7AQ&usg=AFQjCNE_9faiJKaWnF_E1EgGc30V0uJ3rA&sig2=m8zX346ga3u8Jr4P7GH0TQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fwww.irs.gov%2Fpub%2Firs-pdf%2Ffw9.pdf&ei=N2TjSszbKIGe8Abv7Lz7AQ&usg=AFQjCNE_9faiJKaWnF_E1EgGc30V0uJ3rA&sig2=m8zX346ga3u8Jr4P7GH0TQ)

---

### Post by shadowlands on 2009-10-24
I was hoping some one here would have a solution.  I found a bug report where at least three others had the same problem.> **bennachie said:**
> There's something odd going on with the latest version of Evince. See the bug report at [https://bugs.launchpad.net/bugs/459569](https://bugs.launchpad.net/bugs/459569). However, the failure to render certain documents properly is a lot less all-encompassing than the problems you appear to be experiencing.

---

### Post by shadowlands on 2009-10-25
> **shadowlands said:**
> I was hoping some one here would have a solution.  I found a bug report where at least three others had the same problem.

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/445689](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/445689)

---

### Post by shadowlands on 2009-10-25
> **HotShotDJ said:**
> Odd.  I've tested the default PDF reader on several PDF files that I have on hand and they have all worked.  I even tried a W9 form and was able to fill out the form and save it without a problem.

Let's check a few things.  Browse to the file(s) that you are having trouble with using Nautilus and right click -> Properties.  In the "Basic" tab, what is it (what are they) showing for "type"?  It (they) should say "PDF document (application/pdf)"

If it says that, then go to the "Open With" tab and tick off the "Document Viewer" radio button. If that button is not there, click on "Add" and find it in the list, click to highlight and then click the "Add" button.

Hopefully, this will get things fixed up for you.  If not, post back and we can dig deeper.

EDIT:  I've just noticed that your file type isn't coming up correctly.  Is this with all PDF files?  Could you try to download a few?  Here is a link to one that I can confirm works fine on my system: [http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf](http://download.virtualbox.org/virtualbox/3.0.8/UserManual.pdf) -- also one with fillable fields: [http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fwww.irs.gov%2Fpub%2Firs-pdf%2Ffw9.pdf&ei=N2TjSszbKIGe8Abv7Lz7AQ&usg=AFQjCNE_9faiJKaWnF_E1EgGc30V0uJ3rA&sig2=m8zX346ga3u8Jr4P7GH0TQ](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fwww.irs.gov%2Fpub%2Firs-pdf%2Ffw9.pdf&ei=N2TjSszbKIGe8Abv7Lz7AQ&usg=AFQjCNE_9faiJKaWnF_E1EgGc30V0uJ3rA&sig2=m8zX346ga3u8Jr4P7GH0TQ)

Ok those open just fine.  My files must be corrupted.

---

### Post by vinutux on 2009-10-25
hopes all probs fixed before final release  ...

---

### Post by Slug71 on 2009-10-25
Acroread is missing from the repos again too.

---

### Post by HotShotDJ on 2009-10-26
> **Slug71 said:**
> Acroread is missing from the repos again too.I'm not sure that Acroread is needed any more.  What added functionality would having it give users?

---

### Post by psyke83 on 2009-10-26
> **Slug71 said:**
> Acroread is missing from the repos again too.

It's in the partner repository.

---

