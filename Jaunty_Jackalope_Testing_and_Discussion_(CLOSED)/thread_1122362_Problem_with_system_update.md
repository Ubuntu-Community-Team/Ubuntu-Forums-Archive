---
title: "Problem with system update"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by calisun on 2009-04-11
When I did a software update earlier today, I got this message:
-----------------------------------------------------------------
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

-------------------------------------------------------------------

I did software updates for couple of weeks now now on 9.04 and today was the first time I have seen this message. Any why is WINE trying to connect to  budgetdedicated.com ?

---

### Post by kostkon on 2009-04-11
> **calisun said:**
> When I did a software update earlier today, I got this message:
-----------------------------------------------------------------
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused) [IP: 81.171.111.184 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

-------------------------------------------------------------------

I did software updates for couple of weeks now now on 9.04 and today was the first time I have seen this message. Any why is WINE trying to connect to  budgetdedicated.com ?
It seems that the server was down, but as I can see now is up and running OK and these specific files can be accessed just fine.

So, you can just check for updates again (from *System &#8594; Administration &#8594; Update Manager*) and you should be fine.

---

### Post by balaknair on 2009-04-11
wine.budgetdedicated.com is the WineHQ repository, and it's not Wine that is trying to connect to bugetdedicated, it's Synaptic, since you(or someone who installed Wine on your computer) would have added the repos when installing Wine(if you want to use the latest(beta) versions of Wine, which will not be available on the regular Ubuntu repos, but only on the WineHQ repos on budgetdedicated.com)

---

