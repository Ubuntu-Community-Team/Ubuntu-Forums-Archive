---
title: "[SOLVED] Error Reinstalling Google Desktop"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by KeybladeSephi on 2008-07-05
Hello; I have a problem with reinstalling Google Desktop. I manually deleted the google directory from the ~/opt folder, as well as the google directory in the ~/var/cache folder. Furthermore, I also deleted the .google directory in my home folder. When I try to reinstall google desktop with the Deb Package Installer, it says that it cannot open the .deb file because it is either corrupt or I don't have permission to access the file. When I go to the Synaptics Package Manager, it says that google-desktop-linux is still installed; so when I uninstall it from there, it says that could not uninstall everything. After that error message, when I tried to open Synaptic Package Manager again, it says that "The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it." How do I reinstall google-desktop-linux? Thanks :D

---

### Post by prshah on 2008-07-05
> **KeybladeSephi said:**
> Hello; I have a problem with reinstalling Google Desktop. I manually deleted the google directory from the ~/opt folder, as well as the google directory in the ~/var/cache folder. Furthermore, I also deleted the .google directory in my home folder. When I try to reinstall google desktop with the Deb Package Installer, it says that it cannot open the .deb file because it is either corrupt or I don't have permission to access the file. When I go to the Synaptics Package Manager, it says that google-desktop-linux is still installed; so when I uninstall it from there, it says that could not uninstall everything. After that error message, when I tried to open Synaptic Package Manager again, it says that "The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it." How do I reinstall google-desktop-linux? Thanks :D

```
sudo dpkg --purge --force-remove-reinstreq googledesktop.deb
sudo dpkg --install googledesktop.deb
```

Replace googledesktop.deb with the name of your downloaded deb file. If you get any errors, post back here for further guidance. Considering your error ("..corrupt..") it may be better that you redownload the deb file.

btw, if you just double-click the deb file, it will open up in package manager with a big green "reinstall" button. Does this not work for you?

---

### Post by KeybladeSephi on 2008-07-05
When I first tried, it gave me this error:

```
keybladesephi@Sheila:~$ sudo dpkg --purge --force--remove-reinstreq /home/keybladesephi/Desktop/google-desktop-linux_current_i386.deb
[sudo] password for keybladesephi: 
dpkg: unknown force/refuse option `-remove-reinstreq'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

During the second time, it gave me this error for both commands you gave me:

```
keybladesephi@Sheila:~$ sudo dpkg --purge --force-remove-reinstreq ~/Desktop/google-desktop-linux_current_i386.deb
dpkg: status database area is locked by another process
keybladesephi@Sheila:~$ sudo dpkg --install ~/Desktop/google-desktop-linux_current_i386.deb
dpkg: status database area is locked by another process
```

---

### Post by KeybladeSephi on 2008-07-05
> **prshah said:**
> Considering your error ("..corrupt..") it may be better that you redownload the deb file.

btw, if you just double-click the deb file, it will open up in package manager with a big green "reinstall" button. Does this not work for you?

I redownloaded the deb file and tried 3 times; the error is the same message I summarized in my first post.

---

### Post by KeybladeSephi on 2008-07-06
Furthermore, now that this has happened, I am unable to install any more .deb packages as well as basically anything else.

---

### Post by prshah on 2008-07-06
> **KeybladeSephi said:**
> 
```
keybladesephi@Sheila:~$ sudo dpkg --purge --force[color=red]--[/color]remove-reinstreq /home/keybladesephi/Desktop/google-desktop-linux_current_i386.deb
[sudo] password for keybladesephi: 
dpkg: unknown force/refuse option `-remove-reinstreq'

```

You've put in an extra hyphen "-".

> **KeybladeSephi said:**
> 
```
keybladesephi@Sheila:~$ sudo dpkg --purge --force-remove-reinstreq ~/Desktop/google-desktop-linux_current_i386.deb
dpkg: status database area is locked by another process
keybladesephi@Sheila:~$ sudo dpkg --install ~/Desktop/google-desktop-linux_current_i386.deb
dpkg: status database area is locked by another process
```

This means that you've probably another process running which is using the package manager system; eg, were you downloading updates, or using synaptic, or using apt-get or aptitude in another window?

Package managers cannot operate on multiple instances since the first instance will lock the database and prevent other instances from opening it.

> **KeybladeSephi said:**
> Furthermore, now that this has happened, I am unable to install any more .deb packages as well as basically anything else.

What error(s) are you getting?

---

### Post by KeybladeSephi on 2008-07-06
> **prshah said:**
> This means that you've probably another process running which is using the package manager system; eg, were you downloading updates, or using synaptic, or using apt-get or aptitude in another window?

Yeah you were right about having another package installer open. I tried it again and got these errors:

```
keybladesephi@Sheila:~$ sudo dpkg --purge --force-remove-reinstreq ~/Desktop/google-desktop-linux_current_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

```
keybladesephi@Sheila:~$ sudo dpkg --install ~/Desktop/google-desktop-linux_current_i386.deb
(Reading database ... 144716 files and directories currently installed.)
Preparing to replace google-desktop-linux 1.2.0.0088 (using .../google-desktop-linux_current_i386.deb) ...
grep: /opt/google/desktop/.gdl_installed_files: No such file or directory
PREFIX is differ than recorded ROOT_DIR!
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
grep: /opt/google/desktop/.gdl_installed_files: No such file or directory
PREFIX is differ than recorded ROOT_DIR!
dpkg: error processing /home/keybladesephi/Desktop/google-desktop-linux_current_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
File /opt/google/desktop/.gdl_installed_files is missing!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /home/keybladesephi/Desktop/google-desktop-linux_current_i386.deb
```

> What error(s) are you getting?

When I'm trying to install a .deb package, I get the following error:

```
Could not open 'google-desktop-linux_current_i386.deb'

The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```

---

### Post by Partyboi2 on 2008-07-10
try
```
sudo dpkg --purge --force-remove-reinstreq google-desktop-linux_current_i386.deb
```

---

### Post by KeybladeSephi on 2008-07-10
> **Partyboi2 said:**
> try
```
sudo dpkg --purge --force-remove-reinstreq google-desktop-linux_current_i386.deb
```

When I put that command into the terminal, it gave me this error:

```
keybladesephi@Sheila:~/Desktop$ sudo dpkg --purge --force-remove-reinstreq google-desktop-linux_current_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by KeybladeSephi on 2008-07-10
Also, with my update manager, the following error occurs:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

When I run sudo apt-get install -f, the same error occurs from my first post:

```
keybladesephi@Sheila:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it.
```

Please I really need help on this; to make matters worse, when I try to reinstall Ubuntu ([thread here]("http://ubuntuforums.org/showthread.php?p=5355565")), it won't let me, so I can't fix the problem by just reinstalling Ubuntu either. ='[

---

### Post by Partyboi2 on 2008-07-11
> When I run sudo apt-get install -f, the same error occurs from my first post:

     Code:
     keybladesephi@Sheila:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-desktop-linux needs to be reinstalled, but I can't find an archive for it. 
The only other thing I can think of at the moment is to try
```
sudo dpkg --remove --force-remove-reinstreq google-desktop-linux
```

---

### Post by KeybladeSephi on 2008-07-11
I ran that in the terminal and it gave me this:

```
keybladesephi@Sheila:~$ sudo dpkg --remove --force-remove-reinstreq google-desktop-linux
[sudo] password for keybladesephi: 
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 144715 files and directories currently installed.)
Removing google-desktop-linux ...
grep: /opt/google/desktop/.gdl_installed_files: No such file or directory
PREFIX is differ than recorded ROOT_DIR!
dpkg: error processing google-desktop-linux (--remove):
 subprocess pre-removal script returned error exit status 1
File /opt/google/desktop/.gdl_installed_files is missing!
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 google-desktop-linux
```

---

### Post by Partyboi2 on 2008-07-11
This worked for me.
Alt+F2 then enter ```
gksudo nautilus /var/lib/dpkg/info
``` and search for google-desktop-linux-prerm and remove it.
Then back in a terminal change directory to where the google-desktop-linux_current_i386.deb is  and install it again
```
sudo dpkg - i google-desktop-linux_current_i386.deb
```

---

### Post by KeybladeSephi on 2008-07-12
I have done what you told me to do, but when I go to the terminal, put in "cd ~/Desktop" (that's where my deb package is), and input "sudo dpkg - i google-desktop-linux_current_i386.deb", I get this error:

```
keybladesephi@Sheila:~/Desktop$ sudo dpkg - i google-desktop-linux_current_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

I also have a google-desktop-linux.list, google-desktop-linux.md5sums, and google-desktop-linux.postinst. Should I delete those as well to clear things up?

---

### Post by Partyboi2 on 2008-07-12
my mistake it is meant to be
```
 sudo dpkg -i google-desktop-linux_current_i386.deb
```

> I also have a google-desktop-linux.list, google-desktop-linux.md5sums, and google-desktop-linux.postinst. Should I delete those as well to clear things up?
No leave them as they are

---

### Post by KeybladeSephi on 2008-07-12
I gotta tell ya, Partyboi2, you are amazing =] Thank you so much

---

### Post by Partyboi2 on 2008-07-12
glad you got it fixed :)

---

### Post by MaikoID on 2009-08-24
thanks a lot guys, this thread solved my problem.

---

