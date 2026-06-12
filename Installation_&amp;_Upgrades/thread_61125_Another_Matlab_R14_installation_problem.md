---
title: "Another Matlab R14 installation problem"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by bogoliubov on 2005-08-30
Hello. I just tried to install MatLab R14 on my PC with Hoary.
I tried 
"sudo sh /media/cdrom/install_unix.sh"
but that gave me
"/media/cdrom/install_unix.sh: /media/cdrom/unix/install: /bin/sh: bad interpreter: Åtkomst nekas
/media/cdrom/install_unix.sh: line 4: /media/cdrom/unix/install: Lyckat"

where "Åtkomst nekas"=acces denied and "Lyckat"=sucess

Does anyone know how I can fix this?

---

### Post by John.Michael.Kane on 2005-08-30
You will have to wait for help around here seems only vetern users can answer questions around here..

---

### Post by bogoliubov on 2005-09-01
[QUOTE=SD-Plissken]You will have to wait for help around here seems only vetern users can answer questions around here..[/QUOTE]
Ok, I'll wait... :)

---

### Post by [pl]ice on 2005-09-01
which ver. u got? i'm running 7,0,0,1 but i haven't got that script you have mentioned! i got as an installation :  ./Install and a gui pops out, didn't have any problems.

the problem you might get is that matlab shuts down often... :/ this is due to copy/paste from it. haven't found a fix :(

---

### Post by bogoliubov on 2005-09-01
I don't know which version; but I should perhaps mention that it's the student version of R14...

It seems that I'm not allowed to execute the scripts or something; not even with sudo or when being root...

---

### Post by parktownprawn on 2005-09-05
I once got similar messages trying to install Mathematica.

I copied the entire cd to my hard drive and managed to install it from there.

your could always (assuming you have a legal copy) try emailing the Math Lab support 
people

also the thread 
[http://ubuntuforums.org/showthread.php?t=40997&highlight=matlab](http://ubuntuforums.org/showthread.php?t=40997&highlight=matlab)
might help

---

### Post by ubuntme on 2005-09-05
./Install is the way to go,

Also make sure you have your cdrom mounted correctly.  make sure the exec option is set in fstab.  This is prolly whats wrong

Do not copy your contents of your CD to you hard drive, this is unecessary ;)

---

### Post by bogoliubov on 2005-09-05
[QUOTE=ubuntme]./Install is the way to go,

Also make sure you have your cdrom mounted correctly.  make sure the exec option is set in fstab.  This is prolly whats wrong

Do not copy your contents of your CD to you hard drive, this is unecessary ;)[/QUOTE]

Thanks; that worked! I did get some complaints about some lib-file, but the program seems to work anyway... Do you know anything about this?

Anothr thing; the installer installed MatLab right where I told it to, eg it did not create any "matlab" folder. this is rather annoying. So do you know how I can uninstall the program?

---

### Post by parktownprawn on 2005-09-05
[QUOTE=ubuntme]./Install is the way to go,

Also make sure you have your cdrom mounted correctly.  make sure the exec option is set in fstab.  This is prolly whats wrong

Do not copy your contents of your CD to you hard drive, this is unecessary ;)[/QUOTE]

duh!   :oops:   - thats much better advice

---

### Post by ubuntme on 2005-09-05
> Thanks; that worked! I did get some complaints about some lib-file, but the program seems to work anyway... Do you know anything about this?

Anothr thing; the installer installed MatLab right where I told it to, eg it did not create any "matlab" folder. this is rather annoying. So do you know how I can uninstall the program? 

What was the error message?  I didn't get any, but I'm using R13.  Do a google on the error message or look here:
[http://www.mathworks.com/matlabcentral/](http://www.mathworks.com/matlabcentral/) 

This is a good resource :)

Not sure what you mean about a matlab folder, If you want a folder for your code I would make one in your home directory, and add this directory to your matlab paths (there is instructions for this in the installation guide)

Or do you want an entry in a menu / and icon?

I think you will have to do this yourself, If you are doing this make sure you read this page:
[http://www.mathworks.com/support/solutions/data/1-1B5ZV.html?solution=1-1B5ZV](http://www.mathworks.com/support/solutions/data/1-1B5ZV.html?solution=1-1B5ZV)
Otherwise you may not be able to run matlab from a menu.

good luck :)

---

### Post by bogoliubov on 2005-09-07
Thank's for all your help. I have reinstalled matlab and everything works; so I'm happy!

I just want to say that the thing with Linux that amazes me the most is all the helping hands along the way. Great!

---

