---
title: "Epiphany 2.28.0 (karmic) breaks Bank of America website"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DJ_Peng on 2009-10-19
I sis a dist-upgrade on my system to karmic over the weekend and I discoverd a major usability issue in the Epiphany (Webkit) browser. I went to the [Bank of America]("https://www.bankofamerica.com/index.jsp") website, logged in, and tried to snag the new statement that just came out the other day and the transactions for the period. When I tried to get the statement in PDF format I ended up with an error from the Acrobat 8 plugin saying the file couldn't be found (shown in first screenshot).

When I tried to snag the QIF file of the transactions there are no buttons to actually download the file in Epiphany (Webkit, screenshot 2 with the missing buttons circled). When I tried the same tasks in the latest daily build of Chromium I was able to get the PDF as well as the QIF of the transactions (missing buttons shown in the third screenshot).

I know Acrobat 8 is old, but I'm really not thrilled with the way they changed the UI in later versions. The browsers I used are:
[LIST]
[*]epiphany-browser 2.28.0-4ubuntu1
[*]chromium-browser 4.0.223.5~svn20091019r29397-0ubuntu1~ucd1
[/LIST]
Has anyone else found this mis-behavior?

---

