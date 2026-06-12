---
title: "help installing open office 2.1"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by deafchickadee on 2007-03-24
I have uninstalled the OO version that came with the Live CD. No problems.

I've installed the latest open office to my desk top....  but im having a little trouble with the code..  

I am following [slga1's]("http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=openoffice+2.1") method. I did this the other day, but had to reformat again. It worked..  but i can't remember how i managed to get it working.

> 1) download OO 2.1 from openoffice.org
2) remove the Ubuntu version of open office -- it's broken anyway
Code:

```
 dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove
```

3) convert the downloaded openoffice files from rpm to deb:
Code:

```
cd dir_where_you_extracted_the_OO_zip_file
cd RPMS
sudo alien --scripts --keep-version *.rpm
```

4) install the new version of openoffice:
Code:

```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb
```

I've installed the  newest version onto my **desktop,** how do i code step 3 with the correct directory... i'm just  little stuck...  


```
cd /home/ella/Desktop/OOo_2.1.0_LinuxIntel_install_wJRE_en-US.tar.gz'
cd RPMS
sudo alien --scripts --keep-version *.rpm
```


Thanks!!!

---

### Post by Hagar Delest on 2007-03-25
Have you unzipped the archive (tar.gz is an equivalent to zip under *nix) ? the folders are inside.

---

