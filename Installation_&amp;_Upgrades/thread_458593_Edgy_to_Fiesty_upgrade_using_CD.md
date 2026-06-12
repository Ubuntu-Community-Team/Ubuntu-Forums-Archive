---
title: "Edgy to Fiesty upgrade using CD"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by bobity on 2007-05-29
I am trying to upgrade from Edgy 6.10 to Fiesty 7.04 using the standard release CD.  The getubuntu/upgrading web page doesn't help much, as it seems geared to people who have burnt a downloaded CD, not to those using the release CD.  The command line supplied: gksu "sh /cdrom/cdromupgrade"  does nothing.  My Internet connection is very slow (diallup) so I do not wish to use it as I have the CD.  But how can I make this work?  I am sorry if this has already been covered in the forums -- I haven't found it after searching.

---

### Post by Ken_Lewis81 on 2007-05-30
The CD should offer you the chance to upgrade when you put it in the CD drive.  While you're running edgy, put the disk in the drive and ir should offer you upgrades.  If not, check your CD ROM drive is at in the filesystem at /cdrom/, and if it's somewhere else, adjust the command you run.  Maybe it should read ```
gksu "sh /media/cdrom-0/cdromupgrade"
```

Take care.
Ken.

---

### Post by bobity on 2007-05-30
Hi and thanks for the response.  I tried the alternate command line syntax you provided (with and without the hyphen in cdrom-0) and got the same response: a window to enter the password, and then back to command prompt.
I think the system is finding the CD all right -- when I insert the disk a file window opens called cdrom0 with a list of the files and folders on the CD.  I cannot see anything called 'cdromupgrade' however.  So I am wondering just how Ubuntu er, 'autoruns' a new CD.  Somehow or other I seem to have broken this mechanism, whatever it is.

---

