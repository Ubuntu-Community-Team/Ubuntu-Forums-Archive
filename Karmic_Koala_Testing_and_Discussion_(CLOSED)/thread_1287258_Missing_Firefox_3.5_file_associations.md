---
title: "Missing Firefox 3.5 file associations?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ch6574 on 2009-10-09
Seems that Firefox 3.5.3 is unable to launch downloaded files automatically, nor even open the containing folder.

For example, using the following URL to an [Ubuntu torrent file]("http://releases.ubuntu.com/releases/9.10/ubuntu-9.10-beta-desktop-amd64.iso.torrent"), Firefox launches the dialog "you have chosen to open", with "Open with Transmission" as the default action.  Chose OK, and the following appears

> /tmp/ubuntu-9.10-beta-desktop-amd64.iso.torrent could not be opened, because an unknown error occurred.

Try saving to disc first and then opening the file.

Strange.

Then I try Tools->Downloads and see the torrent file listed, so try retry and get the following:

> /tmp/ubuntu-9.10-beta-desktop-amd64.iso.torrent could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.

A known issue?

I created a new profile in case, but still have the same problem.  I can also see the files under /tmp with permissions of 400 on the file.

Also if I select "Open Containing Folder" it then prompts for an application to launch it with, which is also not usual.  I can provide it /usr/bin/nautilus to open it with, but that does nothing.

Note I can manually browse /tmp from nautilus and add / delete files from there.


----

**Update** (25-Oct): solved this by removing all "firefox*" "ubufox" and "xulrunner*" packages I have installed, then reinstalled just the single "firefox" metapackage.

Logged out/in again, then tried with a new Firefox user profile and all was now back working again.  Have since tried Firefox with my old user profile, and again, all is working fine.

---

### Post by ch6574 on 2009-10-10
Small update, downloading assorted file types - a zip/bz2 file for example [Firefox]("http://download.mozilla.org/?product=firefox-3.5.3&os=linux&lang=en-GB") itself will prompt with the same dialog, defaulting to use "Archive Manager".  Select OK and the file downloads and opens correctly.

However, under Tools->Downloads the recently downloaded file is there, and you can select "open" to start the archive manager again, which is expected, but "open containing folder" still prompts for an application to use, and re-entering nautilus makes no difference.

So seems some file types will open correctly, others not.

---

### Post by Laibcoms on 2009-10-10
Might be related to the Nautilus bug wherein file associations showed up as txt files.  Haven't checked yet as to the status of that bug... just got back online after attending my sister's wedding ;)  And I'm still figuring out how to fix the wrong detection of GRUB2 :p

But that should give you a start, and check if it is really related.

---

### Post by ch6574 on 2009-10-10
I can see that all files, when saved on the desktop, have the correct associations set up in Nautilus.  So save the example torrent file to disk, double click it, Transmission launches as expected (also able to launch alternatives with a right click, for example Deluge).

Looks like the issue is contained to just Firefox.

---

### Post by utkjamie on 2009-10-18
I've having the same problem under Kubuntu Karmic. I try to launch an app from Firefox and the file gets saved to /tmp but the associated application never launches. The association works when I click the file in the /tmp folder, however.

---

### Post by ch6574 on 2009-10-25
Fixed it.  Updated the first post with what I did.

---

