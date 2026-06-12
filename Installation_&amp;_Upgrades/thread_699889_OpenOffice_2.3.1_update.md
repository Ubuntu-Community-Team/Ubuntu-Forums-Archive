---
title: "OpenOffice 2.3.1 update"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Kleenux on 2008-02-17
Gutsy comes with OO 2.3.0 which is a bugs nest. Thanks to Ubuntu policy we are stuck with 2.3.0 until next release (march?).

So I searched a few ways to update to 2.3.1 from the net, but the latest OO release does not include a .DEBS folder, only RPMS.

Is there a trick?

---

### Post by Bubba64 on 2008-02-17
I agree that Open Office with Gutsy has some limitations that are causing me to not be able to graph for a science class correctly. At least I am unable to get the spread sheet to do X & Y scatter graphing and not put all the data points in the Y horizontal. I am sure it is my misunderstanding of the parameters to do this correctly, but the help section is no help. consequently I am getting my grade points bumped down it is hair pulling frustration. The programs in Dappers Open Office were straight forward in doing this basic graphing.

---

### Post by Lord Landis on 2008-02-17
> **paris-unmatch said:**
> So I searched a few ways to update to 2.3.1 from the net, but the latest OO release does not include a .DEBS folder, only RPMS.

Is there a trick?

Yes - you'll need to install alien.  It's in the repositories, and is used to convert a package from one format to another.  Because you're trying to convert RPMs to DEBs, you'll also have to have the following packages installed: gcc, make, deb-helper, dpkg-dev, and dpkg.  Most of these should already be installed.

Once you've got the necessary packages for alien installed and you have your RPMs unpacked to a directory, open a console and switch to the directory you unpacked your RPMs to and code:
```
alien -d *.rpm
cd desktop-integration
alien -d *.rpm
```

This will convert all of the RPMs to DEBs.  After that, you need to remove the old version of OpenOffice.

Do that by using the following:
```
dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```

Once that's complete, you can install the new version with:
```
sudo dpkg -i *.deb
cd desktop-integration
sudo dpkg -i *.deb
```

The last step above, the install from the desktop-integration directory, is necessary to get the menu items installed.

---

### Post by jcwmoore on 2008-02-17
you can find DEBs on the official web site

[http://download.openoffice.org/2.3.1/index.html]("http://download.openoffice.org/2.3.1/index.html")

The link to the DEB download is under the linux download "box."  you just extract the files, and then run
```
sudo dpkg -i *.deb
```

the desktop files are stored in another folder called DESKTOP INTEGRATION (i think)

```
cd DESK*
```

and then

```
sudo dpkg -i *.deb
```

---

### Post by Kleenux on 2008-02-17
Thank you (and this time I didn't miss the Thanks icon :)

Actually to complete a bit my first post: 2.3.0 worked ok for most of OO features.
But, for some reasons, after  - my guess -   a security update, some images I embedded in my document a while ago where mixed with the text around it... There was no problem before the update (as the generated PDFs can whitness). 
That was **pretty annoying**.
 (guys, thank you for contributing to Ubuntu/OO but please **test** them carefully before delivering...

---

