---
title: "OpenOffice 3.4 installation on Ubuntu 12.04"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by nikhilbhalwankar on 2012-09-05
Hi Friends,

Can anybody please help me out with OpenOffice 3.4 installation on Ubuntu? I am not able to install the same. I really feel its better than LibreOffice. Your inputs are very much welcome !!


Many Thanks,
Nikhil Bhalwankar

---

### Post by houseworkshy on 2012-09-05
If you get the "deb" file it should work on Ubuntu.  
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)
There is an installation guide here
[http://www.openoffice.org/download/common/instructions.html#linux-deb](http://www.openoffice.org/download/common/instructions.html#linux-deb)
The bit under the title "Linux DEB-based Installation" is the relevant part.
There is also a help forum here
[http://user.services.openoffice.org/en/forum/index.php](http://user.services.openoffice.org/en/forum/index.php)
Which has a sub forum devoted to linux, it may be worth a browse here first so you can be forwarned of any preliminaries or problems.

---

### Post by TenPlus1 on 2012-09-05
LibreOffice is built from OpenOffice with many improvements and bug fixes included...  It's basically the same office suite with many new features...

---

### Post by nikhilbhalwankar on 2012-09-05
> **houseworkshy said:**
> If you get the "deb" file it should work on Ubuntu.  
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)
There is an installation guide here
[http://www.openoffice.org/download/common/instructions.html#linux-deb](http://www.openoffice.org/download/common/instructions.html#linux-deb)
The bit under the title "Linux DEB-based Installation" is the relevant part.
There is also a help forum here
[http://user.services.openoffice.org/en/forum/index.php](http://user.services.openoffice.org/en/forum/index.php)
Which has a sub forum devoted to linux, it may be worth a browse here first so you can be forwarned of any preliminaries or problems.
Thanks a lot friend. I will try this out and get back to you.

---

### Post by nikhilbhalwankar on 2012-09-05
> **TenPlus1 said:**
> LibreOffice is built from OpenOffice with many improvements and bug fixes included...  It's basically the same office suite with many new features...
I have faced issues with LibreOffice when it comes to compatibility with Microsoft Office.  
e.g. Pivot Table created using microsoft office did not worked in LibreOffice. However it worked for OpenOffice in my case. Apache OpenOffice 3.4 did not give the issue.

---

### Post by nikhilbhalwankar on 2012-09-05
> **houseworkshy said:**
> If you get the "deb" file it should work on Ubuntu.  
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)
There is an installation guide here
[http://www.openoffice.org/download/common/instructions.html#linux-deb](http://www.openoffice.org/download/common/instructions.html#linux-deb)
The bit under the title "Linux DEB-based Installation" is the relevant part.
There is also a help forum here
[http://user.services.openoffice.org/en/forum/index.php](http://user.services.openoffice.org/en/forum/index.php)
Which has a sub forum devoted to linux, it may be worth a browse here first so you can be forwarned of any preliminaries or problems.
I am getting below error....

[email]nikhil@Inspiron-N5010:/opt/openoffice.org[/email]3/program$ ./soffice
javaldx: Could not find a Java Runtime Environment! 


I got the same error in Fedora 17 too even though I was having java installed.

---

### Post by houseworkshy on 2012-09-06
I used open office for years but actually switched away from it, even  though it was the default in my 10.04 install, because I prefer it's  philosopy.    So I'm not an expert on this and simply pointed you to  where the experts are.  According to some posts on that forum you may be  up against a bug which only sun can fix.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=47649&p=219652&hilit=Java+Runtime+Environment#p219652](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=47649&p=219652&hilit=Java+Runtime+Environment#p219652)   
If you follow the link to the bug report, the last post on it has a workaround.
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7024514](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7024514)
Apparantly  this bug also affects Libre office and Windows users.  That said I used Open office on Ubuntu 10.04, then also installed Libre Office and didn't  encounter it, both are still running sweetly.  

The last post  date is some time ago, 7/12/11,  so perhaps it has been fixed by now.   If not, according to the thread in the oo forums, you may need to play  around with oo and java versions.  Version 3.3 was ok it seems, there's  nothing wrong with ducking the latest for the sake of stability.  In my  opinion office suits achieved full funcionality many years ago and most  of the new bells and whistles ( new hardware, protocols and exploits  excepted)  are frills added only for the sake of looking innovative.

If  none of the above works then searching for and reading up on "Unity" in  the open office forums may be worthwhile.  As it all works on my  machine and not yours what's the difference?  Well one other thing is  the gui, I'm still on gnome2, and on the forums are several posts along  the lines of "Unity problems".  Why a virtual machine should be affected  by this I don't know.  

To be honest with you I'm feeling in the dark at this point.
If none of the posts on the Open Office forums sort out the problem you could try posting there as well.
The  office suit applications are the most important for me so I can  empathise. If nothing else works and it's critical, involving work for  example, then I can testify that Open Office and Libre Office both work  on Ubuntu 10.04, which is supported untill april next year.    Even though I know one is supposed to have one or the other I haven't removed Open office yet, and I've just tested it.     Libre Office also runs well on Mepris though I can't comment about open office on Mepris as I haven't tried it.  

You could try a live session with the latest Ubuntu 10.04.4 as a tester, or even to get the work done, as Open Office is part of the distro.
Better to fix it of course.  
Good luck.

---

### Post by nikhilbhalwankar on 2012-09-07
> **houseworkshy said:**
> I used open office for years but actually switched away from it, even  though it was the default in my 10.04 install, because I prefer it's  philosopy.    So I'm not an expert on this and simply pointed you to  where the experts are.  According to some posts on that forum you may be  up against a bug which only sun can fix.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=47649&p=219652&hilit=Java+Runtime+Environment#p219652](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=47649&p=219652&hilit=Java+Runtime+Environment#p219652)   
If you follow the link to the bug report, the last post on it has a workaround.
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7024514](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=7024514)
Apparantly  this bug also affects Libre office and Windows users.  That said I used Open office on Ubuntu 10.04, then also installed Libre Office and didn't  encounter it, both are still running sweetly.  

The last post  date is some time ago, 7/12/11,  so perhaps it has been fixed by now.   If not, according to the thread in the oo forums, you may need to play  around with oo and java versions.  Version 3.3 was ok it seems, there's  nothing wrong with ducking the latest for the sake of stability.  In my  opinion office suits achieved full funcionality many years ago and most  of the new bells and whistles ( new hardware, protocols and exploits  excepted)  are frills added only for the sake of looking innovative.

If  none of the above works then searching for and reading up on "Unity" in  the open office forums may be worthwhile.  As it all works on my  machine and not yours what's the difference?  Well one other thing is  the gui, I'm still on gnome2, and on the forums are several posts along  the lines of "Unity problems".  Why a virtual machine should be affected  by this I don't know.  

To be honest with you I'm feeling in the dark at this point.
If none of the posts on the Open Office forums sort out the problem you could try posting there as well.
The  office suit applications are the most important for me so I can  empathise. If nothing else works and it's critical, involving work for  example, then I can testify that Open Office and Libre Office both work  on Ubuntu 10.04, which is supported untill april next year.    Even though I know one is supposed to have one or the other I haven't removed Open office yet, and I've just tested it.     Libre Office also runs well on Mepris though I can't comment about open office on Mepris as I haven't tried it.  

You could try a live session with the latest Ubuntu 10.04.4 as a tester, or even to get the work done, as Open Office is part of the distro.
Better to fix it of course.  
Good luck.
Hi,

I managed to install OpenOffice on Ubuntu 12.04. Below are the commands which I executed,



tar -xzvf Apache_OpenOffice_incubating_3.4.1_Linux_x86_install-deb_en-US.tar.gz


 chmod -R 777 en-US/
 

cd en-US/
 

cd DEBS/
 

sudo dpkg -i *.deb
 

cd desktop-integration/
 

sudo dpkg -i *.deb
 

cd /opt/openoffice.org3/program
 

export PATH=$PATH:/u01/jdk1.6.0_33/bin
 

export PATH=$PATH:/u01/jdk1.6.0_33/jre/bin
 

./soffice.bin 
 

wait for 10-15 seconds and then you will get the desired openoffice window.



Cheers,
Nikhil Bhalwankar

---

### Post by larrypa on 2012-12-27
Thank you Nikhil- worked like a charm!

---

### Post by maljaros on 2012-12-29
Thank you Nikhil. for guidance on installing OpenOffice in 12.04.
It is a relief to be able to use this package after deleting the current build of LibreOffice which kept crashing.
Can you, or somebody, please help me to "associate"  existing *.odt, *.odg and *.ods files so that they open the relevant OpenOffice program?
Although I can launch the package with the command /soffice.bin as you suggest, and can create and save new text, draw or calc files, I cannot open these files from within Nautilus which still wants to use LibreOffice (which is no longer on my system) and does not show OpenOffice in the list of "Other Applications".  
  
What have I missed, or messed up?

---

### Post by nikhilbhalwankar on 2013-01-07
> **maljaros said:**
> Thank you Nikhil. for guidance on installing OpenOffice in 12.04.
It is a relief to be able to use this package after deleting the current build of LibreOffice which kept crashing.
Can you, or somebody, please help me to "associate"  existing *.odt, *.odg and *.ods files so that they open the relevant OpenOffice program?
Although I can launch the package with the command /soffice.bin as you suggest, and can create and save new text, draw or calc files, I cannot open these files from within Nautilus which still wants to use LibreOffice (which is no longer on my system) and does not show OpenOffice in the list of "Other Applications".  
  
What have I missed, or messed up?
Hi,

I will check this out and will get back to you...

---

### Post by Francewhoa on 2013-01-12
> **TenPlus1 said:**
> LibreOffice is built from OpenOffice with many improvements and bug fixes included...  It's basically the same office suite with many new features...

  LibreOffice is a great alternative to Microsoft Office. But LibreOffice 3.5 is currently very unstable. The main motivation behind LibreOffice were concerns over Sun and then Oracle's bad management of the OpenOffice project. Since June 2011, Oracle contributed OpenOffice code and trademarks to the Apache Software Foundation, unilaterally relicensing all contributions under the Apache License, at the suggestion of IBM. Source [http://en.wikipedia.org/wiki/OpenOffice#History](http://en.wikipedia.org/wiki/OpenOffice#History) I hope LibreOffice gets more stable later. Mine crashes every 2 or 3 days while working with large amount of documents. 30 plus documents open at once. It's a big waste of time to re-open all documents after a crash. OpenOffice is more stable than LibreOffice.

---

### Post by Hagar Delest on 2013-01-24
maljaros: right click a file, select Properties (bottom of the list) and in the Open with tab, select the correct component (or just the main AOO icon) and set it to default. If you've installed the desktop-integration packages, then you should have the components in the list of available applications.

> **Onopoc said:**
> The main motivation behind LibreOffice were concerns over Sun and then Oracle's bad management of the OpenOffice project. Since June 2011, Oracle contributed OpenOffice code and trademarks to the Apache Software Foundation, unilaterally relicensing all contributions under the Apache License, at the suggestion of IBM. Source [http://en.wikipedia.org/wiki/OpenOffice#History](http://en.wikipedia.org/wiki/OpenOffice#History)
Beware that this is blattant FUD, the whole article has been revamped. See these threads on the AOO dev mailing list for the whole story:
- [In case you missed it: The OpenOffice Wikipedia page was FUD'ed over the holidays]("http://www.mail-archive.com/dev@openoffice.apache.org/msg03105.html")
- [OpenOffice on Wikipedia (was: In case you missed it: The OpenOffice Wikipedia page was FUD'ed over the holidays)]("http://www.mail-archive.com/dev@openoffice.apache.org/msg03151.html")

Quite sad for the LO team to come to such methods to promote their fork and denigrate Apache OpenOffice. It is just unfair and it undermines their credibility.

---

### Post by astrantzalos on 2013-01-24
Since many 12.04 users may refer here for the same problem, I wonder why nobody proposes using the embedded in ubuntu 12.04 manager to run the open office deb file? It worked smooth and easy for me... on 12.04.1, too!

---

### Post by Hagar Delest on 2013-01-25
I don't like very much the command line but I've to admit that for some tasks, it's much quicker than any GUI. Especially when the bash history keeps all the strings needed in memory.

Usually, I just use the right click to extract the files and then the command line to move to the correct folder and type the dpkg command. At least you know what you do and you can check the output to make sure there has been no problem.

I've already tried to install some debs by double-click (it then uses the Ubuntu software center) but it has not been always satisfactory.

---

### Post by maljaros on 2013-01-25
Thank you Hagar, for good advice on using Nautilus and for installation via command line.
Also interesting read on Wikipedia FUD.
MalJaros

---

### Post by jimwg on 2013-02-14
Greetings!

I've Googled for solutions and most entries are dated and don't work with today's OOo version. I'm running Ubuntu 12.10 with OpenOffice 3.4.1 freshly installed via PPA because it doesn't show on package manager like OOo 3.4 did. OOo operates well except thesaurus icon and menu entry are ghosted. The Extension Manager has English Spelling, Hyphen and Thesaurus set (2010.03.16), and Writing Aids in Language Setting has OOo New Thesaurus checked. I took user advice and downed via command-line a new thesaurus to install but no difference. I did same advice to command-line purge all LibreOffice and OpenOffice and soffice files before doing a fresh OOo install but no change. LibreOffice and OOo 3.4.0 worked well with thesaurus, so is this really a installing flaw of OOo 3.4.1?

Thanks for any advice!

Jim in NYC

---

### Post by Hagar Delest on 2013-02-14
Have a look here: [[Troubleshooting] Spell check in OOo 3.x](http://forum.openoffice.org/en/forum/viewtopic.php?t=16512).

---

### Post by Rebecca_D on 2013-04-21
Thanks for this helpful and clear instruction Nikhil. For other newbies like me that come from the UK, replace US with GB in the first three terminal commands (other country letters may be necessary wherever you are in the world and the package you download). Works like a dream. Glad to be rid of LibreOffice!!!

Ciao

---

### Post by nikhilbhalwankar on 2013-12-03
> **maljaros said:**
> Thank you Nikhil. for guidance on installing OpenOffice in 12.04.
It is a relief to be able to use this package after deleting the current build of LibreOffice which kept crashing.
Can you, or somebody, please help me to "associate"  existing *.odt, *.odg and *.ods files so that they open the relevant OpenOffice program?
Although I can launch the package with the command /soffice.bin as you suggest, and can create and save new text, draw or calc files, I cannot open these files from within Nautilus which still wants to use LibreOffice (which is no longer on my system) and does not show OpenOffice in the list of "Other Applications".  
  
What have I missed, or messed up?


Hi,

Me too facing the same issue. I used to open the openoffice and click file->open to open the existing file. But looks like there is a solution available (the link mentiones its for Ubuntu 13.10). Visit the below link....

[http://itsfoss.com/add-application-list-open-applications-ubuntu-1310/](http://itsfoss.com/add-application-list-open-applications-ubuntu-1310/)


[B]--
Many Thanks,
Nikhil Bhalwankar
[/B]

---

### Post by Eugene King on 2013-12-17
Following Nikhil commands I just installed OpenOffice 4.0.1  I had to tweek a few commands because of the different version. but I figured it out. Forgot I needed to completely remove LibreOffice....or it would have been faster.......

Thanks

---

### Post by nikhilbhalwankar on 2014-01-20
> **Eugene King said:**
> Following Nikhil commands I just installed OpenOffice 4.0.1  I had to tweek a few commands because of the different version. but I figured it out. Forgot I needed to completely remove LibreOffice....or it would have been faster.......

Thanks

Ohh. This is strange. I now have Ubuntu 13.10 Saucy Salamander with OpenOffice 3.4. But I did not have to remove LibreOffice. I have both running fine. I did not remove LibreOffice as it was shipped by default with the Ubuntu distribution.

---

### Post by alvy1 on 2014-01-23
I just installed Openoffice 4 with the help of this thread without issues. Thanks for the post.

---

### Post by nikhilbhalwankar on 2014-05-12
I tried the same commands for OpenOffice 4 installation on Ubuntu 14.04 too. All steps worked successfully except for one error,


nikhil@nikhil-Inspiron-N5010:/opt/en-US/DEBS/desktop-integration$ sudo dpkg -i *.deb
Selecting previously unselected package openoffice-debian-menus.
(Reading database ... 261315 files and directories currently installed.)
Preparing to unpack openoffice4.0-debian-menus_4.0-9714_all.deb ...
Unpacking openoffice-debian-menus (4.0-9714) ...
[I][B]dpkg: error processing archive openoffice4.0-debian-menus_4.0-9714_all.deb (--install):
 trying to overwrite '/usr/bin/soffice', which is also in package libreoffice-common 1:4.2.3~rc3-0ubuntu2
[/B][/I]/usr/bin/gtk-update-icon-cache
.
.
.


I ignored this error as I have LibreOffice preinstalled with Ubuntu 14.04 installation. Might be some conflicts with that.

---

### Post by Hagar Delest on 2014-05-12
Indeed, you need to remove the LibO package that remains. You can try: sudo apt-get remove libreoffice-core
Else, install Synaptic and remove any LibO package.

---

