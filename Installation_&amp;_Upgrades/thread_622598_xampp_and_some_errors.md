---
title: "xampp and some errors"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by myharshdesigner on 2007-11-24
i have **xampp-linux-1.6.4.tar.gz** file i follow these steps :-


> 
Step 2: Installation
After downloading simply type in the following commands:

   1. Go to a Linux shell and login as the system administrator root:

      su

   2. Extract the downloaded archive file to /opt:

      sudo tar xvfz xampp-linux-1.6.4.tar.gz -C /opt

      Warning: Please use only this command to install XAMPP. DON'T use any Microsoft Windows tools to extract the archive, it won't work.

      Warning 2: already installed XAMPP versions get overwritten by this command.

That's all. XAMPP is now installed below the /opt/lampp directory.
* Step 3: Start
To start XAMPP simply call this command:

sudo /opt/lampp/lampp start





but after doing these when i try for 

sudo /opt/lampp/lampp start

i will give me some error :-

> 
harsh@harsh-laptop:~$ sudo /opt/lampp/lampp start
/opt/lampp/lampp: line 74: arch: command not found
Starting XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Another web server daemon is already running.
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting MySQL...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
harsh@harsh-laptop:~$ 


it shows me this:-

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	21-Nov-2004 01:46 	-
[DIR]	samba-images/	23-Nov-2007 21:58 	-
Apache/2.2.4 (Ubuntu) Server at localhost Port 80


and when i try this :-

> 
harsh@harsh-laptop:~$ sudo /opt/lampp/lampp stop
/opt/lampp/lampp: line 74: arch: command not found
Stopping XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: XAMPP-Apache is not running.
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Stopping MySQL...
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: Stopping ProFTPD...
XAMPP stopped.
harsh@harsh-laptop:~$ 



it also shows me this :-

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	21-Nov-2004 01:46 	-
[DIR]	samba-images/	23-Nov-2007 21:58 	-
Apache/2.2.4 (Ubuntu) Server at localhost Port 80


pl tell me why this is happening.

---

### Post by myharshdesigner on 2007-11-25
any one can able to solve my problem ?

---

### Post by jcsteele on 2007-11-25
I would contact the xampp people and see if a patch is available...I believe this to be related to an existing bug ([http://bugs.xampp.org/print_bug_page.php?bug_id=53](http://bugs.xampp.org/print_bug_page.php?bug_id=53))

//jcs

---

### Post by myharshdesigner on 2007-11-25
thanks for the reply

but what i think is it says that :-
XAMPP: Another web server daemon is already running.


> 
harsh@harsh-laptop:~$ sudo /opt/lampp/lampp start
[sudo] password for harsh:
/opt/lampp/lampp: line 74: arch: command not found
Starting XAMPP for Linux 1.6.4...
/opt/lampp/lampp: line 74: arch: command not found
**XAMPP: Another web server daemon is already running.**
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: XAMPP-MySQL is already running.
/opt/lampp/lampp: line 74: arch: command not found
XAMPP: XAMPP-ProFTPD is already running.
XAMPP for Linux started.
harsh@harsh-laptop:~$ 




any suggestions ?




> **jcsteele said:**
> I would contact the xampp people and see if a patch is available...I believe this to be related to an existing bug ([http://bugs.xampp.org/print_bug_page.php?bug_id=53](http://bugs.xampp.org/print_bug_page.php?bug_id=53))

//jcs

---

### Post by jcsteele on 2007-11-25
Not really.  I would deffinitely check with the xampp people (searching mailing lists in particular) to see if anyone has experienced any similar issues.

//jcs

---

### Post by myharshdesigner on 2007-11-25
ok now i am just going to remove xampp 1st the i will see what will happen.

according to me i suppose to get **page canoot found** error.
let's see.

---

### Post by myharshdesigner on 2007-11-25
i have reactifey the problem 60%

actually i have installed samba server i thin samba server use apache and apace default port is 80.

after uninstall xampp i am getting the same result in this command in browser :-

> [http://localhost](http://localhost)

Result :-
> 
Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	21-Nov-2004 01:46 	-
[DIR]	samba-images/	23-Nov-2007 21:58 	-
Apache/2.2.4 (Ubuntu) Server at localhost Port 80


---

