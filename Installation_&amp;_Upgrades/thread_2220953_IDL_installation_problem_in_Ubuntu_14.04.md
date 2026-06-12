---
title: "IDL installation problem in Ubuntu 14.04"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by krishnakumar2 on 2014-04-30
Hi All,

I'm in need of some help from the forum members.

I was using fedora for a long time and now shifted to Ubuntu  because of the LTS.

I uses IDL a lot, so tried to install it in Ubuntu and it peacefully got installed. My system is x64 AMD.
But when I tried to run idl, it showed an error as 

error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory

Eventhough the libXp is available in the system, it is not detecting it.

I installed it for my friend's system which is running a 32 bit version of Ubuntu 14.04 innn i386 intel and it is running without any errors.

Did I miss something while installation or any additional libraries are required?

I tried the solutions got from internet search, but none of them worked.

Please let me know if there is a solution is available to this problem.

Thanks,
Krishnakumar

---

### Post by Sigologo on 2014-05-12
Hi [[COLOR=#000000]krishnakumar2[/COLOR][COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1920774")...
 why version of IDL do you need install? ...
I sending tutorial IDL 7.1 instalation for 12.04 LTS

install packages next  pluggins by aptitude o synaptic
sh
csh
tcsh
bash
ia32-libs(64 bits)
libc6-i386

**install THIS JAVA VERSION jre1.511_32bit en 64 bits**
david@gisws:~/dat2/soft/linux/instaladorjavax86$ sudo mkdir /usr/lib32/jvm
david@gisws:~/dat2/soft/linux/instaladorjavax86$ sudo mv jre1.5.0_11/ /usr/lib32/jvm/
david@gisws:~/dat2/soft/linux/instaladorjavax86$ cd 
david@gisws:~$ sudo update-alternatives  --install "/usr/bin/java" "java" "/usr/lib32/jvm/jre1.5.0_11/bin/java" 
david@gisws:~$ sudo update-alternatives  --config java 

NOW INSTALL IDL

You need to be root (sudo su)
Create a directory &#8220;itt&#8221; inside usr/local and go in it (cd usr/local ; mkdir itt; cd itt)
root@ubuntu:/usr/local/itt# sh /media/IDL71/unix//xinstall.sh -NOGUI
Unix IDL Non-GUI installation
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;
The IDL distribution will be installed in the current directory:
/usr/local/itt.
If this is correct, enter &#8220;y&#8221; to continue the
installation. If it is not correct, enter &#8220;n&#8221; to quit the
installation, change to the correct location, and run this
script again.
Is the installation directory shown correct? (y/n): y
IDL is available for many different systems. In order to conserve disk space, we only install the those you need. You will now be asked a series of questions to determine which versions of IDL to install:

Linux &#8211; X86 (32-bit/64-bit)? (y/n): y
Mac OS X &#8211; PowerPC? (y/n): n
Mac OS X &#8211; Intel (32-bit/64-bit)? (y/n): n
Sun Solaris &#8211; Sparc (32-bit/64-bit)? (y/n): n
Sun Solaris &#8211; x86 (64-bit)? (y/n): n

IDL has optional subsets that need not be installed for normal operation, but which enhance the package when present. In order to conserve disk space, we only install those
you specify. If you have the room, we recommend installing them. If you are installing IDL for demonstration or evaluationpurposes, you should install these subsets.
You will now be asked a series of questions to determine which optional subsets to install:
High Resolution Maps (45 Mbytes)? (y/n): y
DICOM Network Services (2.5 Mbytes)? (y/n): y
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-
Summary:
Product: IDL
Installation location: /usr/local/itt
Login: root
Platforms:
Linux &#8211; X86 (32-bit/64-bit)
Optional subsets:
High Resolution Maps (45 Mbytes)
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

The configuration above will be installed on your system unless you indicate otherwise now.
Install the above configuration? (y/n): y

AND LAST TIPS

[email]david@notebookdl:/usr/local/itt/idl71/bin/bin.linux[/email].x86$ sudo mv gl_driver.so gl_driver.so.back

Regards!!!
 PD If you have a license of new idl appreciate shared with me

---

