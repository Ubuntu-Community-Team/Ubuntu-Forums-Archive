---
title: "regsrv32.exe Wine"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by SkyHawkUb on 2008-06-14
I have Ubuntu installed and working great.
I have installed Wine and it is also working with several windows programs I have Installed.

However I have an application I wish to run and it requires that an .ocx be Registered.

I am new to Ububtu and using Wine and I need help as to how to use the regsrv32.exe file in the System32 folder.

How do you get a terminal window or whatever in necessary to do the Job.

thanks to all
SkyHawkUB

---

### Post by Ub1476 on 2008-06-14
Hi, what application are you trying to install? There might be a guide on the Wine website.

---

### Post by SkyHawkUb on 2008-06-14
The application is one I built with VB6 it requires  X360FtpClient.ocx to be Registered.

All is working except I get Error .ocx or .dll not properly Registered.

This is new to me so I may be trying to do something Wine is not capable of doing.

I use the program with timed event's to transfer files at relative times via FTP Protocal.

I have the Scheduler working like a top. Just need to learn how to Register an .ocx file in Wine.

In Windows all you had to do is open a CMD and cd to Windows\system32\ and enter :>  regserv32 X360FtpClient.ocx and it Registered.

I was looking for some Command to do the same in wine.

As I said I'm new to this.
Thanks
SkyHawkUB

---

### Post by SkyHawkUb on 2008-06-14
Ok Just in Case someone comes across this post an need's to Run regsvr32.exe

Here is how I resolved it.

Open Terminal Window:

Enter the Following
-------------------Terminal Window----------------------------------
jimmiller@jimmiller-desktop:~$ wine cmd
CMD Version 1.0-rc5

Z:\home\jimmiller>cd .wine
Z:\home\jimmiller\.wine>cd drive_c
Z:\home\jimmiller\.wine\drive_c>cd windows
Z:\home\jimmiller\.wine\drive_c\windows>cd system32
Z:\home\jimmiller\.wine\drive_c\windows\system32>regsvr32 YourFile.ocx

The Results will be shown here
----------------------------------------------------------------------

---

