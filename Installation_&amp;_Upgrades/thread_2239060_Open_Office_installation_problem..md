---
title: "Open Office installation problem."
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2014-08-11
Can you help with this problem please. I am trying to install Apache OpenOffice (v.4.1) in Xubuntu 14.04. It seems to download ok but it will not open and run. What is worse, it is causing my hard drive to race unhealthily. I downloaded it from Softpedia website. I have since tried to consign it to the waste bin but the hard drive is still racing. I will shut down now and try a reboot to see if the hard drive has settled down.

---

### Post by ian-weisser on 2014-08-11
> **gordon99 said:**
> It seems to download ok but it will not open and run.

Please describe what happened that leads you to believe the software downloaded properly. Did an icon appear? Where? What was it called?

Please describe exactly how you told the system to 'open and run'? Terminal command? Click on an icon? 
What were you expecting to open? An installer? Or OpenOffice?

How long did you wait before rebooting? What happened after rebooting?

---

### Post by claracc on 2014-08-12
There is a specific method to install openoffice once the software package has been downloaded. Have you followed it?: [https://wiki.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F](https://wiki.openoffice.org/wiki/Documentation/FAQ/Installation/How_do_I_install_OpenOffice.org_on_Linux%3F)

First of all you have to delete the symlink to libreoffice in order not to mess with open office (in the provided guide there are described the steps).

Then you will have to extract and install the .deb package you have downloaded, and then you will have to do the desktop integration. All the method is well explained in the provided link.

---

### Post by gordon99 on 2014-08-12
Truth to tell I cannot exactly remember exactly how and in what order I went about the installation except to say I certainly used the Softpedia website. I had already removed libre office and installed OO from U.  Software Centre. However, this gave me version 4, not 4.1 but I was having a problem with the layout of one document in particular. I had set up the document sometime previously in OO 4.1 within Windows 7 and I wanted to work on it in Xubuntu. Thinking it might be a case of the different OO version causing a problem I tried to update the program with sudo but I ended up still in version 4. I therefore removed 4 in the Software Centre intending to reinstall it there in the hope the latest version of OO would appear. Unfortunately, OO seemed to have gone from the Software Centre list and hence I looked elsewhere with the wrong results.

I will now try the link given by claracc. I will carefully note each step I take and what occurs so that I can come back with a full account if need be. Thanks both for your help and interest.

---

### Post by gordon99 on 2014-08-12
Further to my earlier post I tried for over an hour to follow and carry out the instructions from the wiki website but found the instructions a bit beyond me. For example, after downloading OO, whatever 'linux Package Name' I used to unpack, it always  produced an error message. The instructions seemed to be written for those with a much better understanding of computer language than I have. I then found another site aimed at Newbies like me: " www.liberiangeek.net/2014/06/ubuntu-tips-install-openoffice-4-1-ubuntu/". I found the step by step instructions in this very easy to follow and duly carried them out.

 HOWEVER, having installed all the necessary files, OO will not launch. I turned to the OO 'Readme' file and found this:  "If you experience OpenOffice start-up problems (most notably while using Gnome) please 'unset' the SESSION_MANAGER environment variable inside the shell you use to start OpenOffice. This can be done by adding the line "unset SESSION_MANAGER" to the beginning of the soffice shell script found in the "[office folder]/program" directory". Unfortunately I do not know how to get into (assuming I can find it) the [office folder]/program directory in order to make the changes suggested. Can you help please?

---

### Post by ian-weisser on 2014-08-12
> For example, after downloading OO, whatever 'linux Package Name' I used to unpack, it always  produced an error message.
Can you reproduce that error message?
Can you print copy-and-paste that error message here?
That would help a lot.

---

### Post by claracc on 2014-08-13
> **gordon99 said:**
> Further to my earlier post I tried for over an hour to follow and carry out the instructions from the wiki website but found the instructions a bit beyond me. For example, after downloading OO, whatever 'linux Package Name' I used to unpack, it always  produced an error message. The instructions seemed to be written for those with a much better understanding of computer language than I have. I then found another site aimed at Newbies like me: " www.liberiangeek.net/2014/06/ubuntu-tips-install-openoffice-4-1-ubuntu/". I found the step by step instructions in this very easy to follow and duly carried them out.

 HOWEVER, having installed all the necessary files, OO will not launch. I turned to the OO 'Readme' file and found this:  "If you experience OpenOffice start-up problems (most notably while using Gnome) please 'unset' the SESSION_MANAGER environment variable inside the shell you use to start OpenOffice. This can be done by adding the line "unset SESSION_MANAGER" to the beginning of the soffice shell script found in the "[office folder]/program" directory". Unfortunately I do not know how to get into (assuming I can find it) the [office folder]/program directory in order to make the changes suggested. Can you help please?

"linuxPackage Name" has to be the name of the .deb package you have downloaded, i.e., something similar to Apache_Openoffice_4.1.0_Linux_x86_install-deb.......tar.gz", and you must be in the directory you have downloaded openoffice, it uses to be /home/user_name/Downloads/

What is the error you obtain in launching Open office, please try to launch it from a xterm:

Open xterm with ctrl+alt +t  and then run /usr/bin/soffice & and copy and paste the errors you obtain

---

### Post by vasa1 on 2014-08-13
> **gordon99 said:**
> Can you help with this problem please. I am trying to install Apache OpenOffice (v.4.1) in Xubuntu 14.04. It seems to download ok but it will not open and run. What is worse, it is causing my hard drive to race unhealthily. I downloaded it from Softpedia website. I have since tried to consign it to the waste bin but the hard drive is still racing. I will shut down now and try a reboot to see if the hard drive has settled down.Any reason why you didn't install LibreOffice which is available from the Ubuntu Software Center?

---

### Post by gordon99 on 2014-08-13
Libre was included when I installed Ubuntu 14.04 and then Xubuntu XFCE4. I chose not to persevere with it as I had been using OO  in Windows 7 and had got used to it. Thie error message I get from /usr/bin/soffice  is :gordon@Gordon-HP:~$ /usr/bin/sofficejavaldx: Could not find a Java Runtime Environment!
/opt/openoffice4/program/soffice.bin: symbol lookup error: /opt/openoffice4/program/libsvxcore.so: undefined symbol: _ZThn1192_NK18SvHeaderTabListBox11GetRowCountEv
gordon@Gordon-HP:~$ 
Hope this helps you. Much of it is double Dutch to me. I thought Java could be added later if one wanted to use data base.

---

### Post by claracc on 2014-08-13
Could you see if you have yet libreoffice-core package installed?, if so remove it. You can see it with synaptic manager.

I have found this thread, which seems to reproduce your problem: [https://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=70100](https://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=70100), please see comment 3, where there are steps to fix the problem and also the explanation of it.

---

### Post by gordon99 on 2014-08-13
Please see the result of the change directory command from the thread given in clarrac's latest post.   $ cd <more-path-info>/debs/en-GB/                                                                                                                                                     bash: more-path-info: No such file or directory.                                                                                          I changed US to GB I know but otherwise I believe I have followed the command in the clarrac's thread correctly. I have tried changing the order of the words more-path-info with the same result. Could anyone correct my error please?

---

### Post by claracc on 2014-08-14
The path to the directory refers to the place where you have downloaded and extracted .tar.gz file (apache openoffice software package).

In order to clarify paths (directories) and files:

I downloaded the Apache_OpenOffice_4.1.0_Linux_x86_install-deb_es.tar.gz (note, mine has _es because is for spanish language, yours will hace en_GB for british english or en_US for american english, you have to see what package you have downloaded) and this is downloaded to the /tmp directory.

In the /tmp directory ( open a xterm CTRL+alt+T and go there: cd /tmp) you will have to unpack the downloaded file through the command: tar -xvzf Apache_OpenOffice_4.1.0_Linux_x86_install-deb_es.tar.gz and in this way a /es directory is created (in my case is full path /tmp/es because of spanish language, in your case will be /tmp/en-US  for american english language, or /tmp/en-GB for british english, depends on what is the package you have downloaded, this is your installation directory.

Inside it there is the DEBS directory, you cd into DEBS directory, and there is a lot of .deb packages and also a desktop-integration directory. 

Now, in this directory you will run the following commands:

```
sudo dpkg -i *deb
```, remember, you will have in a directory named /tmp/en_US/DEBS/ (if american english openoffice downloaded). This /tmp/en_US/ is the path referred to <more-path-info> or /tmp/en_GB/ /if british english open office downloaded.

Then you will change to desktop-integration directory: full path /tmp/en_US/DEBS/desktop-integration, and will run: sudo dpkg -i *deb
 
So, referring to the link provided and the steps, I think the correct ones are:

```
sudo apt-get purge openoffice
sudo apt-get update
sudo apt-get autoclean
sudo apt-get autoremove
cd /tmp/en_US/DEBS/
sudo dpkg -i *deb
cd desktop-integration/
sudo dpkg -i *deb
```

Note that you cannot change the name of the files you have downloaded but to put the correct ones (the ones you have en_US or en_GB in order to make the correct names of directories when running the commands.

I hope it helps.

---

### Post by vasa1 on 2014-08-14
> **gordon99 said:**
> Can you help with this problem please. I am trying to install Apache OpenOffice (v.4.1) in Xubuntu 14.04. It seems to download ok but it will not open and run. What is worse, it is causing my hard drive to race unhealthily. I downloaded it from Softpedia website. I have since tried to consign it to the waste bin but the hard drive is still racing. I will shut down now and try a reboot to see if the hard drive has settled down.
I can see that claracc is doing her best to help you but sometimes it's just easier to start all over again. From your various posts, it appears you've started off with Ubuntu (which has LibreOffice installed by default). Then you've added some form of Xfce and then you've downloaded something from Softpedia.

If you wish to stay with XFCE, I feel you should do a clean install of Xubuntu so that you don't have to bother about removing LibreOffice and then install Apache OpenOffice from their official site and not from anywhere else. But, as you've seen the installation can be difficult for a newcomer to the terminal. 

On the other hand, if you do a clean install of Ubuntu you'll get LibreOffice installed by default. As of now, LibreOffice is not significantly different from Apache OpenOffice and you should be able to do with it whatever you could do previously with Openffice (on Windows).

@claracc, I hope you don't mind!

---

### Post by claracc on 2014-08-14
> **vasa1 said:**
> 

@claracc, I hope you don't mind!

Hello vasa1, of course I don't mind, your advice is very reasonable.

Regards.

---

### Post by gordon99 on 2014-08-14
Hello Vasa 1. Yes, I did start with Ubuntu and then changed to Xubuntu. When in Xubuntu I installed Apache OO (version 4.0) from Ubuntu software centre. When using the newly installed OO I found that a particular document I had created in Windows 7 using OO (version 4.1.0) was not transferring via Dropbox exactly as it should. To be precise the document was occupying more space per page. Thinking (probably mistakenly) that this might have been the result of transferring the document from OO v.4.0 to v.4.10 I tried to update v.4.0 to v.4.10 using terminal. This was unsuccessful. I therefore downloaded v.4.1.0 onto Xubuntu using the Softpedia website. It was here I came unstuck as v 4.1.0 would not launch. As I remember, I had already uninstalled  both Libre and OO (v.4.0).
 Before I start again from scratch Vasa, as you suggest, I think I will have one more try to salvage the situation by trying claracc's suggestions. If that doesn't work for me them I will probably go for your nuclear option. I will report back how I get on, though it may take me over the weekend.  Thank you both once again.

---

### Post by gordon99 on 2014-08-16
Hello to all. I am very pleased to be able to say that, after taking the steps outlined in clarrac's penultimate post, OO v.4.1.0 installed and launched successfully. I removed the previous OO downloads from the /opt directory and re-started with a clean download, this time from the OO web site. I do not pretend to understand what the 'Purge', 'Update', 'Autoclean' and Autoremove commands contributed to the installation of a brand new program but hopefully it will all become clear to me in the fullness of time. Thank you very much clarrac for staying with my problem and thanks everyone who gave me their thoughts on the matter. 
gordon99

---

### Post by claracc on 2014-08-16
You are very welcome gordon99.

Glad you got fixed your problem.

Please, mark the thread as solved with "thread tools" menu in the right upper part of the webpage.

Thanks

---

### Post by vasa1 on 2014-08-16
Congrats to both of you! Claracc for patience and gordon for persistence!

---

