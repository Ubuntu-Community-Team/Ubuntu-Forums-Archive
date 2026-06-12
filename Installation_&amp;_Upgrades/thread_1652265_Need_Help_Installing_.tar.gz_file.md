---
title: "Need Help Installing .tar.gz file"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by ranjix on 2010-12-24
I downloaded exaile installer in .tar.gz format. This is my first time trying to install file of this format. Need Help for Installation!!!

---

### Post by Quadunit404 on 2010-12-24
You might have downloaded the source of Exaile by mistake. Installable packages have either the filename extension .deb or .rpm. .tar.gz archives usually just contain the source, which you have to build to install.

---

### Post by tushar maroo on 2010-12-24
Try **sudo tar xvfz filename.tar.gz -C /opt** (location)........
i installed xampp by this command line....:popcorn:

---

### Post by mikewhatever on 2010-12-24
Tar.gz is an archiving format, similar to zip or rar in the Windows world. You can't install a tar.gz, all you can do is unpack it.

---

### Post by Rubi1200 on 2010-12-24
> **ranjix said:**
> I downloaded exaile installer in .tar.gz format. This is my first time trying to install file of this format. Need Help for Installation!!!
Why? 

The program exaile is available from the repositories and you can download and install it via Synaptic (probably the Software Center too).

---

### Post by ranjix on 2010-12-24
I want to keep back up files too. I think I downloaded source file. Where can I download .rpm or .deb file of exaile and gstreamer?

---

### Post by psusi on 2010-12-24
> **ranjix said:**
> I want to keep back up files too. I think I downloaded source file. Where can I download .rpm or .deb file of exaile and gstreamer?

Applications -> Ubuntu Software Center.  Type in exaile, click install.

---

### Post by tommcd on 2010-12-24
> **ranjix said:**
> I want to keep back up files too. ...
When you install packages from Ubuntu's repositories (with the software center, synaptic, or apt-get) the backup 
*.deb* files are kept in */var/cache/apt/archives/*. Have a look in that directory and see for yourself. This is so that if you ever want to reinstall a package, you do not have to download it again.

If you want to clean old .deb files in /var/cache/apt/archives/ that can no longer be downloaded, run:
```
sudo apt-get autoclean
```
This way your archives are always up to date, without any old .debs in there.

---

### Post by ranjix on 2010-12-25
Thanks!! That worked :)

---

### Post by Rubi1200 on 2010-12-25
Glad you got it sorted out :)

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by ranjix on 2010-12-25
Done :)

---

### Post by WthIteh on 2010-12-25
You could also use a deb caching program if you want to have permanent and reliable archive of your programs. The **approx** is a good package for this task.
So **approx** will download files and host them locally for synaptic/apt-get/etc. So you could install them on other computers by adding a "yourip:9999" url to apt sources too.

---

### Post by ranjix on 2010-12-27
Done :)

---

