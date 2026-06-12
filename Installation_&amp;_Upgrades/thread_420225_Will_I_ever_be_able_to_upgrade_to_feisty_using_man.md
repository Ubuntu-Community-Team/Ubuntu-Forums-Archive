---
title: "Will I ever be able to upgrade to feisty using manager?!!"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by tjk on 2007-04-23
I'm getting very frustrated.  I've been trying to upgrade to feisty using the apt upgrade manager (for Kubuntu) for over a week now -- and I'm trying multiple times each day.  I realize that the system is overburdened, but this is ridiculous...

Here's an example of were the process gets stopped -- when I receive the message that I have a network problem (which I don't):

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.bz2) Sub-process bzip2 returned an error code (2)

I've also tried many times to use the "bug report" button on the error dialog, but Konqueror will not open (this would seem to be a bug in itself). I have to close the upgrade manager to get the browser working again (but then I can't send a bug report).

I have tried changing the source to "main", but it doesn't make any difference.

Does anyone have any suggestions of how I can upgrade from edgy to feisty (amd64)?

---

### Post by zvacet on 2007-04-23
```
sudo aptitude update && sudo aptitude upgrade
```

If after this still no luck just download Feisty Kubuntu 64 alternate CD and upgrade from it.

[http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807]("http://www.ubuntu.com/getubuntu/upgrading#head-0aee739ab0dfe9702a69ee3d316f5926d5d31807")

---

### Post by tjk on 2007-04-26
Still can't upgrade! (Now my thread heading should be: Will I ever be able to upgrade!)

I tried the commands in the previous message -- didn't work.

Then I used the commands listed as "Method 2 - using apt-get"
[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html](http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html)
The computer worked on it for about 24 hours, and in the end it didn't upgrade,

So now I tried downloading the alternate CD - as per the link above.  But I nearly messed up my system because I went half-way throught the install process.  Never did I find anything indicating it would "upgrade" my current system.  I was pretty sure that it was going to create a new partition and install it in there...

Please help -- this is getting very frustrating!!

---

### Post by zvacet on 2007-04-26
What exactly do you have on your Hd right now?What is so bad to do clean install instead of upgrade?

---

### Post by Nikola.srb on 2007-05-02
putting  *"Failed to fetch [http://security.ubuntu.com/ubuntu/di...ce/Sources.bz2](http://security.ubuntu.com/ubuntu/di...ce/Sources.bz2) Sub-process bzip2 returned an error code (2)"* in google.com search field brought me here... I have exactly the same problem with my upgrade, with the diference that I firstly tried upgrading from alternate CD, and when that failed then I tried network upgrade. That also failed...

is there any way for me to upgrade to Feisty ?  I was kind of waiting for that version to show to see if some problems in edgy will be fixed, but all I found is buggy updater :S

and no, format+clean install is fixing method that dont want to use.  Its too much windows like, and it realy doesnt fix anything, I will just lose data and several hours on installing all needed programs again.

---

### Post by tjk on 2007-05-02
> **zvacet said:**
> What exactly do you have on your Hd right now?What is so bad to do clean install instead of upgrade?

Well, to follow up on this thread...   After trying every option possible to upgrade, I finally chose to reinstall (clean partition -- except that my home partition is preserved in a separate partition)  And wouldn't you know it.  even with the reinstalation the same problems that existed before are still there.  If that was the only problem, I could maybe accept that ... but now I have no video or sound!!  So I'm trying to get help for some of the problems in a new thread... with little success so far...  see: [http://ubuntuforums.org/showthread.php?t=430859](http://ubuntuforums.org/showthread.php?t=430859)

Something that I discovered a couple of days ago that I didn't know was: that the upgrade manager would have been primarily (maybe entirely) tested on Ubuntu/Gnome and I run KDE/Kubuntu.  That to me explains why KDE has more problems then Gnome -- and I am seriously thinking of switching to Gnome...

---

### Post by zvacet on 2007-05-02
That is easy thing to do.

```
sudo aptitude install ubuntu-desktop
```

---

### Post by tjk on 2007-05-03
> **zvacet said:**
> That is easy thing to do.

```
sudo aptitude install ubuntu-desktop
```

Oh, it's already installed -- I just have to make the decision to permanently switch.  

And if you follow the thread in my previous message you'll find out that creating a new user has solved almost all the problems...  except that I have to reconfigure all my preferences again. :(

---

