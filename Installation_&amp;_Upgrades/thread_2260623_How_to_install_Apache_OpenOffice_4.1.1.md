---
title: "How to install Apache OpenOffice 4.1.1"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by Ursus Maritimus on 2015-01-13
Hi,

I tried to find guide from here and other comments from the net, but I haven't been able to succeed, so far. For some reason, I couldn't even do it with recommendations from Open Office..

I tried to do to use terminal and Synaptic Package Maneger for installation, but Terminal always complained, that something was wrong or couldn't lock up some part. According the comments, I tried to uninstall original LibreOffice first, but even that one didn't help an a result.

So, could I have some instructions, what I should do. Somehow, I've even messed up something or that I haven't found the right way to do it.

Thanks.

---

### Post by pfeiffep on 2015-01-13
You might have a compelling reason to use one over the other but from what I can surmise there's [very little difference]("http://www.howtogeek.com/187663/openoffice-vs.-libreoffice-whats-the-difference-and-which-should-you-use/") between the 2. Both have roots in openoffice.org. I believe that LibreOffice is a bit more advanced in the release schedule.
In order for the learned folks helping at this forum to advise you;  you'll need to post some exact details about the messages that you received. Along with that your computer specifics - ie Ubuntu version, hardware specs etc.

---

### Post by deadflowr on 2015-01-13
> [COLOR=#000000]According the comments, I tried to uninstall original LibreOffice first, but even that one didn't help an a result.[/COLOR]

What command did you use?

It should be of note that Ubuntu does not actually have libreoffice installed, but instead has libreoffice packages installed for the various programs.
Such as libreoffice-writer, and libreoffice-calc. 
So in that case you would use a * symbol to reflect that all packages related to libreoffice be removed.
Something like
```
sudo apt-get purge libreoffice*
```
The * is a fill in the blank which will then make apt-get look for any packages starting with libreoffice, but ending with some or string(s).
If that makes sense.
Once it is fully purge, then you try installing OOo

---

### Post by Ursus Maritimus on 2015-01-13
Ubuntu 14.04 LTS
Intel® Ivybridge Mobile x86/MMX/SSE2
Intel® Celeron(R) CPU 1007U @ 1.50GHz × 2 
32-bit

Did download 
[LIST]
[*]Linux 32-bit DEB
[/LIST]


I tried, **Linux DEB-based Installation**


[LIST=1]
[*][SIZE=2]One you download the Apache OpenOffice tar.gz package, you should be able to decompress typing.
tar Apache-OpenOfficeX.X.X.tar.gz package or using programs such as Ark, or File-Roller.[/SIZE]
[*][SIZE=2]cd into the DEBS subdirectory of the installation directory.
You should see a lot of debs here and one sub-directory called "desktop-integration".[/SIZE]
[*][SIZE=2]Install this new version by typing sudo dpkg -i *.deb or become root using su command.
By default, this will install/update Apache OpenOffice in your /opt directory.
Alternatively, you can use a GUI package installer, reference the installation directory, and install all debs at the top level. This may also aid you in determing any dependency problems if they exist.[/SIZE]
[/LIST]
Terminal:

jukka@jukka-X201EV:~$ sudo dpkg -i *.deb 
[sudo] password for jukka: 
dpkg: error processing archive *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

The reason I wanted to change for Apache is extensions, which provides an opportunity to edit PDF..

---

### Post by deadflowr on 2015-01-13
Where'd you extract it?
Typically it is downloaded into the Downloads folder, then if you use the archive manager to extract it it'll extract it into that folder.
Look in your downloads folder, to see if a folder for apache-openoffice is there.

---

### Post by Ursus Maritimus on 2015-01-13
I used synaptic package manager, when I tried to uninstall Libre, but the way you told was for sure right way to do it.

And yes, I still got it at download folder.

---

### Post by Ursus Maritimus on 2015-01-13
And when I tried to open it from the folder, it opens up software center and provides me this:
The file &#8220;/run/user/1000/gvfs/archive:host=file%253A%252F%252F%252Fhome%252Fjukka%252FDownloads%252FApache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz/en-US/DEBS/desktop-integration/openoffice4.1-debian-menus_4.1.1-9775_all.deb&#8221; could not be opened.

The file I've got is Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz

---

### Post by deadflowr on 2015-01-13
So when you open folders and go to the Downloads folder, you have a file which is marked with a tar.gz at the end, right?
If you double click on that file, it should not open the software center but instead archive manager.
When archive manager opens you then click on the button up top mark extract. This will extract the contents into a folder in the Downloads folder.
Now you should see a new folder in the Downloads folder, it should look like a normal folder, and will not have any extensions at the end of it.
If so, next step would be to open a terminal and change the working directory using the cd command.
typically you could do this in one long command:
```
cd Downloads/Apache_Openoffice_4.1.1_Linux_x86_install-deb_en-US/DEBS
```
If done right your terminal should have a line that looks like this
[COLOR=#000000]```
[/COLOR][COLOR=#000000]jukka@jukka-X201EV:~/[/COLOR]Downloads/Apache_Openoffice_4.1.1_Linux_x86_install-deb_en-US/en-US/DEBS[COLOR=#000000]
```[/COLOR]
if so, now you can run the sudo dpkg -i *.deb command.

Special Note: The terminal has a nice function called TAB completion, which will allow you to autofill the names of the folders so you don't have to keep looking at the name to get it right.
You simply start typing the name of the folder/file and then press TAB button and it will fill in the rest, correctly. I'm probably not explaining it well, but once you try it, you will understand.

---

### Post by Ursus Maritimus on 2015-01-13
I did as you said and everything was fine until :
 jukka@jukka-X201EV:~$ cd Downloads/Apache_Openoffice_4.1.1_Linux_x86_install-deb_en-US/DEBSbash: cd: Downloads/Apache_Openoffice_4.1.1_Linux_x86_install-deb_en-US/DEBS: No such file or directory
jukka@jukka-X201EV:~$

---

### Post by deadflowr on 2015-01-13
Run
```
ls Downloads
```

---

### Post by Ursus Maritimus on 2015-01-13
jukka@jukka-X201EV:~$ ls Downloads
aoo-pdf-import-0.1.0-linux-x86.oxt
Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz

---

### Post by deadflowr on 2015-01-13
> **jukka_suikki said:**
> jukka@jukka-X201EV:~$ ls Downloads
aoo-pdf-import-0.1.0-linux-x86.oxt
Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz

So no extraction.
Try this from a terminal
```
cd Downloads
```
then extarct it in the terminal
```
tar -avxf  Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz
```
it should output a quick list of lines in the terminal and return to your username prompt.
Now redo the 
```
cd Downloads
```
command again.
You should now have a new entry beside the two that were there earlier.
Post what it says.

---

### Post by Ursus Maritimus on 2015-01-13
jukka@jukka-X201EV:~$ cd Downloads
jukka@jukka-X201EV:~/Downloads$ tar -avxf  Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz
en-US/
en-US/DEBS/
en-US/DEBS/openoffice-ooofonts_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-calc_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-writer_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-draw_4.1.1-6_i386.deb
en-US/DEBS/openoffice-javafilter_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core07_4.1.1-6_i386.deb
en-US/DEBS/openoffice-impress_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-impress_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core04_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-impress_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core01_4.1.1-6_i386.deb
en-US/DEBS/openoffice-graphicfilter_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-math_4.1.1-6_i386.deb
en-US/DEBS/openoffice-pyuno_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-writer_4.1.1-6_i386.deb
en-US/DEBS/openoffice-ure_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-res_4.1.1-6_i386.deb
en-US/DEBS/openoffice_4.1.1-6_i386.deb
en-US/DEBS/openoffice-images_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-draw_4.1.1-6_i386.deb
en-US/DEBS/openoffice-base_4.1.1-6_i386.deb
en-US/DEBS/openoffice-draw_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core06_4.1.1-6_i386.deb
en-US/DEBS/openoffice-writer_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core02_4.1.1-6_i386.deb
en-US/DEBS/openoffice-math_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-base_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core05_4.1.1-6_i386.deb
en-US/DEBS/openoffice-onlineupdate_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-en-us_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-calc_4.1.1-6_i386.deb
en-US/DEBS/openoffice-xsltfilter_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-math_4.1.1-6_i386.deb
en-US/DEBS/openoffice-ooolinguistic_4.1.1-6_i386.deb
en-US/DEBS/openoffice-core03_4.1.1-6_i386.deb
en-US/DEBS/openoffice-en-us-help_4.1.1-6_i386.deb
en-US/DEBS/openoffice-gnome-integration_4.1.1-6_i386.deb
en-US/DEBS/openoffice-calc_4.1.1-6_i386.deb
en-US/DEBS/desktop-integration/
en-US/DEBS/desktop-integration/openoffice4.1-debian-menus_4.1.1-9775_all.deb
en-US/DEBS/openoffice-ogltrans_4.1.1-6_i386.deb
en-US/DEBS/openoffice-brand-base_4.1.1-6_i386.deb
en-US/readmes/
en-US/readmes/README_en-US
en-US/readmes/README_en-US.html
en-US/licenses/
en-US/licenses/LICENSE
en-US/licenses/NOTICE
jukka@jukka-X201EV:~/Downloads$ cd Downloads
bash: cd: Downloads: No such file or directory
jukka@jukka-X201EV:~/Downloads$

---

### Post by deadflowr on 2015-01-13
I meant re-run the ls Downloads command.
But since you are now in the Downloads directory, just 
```
ls
```

---

### Post by Ursus Maritimus on 2015-01-13
Did that one as well and it provides the same as earlier
jukka@jukka-X201EV:~/Downloads$ ls
AfterShotPro2_TBYB.i386.rpm
aoo-pdf-import-0.1.0-linux-x86.oxt
Apache_OpenOffice_4.1.1_Linux_x86_install-deb_en-US.tar.gz

---

### Post by deadflowr on 2015-01-13
Try 
```
locate en-US
```
Copy and paste the output

---

### Post by Ursus Maritimus on 2015-01-13
jukka@jukka-X201EV:~/Downloads$ locate en-US
/home/jukka/.config/chromium/Dictionaries/en-US-3-0.bdic
/home/jukka/.config/google-chrome/Dictionaries/en-US-3-0.bdic
/home/jukka/.wine/drive_c/Program Files/support/help/en-US
/home/jukka/.wine/drive_c/Program Files/support/locale/en-US.xml
/home/jukka/.wine/drive_c/Program Files/support/video/core_en-US.swf
/home/jukka/.wine/drive_c/windows/system32/gecko/2.21/wine_gecko/dictionaries/en-US.aff
/home/jukka/.wine/drive_c/windows/system32/gecko/2.21/wine_gecko/dictionaries/en-US.dic
/opt/google/chrome/locales/en-US.pak
/opt/google/chrome-unstable/locales/en-US.pak
/usr/lib/chromium-browser/locales/en-US.pak
/usr/lib/firefox/distribution/searchplugins/locale/en-US
/usr/lib/firefox/distribution/searchplugins/locale/en-US/amazondotcom.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/bing.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/duckduckgo.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/eBay.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/google.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/twitter.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/wikipedia.xml
/usr/lib/firefox/distribution/searchplugins/locale/en-US/yahoo.xml
/usr/lib/i386-linux-gnu/oxide-qt/locales/en-US.pak
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/amazondotcom.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/aol-web-search.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/bing.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/eBay.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/twitter.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/wikipedia.xml
/usr/lib/thunderbird/distribution/searchplugins/locale/en-US/yahoo.xml
/usr/share/xul-ext/unity/locale/en-US
/usr/share/xul-ext/unity/locale/en-US/unity_webapps.properties
jukka@jukka-X201EV:~/Downloads$

---

### Post by deadflowr on 2015-01-13
Try with find
```
find -type d -name 'en-US'
```
The tar command should have placed a folder called en-US inside the Downloads folder.
And if you open Files and go to Downloads, nothing shows for en-US?

---

### Post by Ursus Maritimus on 2015-01-14
jukka@jukka-X201EV:~$ find -type d -name 'en-US'
find: `./.gvfs': Permission denied
find: `./.cache/dconf': Permission denied
./Downloads/en-US
./.wine/drive_c/Program Files/support/help/en-US
jukka@jukka-X201EV:~$


I'm totally without any office now. If I can't set up the Apache Open Office, I will have to set the Libre back. Only reason I wanted to change it, was the possibility to edit PDF-files, with extension of Open Office. If someone could recommend some other way to edit pdf's, I would be happy to continue with the Libre..

---

### Post by pfeiffep on 2015-01-14
There are free alternatives (not a LO integrated workflow) I found with a Google search - ie[ https://dochub.com/]("https://dochub.com/") 

I'm not familar with wine ... I surmise that you've somehow downloaded into a wine directory (./.wine/drive_c/Program Files/support/help/en-US) This certainly could affect the permission problem that you're experiencing.
Before you make a final decision about an office suite I strongly suggest you get assistance from this forum about wine and where downloads are stored. 

What's your purpose of using wine?

---

