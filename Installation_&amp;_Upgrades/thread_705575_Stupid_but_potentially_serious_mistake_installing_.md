---
title: "Stupid but potentially serious mistake installing Google Earth"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by dusen on 2008-02-23
Hey community!

So check this: new and too-smart-for-own-good-little-bit-of-knowledge-a-dangerous-thing Xubuntu-on-an-old-Dell user decides he'd like to install Google Earth. User decides to be smart about it for once, so he looks up instructions [in the documentation]("https://help.ubuntu.com/community/GoogleEarth"). User follows along with instructions as he does installation, feeling that an advance read-through is not necessary. Little did he know, this would turn out to be a mistake, since #7 of the instructions turns out to be pretty important. Now user has installed Google Earth as root, and when trying to undo this damage by following the uninstall instructions in documentation, he gets this:

dusen@dusen:~$ sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth
rm: cannot remove `/usr/share/mime/application/vnd.google-earth.*': No such file or directory
rm: cannot remove `/usr/share/mimelnk/application/vnd.google-earth.*': No such file or directory
rm: cannot remove `/usr/share/applnk/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/share/mime/packages/googleearth-mimetypes.xml': No such file or directory
rm: cannot remove `/usr/share/gnome/apps/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/share/applications/Google-googleearth.desktop': No such file or directory
rm: cannot remove `/usr/local/bin/googleearth': No such file or directory
dusen@dusen:~$ 

User suspects that this is because he installed as root, but uninstall was written for those who do not, in fact, ride the short bus and so did not install as root, as per instructions.

Please send help!

Dusen

---

### Post by pytheas22 on 2008-02-23
It looks to me like the documentation says that you should indeed install the program as root, as per the line
```

 sudo ./GoogleEarthLinux.bin
```

(sudo = root, basically)

Almost all programs in Linux need to be installed as root, because only root has write access to the directories where files need to be installed.  Once root installs the files, however, anyone can RUN them--that's the big difference.

The reason that step #7 says not to press run immediately after install is because if you did, you would be running the program as root (since you are still running the installer as root), which is generally just not a good idea because it removes an important level of security between you and the system, potentially making it easier to damage something important or expose your computer to remote attacks.  But running things as root once by mistake generally shouldn't hurt anything, and you should have still been able to run Google Earth normally afterwards as a non-privileged user, although maybe not anymore, since you tried to uninstall it.

If I were you, I would try installing it again--it should overwrite any remnants of the initial installation--and make sure not to run it as root this time.  I don't think you've caused any serious problems.  If you have trouble, post.

(It is curious that the rm command gave you those errors, which indicate that there were no Google Earth files to remove, as if the installer didn't work for some reason.  So make sure to follow all of the steps precisely so that the installer does what it needs.)

---

### Post by Pumalite on 2008-02-23
In fact you can download the bin file, right click on it, go to permissions, and make it 'executable'. After that double click on it and the file installs itself.

---

### Post by dusen on 2008-02-24
Hey,

Thanks pytheas22. I haven't tried to reinstall the program yet, as there is a piece of information I left out: the file created on my desktop, namely Google-googleearth.desktop, which the documentation says it's ok to delete, is different from every thing else on my account: in the permissions tab of the file's properties, the owner is "root (root), like an application. I grok that this is intentional in Ubuntu to keep users exactly like me from cluster****ing the operating system, and it is respect for that which has brought me to the forums. Should I  delete it by using sudo-terminal kung-fu on it? If that is on my machine, doesn't that mean there are more related files that should also be deleted/uninstalled before I try the installation again? Also, I saw the program install, but now I can't find it! It's not in the applications tab (there isn't even an "internet" tab there like the documentation says) and I am still clueless about Unix-style file structure, having used Windows/DOS until just recently. Can I add it to the apps bar if it's not there? How do I tell where it installed to?

Thanks again to anyone who can help!

Dusen

---

### Post by pytheas22 on 2008-02-24
It sounds like your installation got messed up somewhere, since you don't have an option for Google Earth under the Applications menu.  I am also wondering why you don't have an Internet section under the Applications menu--this should definitely be there by default in any Ubuntu install and includes applications like Firefox, Pidgin and Evolution.  Did you uninstall these for some reason or try customizing the Gnome menus at all?

If you want to find out where files related to Google Earth are, you can use the locate command:

```
locate googlearth
```

which will list the location of every file with "googleearth" in its name.  If you wanted to you could try deleting all of these manually, but as I said before, I think that reinstalling the application would overwrite them; there's no need to manually delete everything.  You can also remove the Google-googleearth.desktop file with

```
sudo rm ~/Desktop/Google-googleearth.desktop
```

but again, it's probably not necessary to do this.

In terms of differences between Linux and Windows concerning installation, the most important thing to understand is that while Windows dumps everything to an arbitrary location (usually in c:\program files, but not necessarily), different parts of applications in Linux have a specific places within the filesystem designed for them.  The executables for most applications get put in the /usr/bin directory, but configuration files and libraries (the equivalent of .dll files in Windows) go elsewhere.  You could browse around the /usr and /etc directories to get a better idea of this.  You could also open your /home folder and press control-h (to view hidden directories) to see how your user configuration files are stored.

In any case, most of the time in Ubuntu you don't need to think about this, because most of your applications are installed using debian packages, which automatically install everything where it needs to be, or uninstall it.  Google Earth is a special case because, since it's not open-source, it needs to be installed in a special way.  In my case, the binary for Google Earth exists at /usr/local/bin

Another important thing to know is that in most cases, you can run any program simply by typing its name inside the terminal, regardless of which directory the terminal prompt is pointed at.  So if you think Google Earth might actually be installed somehow, you could try to run it by typing

```
googleearth
```

at the command line.

---

### Post by Pumalite on 2008-02-24
Google Earth when it installs itself leaves an icon on the Desktop.

---

### Post by dusen on 2008-02-25
Thanks again for the help pytheas22! Your last post was a study in "how to help the Noob". Looking around in the /usr and /etc has been very educational, and Imma play around some more. More importantly, the conceputal difference in where stuff goes (split up, rather than together) was, I think my main stumbling block to understanding Unix-like file systems...that and my conclusion from all my playing around that a Unix system only has one tree trunk, unlike Windows "one trunk per drive" structure.

I think my flavor (Xubuntu) uses the "Network" instead of "Internet", since that's where Firefox etc reside...since I didn't have one, I assumed that the installation would provide me with on, the way that new Windows apps get added to the start menu...Google Earth is not under my "Network" tab, either.

Anyhow, here is my latest progress on Google Earth (BTW, this thread is no longer, to me anyway, about installing Google Earth, but rather understanding GNU/Linux...):

```
dusen@dusen:~$ googleearth
bash: googleearth: command not found
dusen@dusen:~$ locate googleearth
/usr/local/share/applications/Google-googleearth.desktop
/usr/local/share/mime/packages/googleearth-mimetypes.xml
/home/dusen/Desktop/Google-googleearth.desktop
/root/.googleearth
dusen@dusen:~$ sudo googleearth
[sudo] password for dusen:
sudo: googleearth: command not found
dusen@dusen:~$ cd /root/
dusen@dusen:/root$ ls
dusen@dusen:/root$ ls -h
dusen@dusen:/root$
dusen@dusen:/root$ cd ~/Desktop
dusen@dusen:~/Desktop$ ls
david_allen_interview.mp3  Google-googleearth.desktop  wesnoth
dusen@dusen:~/Desktop$ sudo rm Google-googleearth.desktop [JUDO CHOP!]
[sudo] password for dusen:
dusen@dusen:~/Desktop$ ls
david_allen_interview.mp3  wesnoth
dusen@dusen:~/Desktop$  
```

so what is /root/.googleearth? I'm not exactly clear what the prepended period means; so far, whenever I wanted to run something at the command line, I would use ```
parentdir/where_thing_isdir/.thing
```

is that how Unix executables roll? Also, I used the kung-fu on the desktop thingie...thanks Sensei...should I do the same thing to /root/.googleearth?

---

### Post by pytheas22 on 2008-02-25
> so what is /root/.googleearth

directory names that begin with a . are hidden directories, and are generally used to store configuration settings for applications.  In the case above, the .googleearth folder contains root's settings for that program.  Other users should have their own .googlearth folder inside their home directory.  If you use the ls -a command or press control-h in the graphical file browser, you should be able to see this folder, if googleearth were installed properly, which it clearly isn't based on the output that you posted above.

Have you tried reinstalling Google Earth?  The binaries for it apparently no longer exist on your system, so it definitely won't work.  But, as I said before, I imagine that if you reinstall it, it would work.

As for executables in Linux: any application that's installed properly in the normal locations (/usr/bin and so on) can be run from the command line simply by typing its name, because the bash shell (the application running behind the terminal) is smart and knows to look in those locations.  Otherwise, if for some reason you have an executable in another location, you would run it by navigating to its location in the file system and putting a ./ before its name, e.g.:

```
./main.o
```

would run an executable named main.c.  This is probably where your confusion with the . at the beginning of a directory name comes from, but they're actually two different things.

> should I do the same thing to /root/.googleearth?

you can delete this if you want, but it's probably not necessary.  If you do delete it and you do it from the command line, you will need to use the "rm -r" command, as the -r flag is required to delete directories (if you want to learn more about the options for command-line programs, type "man" and the name of the program, e.g. "man rm").

---

### Post by harak on 2008-05-17
even after uninstalling and removiong the .googleearth folders. I still got the following

hara@Tulip:~$ googleearth
bash: /usr/local/bin/googleearth: No such file or directory
hara@Tulip:~$ ls /opt/google-earth/
Google
hara@Tulip:~$ sudo rm -rf /opt/google-earth
hara@Tulip:~$ googleearth
bash: /usr/local/bin/googleearth: No such file or directory

typing "googleearth" makes the system to look for an executable in /usr/local/bin.  silly isn't it and then

hara@Tulip:~/Desktop$ cat /usr/local/share/applications/defaults.list 
[Default Applications]
application/vnd.google-earth.kml+xml=Google-googleearth.desktop
application/vnd.google-earth.kmz=Google-googleearth.desktop
application/earthviewer=Google-googleearth.desktop
application/keyhole=Google-googleearth.desktop

finally

hara@Tulip:~/Desktop$ sudo rm -rf /usr/local/share/applications/defaults.list 
hara@Tulip:~/Desktop$ googlearth
bash: googlearth: command not found

these deletions may be required for "completely" uninstalling googleearth.

---

