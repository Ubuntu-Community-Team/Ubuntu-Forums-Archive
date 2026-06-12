---
title: "Open Office installation failure"
date: 2015-02-08
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2015-02-08
Back again for help I'm afraid.
I have just re-installed Xubuntu v.14.10 and am trying to install the latest version of Open Office.  Everything seems to install OK but OO does not show up on the desktop or in the mouse menu. 
I typed openoffice4 in terminal and the response was as shown[SIZE=3] " /usr/bin/openoffice4: 22: exec: /opt/openoffice4/program/soffice: not found".[/SIZE] I have looked in the /opt folder and confirm there is no reference to OO. I have removed and re-installed OO three times without success[SIZE=2][/SIZE]
Any suggestions please as to what may have gone wrong. Just to confirm - Libre Office is not installed so there is no clash with OO.

---

### Post by vasa1 on 2015-02-08
You'll find more help here: [https://forum.openoffice.org/en/forum/](https://forum.openoffice.org/en/forum/)

---

### Post by ian-weisser on 2015-02-09
When you install OpenOffice, where in the filesystem are you installing it to?

---

### Post by gordon99 on 2015-02-09
"I was only following orders" That's my excuse and I'm sticking to it.
Fact is I downloaded the Linux 64 bit DEBS package and naturally it went into Downloads.
I then unpacked it using "tar -xvzf  ....etc."
Then cd into DEBS subdirectory, followed by "sudo dpkg -i  *.deb"
One guide said "By default this will install OO in your  /opt directory"  This is perhaps where things are not going according to script as my /opt directory  only has "google" in it.
Anyway, I ploughed on and did "cd desktop-integration" followed once again by "sudo dpkg -i  *.deb" 
My understanding is that, at this stage, OO should be ready to open and run. 
To answer your specific question ian I am not myself installing it anywhere in the file system from the time it downloads as none of the guides I have read make any reference to the installer placing the files anywhere.
Hope the above helps to indicate why things aren't doing as they should. Believe me when I say I have been reading a number of installation guides and they all say pretty much the same  though I suspect most are just copies of each other.

---

### Post by deadflowr on 2015-02-09
> **gordon99 said:**
> "I was only following orders" That's my excuse and I'm sticking to it.
Fact is I downloaded the Linux 64 bit DEBS package and naturally it went into Downloads.
I then unpacked it using "tar -xvzf  ....etc."
Then cd into DEBS subdirectory, followed by "sudo dpkg -i  *.deb"
One guide said "By default this will install OO in your  /opt directory"  This is perhaps where things are not going according to script as my /opt directory  only has "google" in it.
Anyway, I ploughed on and did "cd desktop-integration" followed once again by "sudo dpkg -i  *.deb" 
My understanding is that, at this stage, OO should be ready to open and run. 
To answer your specific question ian I am not myself installing it anywhere in the file system from the time it downloads as none of the guides I have read make any reference to the installer placing the files anywhere.
Hope the above helps to indicate why things aren't doing as they should. Believe me when I say I have been reading a number of installation guides and they all say pretty much the same  though I suspect most are just copies of each other.

for what it's worth, though doubtful it'll be more helpful than that, you can use dpkg-query to see where a package has installed any files.
try something like this
```
dpkg-query -L openoffice-writer
```
this should output all the locations that the openoffice-writer package has installed throughout the system.
(the -L means listfiles ;can also be run with just that --listfiles.)
If you have synaptic installed, this output can be seen in properties >> Installed Files. per package.

I currently don't have ooo installed, and cannot remember where it does install, either.

---

### Post by gordon99 on 2015-02-10
Hello deadflowr,. When I type the code this is what I get:
 dpkg-query -L openoffice-writerdpkg-query: package 'openoffice-writer' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
I tried to examine archive files just to see if I could do that but even trying to do that defeated me. It seems to me one needs a masters degree in command line syntax to make progress in Linux.

---

### Post by ian-weisser on 2015-02-10
> **gordon99 said:**
> dpkg-query -L openoffice-writerdpkg-query: package 'openoffice-writer' is not installed
Ah. I had assumed it was still installed.

> **gordon99 said:**
> and dpkg --contents (= dpkg-deb --contents) to list their contents.
That's one you can use when the package is present but not installed.

Example for the 'hello' package located in /var/cache/apt/archives:
```
$ dpkg --contents /var/cache/apt/archives/hello_2.9-1_amd64.deb 
drwxr-xr-x root/root         0 2014-04-26 03:01 ./
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/info/
-rw-r--r-- root/root     11733 2014-04-26 03:01 ./usr/share/info/hello.info.gz
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/man/
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/man/man1/
-rw-r--r-- root/root       725 2014-04-26 03:01 ./usr/share/man/man1/hello.1.gz
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/doc/
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/share/doc/hello/
-rw-r--r-- root/root      1616 2013-10-09 18:46 ./usr/share/doc/hello/NEWS.gz
-rw-r--r-- root/root      2257 2014-04-12 08:00 ./usr/share/doc/hello/copyright
-rw-r--r-- root/root      1277 2014-04-26 03:01 ./usr/share/doc/hello/changelog.Debian.gz
drwxr-xr-x root/root         0 2014-04-26 03:01 ./usr/bin/
-rwxr-xr-x root/root     23144 2014-04-26 03:01 ./usr/bin/hello
```
In this example, you can see that the package will install to /usr/share/info, /usr/share/man, /usr/share/doc, and /usr/bin.

---

### Post by gordon99 on 2015-02-10
After many attempts to install OO I have finally managed it. The solution turned out to be very simple. I  installed the 32 bit version of DEBS instead of the 64 bit. I haven't a clue why the 64 bit would not install as my laptop, a H.P Compaq Presario CQ56 with an AMD v140 processor supports 64 bit. I will mark this thread as solved but if anyone would like to offer an explanation why the  64 bit download would not work I will be very grateful.
Thanks to those who gave me the benefit of their advice.

---

### Post by deadflowr on 2015-02-10
> **gordon99 said:**
> After many attempts to install OO I have finally managed it. The solution turned out to be very simple. I  installed the 32 bit version of DEBS instead of the 64 bit. I haven't a clue why the 64 bit would not install as my laptop, a H.P Compaq Presario CQ56 with an AMD v140 processor supports 64 bit. I will mark this thread as solved but if anyone would like to offer an explanation why the  64 bit download would not work I will be very grateful.
Thanks to those who gave me the benefit of their advice.

You probably installed a 32-bit version of Xubuntu.
It does not matter if the machine is a 64-bit system.It matters that the OS is.
running
```
uname -a
```
if it shows a few X86_64 lines then you've got a 64-bit OS installed.
If it shows lines with i686(or i386) then you've got a 32-bit OS installed.

You can install a 32-bit program(or OS) in 64-bit OS(or machine), but not vice versa.
So 32-bit inside 64-bit, yes
64-bit inside 32-bit, no.

---

### Post by gordon99 on 2015-02-11
What is this telling me please about the version of xubuntu I have installed ? uname -aLinux gordon-Presario-CQ56-Notebook-PC 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 athlon i686 GNU/Linux .Sorry, have re-read your post. Clearly I have installed a 32 bit version of xubuntu then. Don't know why.

---

### Post by tgalati4 on 2015-02-12
Unfortunately, there is no easy way to convert a 32-bit system to 64-bit.  You would need to perform a complete wipe and reinstall a new 64-bit distribution.  Then you can install 64-bit OpenOffice with ease.

---

