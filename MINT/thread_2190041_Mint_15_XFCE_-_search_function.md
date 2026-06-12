---
title: "Mint 15 XFCE - search function?"
date: 2013-11-25
forum: MINT
---

### Post by Haisiong on 2013-11-25
It seems to me Catfish used to be under "Accessories".  It's not there.
Software Manager and Synaptic Package Manager don't find Catfish.
In Thunar, right clicking a folder and left clicking "Search" does nothing.

I do need a search function in an operating system.  Any clues will be appreciated, as I am clueless.
Thank you.

---

### Post by Frogs Hair on 2013-11-25
***Moved to Other OS/Distro Support***

---

### Post by Toz on 2013-11-25
Looks like Mint 15 is based on Ubuntu 13.04. 
According to packages.ubuntu.com, catfish is in the Universe repository so the first thing to check is to make sure the Universe repository is enabled. To do so, go to the Software Centre -> Software Sources, and make sure that "Universe" repository is enabled.

If it is and still no results, open a terminal window and run:
```
sudo apt-get update
```
...and post back if any error messages are seen. Lets see if there is a problem with the package manager on your system.

If there are no error messages, what does the following command return:
```
apt-cache policy catfish
```

---

### Post by Haisiong on 2013-11-25
Thanks for the reply Toz!

first result:
```
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg                            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release.gpg [198 B]                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia Release [18.5 kB]                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages        
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main i386 Packages [23.5 kB]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages        
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream i386 Packages [9,237 B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import i386 Packages [40.2 kB]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en                 
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en_US     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/import Translation-en
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/main Translation-en
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en_US
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) olivia/upstream Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/universe Translation-en_US
Fetched 91.6 kB in 41s (2,208 B/s)
Reading package lists... Done
```

second result:
```
unable to locate package catfish
```

Regards -

---

### Post by Bashing-om on 2013-11-25
Haisiong; Hi !

try:
```

apt-cache search catfish

```
For reference: - it is available for 13.04:
> 
sysop@1304mini:~$ apt-cache search catfish
catfish - a versatile file searching tool
sysop@1304mini:~$ 


[INDENT][INDENT]just my little bit to help
[/INDENT][/INDENT]

---

### Post by Toz on 2013-11-25
Hmm - it is available in the "Ign [noparse]http://archive.ubuntu.com[/noparse] raring/universe Translation-en_US" repository as referenced by the package manager... See: [http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages.bz2]("http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages.bz2"):
> Package: catfish
Priority: optional
Section: universe/utils
Installed-Size: 585
Maintainer: Xubuntu Developers <xubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Cody A.W. Somerville <cody-somerville@ubuntu.com>
Architecture: all
Version: 0.6.3-0ubuntu1
Depends: python (>= 2.7.1-0ubuntu2), gir1.2-glib-2.0, gir1.2-gtk-3.0, gir1.2-pango-1.0, python-zeitgeist, gir1.2-gdkpixbuf-2.0, yelp, gksu, locate, zeitgeist
Filename: pool/universe/c/catfish/catfish_0.6.3-0ubuntu1_all.deb
Size: 72958
MD5sum: eb0d86835b0f3a370d085bba664383e8
SHA1: cb6325b3438160a378b77a85a741b7d5b2d89ffd
SHA256: a7c42f582082224a7b5216c8f330323297b70598fa8c4a59fe13ac966e7080d8
Description: a versatile file searching tool
Homepage: [http://software.twotoasts.de/index.php?/pages/catfish_summary.html](http://software.twotoasts.de/index.php?/pages/catfish_summary.html)
Description-md5: 8a5903f90fc57fc1237e25f0d14ff6ad
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: xubuntu-desktop, ubuntustudio-desktop

...but it seems to be ignored during the update run. Try clearing out package lists:
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
```
...re-running the update:
```
sudo apt-get update
```
...and checking for catfish:
```
apt-cache policy catfish
```

If it exists, try installing it.

Also post back the results of those commands.

---

### Post by Haisiong on 2013-11-25
Toz, you da man.

Clearing out the package lists per your above instructions did the trick.  After I re-ran update, Software Manager was able to find and install Catfish.
Thank you!

God bless and good day -

---

### Post by Toz on 2013-11-25
Glad to hear it worked. Can you please mark this thread as solved using the "Thread Tools" link above?

---

