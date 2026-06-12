---
title: "Open Office 3.1.1 released"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-08-31
3.1.1 was released today.
Looks like Karmic was already using RC builds (although about box said 3.1.0 on alpha 4).

[http://packages.ubuntu.com/karmic/openoffice.org](http://packages.ubuntu.com/karmic/openoffice.org)
Hasn't been updated since August 13. Maybe in time for Alpha 5 on Thursday?

openoffice 3.1.1 will be available for Jaunty PPA.
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
*OpenOffice.org 3.1.1 - Only for JAUNTY (being prepared)*

Openoffice 3.2 is supposed to be released end of November so don't expect to see it in Karmic. Although hopefully PPA is updated for it.

Hopefully less bugs than the 3.1 version in Jaunty that would easily [crash for me and many others](http://www.openoffice.org/issues/show_bug.cgi?id=102456).

Sadly openoffice runs much faster on winxp for me than ubuntu. On winxp I can scroll with no lag at all, but on ubuntu if I want to "page down" 500 rows it takes a while to get there. Several other performance issues. Maybe because of compiz enabled, but I'm pretty sure it was slow before I enabled compiz. Maybe new driver technologies in 9.10 will help solve this problem.

---

### Post by dino99 on 2009-08-31
can't find that ppa at time

---

### Post by andrewabc on 2009-09-05
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Openoffice 3.1.1 for Jaunty has been released.

I had been using intrepid ppa so I switched to jaunty one listed.

I cannot get the keyserver to work (connection timeout) to get the key for the PPA so I don't get errors when updating.

---

### Post by squenson on 2009-09-05
> Sadly openoffice runs much faster on winxp for me than ubuntu. On winxp I can scroll with no lag at all, but on ubuntu if I want to "page down" 500 rows it takes a while to get there. Several other performance issues. Maybe because of compiz enabled, but I'm pretty sure it was slow before I enabled compiz. Maybe new driver technologies in 9.10 will help solve this problem.I have a dual boot laptop (Ubuntu-XP) and I have not noticed any difference in the performance of OOo, in 3.1.0 and after three minutes of tests in 3.1.1. I don't use Compiz.

By the way, to quickly go to a row, press F5, then type the row number in the row box and then Enter.

---

### Post by awlhawk on 2009-09-05
I also dual boot and on Linux it's slower. What's pissing me off more is the ugly bold borders of selected cells in Calc. They should obviously be thinner.
Notice (in screenshot) how striking is the difference between normal and "bordered" cells. Plain ugly.

---

### Post by andrewabc on 2009-09-05
> **awlhawk said:**
> I also dual boot and on Linux it's slower. What's pissing me off more is the ugly bold borders of selected cells in Calc. They should obviously be thinner.
Notice (in screenshot) how striking is the difference between normal and "bordered" cells. Plain ugly.

Odd, I have no problem with selected (or normal black border setting) cells.

With new 3.1.1 the one thing I do notice a difference in is the worksheet tabs at bottom have a much thicker black border around them. Changing my theme to human, it looks normal again. So this is caused by dust theme, not openoffice.

From your screenshot you mean the borders are thicker (it does look bad)? I presume these were applied borders (not regular no border, no colour cells, not the default grey dividers). You say "selected" which I don't see where the selected cells are in your pic. Is it all of them?

Here is part of my spreadsheet with default human theme on jaunty (OOo 3.1.1).
No problems with selection (orange) and thin black borders (grey is background colour for 5 cells).

EDIT:
Done some quick testing, and 3.1.1 seems to be very slightly more responsive for me.
Oh and when I say it is slow in ubuntu compared to winxp, I am using a 155,000 cell spreadsheet with many formulas and stuff. So that is where performance is really showing difference. I doubt I'd see any difference on a small spreadsheet.

---

### Post by andrewabc on 2009-09-05
One unacceptable flaw with 3.1.1 I just noticed is the bottom scrollbar keeps changing back to original length which is too long. I have 21 worksheets, and it cuts off the last 6 tabs (worksheets), so I have to shorten scrollbar size. I save document, close openoffice, open the same document and scrollbar is back to where it was. This did not happen in 3.1.0.

I have 22" monitor 1680*1050, and have openoffice maximized. This should not be happening. Gonna check winxp OOo3.1.1 to see if it happens on there.

:(

EDIT:
I opened spreadsheet in winxp 3.1.0 and scrollbar fine. Updated to 3.1.1 and scrollbar fine. So this appears to be ubuntu specific. Doubt it would be easy to fix.

scrolling/pgupdown in winxp is very fast no lag at all. I disabled compiz and in ubuntu it is now faster. Still some lag but not enough to cause problems like when compiz is enabled. bottom scrollbar is still too long. It remembered scrollbar length in winxp 3.1.0 and 3.1.1, but open the same spreadsheet in jaunty 3.1.1 and doesn't remember (but it remembers when I go into winxp, so it is just not applying the length value for some reason in ubuntu)

---

### Post by squenson on 2009-09-05
> One unacceptable flaw with 3.1.1 I just noticed is the bottom scrollbar keeps changing back to original length which is too long. I have 21 worksheets, and it cuts off the last 6 tabs (worksheets), so I have to shorten scrollbar size. I save document, close openoffice, open the same document and scrollbar is back to where it was. This did not happen in 3.1.0.Strange, I don't see this behavior on my 3.1.1. release. Maybe you should post in the [OpenOffice forum]("http://user.services.openoffice.org/en/forum/index.php").

---

### Post by andrewabc on 2009-09-05
> **squenson said:**
> Strange, I don't see this behavior on my 3.1.1. release. Maybe you should post in the [OpenOffice forum]("http://user.services.openoffice.org/en/forum/index.php").

Hmm, I created a test spreadsheet (just created new file), resized bottom scrollbar, saved, closed, reopened and it remembered scrollbar length.

So must have something to do with my spreadsheet and OOo 3.1.1

Interestingly, I have spreadsheet open, resize to proper length. close spreadsheet (but not calc), reopen spreadsheet, and it remembers scrollbar length. I have link to my spreadsheet on desktop (spreadsheet on ntfs windows partition), but link(shortcut) does not appear to be problem, as same thing occurs when in nautilus and open spreadsheet.

Same scrollbar problem when opening other backups of my spreadsheet.

---

### Post by squenson on 2009-09-05
Just an idea: do you save in Excel or Calc format?

---

### Post by andrewabc on 2009-09-05
> **squenson said:**
> Just an idea: do you save in Excel or Calc format?

I originally had it in excel, but switched to calc over a year ago.

Filename has .ods in it. spreadsheet scrollbar worked fine on ubuntu with 2.4.2, 3.0, 3.1
I just noticed it as soon as I upgraded to 3.1.1 on jaunty using PPA.

---

### Post by andrewabc on 2009-09-20
New bug I found.

Print "selected cells", but if part of the selection is on the (invisible) page divider line, it only prints what is on the page, then what is on second page, even though what is selected can easily be printed all on one page. This bug does not appear in windows version.

I havn't seen if this is only related to my spreadsheet or new spreadsheet, will test tomorrow.

Maybe create new spreadsheet, input lots of stuff in column a, from row 1 to 50 (row 44 appears to be last page 1, row 45 starts page 2). Select part near bottom of first page, and onto second page, and see if it all prints onto one page, instead of cutting off and printing onto two pages.

EDIT:
Yep, even new spreadsheet prints to two pages. I tested with "print to file" instead of wasting paper.

This bug really needs to be fixed. I have to boot into windows in order to do my printing now.

---

### Post by andrewabc on 2009-09-22
Filed bug report at openoffice:
[Ubuntu "Print Selected Cells" can result in multiple pages if on page divider](http://www.openoffice.org/issues/show_bug.cgi?id=105282)

Can anyone confirm this bug? So that I'm not the only person that is experiencing it?

It only takes about 20 seconds to do.
You should experience it on jaunty/karmic as long as you are using openoffice 3.1.1. It doesn't affect windows.

---

### Post by tuggy on 2009-09-22
bug confirmed. (jaunty here)
although in my case I had to put the values between 50-60 to make it to the 2nd page.

---

### Post by andrewabc on 2009-09-22
> **tuggy said:**
> bug confirmed. (jaunty here)
although in my case I had to put the values between 50-60 to make it to the 2nd page.

I figured that might happen if people use different paper size etc. Although if testing alpha 6 default, most should get same page size.

My 155,000 spreadsheet I use and print from is in landscape format, and normally printing 20 or so rows (selected), so it is usually on a page divider, and I've wasted about 20 paper sheets so far. Also the fact that my printer is old and acting up also increases wasted paper. Then of course I tried printing to networked printer, and wasted paper, as this was before I realized it was a bug in OpenOffice. I'm normally in ubuntu but when I have to print something from this spreadsheet I pretty much have to shutdown and boot into windows xp. I've noticed that winxp prints it much darker/bigger than ubuntu. Maybe a setting somewhere in printer settings. Doesn't really matter, but I thought it odd.

---

