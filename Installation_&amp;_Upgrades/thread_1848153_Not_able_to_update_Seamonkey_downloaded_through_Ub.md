---
title: "Not able to update Seamonkey downloaded through Ubuntu Software Center"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2011-09-22
Hello Folks!

Yesterday only, I downloaded "Seamonkey Navigator" using the Ubuntu Software Center present within my Ubuntu 10.10. After making the very first access, I came to know about it being an "Outdated" version--2.0.11.

Since then, Iam using "Check for Updates" within the HELP Menu of the navigator & have also tried the "Ubuntu Updates" option to catch hold of the latest version....but to no avail?!

My Internet connection is working fine, but the former attempt leads to "Checking for latest release"...hovering on endlessly, with no activity showing up on my Router!?

Similarly, Ubuntu updates seem to have NO CONCERN for Seamonkey updates..!!

Where does I go from here...!?


Most importantly, why this download furnished using "Ubuntu Software Center" yielded an Outdated version & WHY NOT the latest ongoing release?


Help & any kind of HONK-HONK in the ears of Ubuntu Maintenance team would be sincerely appreciated.

---

### Post by dino99 on 2011-09-22
look at your synaptic settings tabs: repo checked, main server, ...

---

### Post by naikmanoj1991 on 2011-09-22
ya...try to update it from synaptic package manager..its good...

---

### Post by Saurabhdua on 2011-09-22
Hello Dino99!

Iam not able to exactly follow on what you have stated!? Yes, Iam able to access the "Settings"menu within Synaptic Package Manager....then what next please!?

---

### Post by Saurabhdua on 2011-09-23
Hello There!

Even the 'Synpatic Package Manager' are depicting the installed & the latest release being the same!? Fact lies in complete contradiction to this. 

More inportantly, if I can catch hold of latest updates of Opera & Chromium web browsers through Ubuntu's Software Update; then why this kind of disparity with Mozilla Firefox's "Half-brother">>>aka>>>Seamonkey Navigator?!

---

### Post by missmoondog on 2011-10-07
if you don't know how to use the command line, and even if you do, you have to practically jump through hoops, to get the most recent version of seamonkey installed.

i posted this exact question like 4 days ago and the replies gave pretty decent details and a link on how to do it, but i'm not jumping through those hoops either.

one person did reply stating that those things may be changing in the near future.

here's a link to that thread:
[http://ubuntuforums.org/showthread.php?t=1853950&highlight=seamonkey](http://ubuntuforums.org/showthread.php?t=1853950&highlight=seamonkey)

---

### Post by zvacet on 2011-10-07
@ **Saurabhdua**

You can not update via synaptic or cli because that is package version in repos for 10.10.You can add PPA from [here.]("https://launchpad.net/~seamonkey2/+archive/seamonkey2")Then you will be able to upgrade your browser.

---

### Post by snowpine on 2011-10-07
2.0.11 is the correct Seamonkey for Ubuntu 10.10 according to:

[http://packages.ubuntu.com/search?keywords=seamonkey&searchon=names&suite=maverick&section=all](http://packages.ubuntu.com/search?keywords=seamonkey&searchon=names&suite=maverick&section=all)

You are using the October 2010 Ubuntu release and therefore your default software applications will be from that time period. Just as if you buy a 2010 model car it will not have the same parts as a 2011 or 2012 model car.

You can of course install the 2011 Seamonkey if you prefer; zvacet has given one good way to do this, the other is directly from the Seamonkey website: [http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/)

---

### Post by missmoondog on 2011-10-08
> **zvacet said:**
> @ **Saurabhdua**

You can not update via synaptic or cli because that is package version in repos for 10.10.You can add PPA from [here.]("https://launchpad.net/~seamonkey2/+archive/seamonkey2")Then you will be able to upgrade your browser.

i've looked at the link a few times previously and wasn't really sure i was reading it correctly, but i just now said what the heck, let's try it.

still no current version of seamonkey showing up in synaptic after adding those ppa's. got nothing but several libgwib things which according to the description of is made for social networking crap, which i can't stand!!

---

### Post by zvacet on 2011-10-09
```
sudo add-apt-repository ppa:seamonkey2/seamonkey2
```

Hit enter and then 

```
sudo apt-get update
```

Hit enter one more time and then look in synaptic for new version of Seamonkey.

---

### Post by missmoondog on 2011-10-09
i finally came across the worlds simplest way to get the current version of seamonkey. go to the below link and simply search for seamonkey. click on either one of the linux logo's next to each repository listed (currently 6 listed). the logo to the right will hi-lite the ppa link to copy. the first one listed has a ppa for 2.4.1. simply add that ppa to your sources list and go get the current version through sysnaptic. you will get an error saying key can't be imported or verified when you reload repos, but it still installs everything correctly!!

[http://www.sourceslist.eu/repofinder/](http://www.sourceslist.eu/repofinder/)

Edit:
Not the greatest with command line stuff, but also found a way to add the key for this. simply type sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys "add key line here" into a command line. Where it says "add key line here" is where you enter the key number from the error message you get in synaptic. 

this is all a piece of cake and can't believe it was so hard to get it figured out how to get a current version of seamonkey. can finally use my favorite, and the best, browser again!!  :)

---

