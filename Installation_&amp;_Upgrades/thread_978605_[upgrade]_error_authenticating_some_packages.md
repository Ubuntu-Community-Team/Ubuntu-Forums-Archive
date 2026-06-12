---
title: "[upgrade] error authenticating some packages"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by mozartvn on 2008-11-11
when I upgrade ubuntu 8.04 to 8.10 online, this error appears.
[IMG]http://img222.imageshack.us/my.php?image=screenshottn6.png[/IMG]
[[IMG]http://img222.imageshack.us/img222/973/screenshottn6.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshottn6.png)[[IMG]http://img222.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
what should I do? plz help me, thank u very much. :confused:

---

### Post by aysiu on 2008-11-11
Maybe try another mirror?

Go to System > Administration > Software Sources and pick Main Server or your country's local server or another server.

---

### Post by juanbretti on 2008-12-14
I have a similar error with  8.10.

I have the problem with this packages:

```
openoffice.org-base-core
openoffice.org-calc
openoffice.org-core
openoffice.org-draw
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-math
openoffice.org-writer
python-uno
```

And then, the upgrade close.
Any ideas why?

Thanks!!!

(I leave copy of my Software Source config)
Thanks!

---

### Post by prinknash on 2008-12-14
> **pepemosca said:**
> I have a similar error with  8.10.

I have the problem with this packages:

```
openoffice.org-base-core
openoffice.org-calc
openoffice.org-core
openoffice.org-draw
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-math
openoffice.org-writer
python-uno
```

And then, the upgrade close.
Any ideas why?

Thanks!!!

(I leave copy of my Software Source config)
Thanks!


I have the same problem with those Open Office Org files, and assumed it was because I'd upgraded to version 3 from the version 2 installation which comes with Ubuntu 8.10 - and that the files being held back were appropriate to version 2 of O.O.o which I no longer use. (I'd upgraded directly from the O.O.o website because, as I understand it, Ubuntu aren't offering version 3 for Ubuntu 8.10 and won't offer it until the next version of Ubuntu.)

Of course, I may be entirely wrong in any or all of these assumptions ...

p

---

### Post by juanbretti on 2008-12-14
> **prinknash said:**
> I have the same problem with those Open Office Org files, and assumed it was because I'd upgraded to version 3 from the version 2 installation which comes with Ubuntu 8.10 - and that the files being held back were appropriate to version 2 of O.O.o which I no longer use. (I'd upgraded directly from the O.O.o website because, as I understand it, Ubuntu aren't offering version 3 for Ubuntu 8.10 and won't offer it until the next version of Ubuntu.)

Of course, I may be entirely wrong in any or all of these assumptions ...

p

And how do I hide those upgrades? I mean, how do I take off the error message?

---

### Post by prinknash on 2008-12-14
> **pepemosca said:**
> And how do I hide those upgrades? I mean, how do I take off the error message?

That's what I want to know too!

Actually, I'm not sure you can. May be stuck with them until Ubuntu provides Open Office Org version 3?

p

---

### Post by juanbretti on 2008-12-14
> **prinknash said:**
> That's what I want to know too!

Actually, I'm not sure you can. May be stuck with them until Ubuntu provides Open Office Org version 3?

p
But Ubuntu has the packages: check this tutorial:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

They mentioned the source at lunchpad:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

So I think that Ubuntu supports the OOo 3.

---

### Post by juanbretti on 2008-12-14
Ok, the solution for the Update stop showing the error is to uncheck the OOo repository.
See the attachment.

Actually, is **not** a solution. But stops.

---

### Post by stefanadelbert on 2008-12-20
I was having the same problem when using the Update Manager on my Intrepid installation, but solved it by updating from the commandline using apt, like this:
```
sudo apt-get dist-upgrade
```

---

### Post by juanbretti on 2008-12-21
> **stefanadelbert said:**
> I was having the same problem when using the Update Manager on my Intrepid installation, but solved it by updating from the commandline using apt, like this:
```
sudo apt-get dist-upgrade
```
OK, I was asked to install the "un-authenticated" packages (the OOo 3 packages).

I think the problem is that I don't have the Key of the OOo packages at launchpad.

Does any one knows how's that key?

Thanks!

---

### Post by juanbretti on 2009-01-11
> **pepemosca said:**
> OK, I was asked to install the "un-authenticated" packages (the OOo 3 packages).

I think the problem is that I don't have the Key of the OOo packages at launchpad.

Does any one knows how's that key?

Thanks!
No comments? No ideas? Help?

---

### Post by krisgesling on 2010-02-23
Hey I know this is an old post but I was having issues with package authentication and thought other people might stumble across it as well.

I was getting 
"WARNING: The following packages cannot be authenticated!"
in reference to some open office files when I was trying to run updates.

To fix it in the end all I had to do was run 

sudo apt-get clean

Hope that might help some others.

cheers

---

### Post by juanbretti on 2010-02-23
> **krisgesling said:**
> 
sudo apt-get clean


Thanks! I'll keep it in mind!

---

