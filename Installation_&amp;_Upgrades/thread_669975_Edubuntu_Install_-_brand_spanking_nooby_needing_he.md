---
title: "Edubuntu Install - brand spanking nooby needing help..."
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by tj.baker on 2008-01-16
Hello All,

Please forgive if there is a more appropriate place for this.... I wasn't sure where to put it.

I've just installed Edubuntu for my son to use - mostly for the GCompris educational games as he is only 3.5 years....

Install was fine - except when I try to access certain items in GCompris - I get a an error message:

... this activity requires that you first install the packages with gcompris voices for the locale 'am or 'en'

I've tried searching the .net for answers to no avail.....

The Gcompris website isn't much help either....

Any help would be much appreciated.

peace,

tj

---

### Post by tj.baker on 2008-01-17
Update

I tried the method described here to install the voices file to no avail:

[http://gcompris.net/wiki/index.php/HowTo](http://gcompris.net/wiki/index.php/HowTo)

Any other ideas appreciated.

peace,

tj

---

### Post by zvacet on 2008-01-17
Did you try **system>administration>language support>select **locale wich you want and download it.

---

### Post by RJ Hythloday on 2008-02-23
Did you have any other trouble w/ the install? I was trying an edu install last night w/ no luck. I am thinking off adding edu apps to an xubuntu install or maybe installing the edu desktop.

---

### Post by tj.baker on 2008-02-23
Hello,

Sorry, I have no input to offer.

I had to abandon my efforts due to a lack of time to mess with it.

I just re-formatted and went back to Windows - as I also needed to to a peer-to-peer with the computer and it was just way too much of a hassle to do that as well.

I hope to return to Edubuntu some day when I have more time to learn how to make it work ;)

Best of luck with it.

peace,

tj

---

### Post by RJ Hythloday on 2008-02-23
> **tj.baker said:**
> Hello,

Sorry, I have no input to offer.

I had to abandon my efforts due to a lack of time to mess with it.

I just re-formatted and went back to Windows - as I also needed to to a peer-to-peer with the computer and it was just way too much of a hassle to do that as well.

I hope to return to Edubuntu some day when I have more time to learn how to make it work ;)

Best of luck with it.

peace,

tj
Don't give up! I did that (m$ reinstall) about a year ago after no luck w/ gentoo and ubuntu. After that last m$ install corrupted itself I decided to give it a go again. There is definitely a learning curve but I'm really having a lot of fun, and now am looking forward to some customization!

---

### Post by tj.baker on 2008-02-23
Thanks for the words of encouragement... :)

It's simply a matter of not having time to learn how to make things work right now.  With a full time job and full time school - as well as raising my kids.... I just don't have time right now to mess with making things work.

I will definitely come back to it when I do have time -- it's just not any time in the foreseeable future. ;)

peace,

tj

---

### Post by mmatessa on 2008-07-14
> **tj.baker said:**
> Install was fine - except when I try to access certain items in GCompris - I get a an error message:

... this activity requires that you first install the packages with gcompris voices for the locale 'am or 'en'


I had the same problem and typed the following in a terminal window:
sudo apt-get install gcompris-sound-en gcompris

That fixed it.

---

