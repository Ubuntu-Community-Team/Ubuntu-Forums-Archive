---
title: "small size of offline repos; how is this possible?"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by MichaelBurns on 2009-12-29
I just finished downloading all 4 offline repositories (main, universe, multiverse, restricted) for jaunty binary-i386.  They ***total*** less than 30 MB on my flash drive.  How is this possible?!  Some single applications alone that I have installed online have required 100's of MB of storage on my harddrive.  What am I doing wrong?  Or what am I misunderstanding?

---

### Post by avtolle on 2009-12-29
> **MichaelBurns said:**
> I just finished downloading all 4 offline repositories (main, universe, multiverse, restricted) for jaunty binary-i386.  They ***total*** less than 30 MB on my flash drive.  How is this possible?!  Some single applications alone that I have installed online have required 100's of MB of storage on my harddrive.  What am I doing wrong?  Or what am I misunderstanding?
The packages in the repositories are compressed, I believe.

---

### Post by MichaelBurns on 2009-12-29
> **avtolle said:**
> The packages in the repositories are compressed, I believe.I assumed as much, but even still ... GB's compressed into 30 MB?!

---

### Post by avtolle on 2009-12-29
Upon further review, did you in fact d/lall packages in the repositories listed, or just the list of the packages therein contained?

---

### Post by MichaelBurns on 2009-12-29
> **avtolle said:**
> ... did you in fact d/lall packages in the repositories listed, ...What does that mean?

(*EDIT:  Oh, sorry, I'll never keep up with the abbreviations.  Yes, I believe that I d/ledall (downloaded all) of the packages.  That belief is based on the fact that I downloaded the so-called Packages files; see my next comment.*)

I simply followed the instructions at [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by avtolle on 2009-12-29
Sorry for the typo, which you accurately deciphered. 

Looked at your link, and it definitely implies that "you have the whole shooting match" on the flash drive. Have you tried to access the same yet to install a package? Totally to satisfy my curiosity.

---

### Post by MichaelBurns on 2009-12-29
Here's what I did in order to test my new offline repos (and satisfy your curiosity).  Apparently there *IS* a problem:

**System** > **Administration** > **Software Sources** >> ***Ubuntu Software*** tab.
Unchecked *everything* (so that I know it is not going online to install the software).
**System** > **Administration** > **Software Sources** >> ***Third-Party Software*** tab.
Clicked ***Add...*** button.
Entered "deb file:///media/BACKUP/after_harddrive_failure/offline_jaunty_repos/ jaunty main universe multiverse restricted" into the ***APT line*** field.
Clicked ***Add Source*** button.
Clicked ***Reload*** button.
Received error message:  "Failed to fetch ..." for all 4 components.  Apparently, it is looking for one of the 2 "Package" files in each of the 4 component directories.  I don't know why it can't find them, because I can see them in the file browser (see crude directory tree below for precise location).
On the ***command line*** I entered:  "sudo apt-get install texlive-latex-base".
Received error message:  "E: Couldn't find package texlive-latex-base".


The repo source is a folder on my flash drive.  The folder is named "offline_jaunty_repos", and it contains folders named "main", "universe", "multiverse", and "restricted" (corresponding to the 4 so-called components?).  Each of these 4 folders contains a folder named "binary-i386", and in this folder the 2 "Package" files and one "Release" file that I downloaded for each of the 4 so-called components.  There are also 2 "Release" files and one "Contents" file that I downloaded and put directly inside the "offline_jaunty_repos" folder.  I downloaded these files and followed the directory structure according to the instructions in the webpage that I linked to in a previous post.

Here is a crude representation of that directory tree:
```

offline_jaunty_repos/
           |---------main/
           |           ---binary-i386/
           |                   |------Packages.gz
           |                    \-----Packages.bz2
           |                      ----Release.htm
           |---------universe/
           |             -----binary-i386/
           |                       |------Packages.gz
           |                        \-----Packages.bz2
           |                          ----Release.htm
           |---------multiverse/
           |              ------binary-i386/
           |                         |------Packages.gz
           |                          \-----Packages.bz2
           |                            ----Release.htm
           |---------restricted/
           |              ------binary-i386/
           |                         |------Packages.gz
           |                          \-----Packages.bz2
           |                            ----Release.htm
           |---------Release
            \--------Release.gpg
              -------Contents-i386.gz

```
Note:  this is on a usb flash drive.  In case it is relevant, by computer is not capable of booting from usb (it is 4 years old).

---

### Post by hugmenot on 2009-12-29
What you have are just the package *lists*, containing the descriptions.

The lists are in dists, the packages are in pool.

---

### Post by MichaelBurns on 2009-12-30
OK.  Are the instructions on that ubuntu help webpage incorrect, then?  Or I just have absolutely no clue what I'm doing?  Those instructions were in fact not very clear - I had to fill in some blanks.  Maybe I need the missing steps.

---

### Post by Bartender on 2009-12-30
Michael -
What is it you're trying to do?  Do you want the entire repositories for some sort of big project, or are you just trying to update one offline PC?

I tried following those directions and they weren't very clear to me either.  Obviously written by someone a little too familiar with the steps..

---

### Post by MichaelBurns on 2009-12-30
> **Bartender said:**
> What is it you're trying to do?  Do you want the entire repositories ...Basically, yes.  I'm just playin' around while I run off of a live cd.  I'm sort of playing a computer survival game with myself, and I've come to the hypothesis that it would be nice to have a usb drive with all possible packages on it ready to go.  I have no idea how big I should expect this collection to be, but I've got a 8 GB flash drive.  Of course, I still have yet to figure out how to use these repos from the usb drive, but one thing at a time.

Unfortunately, I'm now locked out of my usb drive, so I'm in the process of trying to resolve that situation before I can get back to the offline repo game.

---

