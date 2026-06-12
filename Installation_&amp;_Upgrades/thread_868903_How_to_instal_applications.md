---
title: "How to instal applications?"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by manoka on 2008-07-24
Hello,

I have downloaded the "Gnu Aspell" spellchecker for the Opera browser, but don't know how to install it, as, when I open the file, there is nothing that reads "Install package", or the like, to click on for installation.
The new Firefox seems to be rather unstable on my Ubuntu 7.10.

Just in case, I also have the following three more questions:
- Does this work like the Firefox "Add-ons" spellchecking dictionaries, by automatically and constantly checking every newly writen or changed word?
- Do I need to download a special file for the Linux Ubuntu OS?
- Where do I find the different files for different languages?

Many thanks in advance for any information!

manoka

---

### Post by argail1980 on 2008-07-24
What type of file have you downloaded? is it a tarball (.tar.gz or .tar.bz2)?
what kinds of files are in there. Maybe there's a install option from within opera.

---

### Post by manoka on 2008-07-25
I downloaded "aspell-0.60.6.tar.gz", though there seem to be other ones available too - but I haven't got the savvy for all these variations.
Where would I have to look for a install option from within opera?

---

### Post by Partyboi2 on 2008-07-25
aspell is in the ubuntu repos you can install it by opening a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install aspell
```
Unless there is a reason why you need that particular version.

---

### Post by manoka on 2008-07-25
Thanks, that seems to be done now. 
But it still doesn't work - there is no "Check spelling" button visible on the toolbar.
At 
[www.opera.com/support/tutorials/opera/spellcheck](www.opera.com/support/tutorials/opera/spellcheck) 
it also reads:

"2. Install one or more Aspell dictionaries."

How would I be able to do that after I have downloaded them?

---

### Post by Partyboi2 on 2008-07-25
To install one or more aspell dictionaries, open up synaptic package manager (System>Admin>Synaptic Package Manager and do a search for "aspell". It should give you a list of all the different dictionaries you can install. Choose one or more and install.

---

