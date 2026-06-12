---
title: "How to upgrade LibreOffice to ver 3.5.0 in Ubuntu 10.10 system?"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2012-02-15
I would like to use **LibreOffice 3.5** on my **Ubuntu 10.10** OS laptop, but I can not find upgrade or remove/install instructions for that combination (LO3.5 & Ubuntu 10.10)  The PPA keeps on loading LO 3.3.2, which seems now to be slightly out of date.

Why isn't there a good update application for LibreOffice?  Why isn't LibreOffice in the Ubuntu Software Center for download?

---

### Post by eveningpolestar on 2012-02-15
I am facing the same problem. Can anyone help please?

---

### Post by srpc1979 on 2012-03-14
Hi!
Open a terminal window and type:

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get dist-upgrade

The LibreOffice global menu should  work when using the packages in the PPA. If it doesn't, removing and  reinstalling it should get it working:

sudo apt-get remove lo-menubar
sudo apt-get install lo-menuba

It worked perfectly for me. Give it a try and post back here, ok!

---

### Post by jlh68 on 2012-03-15
I did what you recommended.  No success as I still have LO 3.3.2.  Also > sudo apt-get remove lo-menubar was not found

Remember I am using Ubuntu 10.10 on this laptop.  I think the repository only allows LO 3.3.2 as the most up to date on 10.10.

I even tried to purge LO and install it again, and still it was version 3.3.2.  

I sure would like to get version 3.5.x

---

### Post by lferree on 2012-03-15
Also having the same problem.. Did this on my Linux Mint 12 install, no prob

Doesn't seem to work on Ubuntu 10.10 though :(

EDIT: I think mine may be working now..
running the mentioned commands it uninstalled LibreOffice
so I just ran sudo apt-get install libreoffice
noticed 2.5 in the download list

EDIT: NOPE! Put 3.3.2 back on :(

---

### Post by lferree on 2012-03-15
OK folks..

here's the fix
[http://www.webupd8.org/2012/02/libreoffice-35-has-been-released.html]("http://www.webupd8.org/2012/02/libreoffice-35-has-been-released.html")

---

### Post by jlh68 on 2012-03-16
Okay, I purged LibreOffice and tried to install 3.5 and I get some error messages.> Error: Dependency is not satisfiable: libobasis3.5-en-US  and > Error: Breaks existing package 'libreoffice-debian-menus' conflict: libreoffice-debian-menus ( ).

So now what? It would have been so much easier if Ubuntu would have just updated the PPA.

---

### Post by jlh68 on 2012-03-16
Although I downloaded the 64bit version I am getting the following error > Unpacking replacement libdvdcss2 ...
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Preparing to replace w64codecs 20071007-0medibuntu1 (using w64codecs_20071007-0medibuntu1_amd64.deb) ...
Unpacking replacement w64codecs ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...
Setting up w64codecs (20071007-0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_i386.deb

This indicated that even thought named 64 the downloaded is i386.Here are the files I downloaded:> /home/john/Downloads/LibO_3.5.1_Linux_x86-64_helppack-deb_en-US.tar.gz and /home/john/Downloads/LibO_3.5.1_Linux_x86-64_install-deb_en-US.tar.gz

What is going on?

---

### Post by jlh68 on 2012-03-16
I am having trouble in this area > This directory contains a subdirectory called "DEBS". Change directory to the "DEBS" directory.

Right-click within the directory and choose "Open in Terminal". A terminal window will open. From the command line of the terminal window, enter the following command (you will be prompted to enter your root user's password before the command will execute):

---

### Post by Andrew_P on 2012-03-20
> **jlh68 said:**
> I am having trouble in this area:

> This directory contains a subdirectory called "DEBS". Change directory to the "DEBS" directory.

Right-click within the directory and choose "Open in Terminal". A terminal window will open. From the command line of the terminal window, enter the following command (you will be prompted to enter your root user's password before the command will execute)

The README files in the LibreOffice archive packages are hosed, at least through release 3.5.1.  The "Open in Terminal" extension isn't installed in Nautilus by default.  You can install it from the Ubuntu Software Center, or manually with "[FONT="Fixedsys"]sudo apt-get install nautilus-open-terminal[/FONT]".  In the alternative, open a terminal window and use the "cd" command to manually navigate to the directory where the DEBS subdirectory is located, then run the dpkg command as described in the README file.

The "Open in Terminal" extension is handy to have in any case, so you might as well install it.

---

### Post by Andrew_P on 2012-03-20
I'm finding that the packaging of LibreOffice is just plain awful.  I installed version 3.5.1 with .debs extracted from an archive that I got directly from the libreoffice.org site.  Instead of just clicking on a .deb file icon to start the installation process, it requires using the terminal window and typing various commands.  It also requires a second installation step to integrate LibreOffice with the GNOME desktop environment, something that is automatic with most software -- very messy.  I also installed the LibO_3.5.1rc2_Linux_x86_helppack-deb_en-US, but when I click on the "Help" menu, it brings up the online help in Firefox, not local help.

Eventually, I found LibreOffice - Ubuntu Wiki at [https://wiki.ubuntu.com/LibreOffice](https://wiki.ubuntu.com/LibreOffice) that purports to explain how to install local help, so I ran the command "[FONT="Fixedsys"]sudo apt-get install libreoffice-help-en-us[/FONT]" whereupon it proceeded to *completely overwrite the 3.5.1 installation with 3.5.0!*  Local help now works, but it broke the desktop integration, since the LibreOffice applications come up in a strange GTK style, instead of in the Clearlooks theme that I have selected for GNOME.  (The previous manually-installed version respected the installed desktop theme and came up in Clearlooks.)

The first installation directly from LibreOffice was a mess, and the second semi-official Ubuntu installation was a mess, too.  LibreOffice isn't ready for deployment on either Ubuntu or Debian systems in its present condition, in my opinion.

---

### Post by jlh68 on 2012-03-21
I tried to use _gDebi_ to install all the LO files individually, I got some installed but then I would hit dependency problems.  I am not sure why someone can't produce a neat installation of LO 3.5.1 and subsequent versions.  I never could get the terminal to find the files so I could install them.

**Andrew_P**  I concur with your assessment that LO 3.5.1 is not ready for nor is it ready to upgrade in Ubuntu.  Maybe that is why Ubuntu is slow in including it in the repository or Ubuntu is trying to get us to upgrade the OS from 10.10 to 11.10 or even 12.04LTS.  

I anticipate that I will upgrade to 12.04LTS when it comes out and I believe it will have LO 3.5.1.

---

### Post by Andrew_P on 2012-03-21
I ended up completely removing the 3.5.0 installation; additional work was needed with Synaptic Package Manager to scrub all traces of 3.5.1 as well.  I then installed US-English LibreOffice 3.4.5 instead, released a couple of months ago.  Even that was a mess and it cost a half hour, or so, just to get the basic installation done:  I examined the contents of the 3.4.5 DEBS directory after extracting the archive and found that it contained two unneeded dictionary .deb files — French and Spanish — which I deleted.  I also got the separate help .deb file and copied it into the DEBS directory so that it would be slurped up by the dpkg command while installing the rest of the suite, _before_ performing the second installation step of desktop integration.  This finally worked; the local help function comes up and the Web browser doesn't get launched.  I wanted to add a couple of more dictionaries of my choice for spell-checking, but so far have not be able to get the additional languages to appear in the Tools menu in Writer so that blocks of text could be marked with a particular language and checked against the appropriate dictionary.

This is more difficult than it needs to be and more difficult than I like it.  It's hardly competitive with Microsoft Office 97, which was released 15 years ago.

EDIT:  I found some useful information at [http://askubuntu.com/questions/72099/how-to-install-a-libreoffice-dictionary-spelling-check-thesaurus](http://askubuntu.com/questions/72099/how-to-install-a-libreoffice-dictionary-spelling-check-thesaurus) on how to install additional dictionaries on Ubuntu.  Instead of trying to do it with the installers from LibreOffice, go to System > Administration > Language Support to download and install additional language packs from the Canonical repositories.  It's a bit of overkill, because it installs more than just the dictionaries, but it appears to to so without breaking anything.  When LibreOffice Writer is restarted, one can see the additional language support in the Tools > Language menu.

---

### Post by compuguy1088 on 2012-03-27
Having similar issues with installing 3.5.1 via the ppa. Seems to be an issue with broken dependencies...

---

### Post by jlh68 on 2012-03-28
That is what I experienced, BROKEN dependencies.

---

### Post by Rayonant on 2012-04-14
I faced the same problem, even installing it trough .debs with [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**dpkg**[/COLOR] [COLOR=#660033]-i[/COLOR] [COLOR=#000000]*****[/COLOR].deb 

Has done the job but leaves a LO unsuable, since 10.10 will be out of support soon, i guess the LO team won't update de ppa for it, to overcome this what I've done is modify the ppa in synaptic so that they point to lucid wich wont give broken dependencies since it is a previous version but will update due to LTS.

So a resume of what I did:

1)   [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] purge libreoffice[COLOR=#000000][B]*

[/B][/COLOR]2) Go to[COLOR=#000000]** synaptic settings repositories  **[/COLOR]And leave the things like in the image, which is change maverick for lucid. [COLOR=#000000][B]

[[IMG]http://s15.postimage.org/r77zhlitz/Pantallazo.jpg[/IMG]]("http://postimage.org/image/r77zhlitz/")

[/B][/COLOR]

[[IMG]http://s15.postimage.org/6yp79m8wn/Pantallazo_1.jpg[/IMG]]("http://postimage.org/image/6yp79m8wn/")


3)[COLOR=#c20cb9]** sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] libreoffice libreoffice-l10n-es libreoffice-help-es

an thats it Libreoffice 3.5.2 installed, of course change the locales according to yur needs and if you want gnome or kde integration install it with 

[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] libreoffice-gnome
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] libreoffice-kde

---

