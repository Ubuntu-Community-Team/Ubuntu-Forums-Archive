---
title: "New instalation, keep /home"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by jmvidalvia on 2007-04-18
I have Dapper, and would like to upgrade to Feisty.
When I did my first installation I made a different partition for /home folder, because I read it was safer.
I understand I won't loss any personal data if I make a new insatlation for Feisty, but my questions are:

1- Will my old configuration files work as well in Feisty (i.e. Firefox)?
2- Will the new installation add new directories or data in my old /home?
3- What about config files related with programs I had in Dapper that are not going to be in Feisty unless I install them (i.e. wine, or skype)? Won't it be a mess if I keep old ./ folders I just don't need?
4- What is better: a) backup present /home and later restore certain folders, or b) just leave the folder and tell the instalation wizzard not to format the /home partition?

Thank you very much!

---

### Post by TimelessRogue on 2007-04-18
Good morning ...

Firstly, you're gonna get lots of info on this question ... some of it conflicting with other suggestions.  Most responses with be based on that individual's particular experience with the upgrade.  But this is what worked for me ... step by step ...

1.  Update your Dapper installation with "sudo apt-get update" ...
2.  Edit your sources.list with "sudo gedit /etc/apt/sources.list" by doing a search/replace to change any reference of Dapper to Edgy and commenting out Automatix and such outside sources ...
3.  Save your sources.list after checking it to verify the replace operation ...
4.  Perform another "sudo apt-get update" and "sudo apt-get upgrade", which will upgrade your Dapper system ...
5.  Now do the same thing with your updated Dapper installation, step by step, after which you will end up with an Edgy system ...
6.  And do this again to change Edgy to Feisty ...
7.  At some point in both upgrades you may be prompted to perform a dist-upgrade ... do it ...  
8.  You now have a Feisty system with the latest kernel, which will be 2.6.20-15.27 ... without formating, loss of data, configurations, etc.  Regarding the configurations, at various stages you will be asked if you want to use your current configuration or use the new ones offered by the upgrade ... I elected to use the new ones and all went well so that I ended up with my current configuration with whatever upgrades were being offered.
9.  Now ... back to editing your sources.list ... go back in and uncomment your outside sources one by one and update again.  Some will be accepted and some will not (such as Automatix) ... simply remove or comment out the ones that can't be used ...
Now ... as I said, this what worked for me on both an older HP n5000 laptop (night before last) as well as my rather esoteric desktop (last evening) that I put together about four years ago with AMD processor, ATI 9700 graphics card, Creative sound card, Linksys wireless, etc and the only thing that I am still working on is the wireless on both.  This won't be a fast operation ... it will take several hours to do both upgrades.  But I must say it was an enlightening process ... at least for me ...

Again, you will probably get many responses on this question from an upgrade as I did to full re-installation ... choose the one you feel most comfortable with and go for it.  Either method will take quite some time ... the double upgrade or downloading the Feisty installation disc and reinstalling.

Feisty is the best so far ... and good luck ...

---

### Post by jmvidalvia on 2007-04-18
Thank you very much!
I would prefer a new installation instead of upgrading, but I'll consider it again.

---

### Post by TimelessRogue on 2007-04-18
No problem ... you're welcome and hope is of some use to you ...

As is said, either method will take some time ... a lot of it ... but the new installation process might be a bit faster and to be safe, you may need to do some back-up work before hand.  If you want a bit of safety (both now and in the future) with your /home directory you might want to create an separate /home partition before reinstalling.

Either way, good luck and have fun!

---

