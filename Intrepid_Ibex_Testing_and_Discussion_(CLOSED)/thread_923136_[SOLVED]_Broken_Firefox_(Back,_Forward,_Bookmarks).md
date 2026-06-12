---
title: "[SOLVED] Broken Firefox (Back, Forward, Bookmarks)"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Rashedul on 2008-09-18
Firefox seems to be broken for the past few days. My bookmarks are gone, the bookmark toolbar is missing (along with the Live bookmarks from BBC and Most visited bookmark area). That area is completely blank. The back and forward buttons don't work. I don't think Firefox is keeping track of Back and Forward since Alt+backspace doesn't work either. Whenever I click on a link the address bar doesn't update to the new location. 

Example: type in [www.google.com](www.google.com), visit a link from there but address bar is still [www.google.com](www.google.com). Same with new tabs. If type in [www.google.com](www.google.com) in one tab and open anoter new tab with a different location the address bar still displays [www.google.com](www.google.com). Pages are rendering fine but seems like the firefox interface is broken. 

Running from Terminal gives this error message at startup

> Error sanitizing history: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: chrome://browser/content/sanitize.js :: anonymous :: line 115"  data: no]


I'm running Epiphany in the meantime. I had Swiftfox installed before but that was broken too, same condition as firefox. Removed swiftfox. Should I file a bug report?

---

### Post by caryb on 2008-09-18
I had the same problem a few days ago & some kind sole suggested I delete ~/.mozilla/firefox folder & bingo all works well now!


Cary

---

### Post by Bakon Jarser on 2008-09-18
The first thing I would do is back up your bookmarks.  If you can't get the export feature to work in the bookmarks menu then you will have to go into your home folder and find the .mozilla folder (make sure view hidden folders is enabled).  Look for a file called bookmarks.html and make a copy of it somewhere else.  Then I would go into the synaptic package manager, find firefox, and mark for complete romoval.  Then I'd do a reinstall.  I'm not sure if the complete removal gets rid of the .mozilla folder or not, so if that doesn't work do the complete removal again and manually delete the .mozilla folder before reinstalling.

Edit:  just saw the other response.  sounds easier.  try that first but still back up your bookmarks first.

---

### Post by Rashedul on 2008-09-18
> **caryb said:**
> I had the same problem a few days ago & some kind sole suggested I delete ~/.mozilla/firefox folder & bingo all works well now!


Cary

Thank you. That Worked.

Unfortunately I already tried the purging and reinstalling method and lost all my bookmarks. Anyway everything is working again. Thanks.

---

### Post by tricktone on 2008-10-27
I had this same issue, it's caused by running firefox as root then killing the process before allowing firefox to clean up after itself. 

An alternative solution is to simply run firefox as root, then close it normally. Afterwards, it should execute with no problems.

---

