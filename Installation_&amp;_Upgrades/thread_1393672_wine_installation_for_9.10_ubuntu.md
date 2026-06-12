---
title: "wine installation for 9.10 ubuntu"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by alchemist330 on 2010-01-29
ok ive had one stressful day figuring this all out and im jus confused on how to install it and ive got no clue so not even the website for wine helps......im jus extremely confused so if someone could help me thatd be awsome...or else ima jus throw this thing out the window

---

### Post by hemimaniac on 2010-01-29
it should be enabled in the repos so you can use synaptic to install it, other than that a bit more explanation as to what the trouble is ot any errors may generate alot more help, and quickly

---

### Post by ajgreeny on 2010-01-29
Go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and you will see how you can add the most updated versions to your system using the wine repository.  There is no need to install by any other means than synaptic.

You obviously didn't look very closely on the wine website, or maybe it all was a bit over your head.  Stick with it and ubuntu will soon become as easy as windows, if not even more easy.

---

### Post by alchemist330 on 2010-01-29
thanks you cuz seriously this is just so new for me and its my first time even usin sumtin this complicated but the synaptic thing.....im gunnna need a kinda step by step thing for this

---

### Post by hemimaniac on 2010-01-29
well synaptic is for the most part the easiest way to get programs for you system, simply go

menu/system > administration > synaptic package manager

enter wine in the search bar. check all you need then hit apply

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by alchemist330 on 2010-01-29
ok so i got that now what lol

---

### Post by hemimaniac on 2010-01-29
well now that you have it, you need to configure it, this is the [guide]("http://www.winehq.org/docs/wineusr-guide/config-wine-main") i go by, i'm sure there are more intuitive ones out there so if anyone has one i hope they post it. then any .exe you grab you can add it to wine via right click and open with wine.

---

### Post by Mark Phelps on 2010-02-01
> **alchemist330 said:**
> ok so i got that now what lol

Before you do much else, you should go back to the WinHQ site, look up their application compatibility page and do searches using the names of the MS Windows apps you want to run.  The ratings you get back will be a good indication of whether or not you're wasting your time trying to install them.

Wine runs SOME MS Windows apps very well, others not so well, and a LOT, not at all.

---

### Post by preit on 2010-02-03
ok, i am new to Ubuntu as well...and this guide has fixed one problem I was receiving while trying to d/l wine...but now I have another issue.  When I go into Ubuntu Software Center and attempt to download "Wine Microsoft Windows Compatibility Layer" when it gets to 3% I get this error:

---

### Post by hemimaniac on 2010-02-03
open the details in that box and post the content here please

---

### Post by preit on 2010-02-03
all it says is "wine" but here is the attachment:

---

### Post by mcoleman44 on 2010-02-03
just open a terminal and type:
sudo apt-get install wine

---

### Post by hemimaniac on 2010-02-03
thats is a new one to me, did you install wine and all its dependencies via synaptic? hopefully someone else will chime in here, *** that one totally escapes me

---

### Post by preit on 2010-02-03
> **mcoleman44 said:**
> just open a terminal and type:
sudo apt-get install wine

ok, baby steps please...how do i open a terminal (when i hear terminal i think of a place to board a plane)

thanks

---

### Post by mcoleman44 on 2010-02-03
haha....ok

Applications >Accessories >Terminal

---

### Post by preit on 2010-02-03
ok, getting somewhere...at least have some more information:

---

### Post by mcoleman44 on 2010-02-03
Close out synaptic package manager and then try it again

---

### Post by preit on 2010-02-03
sweet...now we are in Mission Impossible

---

### Post by hemimaniac on 2010-02-03
> **preit said:**
> ok, baby steps please...how do i open a terminal (when i hear terminal i think of a place to board a plane)

thanks

LOL nice, thanks for the lolz, unfortunately sometimes it takes a remark like that to remind ALL of us that the users coming to *nix really are use to something else and just need a little help and understanding. ;)

---

### Post by preit on 2010-02-03
> **hemimaniac said:**
> LOL nice, thanks for the lolz, unfortunately sometimes it takes a remark like that to remind ALL of us that the users coming to *nix really are use to something else and just need a little help and understanding. ;)

tell me to open regedit and delete HKEY_USER_blah blah blah to remove a stupid virus...i would be with that

---

### Post by mcoleman44 on 2010-02-03
Have you installed all updates through update manager?

To get to update manager:
System >Admin >update manager

And what kind of computer do you have?

---

### Post by preit on 2010-02-03
ok...here comes the updates, too bad the internet connection i am currently on is slow.  this will take awhile, hopefully by tomorrow evening (after work and all) i can continue to troubleshoot (if the updates don't fix it).

As far as my computer.  It is an HP Pavilion tx1000cto 2GB RAM 2.00GHz AMD Turion 64bit processor.

---

### Post by preit on 2010-02-03
furthermore, is it possible to save these forums in a file?  The reason being, I am in a process of testing out Ubuntu (currently have it fully installed on a 30GB portion of my HD) and want to see if it will allow me to play certain video games (rated on the Platinum and Silver with WineHQ).  If it works better than vista (the resource hog), I am going to do a complete reformat of my laptop and reinstall Ubuntu with windows on a much much smaller partition than it is now

---

### Post by mcoleman44 on 2010-02-03
You should know that wine isn't exactly reliable. Depending on what type of computer you have it may not even run the programs it claims the ability to. Is this the only reason you would make the switch to Ubuntu?

---

### Post by preit on 2010-02-03
no, far from it...this will determine basically what size partition i would use on my HD (i do enjoy my gaming, and would prefer to use one OS to do everything i want).  What would end up happening if wine is unable to play the games well, I would just have MS as my secondary partition (with about 10-15GB) and bare boned...keep it from even accessing the internet, and use ubuntu for all my surfing and real work

---

### Post by houseworkshy on 2010-02-03
There is another thing worth looking at and that is the software sources.  System>Administration>Software sources.  Look at the tab third party software and make sure that all boxes bar the source code one are checked.  If they are not when you check them and close the window you will be told that your lists are out of date and be prompted to reload, do it and after that your synaptic package manager ( as mentioned above ) should work for you.

It is also worth looking through this. [https://help.ubuntu.com/](https://help.ubuntu.com/) There is a new feature, called apt:urls, in effect as you go through the guides there are hot links which install things for you.  One I'd recommend is the restricted extras package.

---

### Post by preit on 2010-02-04
thanks everyone for the assistance...got it working.  this just further shows why i will switch to linux, i didn't spend 30 minutes playing phone and button tag to talk to Randall (who has a thick indian accent) just to ask me if my computer is plugged in, turned on, and connected to the internet.

---

### Post by mcoleman44 on 2010-02-04
Just out of curiosity, what got it working?

---

### Post by preit on 2010-02-04
you know to be honest, i can't quite say...it may have been the updates or the software sources.  Once i received all the updates and made sure sources were enabled, when i tried again it worked.  Possibly a combination of things?

---

