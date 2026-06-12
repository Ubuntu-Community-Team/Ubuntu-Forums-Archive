---
title: "How to revert an upgrade"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-09-07
There is a package on Ubuntu that I use in an unusual way.  If I upgrade it, it may break (probably only for me, and not for others).  I do not have the time to work out why it would break and fix it if it does.  I'm more inclined to just not upgrade it at all.  But I have been urged that I should upgrade so I am willing to try.  But before I do that I MUST have a known good means to revert the upgrade.

I won't give specifics because that might lead to specific answers for the package.  I do not want to know that kind of answer.  What I want to know is the general process to do this.

For example, is there a means to "hold back" everything that represents the currently installed package to allow an upgrade to be tested?  Or is EVERY past package version guaranteed to be available that would allow me to just do the install of the old specific version?  Is there a way to see the list of all old versions to confirm that what I am running now is still available to re-install back (if there is no revert option)?

I will have time later on, like in 3-4 months.  But then I'll have time to upgrade my entire system by just doing a fresh re-install and spending the next week or so working out all the mess it caused to the things I regularly do.  Maybe I should just wait until then?  I'm on 10.10 Maverick now, and would upgrade (fresh install) to 12.04 LTS Precise later on.

But I want to consider this special upgrade now, so I'm seeking that answer about how to build a plan to fallback and revert the upgrade if it fails.

---

### Post by Stonecold1995 on 2012-09-07
Yeah you can.  To remove the package if the upgrade failed, you do:
```
sudo apt-get purge packagename-3.2
```

Then to install the old version, if should be something like this (it may be different for your package):
```
sudo apt-get install packagename-3.1
```

If you can not go back to the old package version using apt, you can download and compile and older version from source, which should be available on the developer's website.  To compile a package, this is what you do (I'm using vim 7.3 as an example):
```
wget ftp://ftp.vim.org/pub/vim/unix/vim-7.3.tar.bz2
bzip2 -d vim-7.3.tar.bz2
tar -xf vim-7.3.tar
rm vim-7.3.tar
cd vim73
./configure
make
sudo make install
cd ..
rm -r vim73
```

---

### Post by oldfred on 2012-09-08
You may be back to the old time dependency issues. The package managers have pretty well eliminated those type of issues. But if your version requires python2.5, then you have to also install that. Then to install python2.5 you may need something else ad nausum. 

If you have 25GB available just do a new install of 12.04. Then you can test that without changing anything in your current install.

---

### Post by grahammechanical on 2012-09-08
Do what I have been doing for some years before I install the latest version of Ubuntu.

I created another partition of about 10GB to 15GB. I install the latest version of Ubuntu into it and then install all by special programs that I need and I see if I can get everything working as I like it. I do this before I upgrade to the next version of Ubuntu.

You can do this with your existing version of Ubuntu and the present version of that program and then run  the update. If things work well then you have your answer.

If things do not work out then you can delete that additional partition and you will not have messed up your present OS or the program that you use.

Regards.

---

### Post by afulldeck on 2012-09-08
> **grahammechanical said:**
> Do what I have been doing for some years before I install the latest version of Ubuntu.

I created another partition of about 10GB to 15GB. I install the latest version of Ubuntu into it and then install all by special programs that I need and I see if I can get everything working as I like it. I do this before I upgrade to the next version of Ubuntu.

You can do this with your existing version of Ubuntu and the present version of that program and then run  the update. If things work well then you have your answer.

If things do not work out then you can delete that additional partition and you will not have messed up your present OS or the program that you use.

Regards.

Alternatively, install the latest version on a USB 3.0 stick. You can see if you have any incapabilities long before you make any changes to the hard drive (if that even is a concern)

---

### Post by Skaperen on 2012-09-08
I do know that problems are almost a certainty if I install from source a package that others depend on.  I've also seen that a package I am actually running is no longer available on the repository in that version.

What I had hopes was that apt-get or dpkg would have a means to "repackage" the files of a package.  Apparently the names of files in a package stays known (dpkg -L ${PKGNAME}).  So in theory these could be saved and restored.  If I were to do that manually, I might get the files back, but the dependency info would be lots (the packaging system would not know I restored).

Basically it would be something like an "OS snapshot".  One would run the snapshot program which would confirm the snapshot date and time.  Then if things go wrong, the snapshot restore program could be run to go back to whatever identified snapshot is desired (there would also be a means to delete snapshots to save space).

So I guess I need to check if the current version I have installed still has the package available to restore with, along with everything else that might also have to be restored.

---

