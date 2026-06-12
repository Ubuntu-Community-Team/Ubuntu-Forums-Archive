---
title: "Migration Advice - Dapper to Lucid"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by houseisland on 2010-07-02
Hi,

My daughter has been happily using the Dapper installation I did for her ***years*** ago, but now it is time to update her system.  Technology has moved on and support for new social networking stuff in Dapper has not progressed (not surprisingly).  And more importantly her hard drive is dying.  

I am going to do a clean installation of Lucid on a new drive.  I have done a pilot installation on another PC, and it looks very nice.

I would like to recover as much as possible (settings and data) from her profile in Dapper.

Are there any general advice links that someone can point me to?

Thanks.

;)

____________________________________________
 
 [IMG]http://i1.tinypic.com/n5ngxw.jpg[/IMG]
 
 It is my pure and virtuous heart that
 gives me the strength of ten!

---

### Post by davidmohammed on 2010-07-02
generally, the only areas to concentrate on is the /home folder and usually just your main user account.

save files saved on the Desktop, Documents, Downloads, Music, Pictures etc.

Don't bother saving anything in hidden files & folders.  These can easily be recreated by tweaking applications.

Dont forget to note down all the applications that you need to reinstall - just examine the main menu.

On the fresh install, just reinstall either via synaptic manager or software-centre.

---

### Post by houseisland on 2010-07-02
> **davidmohammed said:**
> generally, the only areas to concentrate on is the /home folder and usually just your main user account.

save files saved on the Desktop, Documents, Downloads, Music, Pictures etc.

Don't bother saving anything in hidden files & folders.  These can easily be recreated by tweaking applications.

Dont forget to note down all the applications that you need to reinstall - just examine the main menu.

On the fresh install, just reinstall either via synaptic manager or software-centre.

Thanks.

What about email?  She is using Evolution.  I assume that her mail box can be ported over.

Browser favourites?

I seem to remember that it took a long time to get all the codec packages, the ones necessary to function in the non-Linux world, installed.  I guess if I just try to replicate what I did before, it should be OK.


____________________________________________
 
 [IMG]http://i1.tinypic.com/n5ngxw.jpg[/IMG]
 
 It is my pure and virtuous heart that
 gives me the strength of ten!

---

### Post by warfacegod on 2010-07-02
Firefox Add-ons and Bookmarks are found in .firefox a hidden folder in /home. I assume Evolution contacts would be found in a similar folder in /home.

---

### Post by davidmohammed on 2010-07-03
For evolution - the easiest way would be to export all emails - migrate and then import

see this [link]("http://email.about.com/cs/evolutiontips/qt/et110103.htm") - 

for firefox settings - look at using an addon like xmarks - this allows you to backup history, bookmarks, passwords etc and transfer them to another computer.

codec packages are easily reinstalled

sudo apt-get install w32codecs
sudo apt-get install ubuntu-restricted-extras

---

### Post by houseisland on 2010-07-03
Thanks all!


:)

____________________________________________
 
 [IMG]http://i1.tinypic.com/n5ngxw.jpg[/IMG]
 
 It is my pure and virtuous heart that
 gives me the strength of ten!

---

### Post by houseisland on 2010-07-04
Hi,

It is all going mostly OK.  

A combination of the help here (both in this thread and elsewhere in the forums) and persistence has moved things forward.

I have given up on Brasero.  After beating my head to a pulp on the edge of the desk, I installed K3b.  A quick search of the forums will give you more than you want to know about issues with Brasero and Lucid.

](*,)

I am having difficulty connecting to Windows shares now - Windows Home Server (modified W2K3 Standard in workgroup).  

This is curious because on the pilot installation of Lucid that I did on another machine a month or more ago this all worked flawlessly, and I was very impressed with the ease of interoperability.  

Now on the fully patched installation I am currently working on, nothing I try works. 

If I do not specify a share name, Lucid cannot retrieve a list of shares.  If I specify a share name, Lucid cannot mount it.

I have tried specifying the server by IP address and by server name (SERVERNAME or \\SERVERNAME - windows UNC).  

I have tried user name, USERNAME and SERVERNAME\USERNAME.

Nada. ](*,)

Any advice?

Thanks.

____________________________________________
 
 [IMG]http://i1.tinypic.com/n5ngxw.jpg[/IMG]
 
 It is my pure and virtuous heart that
 gives me the strength of ten!

---

### Post by davidmohammed on 2010-07-04
very strange - dont know an answer for nautilus

possibly [this]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/544847") is your bug...

can you connect via the command line
e.g.

sudo apt-get install smbfs

sudo mount -t cifs //<windows-IP>/<folder-sharename> /<my-mount-folder> -o rw -o username=user

---

### Post by houseisland on 2010-07-04
> **davidmohammed said:**
> very strange - dont know an answer for nautilus

possibly [this]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/544847") is your bug...

can you connect via the command line
e.g.

sudo apt-get install smbfs

sudo mount -t cifs //<windows-IP>/<folder-sharename> /<my-mount-folder> -o rw -o username=user

Thx.  That bug appears to be the one.  Same symptoms.  The bug is not there in the earlier installation of Lucid I did.  I dug that box out of the pile of cases and powered it up.  Lots of updates since I did that installation - something among them breaks interoperability with Windows.

I will try the command line option when I have a bit more time.  More later......

____________________________________________
 
 [IMG]http://i1.tinypic.com/n5ngxw.jpg[/IMG]
 
 It is my pure and virtuous heart that
 gives me the strength of ten!

---

