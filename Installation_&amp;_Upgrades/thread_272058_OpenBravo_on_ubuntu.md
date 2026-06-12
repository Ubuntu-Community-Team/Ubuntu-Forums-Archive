---
title: "OpenBravo on ubuntu"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by dootch on 2006-10-05
Has anyone installed Openbravo on Dapper Drake 6.06 yet?  I am getting ready to give it a whirl and was wondering if anyone has any advise.

---

### Post by blackgecko on 2006-11-23
Im trying to install it, sun-java5-sdk, and tomcat5.5 are installed, but when i launch the install.sh just a blank window appears, nothing else.
Im using edgy

---

### Post by xboxer21 on 2006-12-07
> **blackgecko said:**
> Im trying to install it, sun-java5-sdk, and tomcat5.5 are installed, but when i launch the install.sh just a blank window appears, nothing else.
Im using edgy
are you using postgresql or oracle ?
if you are using postgresql then check the console where you launched ./install.sh it will be waiting for a password. I guess its looking for the sudo/root password.

---

### Post by blackgecko on 2007-01-14
im using postgresql, and all it says is something about donload.jar.

---

### Post by alamba on 2007-03-24
Any luck with this?

A

---

### Post by newtonviet on 2007-03-29
After install all dependencies like Sun java (sdk 1.5), Tomcat5, Apache-Ant, Postgres SQL 8.1, I am able to install it using the full version OpenbravoERP-2.22-UniversalInstaller_linux.bin 

Note: you must change its permission:  
sudo chmod a+x OpenbravoERP-2.22-UniversalInstaller_linux.bin 

and then install:  
sudo ./OpenbravoERP-2.22-UniversalInstaller_linux.bin 
 
Only one thing, the compiling will take more than 1 hour!

---

### Post by adrianmooreuk on 2007-04-09
I got to that install screen on feisty, it carried on and set up database on postgresql and claimed to be successful.  [http://127.0.0.1:8180/openbravo](http://127.0.0.1:8180/openbravo)  just gives 
HTTP Status 404 - /openbravo
type Status report
description The requested resource (/openbravo) is not available.
Apache Tomcat/5.5

so tomcat is working and pgsql is working but i cannot get to the login screen. Any ideas as to what configuration might be wrong?

---

### Post by alamba on 2007-04-12
newtonviet: I still haven't been able to get this to work on dapper, edgy or feisty. Which version of the OS are you using? Also, where are you picking up the neccessary dependencies, i.e. Sun java (sdk 1.5), Tomcat5, Apache-Ant, Postgres SQL 8.1

A

---

### Post by adrianmooreuk on 2007-04-29
I have it working at last.

Info sources: [http://downloads.sourceforge.net/openbravo/Openbravo_PostgreSQL_r2.11_quick-start_installation_guide_v1.0.1.pdf?modtime=1156239251&big_mirror=0](http://downloads.sourceforge.net/openbravo/Openbravo_PostgreSQL_r2.11_quick-start_installation_guide_v1.0.1.pdf?modtime=1156239251&big_mirror=0)

[http://www.gentoo-wiki.com/HOWTO_Install_Openbravo_ERP](http://www.gentoo-wiki.com/HOWTO_Install_Openbravo_ERP) 

Note Gentoo wiki uses file names tomcat-5.5 whereas my installation is tomcat5.5 i.e. without the hyphen

[http://ubuntuforums.org/showthread.php?t=380470](http://ubuntuforums.org/showthread.php?t=380470)

Above for tomcat5.5 probs start tomcat with sudo /usr/share/tomcat5.5/bin/catalina.sh run

.bashrc for my setup

export JAVA_HOME=/usr/local/bin/jdk1.5.0_11

#openbravo
CATALINA_HOME=/usr/share/tomcat5.5
CATALINA_BASE=/var/lib/tomcat5.5
CATALINA_OPTS="-server -Xms384M -Xmx512M"
export CATALINA_HOME CATALINA_OPTS CATALINA_BASE
#ANT
ANT_HOME="/usr/share/ant"
export ANT_HOME



Login is user Openbravo password openbravo

---

### Post by alamba on 2007-04-30
How did you resolve "The requested resource (/openbravo/) is not available". Based on your feedback I worked on it today and was able to setup all the dependencies and now have tomcat running too. The installation of openbravo went through just fine and completed in a "success". However, the login screen is still not showing up.

A

---

### Post by adrianmooreuk on 2007-04-30
Following the gentoo wiki 

[http://www.gentoo-wiki.com/HOWTO_Install_Openbravo_ERP](http://www.gentoo-wiki.com/HOWTO_Install_Openbravo_ERP)

I made a list of the Ubuntu Tomcat Layout.

I set the appropriate environment variables in .bashrc as above. Check your install is the same.

I altered /opt/OpenbravoERP-2.22/AppsOpenbravo/build.xml to 
<property name="log.path" value="${env.CATALINA_BASE}/logs"/>

Compiled openbravo again

cd /opt/OpenbravoERP-2.22/AppsOpenbravo/
ant war

Copied the openbravo.war from  /opt/OpenbravoERP-2.22/AppsOpenbravo/  to /var/lib/tomcat5.5/webapps

rebooted

started tomcat5.5 with: sudo /usr/share/tomcat5.5/bin/catalina.sh run

Opened  [http://localhost:8180/openbravo/security/Login_FS.html](http://localhost:8180/openbravo/security/Login_FS.html)

Usr name Openbravo
passwd openbravo

I am an Linux newbie so if anyone with some knowledge wants to point out
any errors I wont be offended.

Also does anyone have a UK chart of accounts for Openbravo?

---

### Post by alamba on 2007-04-30
Thanks buddy. It was quite a nightmare but have got it up and running now. Appreciate all the help. I've created a concise note on configuring this on my blog now.

A

---

### Post by alamba on 2007-04-30
Just wondering if you saw this. I now have OpenBravo working just fine. On the local machine I'm able to login and use all functions perfectly. However, when I access the application with a web browser from another PC on the LAN, the login page opens, but doesn't show any of the graphics and a user isn't able to login. The login check mark isn't shown and does nothing on clicking it.

EDIT: I tried recompiling by ant war after changing the localhost IP (127.0.0.1) to the IP address of the openbravo machine. Copied the file to /var/share.... and restarted tomcat. Didn't help.

A

---

### Post by adrianmooreuk on 2007-04-30
Haven't got around to Lan deployment yet I am just trying to get to grips with it as a local user at the moment.
The documentation   [http://wiki.openbravo.com/wiki/index.php/Creating_New_Entity](http://wiki.openbravo.com/wiki/index.php/Creating_New_Entity)
shows a creating entity screen. ClientRules->Initial Client Setup doesn't give me that but
just Organization screen. If you know location of any other usage docs. not obviously on Openbravo site
I would be grateful for details. Is there some Compiere or Adempiere sources for docs. I am a new user I
do not know whether they have similar GUI's?

Aha! The answer is... You just open initial client setup in a new tab/window

---

### Post by alamba on 2007-04-30
I don't mean setting up a new entity of any feature set of the package. Just regular old access over the LAN on the same URL that you would use locally. The default username and password should give you the same access that you would when firing up the app locally.

I haven't used compiere or adempiere so sorry can't help you there. Also, am not really bothered about the functionality or feature set of the application. I'm just the setup/network management guy.

A

---

### Post by adrianmooreuk on 2007-04-30
This link might help:

[http://sourceforge.net/forum/forum.php?thread_id=1679432&forum_id=549511](http://sourceforge.net/forum/forum.php?thread_id=1679432&forum_id=549511)

---

### Post by alamba on 2007-05-01
Thanks. After some lurking in the forums over at sourceforge, I've decided to redo a clean install on feisty. Will post how it goes.

A

---

### Post by adrianmooreuk on 2007-05-01
It would be great if you could document your procedure :)

---

### Post by alamba on 2007-05-01
Already in the process of doing that. Specially the tricky bits. Its uploaded on my blog.

A

---

### Post by adrianmooreuk on 2007-05-03
Did it work ?

If so can you post the install documentation here so others can add to it?

---

### Post by alamba on 2007-05-03
So far - no. I had to cancel the compilation step the other day due to other pressing matters that needed my attention. Haven't gotten back to it yet. Am still building the doc, WIP of the doc is on my blog. Once I have it completed and am sure that it works I will post it here.

A

---

### Post by alamba on 2007-05-08
Phew...finally got the thing to work out. Primarily there are a number of places you need to careful off in ubuntu in terms of the patch being used. CATALINA_HOME & CATALINA_BASE are 2 different paths. This also get's reflected in the 05openbravo.policy file. 

Also, one needs to be careful of the IP address being used while compiling the app. I will post a detailed how-to as a seperate thread and link it to this thread.

A

---

### Post by MickKi on 2007-05-27
I am looking forward to your instructions!  :)

I haven't been able to get it to install on a Ubuntu server.  I am getting tomcat dependencies problems as well as some java errors:

1. Java. 
I managed to install sun-java6-jdk, but then I got this as I went through the configuration instructions on the Openbravo website: 
===================================== 
$ sudo update-java-alternatives -s java-1.6.0-sun 
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun 
$ sudo echo "JAVA_HOME=/usr/lib/jvm/java-1.6.0-sun" >> /etc/environment 
-sh: cannot create /etc/environment: Permission denied 
===================================== 
 
2. tomcat 
Here there seems to be a dependency error, which I am not sure how to fix (the box has apache2 on it): 
===================================== 
$ sudo apt-get install tomcat5.5 tomcat5.5-admin tomcat5.5-webapps 
Reading package lists... Done 
Building dependency tree  
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 
The following information may help to resolve the situation: 
 
The following packages have unmet dependencies: 
tomcat5.5: Depends: apache-utils (>= 1.3.33-1) but it is not installable or 
apache2-common but it is not installable 
E: Broken packages 
===================================== 
 
Can you please guide me to complete the installation? 
-- 
Regards,
Mick

---

### Post by dbutcher on 2007-06-17
Hi guys,
I appreciate the info on this thread so far.
I have OpenBravo running on 6.06 with Tomcat5 (not 5.5).  Everything seems to work fine when I access from the local machine, but I have alamba's earlier situation that accessing from another machine brings up broken graphics and an inability to log in.
I have changed the build.xml settings to reflect ip address instead of 127.0.0.1 but this didn't appear to have any effect.
Was there any resolution to this problem?
Cheers,
Dave

---

### Post by alamba on 2007-06-19
Hi Dave,

Are you using the tar version of the installer or the bin? Personally, I used the bin, what I found out what that changing the IP address in build.xml doesn't help when using the bin (atleast, not sure about tar). What does work is specifying the correct IP address during the first stage of the bin installed. My gut feel says that during the initial compilation, the app is hardcoding the IP address in a number of places. 

Short version of the story, reinstall with the correct IP in stage 1 of the install procedure and u'll be good to go.

Best,
A

---

### Post by dbutcher on 2007-06-26
Sorry, it took me a while to get back to this.  alamba, I was using the bin installer.
Reinstalled as you suggested and everything's working now, so it looks like your theory is correct that the installer hard-codes the settings somewhere.  
Thanks for the tip.
Cheers,
Dave

---

### Post by alamba on 2007-06-28
Jolly good buddy. Enjoy it, I actually had to switch to adempiere ERP as against openbravo for my needs. On a completely off topic note, have a look at Zimbra - amazing collab tool with very well integrated components.

A

---

### Post by knowhow on 2007-10-25
I had same problem (login screen not showing up). I solved it by modifying /etc/init.d/tomcat5.5. in command line type "sudo /etc/init.d/tomcat5.5" (without quotes) and change the line that reads TOMCAT5_SECURITY=yes to TOMCAT5_SECURITY=no it will allow tomcat to access openbravo content. I hope this helps.

---

### Post by cacycleworks on 2007-12-30
Hi, I'm working on installing and using openbravo, too. They have version 2.35 available...

I read some more about the tomcat5_security yes/no issue... 

Seems there's a better way, but I'm not yet sure what that would be...

This thread is related:
[http://ubuntuforums.org/showthread.php?t=227286](http://ubuntuforums.org/showthread.php?t=227286)

As is this url:
[http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall](http://jspwiki.org/wiki/BugFailsToLoadOnUbuntuDapperInstall)

Specifically of note:> 
add the required permissions in a 
new file in /etc/tomcat5/policy.d/ restart and re-enable the security 
manager. Disabling the security manager is not recommended on production 
systems since a call to System.exit() in a servlet of JSP page would then 
stop the whole virtual machine that is running Tomcat.

I wonder what the permissions required would be for openbravo ?? If I figure it out before someone replies, I'll post it.

:) Chris

---

### Post by ArNike on 2008-01-03
Hi, I have the same issue as a **dbutcher**, but it appears when I access from local machine. I tried to play with TOMCAT5_SECURITY=yes/no options, copied the new AppsOpenbravo/lib/openbravo.war into tomcat/webapps... No success :( Any suggestion?
Ubuntu 7.10, tomcat5.5, openbravo 2.35.
Thanks.

---

### Post by cacycleworks on 2008-01-04
> **ArNike said:**
> Hi, I have the same issue as a **dbutcher**, but it appears when I access from local machine. I tried to play with TOMCAT5_SECURITY=yes/no options, copied the new AppsOpenbravo/lib/openbravo.war into tomcat/webapps... No success :( Any suggestion?
Ubuntu 7.10, tomcat5.5, openbravo 2.35.
Thanks.

This certainly has to do with the installation step where you set the name of the openbravo machine. I recorded all settings I have done and when I get some time, I can share these. Unfortunately, I just got 2 more projects dumped on top of the 2 I'm working on... it might be some time. 

I am definitely going to post more about OB as we learn more. We're working on using a LAMP server in our office to handle all processes and have it connect to OB for accounting -- as well as anything else we can use OB for. Right now, though, OB has me feeling rather stupid with its intense learning curve.

With the notes above in this thread, I was able to do an install which allows remote login with ok graphics. I also wrote down the steps to perform on the installation computer to use SSL and also about how to turn off the default tomcat homepage. Initially during install, I had our firewall route the OB port and I was able to login from home! 

Some notes: my IT specialist required that we upgrade our computer. We went to a computer store and bought a 1.6G AMD X2 and 4M of RAM. This brought the load down from 9 to 1~2 where it belongs! Java is intense on the CPU! 

I installed with Java 6 and did need to change a couple settings which made sense.

:) Chris

---

### Post by ArNike on 2008-01-15
> **cacycleworks said:**
> This certainly has to do with the installation step where you set the name of the openbravo machine. 


Thank you. After correct installation it works fine.

---

### Post by Fintan on 2008-04-04
I just posted this on the Kubuntu forum. 
It is for HH but should work on GG as well.

I hope this helps here as well:)


[http://kubuntuforums.net/forums/index.php?topic=3092944.0]("http://kubuntuforums.net/forums/index.php?topic=3092944.0")

---

### Post by ramasdf123 on 2008-05-20
Hi,

I am trying to test of OpenBravo on Ubuntu 8.0 Server Edition.  I am at the install the openbravo section of the installation process using OpenSSH.  The database I installed was PostgreSQL instead of Oracle.   

When i enter 'ant install.source', I get the error below.


```
rama@ubuntu:~/openbravo-235mp4$ ant install.source
Buildfile: build.xml

install.source:

database.lib:

clean:
   [delete] Deleting directory /home/rama/openbravo-235mp4/src-db/build/classes
   [delete] Deleting directory /home/rama/openbravo-235mp4/src-db/build/lib
   [delete] Deleting directory /home/rama/openbravo-235mp4/src-db/docs

init:
    [mkdir] Created dir: /home/rama/openbravo-235mp4/src-db/docs

compile:

build.jar:

jar:
     [copy] Copying 1 file to /home/rama/openbravo-235mp4/database/lib

create.database:

clean.database.ORACLE:

BUILD FAILED
/home/rama/openbravo-235mp4/build.xml:214: The following error occurred while executing this line:
/home/rama/openbravo-235mp4/database/build.xml:97: The following error occurred while executing this line:
/home/rama/openbravo-235mp4/database/build.xml:116: java.sql.SQLException: Io exception: The Network Adapter could not establish the connection

Total time: 1 second
rama@ubuntu:~/openbravo-235mp4$

```

---

