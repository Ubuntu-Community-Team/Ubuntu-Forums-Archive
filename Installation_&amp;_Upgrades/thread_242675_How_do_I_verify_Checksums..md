---
title: "How do I verify Checksums."
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by MacLingo on 2006-08-24
On the "BurningISOHowto" page, for Windows XP Step 1 is "Verify the ISO file."  That is a pointer to the OpenOffice.Org.  That takes you to an OpenOffice page "Using MD5Sums" ([http://www.openoffice.org/dev_docs/using_md5sums.html)](http://www.openoffice.org/dev_docs/using_md5sums.html)).

Step 3 says "In Firefox, go to the "Downloads" window  and right click the OpenOffice.org archive file, then select "Check Digest" as shown below."

When I right click on that file, which is called "OOo_2.0.3_Win32Intel_install.exe" (OpenOffice.Org), a window opens, but it is only a file information window, and there is no option "Check Digest".

So what am I doing wrong?

And another question: where do the checksums come from. In step 4 it says "Copy the MD5 Checksum for the corresponding OpenOffice.org archive file from the MD5Sum page (linked to on the latest download page) and paste it into the "Reference Digest" space. "  What is the "OpenOffice.org archive file" and what is the "MD5Sum page (linked to on the latest download page)"?

None of these steps seems to have any relation to what I see on the screens.

Thanks,
Befuddled user Mac  ](*,)

---

### Post by encompass on 2006-08-24
What is it your trying to do... check the md5sum of a file?  Or install Openoffice?

---

### Post by MacLingo on 2006-08-24
Trying to figure out how to verify an iso version of ubuntu.
Tnx,
Mac

---

### Post by encompass on 2006-08-24
if your in linux.. just type:
```
md5sum file.iso
```
it will give you a big number and letter line and compair that with the one on the website.
If you have already burned it... just do the check the cdrom section of the boot menu.
Lastly:
if you in windows install md5sum...
[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)
(I just typed md5sum windows in the firefox address bar.)
Hope this helps.
use that md5sum program the same in in linux... jsut you have to use the md5sum where it is put and not anywhere you like in linux.

---

### Post by aysiu on 2006-08-24
> **MacLingo said:**
> Trying to figure out how to verify an iso version of ubuntu.
Tnx,
Mac
Read this:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by MacLingo on 2006-08-24
I've found that page, but it isn't any more helpful, or at least I am not adept at deciphering it.

The operational line is "While that's downloading, scroll down the page to a directory tree where you'll see a file called MD5SUMS. Click on it."  But I don't see for the life of me how to see the "directory tree".  Where does it come from?

Tnx,
Mac

---

### Post by aysiu on 2006-08-24
For example, on this page:
[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

Scroll down and look for this part of the page (see attached screenshot).

I really don't see how that needs deciphering.

---

