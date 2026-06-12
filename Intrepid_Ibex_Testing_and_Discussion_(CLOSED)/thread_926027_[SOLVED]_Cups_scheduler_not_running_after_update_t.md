---
title: "[SOLVED] Cups scheduler not running after update to alpha 5"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by amano on 2008-09-21
I think, that I need some community help this time.

I had decided to ignore my problem for some time and see if this was a common problem or not, but I didn't find any bugs on it, nor people complaining about it, thus I didn't file a bug and try to seek your help here first.

I cannot print, because the cups server is not running and I have no clue how to get it running. When I click on Standard Printer in the Gnome Settings, there appears an Error dialog: **CUPS server error** *The CUPS sheduler is not running.*

I then tried to to purge all CUPS related packages and reinstalled them --> no joy
I tried to restart the CUPS server manually and googled */etc/init.d/cupsd restart* to be the correct command. But this just gave *bash: /etc/init.d/cupsd: No such file or directory*

I then came across the fact that cupsys was renamed to cups on the package level for Intrepid and that the cupsys packages were just transitional dummy packages, but I cannot draw any conclusions from these things.

Can anyone help? Does anybody have the same problem? Any other suggestens?

Thanks in advance.

---

### Post by amano on 2008-09-21
Just for the record

Those lines won't give any different results either:

> /etc/init.d/cupsys restart -->  /etc/init.d/cupsys: No such file or directory

/etc/init.d/cupsys restart --> bash: /etc/init.d/cups: No such file or directory


The Cups packages are installed correctly. Where is the command gone?

---

### Post by amano on 2008-09-22
*Bump* :(

Anybody any ideas? :confused:

What happens if you try to restart CUPS? Does that work? What command works?

Restarting CUPS shouldn't do any harm to your system.

---

### Post by ronacc on 2008-09-22
check your permissions on the file /etc/init.d/cups and see if they are correct , I have  root = read write    group (root) = read only   others = read only    also make sure it is marked executable . , here is the output when I run the cmd .

ron@ron-desktop3:~$ /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 5075: Operation not permitted
cupsd: Child exited with status 1!
                                                                         [fail]
ron@ron-desktop3:~$ sudo /etc/init.d/cups restart
[sudo] password for ron: 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
ron@ron-desktop3:~$ 


note that you have to use sudo for it to work , since you get "No such file or directory" I suspect it is not exectuable.

---

### Post by amano on 2008-09-24
Thanks for making me think that the file itself could be wrong somehow! I just burnt a current live CD and copied the file from the alpha 6 CD. CUPS is starting up again :D

---

