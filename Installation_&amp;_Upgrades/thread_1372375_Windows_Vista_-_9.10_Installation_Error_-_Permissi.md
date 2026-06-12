---
title: "Windows Vista - 9.10 Installation Error - Permission Denied"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Master Jake on 2010-01-04
I'm trying to install Ubuntu 9.10 on my Windows Vista Home Premium machine. My specs far exceed the requirements to install, so I know there's no problem there.

On installation I receive an error somewhat through that says something like:

> 
An error occured:

Permission denied

For more information, please see the log file:
C:\Users\Username\AppData\Local\Temp\wubi-9.10ubuntu1-rev160.log


So.... I go to that file, and the last line in it is:

> 
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'


I did run Wubi Installer as an Administrator, and unblocked it giving it full privileges. It's really annoying because my download speed is 80kb/s so it takes about 3 hours to download. During that 3 hours I can't use my internet so I have to wait, and wait, and wait, and then boom... error. And wubi can't pick up where it left off, you have to uninstall to reinstall, which sucks tremendously.

Please help.

---

### Post by tachuela on 2010-01-04
Do you have a 64 bit processor?

---

### Post by gargaralarga on 2010-01-05
I have the same problem!

---

### Post by gargaralarga on 2010-01-05
Folks,

This is the thing I did.

I downloaded the CD-Image 32-bit and the wubi.exe 32-bit as well. And then I installed as usual. You have to donwload both in the same location by the way. At least worked for me.

---

### Post by only4manni on 2010-04-18
Hi there i have something same problem please....
Can anybody please help me ?
I have got an error in installing the ubuntu through wubi on windows 7.
Look i download the wubi installer from this ( [http://wubi-installer.org/](http://wubi-installer.org/) ) site and then goes to run the .exe file thai is wubi.exe and then simply fills the requirements as i need. And then i don't know what gonna happen there to installation as it gives such an error like [ Please you can also see this ( [http://www.7bucket.com/i/00000/spmog3vavgtw.png](http://www.7bucket.com/i/00000/spmog3vavgtw.png) )one snapshot contains two windows one is downloading as it shows the remaining time and down to this is the error window ]. Please if anyone please help me as early as possible by you.

An error occurred:

Permission Denied

Fore more information, please see the log file:
C:\users\manni\appdata\local\wubi-9.10ubuntu1-rev160.log

THANKS YOU VERY MUCH

---

### Post by only4manni on 2010-04-18
Hi there i have something same problem please....
Can anybody please help me ?
I have got an error in installing the ubuntu through wubi on windows 7.
Look i download the wubi installer from this ( [http://wubi-installer.org/](http://wubi-installer.org/) ) site and then goes to run the .exe file thai is wubi.exe and then simply fills the requirements as i need. And then i don't know what gonna happen there to installation as it gives such an error like [ Please you can also see this ( [http://www.7bucket.com/i/00000/spmog3vavgtw.png](http://www.7bucket.com/i/00000/spmog3vavgtw.png) )one snapshot contains two windows one is downloading as it shows the remaining time and down to this is the error window ]. Please if anyone please help me as early as possible by you.

An error occurred:

Permission Denied

Fore more information, please see the log file:
C:\users\manni\appdata\local\wubi-9.10ubuntu1-rev160.log

Hey please SIR if you got solve this one problem then please reply me on my own id ( [EMAIL="manni_di_sardari@yahoo.com"]manni_di_sardari@yahoo.com[/EMAIL] )if you don't mind 

THANKS YOU VERY MUCH

---

### Post by Nhorning on 2010-06-07
One of the posts in these forums said I could simply take the wubi.exe file and copy it into the same folder as a freshly downloaded ubuntu iso before running it.  THIS WORKED FOR ME! 

it was quite a shock actually...

I didn't even have to use a 3rd party program to mount the iso. I suggest trying this method first.

---

