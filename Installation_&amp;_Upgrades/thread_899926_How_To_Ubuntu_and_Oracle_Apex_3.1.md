---
title: "How To: Ubuntu and Oracle Apex 3.1"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by markwyatt on 2008-08-24
The following is how to install Oracle 10g Express and Apex 3.1
Using Ubuntu 8.04

Download oracle-xe-universal_10.2.0.1-1.0_i386.deb from oracle.com
Download apex_3.1.1.zip from apex.oralce.com

double click oracle-xe-universal_10.2.0.1-1.0_i386.deb file
then in Terminal window type:

Type: sudo /etc/init.d/oracle-xe configure

admin: system
password: password

**************  install complete of 10g express **************  

Apex 3.1 upgrade:

Note: The files are in a folder called apex on my desktop
Note: Run Terminal

Type: websoft@websoft-server:~$ cd Desktop
Type: websoft@websoft-server:~/Desktop$ cd apex

Type: websoft@websoft-server:~/Desktop/apex$  /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/config/scripts/runsqlplus.sh

Note: The previous line launches new Terminal in SQL*Plus

Type: $ sqlplus /nolog
Type: connect sys as sysdba

Note: Prompt for password of database admin login

Type: @apexins SYSAUX SYSAUX TEMP /i/


Once you complete the standard install, you need to perform the following steps to complete the upgrade:


Connect to SQL*Plus as SYS
Type: $ sqlplus /nolog
Type: connect sys as sysdba


Type: @apxldimg.sql APEX_HOME (this may not work - see issue below)
Type: @apxxepwd.sql password
      (where password is the password of the Application Express internal ADMIN account)

For the steps above, apex folder on the desktop is the directory where the Application Express software was unzipped.



***** ISSUE: login button not working ***** 

The following was posted from someone using Windows (Ubuntu instructions are below)

I found the problem why I couldn't login. It is in the script apxldimg.sql...

I had unzipped to c:\oracle\apex_31. When running this script the parameter is used for finding the images map (where also the javascript files are located). In my case the program was looking in c:\oracle\apex_31\apex\images (see line 31 in the file, the &1 is replaced by the parameter). Of course this was faulty...

By manually changing the script on line 31 to:
create directory APEX_IMAGES as 'C:\oracle\apex_31\images';

and running the script again (now without any parameters, as I deleted the reference to it by modifying line 31 in the script). The script runs now for several minutes (3-4 minutes)... and after that running the script apxxepwd.sql with a parameter telling the password for the admin account everything now works very well!

Try it for yourself...

Another option is naming the unzipped map as it is unzipped, simply 'apex'. The parameter for the script then should be the directory before the apex directory (eg c:\oracle in my case or c:\ when you place the apex directory in c:\apex ).

************* Ubuntu Instructions*****************

**** Original code in file apxldimg.sql
create directory APEX_IMAGES as '&1/apex/images';

**** change to New code in file apxldimg.sql
create directory APEX_IMAGES as '/home/websoft/Desktop/apex/images';

Type: @apxldimg.sql
Type: @apxxepwd.sql password
      (where password is the password of the Application Express internal ADMIN account)


**** Apex 3.1 installation complete **** 

In Firefox Web Browser go to:
[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

Workspace: internal
username: admin
password: password

If you need any help with this please email me at [email]mark@go-websoft.com[/email]
I will be glad to schedule a chat to help you, or answer any questions.

Mark Wyatt

---

### Post by wingkitf on 2009-03-22
Hi Mark,

Thanks for the instruction! I have also got the newest APEX 3.2 worked on my Ubuntu box:p. 

For [FONT="Arial Black"][COLOR="DarkOliveGreen"]apxldimg.sql[/COLOR][/FONT], line 35 could be corrected by pointing a created directory [FONT="Arial Black"][COLOR="Red"]APEX_IMAGES [/COLOR][/FONT]
from [FONT="Arial Black"]'&1/apex/images'[/FONT] 
to an exact location like [FONT="Arial Black"][COLOR="DarkRed"]'/home/{username}/Desktop/apex/images'[/COLOR][/FONT]

where [COLOR="darkred"][FONT="Arial Black"]'/home/{username}/Desktop/apex'[/FONT][/COLOR] is the extracted directory of apex_3.2.zip in my case. You may change it to somewhere else in your convenience.

Cheers:D!
Kenneth

---

### Post by naushadnaleer on 2009-09-28
Hi, I'm new to Ubuntu Linux and Oracle Apex. I have tried to upgrade Apex in Oracle XE 10 to Apex 3.2. I have followed all the instructions and as said in the above article my login button does not work. I have tried to change the code on apxldimg.sql as mentioned but unable to save the changes, I saved it under a different file name. I still can't run this file, I get "unable to open file 'apxldimg.sql', can you please help me? following is the msg:

SQL> @apxldimg.sql
SP2-0310: unable to open file "apxldimg.sql"


Thanks in advance, Naushad.

---

### Post by Waappu on 2009-09-28
Hi,

Place apex_3.2.zip to folder /tmp.
Then
```
cd /tmp
unzip apex_3.2.zip
cd /tmp/apex
sqlplus '/as sysdba'
@apxldimg.sql /tmp

```
That should work

---

### Post by Waappu on 2009-09-28
> **wingkitf said:**
> Hi Mark,

Thanks for the instruction! I have also got the newest APEX 3.2 worked on my Ubuntu box:p. 

For [FONT="Arial Black"][COLOR="DarkOliveGreen"]apxldimg.sql[/COLOR][/FONT], line 35 could be corrected by pointing a created directory [FONT="Arial Black"][COLOR="Red"]APEX_IMAGES [/COLOR][/FONT]
from [FONT="Arial Black"]'&1/apex/images'[/FONT] 
to an exact location like [FONT="Arial Black"][COLOR="DarkRed"]'/home/{username}/Desktop/apex/images'[/COLOR][/FONT]

where [COLOR="darkred"][FONT="Arial Black"]'/home/{username}/Desktop/apex'[/FONT][/COLOR] is the extracted directory of apex_3.2.zip in my case. You may change it to somewhere else in your convenience.

Cheers:D!
Kenneth

Modifying script is not needed if you follow Oracle documentation.

---

### Post by naushadnaleer on 2009-09-29
> **Waappu said:**
> Hi,

Place apex_3.2.zip to folder /tmp.
Then
```
cd /tmp
unzip apex_3.2.zip
cd /tmp/apex
sqlplus '/as sysdba'
@apxldimg.sql /tmp

```That should work

THANK YOU VERY MUCH, I managed to successfully upgrade Apex. I still have a problem, what is the "workspace,username & password"? I tried to use my old username and password before upgrade, it didn't work! I still don't know what to enter for the workspace. PLEASE HELP!
Naushad.

---

### Post by naushadnaleer on 2009-09-29
> **naushadnaleer said:**
> THANK YOU VERY MUCH, I managed to successfully upgrade Apex. I still have a problem, what is the "workspace,username & password"? I tried to use my old username and password before upgrade, it didn't work! I still don't know what to enter for the workspace. PLEASE HELP!
Naushad.


HELLO, JUST WANTED TO LET YOU GUYS KNOW I MANAGED TO GET IN! I forgot to run apxxepwd.sql, thanks anyway!

naushad.

---

### Post by darcsacka on 2010-02-26
> **naushadnaleer said:**
> THANK YOU VERY MUCH, I managed to successfully upgrade Apex. I still have a problem, what is the "workspace,username & password"? I tried to use my old username and password before upgrade, it didn't work! I still don't know what to enter for the workspace. PLEASE HELP!
Naushad.

well there are 2 options for user name, pass and workspaces:
1. standard workspace is "internal"
2. you can use for username SYSTEM and pass(your password set during the instalation) or the standar user created by the new apex called ADMIN with the password "oracle"

cheers

---

### Post by Waappu on 2010-02-27
Hi,

You can not use user SYSTEM to login to INTERNAL workspace.
That do not work Apex 3.1 ->

Default password for Apex instance administrator ADMIN is not oracle on Apex version 3.1 ->.

You need set password after you did upgrade Apex to version 3.1 or above

---

### Post by r351574nc3 on 2010-06-07
I just used this process to upgrade to 3.2.1

It seems to have worked ok, but now apex does not seem to start. Here is my status output of oracle-xe

STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 10.2.0.1.0 - Production
Start Date                07-JUN-2010 20:22:50
Uptime                    0 days 0 hr. 2 min. 8 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Listener Log File         /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=EXTPROC_FOR_XE)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=ip-10-160-38-207.us-west-1.compute.internal)(PORT=1521)))
Services Summary...
Service "PLSExtProc" ha

So...the database is started ok, but apex is not starting. Any ideas?

---

### Post by Waappu on 2010-06-08
Hi,

Apex is inside database. How you did check database is started ?
Run in terminal
```

sudo /etc/init.d/oracle-xe restart

```

And see does your listerner and database start

---

