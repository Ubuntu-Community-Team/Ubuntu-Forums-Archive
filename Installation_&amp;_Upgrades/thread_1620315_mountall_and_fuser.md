---
title: "mountall and fuser"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by ubscott on 2010-11-12
hello,

i have been trying to install PEAR so that i can install xdebug.  for hours now i've been trying to deal with an error i get when attempting to install PEAR in a terminal.  the error is:

[I]Could not perform immediate configuration (2) on mountall

[/I]Is there a way to know what process is giving me this error?  I've been researching fuser for quite some time trying to solve this.  

i've been studying these pages:
[http://www.linux.com/archive/articles/121049](http://www.linux.com/archive/articles/121049)
[http://www.linux.com/archive/articles/121049](http://www.linux.com/archive/articles/121049)
[http://ubuntuforums.org/showthread.php?t=1465023](http://ubuntuforums.org/showthread.php?t=1465023)

this has led me to put this command in a terminal:
fuser -m -v /mypath/myfolder

this shows me a list of about 25 processes with their IDs.  I've tried to kill them all, with this command:
sudo fuser -k -v /mypath/myfolder

Doing this closes the RealVNC viewer i'm using to connect to my Linux box. in addition, i'm logged out of Ubuntu.

it seems to me that maybe i can kill whatever processes i need to to remove the conflict with the PEAR installer.  However, i have no idea what these are.

does anyone have any suggestions?  thanks.

---

### Post by ubscott on 2010-11-13
hi,
i have been trying to kill off some process before attempting to run the command to install PEAR:
sudo apt-get install php5-dev php-pear

everything i try fails. i have even tried to do these commands without RealVNC, thinking that was the culprit.

does anyone know of a resource to assist with this dreaded error:
E:Internal Error, Could not perform immediate *configuration* (2) on *mountall* 

This error is a show-stopper.  having spent two days trying to get past this, i still don't have an idea how to proceed.

any help appreciated.  thanks.

---

