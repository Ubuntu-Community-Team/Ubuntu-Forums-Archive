---
title: "How to install MS office 2007 in ubuntu ?"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by honey_bee on 2012-06-29
hi,
     I am using ubuntu 10.10 in my system .I want to install MS office 2007 in my ubuntu box. Is it possible ? if yes then please  guide me the steps so i may enjoy it.:p

thanks,
honey

---

### Post by Karlchen on 2012-06-29
> **honey_bee said:**
> I am using ubuntu 10.10 in my system .I want to install MS office 2007 in my ubuntu box. Google for the search string "Unbuntu install MS Office 2007". Returns quite a number of hits.
Among them e.g. this one: [How To Install Microsoft Office 2007 In Ubuntu (Under Wine)]("http://www.webupd8.org/2011/01/how-to-install-microsoft-office-2007-in.html")
There are other instructions, verbal and video, out there, the one linked above is not the only one.

Karl

---

### Post by coffeecat on 2012-06-29
> **honey_bee said:**
> I am using ubuntu 10.10 in my system .

Ubuntu 10.10 has passed end-of-life and is now unsupported - no updates, no security patches. I suggest you consider upgrading to or installing a supported version of Ubuntu before you try to install MS Office in wine.

---

### Post by Mark Phelps on 2012-06-29
Also, understand that only SOME MS Office components will work with Wine; others will not.

You need to go to the WineHQ website, select their application compatibility database menu item, and then do searches for the Office components you want to use.

Any component with a rating less than Gold is going to have so much functionality missing that it will be a waste of time trying to use it.

---

### Post by honey_bee on 2012-07-01
thanks for the help. I am unable to understand wine application database. For MS office 2007 or 2010  how can I search from the database.I have tried but unable to see appropriate results.
The default home page [http://appdb.winehq.org/](http://appdb.winehq.org/) show top 10 applications  which are mostly games. If I try to the following link then still no success. Surely i am doing mistake in searching.

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

From Top-10 [Platinum]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse+Applications&iappVersion-ratingOp0=5&sappVersion-ratingData0=Platinum&sOrderBy=appName&bAscending=true") List how can I search it ? 

please help me
thanks
honey

---

### Post by raja.genupula on 2012-07-02
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

click there , check out the components you need .

---

### Post by Lyfang on 2012-07-02
CrossOver Linux (fork of Wine) is a commercial application. [http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by kurt18947 on 2012-07-02
Playonlinux would be another choice.  Outlook, Access and Groove are shown to not work.  Other options if you have a Windows license would be to dual boot or, if your machine supports it, run Windows in a virtual machine.  I have no experience with either WINE or PlayOnLinux but suspect that if you need 100% fidelity,  dual boot or VM are the best choice.

---

