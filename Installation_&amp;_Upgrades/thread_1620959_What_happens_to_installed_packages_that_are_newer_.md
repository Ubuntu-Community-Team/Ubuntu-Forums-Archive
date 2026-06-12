---
title: "What happens to installed packages that are newer than those in the Ubuntu upgrade?"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by martini1179 on 2010-11-13
After upgrading from one version of Ubuntu to another, what happens to packages that have been installed prior to the upgrade that have higher version numbers (are newer) than the ones that are supposed to be installed via the Ubuntu upgrade? 

Specifically, I'm referring to compiling the latest version of FreeType to try to alleviate some dependency issues related to compiling Wine (I need a custom Wine patch), and I was wondering what would happen if I had a newer version of FreeType installed if I then later upgraded from Lucid to Maverick, and if Maverick used an older version of FreeType by default than the one already installed on my system.

---

### Post by searchfgold6789 on 2010-11-13
Probably nothing.

---

### Post by martini1179 on 2010-11-14
So just to clarify, does Ubuntu typically keep the newer version, or does it install the older one contained in the upgrade packages? 

I don't want to break my future Maverick upgrade, but I don't know if I should sweat over Freetype.

---

### Post by oldos2er on 2010-11-14
How did you install the software after compiling it? If you used the standard "sudo make install" it should've been placed in /usr/local. Whether /usr/local/* remains unchanged after an upgrade, I can't say. But just to be sure I would backup anything there before any upgrade.

If you created a *deb using checkinstall, you'd need to reinstall it after an upgrade.

---

### Post by martini1179 on 2010-11-14
Well I didn't install anything yet, and I have to confess that I've never compiled anything before. But I'm good at following well-written instructions. 

According to the docs that come with freetype, to upgrade it, you type 

sudo make install 

and I believe they'll be installed to /usr not /usr/local according to the output of

freetype-config --prefix

I also have the same libfreetype files installed in /usr/lib32, so would I have to install the newer version of freetype twice, once in /usr/lib and once in /usr/lib32 ? 

I just want to be able to compile Wine without all of these freetype errors.

---

### Post by Decatf on 2010-11-14
The upgrade to Maverick would overwrite the files from what ever you currently have installed. The package manager tracks what is installed based on the .deb packages but it doesn't know when you do a make install.  By doing make install you are by passing the package manager so as far as it knows the version you have installed is whatever is listed in it's database (i.e. the Lucid package)

---

