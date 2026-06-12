---
title: "Accessing files not &quot;owned&quot;"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by the.scarecrow on 2010-01-27
In my attempts to test Lucid from a USB bootable stick I often want to access my files in my Karmic installation on my HD.

Mostly I can't do this because I am not the "owner" of my files in Karmic which often frustrates my testing.

I don't want to open up access to all of my Karmic files as this is a reduction in security, so what is the easiest way of accessing my Karmic files from Lucid without changing the files access restrictions?

Posted from Lucid

---

### Post by cariboo on 2010-01-27
If I understand you correctly, You just want to access the files on your hard drive. to do this press Alt-F2 and type:

```
gksu nautilus
```

this will open the files as root.

---

### Post by ranch hand on 2010-01-27
Or install nautilus-gksu and then you can right click on any file and hit the option to "open as administrator".  This does require restarting x (log out, reboot, whatever you like).

---

### Post by sisco311 on 2010-01-28
> **the.scarecrow said:**
> In my attempts to test Lucid from a USB bootable stick I often want to access my files in my Karmic installation on my HD.

Mostly I can't do this because I am not the "owner" of my files in Karmic which often frustrates my testing.

I don't want to open up access to all of my Karmic files as this is a reduction in security, so what is the easiest way of accessing my Karmic files from Lucid without changing the files access restrictions?

Posted from Lucid

You want to access the files owned by your user in Karmic, right?

If so, then change your user ID in Lucid to match the user ID in Karmic.

The uid of the first user created during the installation is 1000. On a Live CD/USB the default login name is ubuntu and its uid is 999.

To find your user ID check the /etc/passwd file (the 2nd field after the login name is the uid).

To change the uid, boot in recovery mode & run:
```
usermod -u 1000 ubuntu
```
replace 1000 with the uid of user in Karmic & ubuntu with the login name of the user in Lucid.

---

### Post by the.scarecrow on 2010-01-28
Hey guys, thanks for all your replies.

They kick started my train of thought and I opted to **Add** my Karmic username to the Lucid USB. This was automatically given user ID: 1000.

Now I can switch between my Karmic ID and access all my files or the superuser ubuntu ID in just a few seconds, just what I wanted - wonderful! 

Thanks for your help, I wasn't getting there without it.

---

