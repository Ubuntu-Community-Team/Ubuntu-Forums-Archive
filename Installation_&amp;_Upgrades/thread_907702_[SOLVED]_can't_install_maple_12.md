---
title: "[SOLVED] can't install maple 12"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by jmd9qs on 2008-09-01
hi,

recently purchased and downloaded Maple 12 (32-bit) for my Hardy box... i chmod +x'd it and then ran ./ to install.

however, when i did this, this was the output:

```
jmd9qs@jmd9qs-desktop:~/Desktop$ chmod +x Maple12Linux32Installer.bin
jmd9qs@jmd9qs-desktop:~/Desktop$ ./Maple12Linux32Installer.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
The size of the extracted files to be installed are corrupted.  Please
try to download the installer again and make sure that you download
using 'binary' mode.
Please do not attempt to install this currently downloaded copy
```.


can't find anything on their support site or google.... any help guys?

---

### Post by tuxulin on 2008-09-01
> recently purchased and downloaded Maple 12 (32-bit)

did you buy this software on the net and if so did you use FTP to 
download it to your machine ?

if yes then simply change the mode of the FTP product from ASCII to Binary as suggested by the given error report

> try to download the installer again and make sure that you download
using **'binary' mode**.

Tuxulin

---

### Post by jmd9qs on 2008-09-02
i did buy the software online, but not via FTP...

any other suggestions?

---

### Post by baggins on 2008-09-02
Don't know if this will help, but...
I just finished installing Maple12 on 40+ machines at work, but I ran the install from a CD, everything went fine . So the maple Linux installer work.
I guess that something went wrong when you downloaded.
Can you re-download? 
Or if you know someone with a CD, or a good download you could use that.
As I understand it it's only the license.dat file that differs, and that is generated from your registration key during install. So as long as you use your own reg. key. it ought to be legal. (although I give no guarantees :) )

-- Jon

---

### Post by jmd9qs on 2008-09-02
i don't have an install cd... i'm pretty sure if i try to download again they'll charge me again. i don't know... the download seemed to go fine, so i'm not sure if it is actually corrupted or not.

thanks for your help, though

---

### Post by baggins on 2008-09-02
I think what they charge you for is the registration key, but we have a site license here so I'm not really that familiar with the procedures.

Try mailing them though. Usually maplesoft are quite reasonable people. 
And I guess that a bum download happens often enough, that they must have procedures in place. 
After all any company ultimately lives off happy customers. :)

 -- Jon

---

### Post by baggins on 2008-09-02
Ohh by the way if/when you get it installed, if you use compiz you will need to modify the xmaple script. Just add the following

```
AWT_TOOLKIT=MToolkit
export AWT_TOOLKIT
```
 somewhere above this line:
```
"${MAPLE}/bin/maple" -x $*
```

Maple aparently ships with some "funny" java libraries, text mode should work as is.

 -- Jon

---

### Post by jmd9qs on 2008-09-02
thanx...

i am currently waiting for the download to finish (i finally said 'screw it' and came to the same conclusion: i'm paying for the registration key)... i'll update when possible.

by the way, can you tell me where that script is... still kind of a newbie and don't know my way around as well as i would like.

thanks for your continued help!

---

### Post by baggins on 2008-09-02
I am going to asume that you install maple in /opt/maple12 then the executable will be in 
/opt/maple12/bin/ in this case you want to edit /opt/maple12/bin/xmaple so it looks like this:
```
#!/bin/sh

# Copyright (c) 1993-2003 by Maplesoft, a division of Waterloo Maple Inc.
# All rights reserved. Unauthorized duplication prohibited.
# Permission is granted to modify this file to be appropriate
# for use at the installation for which Maple was purchased.

# This script runs Maple with the Java interface.
MAPLE='/opt/maple12'
AWT_TOOLKIT=MToolkit

export MAPLE AWT_TOOLKIT

"${MAPLE}/bin/maple" -x $*
```
Next you probably want to include the maple-path in your path variable
Assuming that you use bash add the following lines into your ~/.bashrc
```
export PATH=$PATH:/opt/maple12/bin
```
Finaly if you want to user maple and latex, there is a number of maple styles for latex in /opt/maple12/etc

-- Jon

---

### Post by jmd9qs on 2008-09-02
ok... the download was sucessfull and the install worked as well...

now, how do i start maple? i tried running maple, then maple 12 via terminal, but didn't work (tried as root, too, still no luck). 

i chose the install path to be /root/maple12, and when i navigate to that point, i see all the maple folders and stuff, but can't find an executable icon.

what am i missing here?

---

### Post by baggins on 2008-09-02
If you installed to /root/maple12/
then your xmaple cam be startted from the command line by :

/root/maple12/bin/xmaple

-- Jon

---

### Post by jmd9qs on 2008-09-02
excellent... that worked great! thanks for your help.

---

### Post by baggins on 2008-09-03
You are quite welcome :)

---

