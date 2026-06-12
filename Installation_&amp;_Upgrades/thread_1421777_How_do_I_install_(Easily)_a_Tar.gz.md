---
title: "How do I install (Easily) a Tar.gz?"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Saito Chikara on 2010-03-04
I have this file, called gxiso-1.5.tar.gz and I have no idea how to "install" it. 

my current path to the file is: /usr/local/src/

I would appreciate some help.

Thanks!!

---

### Post by mikewhatever on 2010-03-04
Well, a tar.gz is just an archive, similar to .zip or .rar in Windows, and usually, it has one of the two things inside: the source code or the binaries. If it is the source code, you don't really install it, but rather build or compile, and these are binaries, then you run them. Instead of us googling blindly, perhaps you can tell more about what it is you are trying to install.

---

### Post by Saito Chikara on 2010-03-04
the site i downloaded it from said it was source...

---

### Post by Mihai Chezan on 2010-03-04
I'm going to give it a try.

Searching on google reveals that "gXiso is graphical tool to extract and/or upload xbox iso images to xbox."

So I'm going to proceed with the assumption that that's the program you are trying to install.

1. Extract the archive (gxiso-1.5.tar.gz is an archive)
- open Nautilus, go to where the file is, right click on the file, choose "Extract Here" option

2. Installing the program
- the README file from the archive says to run this command:
sudo python setup.py install

Also the README file says this:
> 
notes: 
	* xbox has to be started (ahem) and running a FTP server to receive files.
	* when using avalaunch: disable boost mode and free root space
	* if you erase files or destroy your xbox: WE ARE NOT RESPONSIBLE !
	* USE AT YOU OWN RISK !
	* do not use with copyrighted material.
	* use with this: [http://www.pouet.net/prod.php?which=10586](http://www.pouet.net/prod.php?which=10586)


* One more thing: running/executing programs you download from the internet can have serious security consequences. You should do such an operation only if you trust the site from where you download the program and the person that wrote the program.

---

### Post by mikewhatever on 2010-03-04
OK, here you go:

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by JackRock on 2010-03-04
> **Saito Chikara said:**
> the site i downloaded it from said it was source...

It is the source, most likely.  But an archive of the source, so it's all in a single download, instead of hundreds of smaller ones.  The same way when you download a Windows program that you install.

---

### Post by widda on 2010-03-05
*[SIZE="2"][SIZE="3"]Here's something I found useful on the tar subject (quoting from Carsto in LQ)[/SIZE][/SIZE]*

"Make a habit of dropping the tar file into the home directory. Linux is meant to work this way, nothing lies around. Do su - into root. cd into /home/user, then ls shows the content. Do tar -xf <file as you see it there>, the correct directory will be created and all installed as needed. Usually into /usr/local, icons will be somewhere in /usr/share.

Right click on the desktop to Create Link to application. Click Application tab first, do command - Browse. Pick either .bin file or the one with a terminal icon. OK. Click on workpath floppy icon, self-completes, OK. Click on left most tab, click on icon, Other icons, Browse, pick one, OK. Rename Link to Application to suit. OK.

Click desktop icon to start your new app."

---

### Post by Saito Chikara on 2010-03-06
Okay, I'm lost. I had the extracted items in: usr/local/src/gxiso-1.5

Then I moved it to (after having problems) to the Desktop. desktop/gxiso-1.5

I then removed the "-1.5" from the end, and hoped it would work... nothing.

Here's the terminal output. What did I do wrong?






logan@logan-desktop:~$ sudo python setup.py install
[sudo] password for logan: 
python: can't open file 'setup.py': [Errno 2] No such file or directory
logan@logan-desktop:~$ cd usr/local/src/gxiso-1.5
bash: cd: usr/local/src/gxiso-1.5: No such file or directory
logan@logan-desktop:~$ cd usr/local/src
bash: cd: usr/local/src: No such file or directory
logan@logan-desktop:~$ cd /home
logan@logan-desktop:/home$ cd
logan@logan-desktop:~$ cd
logan@logan-desktop:~$ cd-
No command 'cd-' found, did you mean:
 Command 'cda' from package 'xmcd' (universe)
 Command 'cdb' from package 'tinycdb' (main)
 Command 'cdo' from package 'cdo' (universe)
 Command 'cdv' from package 'codeville' (universe)
 Command 'cdp' from package 'irpas' (multiverse)
 Command 'cdw' from package 'cdw' (universe)
cd-: command not found
logan@logan-desktop:~$ cd /gxiso-1.5
bash: cd: /gxiso-1.5: No such file or directory
logan@logan-desktop:~$ cd/gxiso
bash: cd/gxiso: No such file or directory
logan@logan-desktop:~$ gxiso
gxiso: command not found
logan@logan-desktop:~$ cd /Desktop/gxiso
bash: cd: /Desktop/gxiso: No such file or directory
logan@logan-desktop:~$ cd /desktop
bash: cd: /desktop: No such file or directory
logan@logan-desktop:~$ cd /Desktop
bash: cd: /Desktop: No such file or directory
logan@logan-desktop:~$ sudo python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory
logan@logan-desktop:~$ sudo python setup.py install
python: can't open file 'setup.py': [Errno 2] No such file or directory
logan@logan-desktop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

logan@logan-desktop:~$ ./configure
bash: ./configure: No such file or directory
logan@logan-desktop:~$

---

