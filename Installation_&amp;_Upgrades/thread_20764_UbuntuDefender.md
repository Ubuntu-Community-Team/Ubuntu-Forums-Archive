---
title: "UbuntuDefender"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by davidwashere2003 on 2005-03-18
I'm trying to install BitDefender on Ubuntu, but can't figure out what to do.
I know Linux may be safe from most virus infection but I deal with alot of Windows machines that are not safe, and I'd prefer to catch the infection at the source.

I've downloaded the following files from [www.bitdefender.com:](www.bitdefender.com:)

# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.rpm
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.run
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.deb
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.rpm
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.run
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.deb 

But I don't know where to go from here.

Any help would be appreciated.

---Or if there's an antivirus already included in Ubuntu, could you point me in the right direction.

Thanks

---

### Post by ubuntu_demon on 2005-03-18
[QUOTE=davidwashere2003]I'm trying to install BitDefender on Ubuntu, but can't figure out what to do.
I know Linux may be safe from most virus infection but I deal with alot of Windows machines that are not safe, and I'd prefer to catch the infection at the source.

I've downloaded the following files from [www.bitdefender.com:](www.bitdefender.com:)

# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.rpm
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.run
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.deb
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.rpm
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.run
# BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.deb 

But I don't know where to go from here.

Any help would be appreciated.

---Or if there's an antivirus already included in Ubuntu, could you point me in the right direction.

Thanks[/QUOTE]
 maybe you can try this :

[http://www.ubuntuforums.org/showthread.php?t=9328&highlight=anti-virus](http://www.ubuntuforums.org/showthread.php?t=9328&highlight=anti-virus)

---

### Post by davidwashere2003 on 2005-03-18
Right on,

I can scratch the BitDefender.
I've used it for Windows, and it works fine, but I was just going for it because it was the first to popup in the search for Linux virus protection.

I'll try out the steps listed there.

Thanks.

---

### Post by bored2k on 2005-03-18
[QUOTE=davidwashere2003]Right on,

I can scratch the BitDefender.
I've used it for Windows, and it works fine, but I was just going for it because it was the first to popup in the search for Linux virus protection.

I'll try out the steps listed there.

Thanks.[/QUOTE]
 You could just 
> sudo dpkg -i BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.deb or with 
BitDefender-Console-Antivirus-7.0.1-3.linux-gcc3x.i586.deb 


To install it .

---

### Post by davidwashere2003 on 2005-03-18
Ah, thanks.

I tried dpkg -i BitDefender-Console-Antivirus-7.0.1-3.linux-gcc29x.i586.deb

Ran through with sudo dpkg -i 
Install worked no problem.

Now what do I do with it?

I can browse to the directory it's installed in but can't run the program.

Help I'm up stuck!

----Just an update...

> 
      cd xfprot-1.9
      ./configure
      make
      sudo make install
      
      nautilus applications:///System

Managed to get something.
Ran root terminal and made my way to /opt/bdc/

Tried ./configure and it didn't do anything, so I'll assume that is a part of FProt.

Tried ./bdc /home

Managed to get a scan of some files...

Tried 

./bdc /

This is much more thorough. 
Believe that got the whole system.

=====================================
Anyone know if there's a graphical side to the program?

Is there a way I can set it up to be run from the GUI, rather than stumbling my way through the terminal? I've used DOS, but that's pretty basic in comparison, and some of the linux commands and thier uses are beyond me.

> 
 file menu ----> Create launcher

basic tab ---->
Name: F-Prot
Command: xfprot
Icon: /usr/local/xfprot/icons/antivirus-48x48.png

I don't really follow that step, I can't find "Create Launcher" in any menus.

====

Ok, I'm a dumbass.

Right click desktop to bring up Create Launcher... easy enuff!

Ah, it still gives no window to let me know if it's really running or not.

I created a launcher and gave it the following command:

/opt/bdc/bdc /

There is no results or anything listed when I run the launcher though.

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
Ok, think I'm getting somewhere...

Modified the launcher to:

/opt/bdc/bdc --log=scan /

-This runs a thorough scan of everything. Tried and true enough for me. It also
writes a log file called scan with all the info about the scan.

Made another desktop launcher:

Name: Bitdefender Log
Command: gedit /opt/bdc/scan

-This opens a window with the scan info.

It's a little more complex than Windows methods, but it's kinda like building something and feeling proud for the work done. 

Thanks for the help anyway, and if you know a way to make my little process easier please share!

---

