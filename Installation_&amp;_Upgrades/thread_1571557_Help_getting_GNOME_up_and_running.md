---
title: "Help getting GNOME up and running"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by K3fka on 2010-09-09
Hey guys, I'm K3fka. I'm new to the world of Linux, so I would really appreciate some help with this. I just got Ubuntu to install, which is great. However, during the part of the installation that involved setting up software, something went wrong. I used the alternate installer and toward the end of that step, it told me the step failed. I simply skipped the step because of this. The result: I've got Ubuntu going, but it's only the command line. I need some help getting GNOME installed from here. I searched and saw people saying to use sudo apt-get install ubuntu-desktop, but that just fills my screen with messages about missing files. I would really appreciate some help with this!

---

### Post by tommcd on 2010-09-09
> **K3fka said:**
> However, during the part of the installation that involved setting up software, something went wrong. I used the alternate installer and toward the end of that step, it told me the step failed. ...
Exactly what step failed? 
Did you run the option: "*check disc for defects*" when you booted from the alternate CD to verify that the CD was good? If not, then you should do that now to make sure the CD is not corrupted.

For installing the Ubuntu desktop:
Did you run *apt-get update* first?
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

And welcome to the Ubuntu forums!

---

### Post by K3fka on 2010-09-10
Okay, I just tried to verify the CD. It told me that packages.tar.gz failed the checksum test. I don't know how the file could've been altered since I downloaded it from here. So I somehow have to get a correct packages.tar.gz, so how would I do this? Thanks for the help, by the way! :)

---

### Post by tommcd on 2010-09-10
> **K3fka said:**
> Okay, I just tried to verify the CD. It told me that packages.tar.gz failed the checksum test. I don't know how the file could've been altered since I downloaded it from here. So I somehow have to get a correct packages.tar.gz, so how would I do this? 
Have you been able to install the ubuntu-desktop metapackage and boot to the Ubuntu desktop?

Did you burn the Ubuntu CD from Windows? 
If so, then what program did you use to burn the CD?
If the CD fails the integrity test, it cannot be relied upon for installing Ubuntu. If you are still unable to install gnome or the ubuntu-desktop, the best course of action would probably be to:
1. Verify the md5sum of the Ubuntu iso image file you downloaded. See the *md5sum on Windows* section here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If the iso image you downloaded does not pass the md5sum check, you should download the Ubuntu alternate iso again from a different mirror. Then check the md5sum again.
2.If the iso image file passes the md5sum test, then burn a new Ubuntu install CD. If you are burning the CD from Windows, use Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then boot the new alternate CD and run the option *check disc for defects again*. If it passes the integrity test then the CD is good and you can reinstall Ubuntu from the new CD.

---

### Post by krimzonstarr on 2010-09-10
The iso wasn't changed so much as there are sometimes small errors in the downloaded file. It is always good practice to check your downloaded iso's for matching checksums before using them.

The best method for you to fix the missing Gnome install: Download a new iso, verify the checksum, and try again!

[Edit]Glad someone beat me to it... with better info as well!

---

### Post by K3fka on 2010-09-10
No, I haven't been able to boot to the desktop.
I did burn from Windows using PowerISO.
I just ran the MD5 check on the ISO and it returns the expected result.
Not really sure what to do in this case. I burned at the slowest speed (which was 4x), and I had it verify the written data after burning.

---

### Post by tommcd on 2010-09-10
> **K3fka said:**
> 
I just ran the MD5 check on the ISO and it returns the expected result.
Not really sure what to do in this case. I burned at the slowest speed (which was 4x), and I had it verify the written data after burning.
You CD is bad if it does not pass the check for defects test.
Try burning a new CD using **Iso Recorder** or **Infra Recorder** as I said in my last post:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Burn the CD at the slowest possible speed. Then boot up the new CD and run the *check disc for defects* option again.
Also, us a CDR to burn the CD, not a CDRW.

---

