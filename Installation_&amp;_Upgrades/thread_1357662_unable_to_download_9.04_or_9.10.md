---
title: "unable to download 9.04 or 9.10"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by trp on 2009-12-17
Hello all!  I have a Dell mini 9 with 8.04 installed.  Today I attempted to upgrade to 9.10 all went well until the software attempted to format the partition, I received this error message "The attempt to mount a file system with type ext3 in SCSl1 (0.00) partition 1 (sda) at/ failed"  Tried several more installs with the same result. I then went back to try to install 8.04 from the original Dell installation disk and got it to install, however when I go to boot the system up I get MBR 1FA, I then have to type lower case a and then hit 2 to boot to the desktop. Very annoying!  Any idea what is going on?    P.S.  I also tried 2 different 9.04 install disks, checked each one for errors and found none, and got the same download failure describes above.  Several months ago installed 9.04 succesfully on the Dell, but went back to 8.04 because I could not get wireless to work so I know the 9.04 disk is fine. Any help would be appreciated.  Thank you in advance.  Tom

---

### Post by trp on 2009-12-17
Hello! Fixed my own problem.  Turns out the MBR was corrupted when trying, unsuccesfully, to install 9.10.  To fix this problem is realatively simple yet not so easy to find on the web.  I am posting the link to the fix for anyone who might have a similar issue.    I have only been using Ubuntu for bout 9 months and love it!  Will never go back to MS and windows (add #, 7, 8 --10).  Anyway, here is the link.    Cheers,  Tom  [http://ubuntuforums.org/showthread.php?t=887895](http://ubuntuforums.org/showthread.php?t=887895)

---

### Post by mikewhatever on 2009-12-17
Glad you solved the problem, but you might think of a better, more informative thread title next time. As you can see, the current thread title has nothing, whatsoever to do with the issue you were having.

---

### Post by sarsar on 2009-12-17
Hey, i had the same problem with the uploading boot from memory stick. Pleased to hear someone has solved the UNR problem. I will now try and install UNR 9.10 this weekend. 
Id like to add, having only had UNR 9.04 and recently desktop 9.10 i would also never go back. Im also recruiting some of my friends who are having problems with windows lol.

---

### Post by trp on 2009-12-20
> **mikewhatever said:**
> Glad you solved the problem, but you might think of a better, more informative thread title next time. As you can see, the current thread title has nothing, whatsoever to do with the issue you were having.



i agree with you 100%.  At the time of the initial posting, I *was not sure* what was going on.  As research progressed I discovered the corrupt boot loader as a possible (likely) reason for my difficulties.  As I said before I am a relative noob to Linux and do not quite have the vocabulary to sometime communicate my issues in the most effective way.  I hope my future users will be able to navigate thru the sea of threads to find mine.  I will, in the future try to be a little more accurate in my thread postings.  Merry X-Mas to you all and to all a good night.  Tom

---

