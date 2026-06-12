---
title: "Problems managing Synaptic repositories (redux...)"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2007-02-13
This is the second such post I've had to create to try and locate the origin and solution to a persistent "-1" error from Synaptic regarding a repository.   This time it's:

> [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Sub-process gzip returned an error code (1)


Based on my earlier experience with this sort of problem (per [http://ubuntuforums.org/showthread.php?t=347263](http://ubuntuforums.org/showthread.php?t=347263)), I first tried locating the misbehaving repository in */etc/apt/sources.list* so I could perhaps remove an errant "us" specifier.  But I couldn't find an obvious match in the repositories listed in *source.list*.

I then tried using Synaptic itself to edit or remove the misbehaving repository, but my *guess* as to which one was the problem was wrong.

Finally, I tried running *sudo apt-get* { *upgrade* | *update* } to see if that would clear the problem.  It didn't.

So I still don't have a fix for my immediate problem.  What I do now have is a two part question:

[LIST]
[*]How can I fix my immediate problem, which is that the aforementioned repository URL is evidently incorrect.

[*]How can I manage / obtain / monitor my Synaptic repositories so that I have the ones I need and want without having to go through this every week or so?
[/LIST]

Cheers & thanks,
Ric

---

### Post by bapoumba on 2007-02-13
hello, please open a terminal (> Accessories > Terminal) and post the output to **cat /etc/apt/sources.list**.

---

### Post by Phrawm48 on 2007-02-13
B:

Okay, here it is, line numbers (28 total) added by cat for ease of reference:

> ric@ric-desktop:~$ cat -b /etc/apt/sources.list

     1  # Deleted "us." from archive to resolve "-1" error in Synaptic, 2007-02-06, Ric
     2  deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

     3  ## Major bug fix updates produced after the final release of the
     4  ## distribution.
     5  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
     6  deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

     7  ## Uncomment the following two lines to add software from the 'universe'
     8  ## repository.
     9  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    10  ## team, and may not be under a free licence. Please satisfy yourself as to
    11  ## your rights to use the software. Also, please note that software in
    12  ## universe WILL NOT receive any review or updates from the Ubuntu security
    13  ## team.
    14  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
    15  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

    16  ## Uncomment the following two lines to add software from the 'backports'
    17  ## repository.
    18  ## N.B. software from this repository may not have been tested as
    19  ## extensively as that contained in the main release, although it includes
    20  ## newer versions of some applications which may provide useful features.
    21  ## Also, please note that software in backports WILL NOT receive any review
    22  ## or updates from the Ubuntu security team.
    23  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
    24  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

    25  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
    26  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
    27  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
    28  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

ric@ric-desktop:~$

You can see near the top of the file where on 06 February I made edited  *sources.list* per my first forum thread for this issue.

The larger question for me is how to be sure that I have a complete and accurate list of Synaptic repositories, not only to prevent problems with the actual URL specifiers, but so that I'm sure I'm always working with a complete list of the "latest and greatest" repositories.

Cheers & thanks for your help,
Ric
SFO

---

