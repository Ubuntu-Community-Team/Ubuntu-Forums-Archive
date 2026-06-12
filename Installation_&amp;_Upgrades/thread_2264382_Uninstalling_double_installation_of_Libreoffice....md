---
title: "Uninstalling double installation of Libreoffice..."
date: 2015-02-07
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2015-02-07
Today I've installed Libreoffice via deb files, but then I realized I could install it via ppa, too - so I did...

Its the new version 4.4.

Now I would like to remove the version I installed using the deb files, but I'm not sure how to do it...

Could anyone help?

---

### Post by ajgreeny on 2015-02-07
How did you install the deb files?

If with **dpkg** you will, I think, have to use **dpkg** to remove them as well.

See **man dpkg** for more details and come back again if this is all gobbledegook to you.

---

### Post by orange2k on 2015-02-07
Yes, I did use the dpkg command, to be exact in terminal I went to the directory of the extracted tar.gz file, went to the debs directory and there I did ```
sudo dpkg -i *.deb
```

I know that I could use the dpkg -r *filename*, but where will I find the files to remove?

There is no record of these installed files in the /var/log/apt/history.log file, only the files installed with the use of the upgrade process of the Libreoffice ppa...

---

### Post by ajgreeny on 2015-02-07
> **orange2k said:**
> Yes, I did use the dpkg command, to be exact in terminal I went to the directory of the extracted tar.gz file, went to the debs directory and there I did ```
sudo dpkg -i *.deb
```

I know that I could use the dpkg -r *filename*, but where will I find the files to remove?

There is no record of these installed files in the /var/log/apt/history.log file...
That's because you installed them with dpkg, not using apt, so apt does not know about them.

You need the list of packages installed and run ```
sudo dpkg --simulate -P packagename1 packagename2 packagename3
``` to purge the installation, though I am not sure whether or not that will remove both versions; if it does you will need reinstall the repository version again.

I used the --simulate option in that command as it will not actually do anything but will show you any likely problems.  If that command runs and says it will purge the packages with no errors, run it again without the --simulate option to actually purge them, then reinstall from the repos if necessary.  Your own configurations for LO will not be lost.

---

### Post by orange2k on 2015-02-07
I have no idea where to look for the packages...

They aren't in the usr/bin directory...

Or should I just purge everything that starts with Libreoffice?

---

### Post by SeijiSensei on 2015-02-07
Did the deb package carry a version number, like libreoffice-4.4?  One might be called that and the other called simply libreoffice.

You can use the locate command to find instances of libreoffice on your system.  On my machine with stock libreoffice, the command "locate soffice | grep bin" returns
```

$ locate soffice | grep bin
/usr/bin/soffice
/usr/lib/libreoffice/program/soffice.bin

```
Do you have multiple copies of soffice, maybe one in /usr/local/bin?

---

### Post by orange2k on 2015-02-07
Problem solved...

I used ```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove

```

and then I used

```
sudo apt-get install libreoffice
```

to reinstall it again from the Libreoffice ppa...

---

### Post by ajgreeny on 2015-02-07
I am not convinced that will have got rid of the LO version that you installed direct from the LO archive.  If I remember correctly, that used to install the office-suite into /opt, so have a look there just to make sure you have only the one installation.

---

### Post by orange2k on 2015-02-08
It did remove Libreoffice entirely, there is no trace of the other installation as far as I can see...

---

