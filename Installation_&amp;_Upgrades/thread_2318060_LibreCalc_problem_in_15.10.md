---
title: "LibreCalc problem in 15.10"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2016-03-22
In LibreCalc under Ub 15.10, I ran into an problem - when I did a standard copy-paste or cut-paste, a dialog came up like I was importing something, and when pasted, formulas, comments, format was lost. It's bizarre - it won't paste formulas, format comments - just a conversion to text.

I decided to see if if it was like that in a Ub Studio 14.04 o/s I had installed. Using the same Calc version and same spreadsheet it worked as it should.

I guess it's a Ub 15.10 problem.

---

### Post by grahammechanical on 2016-03-22
Mostly likely a Libreoffice 5 problem.

I have noticed strange things happening with Libreoffice 5 Writer.

Copying & pasting a line of text from one document to another and the format gets changed. It does not happen every time. If the text has a certain colour then part of the line of text reverts to Automatic (black). If sections of the text are underlined, then the underline is removed but other sections the underline remains. Existing text underneath the pasted text changes font and size to the page defaults.

Libreoffice works directly with the X server and has its own tool kit. 

[https://ask.libreoffice.org/en/question/59484/does-libre-office-5-have-lots-of-bugs-on-ubuntu-linux/](https://ask.libreoffice.org/en/question/59484/does-libre-office-5-have-lots-of-bugs-on-ubuntu-linux/)

Regards.

---

### Post by ra7411 on 2016-03-22
> **grahammechanical said:**
> Mostly likely a Libreoffice 5 problem.

I have noticed strange things happening with Libreoffice 5 Writer.

Copying & pasting a line of text from one document to another and the format gets changed. It does not happen every time. If the text has a certain colour then part of the line of text reverts to Automatic (black). If sections of the text are underlined, then the underline is removed but other sections the underline remains. Existing text underneath the pasted text changes font and size to the page defaults.

Libreoffice works directly with the X server and has its own tool kit. 

[https://ask.libreoffice.org/en/question/59484/does-libre-office-5-have-lots-of-bugs-on-ubuntu-linux/](https://ask.libreoffice.org/en/question/59484/does-libre-office-5-have-lots-of-bugs-on-ubuntu-linux/)

Regards.

As I posted, in my case w/ Calc, it has worked ok w/ Ub 14.04, Ub studio 14.04, but has problems in 15.10.

---

### Post by vasa1 on 2016-03-22
> **ra7411 said:**
> In LibreCalc under Ub 15.10, ... Using **the same Calc version** and same spreadsheet it worked as it should.

I guess it's a Ub 15.10 problem.
It's useful to mention the actual version number of programs you are reporting about. 

Further, this forum allows you to attach a (small) spreadsheet to illustrate the issue.

You could also attach an image of what you seen when you attempt to paste.

---

### Post by ra7411 on 2016-03-23
> **vasa1 said:**
> It's useful to mention the actual version number of programs you are reporting about. 

Further, this forum allows you to attach a (small) spreadsheet to illustrate the issue.

You could also attach an image of what you seen when you attempt to paste.


Not a problem - I fixed it by simply re-installing 14.04.

---

