---
title: "Package scripts?"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by bobn9lvu on 2005-03-19
I would like to install some different packages to the basic install, would running a script be the best way?  

I would like to add packages to set up a web server, and a FTP server, with
Webadmin, for starters. What would the command be to install the full packages.

This would be for my fellow classmates in  Web Server Services, to get some experiance in using Linux. It would be nice to have the above options in the install
menu to pick extra packages to add to the install.

Thanks for any help!

Bob N9LVU  8) 

I can also be reached direct;

[email]bobn9lvu@sbcglobal.net[/email]

---

### Post by DJ_Max on 2005-03-19
System >> Administration >> Synaptic Package Manager

I advise you to read [www.ubuntuguide.org/](www.ubuntuguide.org/), just to get a basic understanding of Ubuntu, and Linux in general.

---

### Post by bobn9lvu on 2005-03-20
[QUOTE=DJ_Max]System >> Administration >> Synaptic Package Manager

I advise you to read [www.ubuntuguide.org/](www.ubuntuguide.org/), just to get a basic understanding of Ubuntu, and Linux in general.[/QUOTE]

Thank you, BUT this does not really answer my question. I am looking for a way to set up a web/ftp server with Linux in an easy as possible way,  to give  my classmates exposure to Linux and its features.. I suppose I will have to write each step I used to set up my own box, and walk my classmates through the steps I used. I was looking for a way to automate the installation .

 I am not a power user.. I have only  used Linux for the last year, and having taken  the only class offered in Linux, at least I know I am  a relative newbee.

Thanks for the help?

Bob :???:

---

### Post by kperkins on 2005-03-20
With Debian based systems (like Ubuntu) DJ_Max's answer is the easiest way possible (or you could use apt-get). It will download and install what you want/need, and set up basic configurations, which you can fine tune from there.

---

### Post by DJ_Max on 2005-03-20
If you want HTTP connection(web) use[Apache Webserver](http://httpd.apache.org/). This can be installed via Synaptic. For FTP, you need a FTP Daemon like [ProFTPD](http://proftpd.org/)

If you really want an experiance, skip Synaptic & Deb binaries, and install everything manually from source.

---

### Post by WW on 2005-03-20
Yes, it should be possible to do what you want with a script, assuming I understand
just what it is you want to do.  It sounds like you have already figured out what
to install to set up your system with an assortment of services.  You would like
to make it easy for your classmate to do the same with their Ubuntu installation.

Let's say the packages to be installed are package1, package2 and package3.
In a terminal, you can use "apt-get install" to install these:
```
sudo apt-get install -y package1
sudo apt-get install -y package2
sudo apt-get install -y pacakge3
```
or even
```
sudo apt-get install -y package1 package2 package3
```
Put the commands in a file, say ServerInstall.sh, give it to your classmates,
and tell them to run it in a console with the command
```
sh ServerInstall.sh
```
The first sudo will prompt for the user's password.  I'm assuming that your
classmates have the necessary privileges to install packages.  The "-y" option
tells apt-get to assume that the answer to any questions is yes.  (I am
assuming that you have tested the script to make sure this makes sense on
the computers that your classmates are using.)

If there are additional commands to be run after the programs have been
installed, you can put them in the script, too.

---

### Post by az on 2005-03-20
"Thank you, BUT this does not really answer my question. I am looking for a way to set up a web/ftp server with Linux in an easy as possible way, to give my classmates exposure to Linux and its features"

I do not know what you are expecting.  Really, you should read the documentation.

Be prepared to run back to windows.  There is no button for you to push to get the job done in one click, here.

---

### Post by mmealman on 2005-03-20
[QUOTE=azz]
I do not know what you are expecting.  Really, you should read the documentation.

Be prepared to run back to windows.  There is no button for you to push to get the job done in one click, here.[/QUOTE]

The guy is asking if Linux can do scripted installs, not whether or not you can simply click 1 button and have everything "just work"(though you can do that under Linux to, it's called LiveCDs).

To the origional poster, yes there are various ways to do this. One would be to do something like:

---------
prototype-node:
 dselect  (install and configure everything you want)
 dpkg --get-selections > selection.file

second node:

  dpkg --set-selections < selection.file
  apt-get install dselect-upgrade
  [log any questions and answers]
  [create an expect script with your responses to any questions]

rest-of-nodes:

   dpkg --set-selections < selection.file
  expect -c "apt-get install dselect-upgrade" -f expect-script
---------

Basically just set a standard list of packages you're going to install and use expect to script the answers. Then you can script in any customized scripts you have(use wget to pull them down to the local machine and just copy them into place).

---

### Post by az on 2005-03-21
"This would be for my fellow classmates in Web Server Services, to get some experiance in using Linux. It would be nice to have the above options in the install
menu to pick extra packages to add to the install.`"

Actually, he seems to be asking for a custom cd.  Or for something that will install and configure his system like a knoppix live cd with ftp server.  

If this is not what he is asking, why is synaptic a bad choice?  It is _much_ simpler than installing and then running a --set-selections script.

It just seems that all the simple solutions are already there, and either they are not simple enough (in which case, it is probable unreasonable to expect more) or untried (in which case, go try them)


I don't want to be mean.  I am just being realistic.

---

### Post by bobn9lvu on 2005-03-21
[QUOTE=WW]Yes, it should be possible to do what you want with a script, assuming I understand
just what it is you want to do.  It sounds like you have already figured out what
to install to set up your system with an assortment of services.  You would like
to make it easy for your classmate to do the same with their Ubuntu installation.

Let's say the packages to be installed are package1, package2 and package3.
In a terminal, you can use "apt-get install" to install these:
```
sudo apt-get install -y package1
sudo apt-get install -y package2
sudo apt-get install -y pacakge3
```
or even
```
sudo apt-get install -y package1 package2 package3
```
Put the commands in a file, say ServerInstall.sh, give it to your classmates,
and tell them to run it in a console with the command
```
sh ServerInstall.sh
```
The first sudo will prompt for the user's password.  I'm assuming that your
classmates have the necessary privileges to install packages.  The "-y" option
tells apt-get to assume that the answer to any questions is yes.  (I am
assuming that you have tested the script to make sure this makes sense on
the computers that your classmates are using.)

If there are additional commands to be run after the programs have been
installed, you can put them in the script, too.[/QUOTE]

Yes, I just wasn't sure, as I haven't done much scripting in Linux. I know which packages I need, and will be writing a script to install them on my fellow students
boxes. Not one of them has ever worked with Linux before. I would like to get some interest going, and maybe persuade the faculty to add some advanced Linux classes to the curriculum.

Thanks for the help!

Bob 8)

---

