---
title: "Firefox 3 file associations messed up"
date: 2008-07-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by minisori on 2008-07-06
Does anyone have trouble with firefox and the mime types?

At times when i try to open a file, from firefox, like maybe a txt or a pdf it just download the file and then pop ups with a message telling that can't open the file.

Other's just the applications listed to open a file type, there is not even the default one. Like for example i try to open a txt file and it's only listed "less" oO

I've had this problem also in hardy at last.

---

### Post by wh0rd on 2008-07-06
The configuration for it in Firefox 3 is located at Edit > Preferences > Applications tab.

---

### Post by minisori on 2008-07-06
Yes i know, i messed around time ago with no results. All seem to be ok there.

---

### Post by barry_nay on 2008-07-09
I have the same problem with messed up mime-types on Firefox 3.0 (Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008061015 Firefox/3.0) on Hardy Heron (Kubuntu).

For .txt files I get 'less' and for almost everything else I get 'kpdf'.  My Edit->Preferences->Applications tab is empty and there appears to be no way to edit or add an entry.

Konqueror and Dolphin have no problem opening the correct program for a particular MIME-type so I know the MIME-types are set up right on the OS.

Firefox is messed up.

---

### Post by barry_nay on 2008-07-09
Caught this on another thread:

[https://wiki.ubuntu.com/Firefox3KDEIntegrationIntrepid](https://wiki.ubuntu.com/Firefox3KDEIntegrationIntrepid) has answers and proposals for the fix for MIME-types for kubuntu users.

---

### Post by forger on 2008-07-09
something like this bug?
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239952](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239952)

* or *
close firefox, clear and update your mime cache:
```
rm -rf $HOME/.local/share/mime/*
sudo update-mime-database /usr/share/mime/
gtk-update-icon-cache /usr/share/icons/Human/
```
and try again

---

### Post by minisori on 2008-07-09
Yes that is one of the things, tried something similar but did not fix anything.

---

### Post by forger on 2008-07-09
[http://kb.mozillazine.org/File_types_and_download_actions#Unknown_or_incorrect_MIME_types](http://kb.mozillazine.org/File_types_and_download_actions#Unknown_or_incorrect_MIME_types)

[http://kb.mozillazine.org/File_types_and_download_actions#Resetting_download_actions](http://kb.mozillazine.org/File_types_and_download_actions#Resetting_download_actions)

read the above.

now close your firefox and delete the mimeTypes.rdf file

your mimeTypes.rdf should be in $HOME/.mozilla/firefox/something.default/mimeTypes.rdf
to find it, type in terminal:
> find .mozilla/ -depth -name "*mime*"

---

### Post by cnidus on 2008-07-12
I had this problem too; no helper applications in firefox3 when using KDE.  After much screwing around with mime types, the only solution I found with to install 'firefox-3.0-gnome-support'.  After a restart, all of my file associations showed up just fine and works as expected.

---

