---
title: "[SOLVED] How to Install &amp;amp; run Eclipse 3.3 in Ubuntu 8.04 ?"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by pe7er on 2008-08-17
I hope that "Installation & Upgrades" is the right board for my Eclipse 3.3 installation question...
I am not experienced with Linux yet and have difficulties with the installation & running Eclipse 3.3 in Ununtu 8.04.

Eclipse 3.2 is in the Ubuntu repository. 
I was able to install 3.2 using Synaptic Package Manager or apt-get from command line. 
However the PHP plugin / Eclipse PDT that I want to use, needs Eclipse 3.3.
Upgrading Eclipse 3.2 to 3.3 from within Eclipse did not work well, so I uninstalled Eclipse 3.2.

The tutorial at [http://www.friendlyarm.com/install-eclipse-33-on-ubuntu-804/](http://www.friendlyarm.com/install-eclipse-33-on-ubuntu-804/) helped me 
with the installation of eclipse-SDK-3.3.2-linux-gtk.tar.gz (the Linux (x86/GTK 2) version).
I was able to perform every step from that tutorial, except for the last step: 
"Run Eclipse" does not seem to work here...

Eclipse is installed in /usr/local/opt/eclipse and I can get there by:
> cd /usr/local/opt/eclipse
But if I use the following command, 
```
./eclipse
```
the following error is displayed:
> bash: ./eclipse: No such file or directory

Clicking on the "eclipse" icon from within the File Browser does not work and using the following on the command line:
```
eclipse
``` results in
> The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
bash: eclipse: command not found


What do I have to do to get Eclipse working?
Do I have to create some reference to the software somewhere, 
or change some permissions of file / directory?

PS: the command *update-java-alternatives -l* did not show the second line: java-gcj 1042 /usr/lib/jvm/java-gcj
but only: java-6-sun 63 /usr/lib/jvm/java-6-sun

---

### Post by Partyboi2 on 2008-08-18
Maybe go back and double check that you did everything that is mentioned in the howto. I just tried the how-to and successfully have Eclipse working.

---

### Post by pe7er on 2008-08-18
Thank you for your reply! However, I am still not able to run Eclipse 3.3.

Just to make sure, I completely reinstalled Ubuntu 8.04 and tried the full tutorial again.
Everything went fine, except for the last step:```
./eclipse
``` does not start Eclipse 3.3 but instead I still get the following error:
> bash: ./eclipse: No such file or directory
and [COLOR="Blue"]sudo ./eclipse[/COLOR] results in the same error.

Do I need to create a reference or something to the eclipse program ?

**edit:** I checked the permissions, 
the "executable" eclipse file is 755, and its directory is also 755.

---

### Post by Partyboi2 on 2008-08-18
Are you in the correct directory when you try and start it?
```
cd /usr/local/opt/eclipse
``````
 ./eclipse
```When you are in the directory you can use the ls command to see what is listed
```
ls
```
it should look something like this:
> karl@ubuntu:/usr/local/opt/eclipse$ ls
about_files  configuration  eclipse.ini   features  libcairo-swt.so  plugins
about.html   eclipse        epl-v10.html  icon.xpm  notice.html      readme

---

### Post by pe7er on 2008-08-18
> **Partyboi2 said:**
> Are you in the correct directory when you try and start it?
Yes, I was in the correct directory. I used the Terminal via: Applications > Accessories > Terminal
```
pe7er@mypc:~$ cd /usr/local/opt/eclipse
pe7er@mypc:/usr/local/opt/eclipse$ ls
about_files  configuration  eclipse.ini   features  libcairo-swt.so  plugins
about.html   eclipse        epl-v10.html  icon.xpm  notice.html      readme
pe7er@mypc:/usr/local/opt/eclipse$
```
And I tried:
```
pe7er@mypc:/usr/local/opt/eclipse$ eclipse
The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
bash: eclipse: command not found
pe7er@mypc:/usr/local/opt/eclipse$ ./eclipse
bash: ./eclipse: No such file or directory
```

With the File Browser I can see that the "eclipse" program is 20.9 KB, that it's an executable, and that the Octal Permission is 100755.

Thanks again!

---

### Post by dustman on 2008-08-18
hey! 

check out the download link for Eclipse 3.3 on their web page ;) : [http://download.eclipse.org/eclipse/downloads/](http://download.eclipse.org/eclipse/downloads/) (it's under the subtopic "Latest Releases->Build Name->3.3.2) ...just download, unpack where you want it, then launch Eclipse; simple and easy 

Cheers!


Radu

---

### Post by pe7er on 2008-08-18
**Additional info:** I've Unbuntu 8.04 for AMD 64.

I tried to install **eclipse-SDK-3.3.2-linux-gtk.tar.gz** (the Linux (x86/GTK 2) version).

Should I install **eclipse-SDK-3.3.2-linux-gtk-x86_64.tar.gz** (for Linux (x86_64/GTK 2)) instead?

---

### Post by pe7er on 2008-08-18
> **dustman said:**
> check out the download link for Eclipse 3.3 on their web page ;) : [http://download.eclipse.org/eclipse/downloads/](http://download.eclipse.org/eclipse/downloads/) (it's under the subtopic "Latest Releases->Build Name->3.3.2) ...just download, unpack where you want it, then launch Eclipse; simple and easy
Thanks, but it redirects me to the same page as where I downloaded **eclipse-SDK-3.3.2-linux-gtk.tar.gz**

Downloading and unpacking was simple and easy indeed...
But I cannot get it to launch (which I described in my 1st post).

---

### Post by dustman on 2008-08-18
> **pe7er said:**
> **Additional info:** I've Unbuntu 8.04 for AMD 64.

I tried to install **eclipse-SDK-3.3.2-linux-gtk.tar.gz** (the Linux (x86/GTK 2) version).

Should I install **eclipse-SDK-3.3.2-linux-gtk-x86_64.tar.gz** (for Linux (x86_64/GTK 2)) instead?

sure :) . Install the x86_64 version. Then feedback here ;)

---

### Post by pe7er on 2008-08-18
I tried again, but now with
eclipse-SDK-3.3.2-linux-gtk-x86_64.tar.gz (the 64 bit version of Eclipse 3.3).

And now it works!! \\:D/
Thank you both for your help!

---

### Post by dustman on 2008-08-18
no problem :) glad i could help. 


please mark your thread as solved :D if it's not too much to ask

Cheers!


Radu

---

### Post by pe7er on 2008-08-18
Sure, I already did (see the [solved] in the subject of your message) :)

BTW: As I manually installed the package, there was no menu entry in "Applications". 
Therefore I manually created a menu entry with
[COLOR="Blue"]sudo gedit /usr/share/applications/eclipse.desktop[/COLOR]
and using the following code:
```
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse PHP IDE
Exec=/usr/local/opt/eclipse/eclipse
Icon=/usr/local/opt/eclipse/eclipse/icon.xpm	
StartupNotify=true
Terminal=false
Type=Application
Categories=Development;Application
```

---

