---
title: "Preserve GQView in 10.04 Lucid Lynx"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by UBM7Tablet on 2010-05-13
This is a synopsis of how I configured the Lovely Lucid Lynx v 10.04 to use GQView in preference to Geeqie, and prevented automatic removal of GQView / re-installation of Geeqie during software auto updates.  Hopefully it will be useful to other users in the forum.  

BACKGROUND/MOTIVATION:
I've come to rely on one *critical* feature of the GQView application; the ability to preview images in a dialog box in the event of a copy/move conflict.  (This is most useful when dealing with digital camera pictures with automatic file names such as "DSC_0001.JPG" which makes duplicate files names fairly common).  When GQView detects a potential conflict, it shows a preview of both images so you can decide if they are the same or two different images with the same name.  The previews allow you to intelligently decide whether to Cancel/Rename/Overwrite. 

Geeqie (version "1:1.0~beta2-9") is *almost* identical to GQView, but lacks this key "image conflict preview" feature, so I have avoided using it in the past.


"ISSUE" DESCRIPTION
I first installed GQView under 8.04, via the "Universe - community maintained software" channel as it was not one of the applications supported by Canonical.  GQView lived happily on my system until the otherwise uneventful double-upgrade from 8 to 9 to 10.04 LTS.  

The new Ubuntu Software Center and Update Manager detect Geeqie as a newer/(more actively maintained?) version of GQView as defined in the repositories.  GQView is replaced automatically during the upgrade/software update process.  

I initially uninstalled Geeqie via Software Center, and re-installed GQView manually via a .DEB package, only to find that the next automatic update would again remove GQview and re-install Geeqie.
(Note that this is functionally correct behavior for automatic updates, and if you keep an eye out for Geeqie in the update list you can manually uncheck it each time).  

I needed to find a way to both install the "old" version that I preferred, and lock it down to prevent automatic overwrites going forward.

SOLUTION  (please post a better one in reply if you can!)
The Synaptic package manager (under the System->Administration menu) provides more advanced options required to prevent automatic overwrites via "Lock Version", but does not provide a direct downgrade path from Geeqie to GQView via the "Force Version" feature, so this is a two-part/3-step solution:.

Launch Synaptic PM
Search for "Geegie" under category "All"
Select the package labeled "Geegie" / "image viewer using GTK+"
From the menu choose: "Package->Mark for Removal", press "Apply" and confirm the removal of Geeqie and related packages.
Quit Synaptic.

Acquire a GQView .DEB manual installation package via [http://ftp.debian.org/debian/pool/main/g/gqview/](http://ftp.debian.org/debian/pool/main/g/gqview/) (choose the correct version for your platform - Ex: "gqview_2.0.4-4_i386.deb" for 32-bit Ubuntu on Intel/AMD  [not the gqview-dbg* debug? packages at the top])
or create/compile one from SourceForge
Double-click on the .deb file and perform a manual install via the prompts.

Open Synaptic, Search for the newly installed Package "GQView" and Select it.
Choose Package->Force Version and select 2.0.4-4
Choose Package->Lock Version and APPLY to prevent automatic re-installation of the accursed Geeqie.

---

### Post by hellfroze on 2010-05-25
Thanks for this post - I also quickly ran into a shortcoming with geeqie: it won't allow you to rename the file during  a copy or a move operation. Which means if you want to make a copy of a file in a different directory, first you have to copy it to that directory, then navigate to it, then rename it, then navigate back and then try to find where you were.

Unacceptable.

I'm posting here to help people who might be looking for "geeqie rename move copy" keywords.

---

### Post by MrSqueezles on 2010-06-06
Thank you!  This was a great help.

---

### Post by bjornsol on 2010-07-01
Another thank you!  I wonder why they decide to go with an inferior package though rather than continue something that works great (gqview).

Thanks,

Bjorn.

---

### Post by crossy on 2010-08-27
Many thanks for this post - it turned out to be very useful. :D

I've stuck with Geegie for a while, but thought it was a little on the slow side (v's GQview!). However, today I was trying to do some admin on a large directory of files - (more than 10,000) - by spawning off Geegie and then using a command line to move the files as needed into other directories.

This worked fine with GQview in the past, but when I did that with Geegie it then told me that all the remaining files were readonly (*no, they weren't*) and a Refresh then core dumped. :( Same deal when I restarted - I moved a batch of files - the remainder were then readonly and Geegie barfed.

Used your process to reinstate GQview which subsequently had _no problems_ with what I was trying to do. I'll maybe get around to filing a bug report - although personally I'd prefer to keep with GQview because it appears quicker.

Bob

---

### Post by mrz80 on 2010-11-10
Huzzah Huzzah Huzzah!

Geeqie is enough different from GQview, which I've used for years now and to which I've become thoroughly accustomed, that just starting it was driving me up the wall and out across the ceiling.  And it looks to be *much* slower than GQview.  So thank you Thank you THANK YOU for the quick-and-dirty fix!  Back to shoving pictures around from point a to point b...

---

