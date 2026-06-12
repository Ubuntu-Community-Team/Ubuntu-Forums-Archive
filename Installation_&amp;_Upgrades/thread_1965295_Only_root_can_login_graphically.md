---
title: "Only root can login graphically"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by Qeu on 2012-04-25
Hi all!

I've updated my parents computer from lubuntu 11.04 to 11.10. Everything went as a charm even though it was a an update made via ssh. But when it finished I got this problem:

I cannot login graphically with any user rather than root. Not even new users created with adduser. All of them work perfectly on a terminal, but when I try to login to the GUI after entering user and password, it "blinks", gives no error but goes back to ask for the username.

Anyone can provide any help?


PS: First post with this username. I'd reckon I had registered about 5 or 6 years ago, but couldn't remember nor find the user. Shrug.

---

### Post by Qeu on 2012-04-25
Ok, I solved after deleting the  *.xsession-errors* file on the home directory of every user as there was something corrupted and seemed to be about 115GB each -which is impossible as my HD is just 20GB-.

So if anyone lands here using google, look upon those perky files on your home directory as they may be got corrupted when updating.

---

### Post by Toz on 2012-04-25
There is no normal reason why the .xsession-errors file should be so large. It might be worth your while to have a look at the file to see if there are any repeating warnings and/or error messages. There is a good chance you might end up in a similar situation again if .xsession-errors keeps growing in size and using up all your free space.

---

