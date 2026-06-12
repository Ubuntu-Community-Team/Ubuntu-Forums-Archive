---
title: "Unable to read help in Eclipse 3.8.1 on Ubuntu 13.04 [server error 500]"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by Mystic38 on 2013-06-25
[FONT=tahoma]I have very recently setup a dual boot windows 7 ubuntu 13.04 machine for the purposes of learning linux and entertaining some C++ programming & development. 

the Ubuntu install is pretty minimal, ie installed Ubuntu 32 bit, some plugs for mp3 etc, then installed Eclipse via the service center. I cannot read any of the help files and get:[/FONT]
>
**HTTP ERROR: 500**

 Problem accessing /help/index.jsp. Reason: 

Server Error
<

[FONT=tahoma]are there some plug-ins or other stuff that i need to enable Eclipse to correctly display the help files?.. 

thanks..

nb: My last programming in anger was > 25 years ago so if you assume i know next to nothing about linux and so need noob level step by step instructions you would actually, be quite accurate...:D
.
[/FONT]

---

### Post by dino99 on 2013-06-25
[http://stackoverflow.com/questions/6150807/how-to-solve-this-http-500-error](http://stackoverflow.com/questions/6150807/how-to-solve-this-http-500-error)
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by Mystic38 on 2013-06-25
thanks for a quick reply.. 

i had already spend over 2hrs searching the web and fully read both of these targets prior to joining and posting here. Neither of those offer any insight as to why on a fresh install of ubuntu a fresh install of eclipse will open, yet not display help. Clearly there is some configuration issue or item missing so if you have any direct ideas that would be awesome!


> **dino99 said:**
> [http://stackoverflow.com/questions/6150807/how-to-solve-this-http-500-error](http://stackoverflow.com/questions/6150807/how-to-solve-this-http-500-error)
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by Mystic38 on 2013-06-25
For clarification, just in case anyone is tempted to help, lol, 
1. Eclipse will run and the workspace will appear, so my understanding from the various searches i have done is that this is not a java runtime related issue.
2. I also understand that the help file uses the browser and points to the help file via localhost (apologies for any incorrect terminology here..am quite rusty..).. anyway, Firefox would not access localhost and i installed apache from the software center.. so now when "localhost" is in the address bar it sees 

[It works! This is the default web page for this server.
 The web server software is running but no content has been added, yet.]

3. In Eclipse when i select help for "workbench basics" it sets the addr to "http://127.0.0.1:40371/help/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2FgettingStarted%2Fintro%2Foverview.htm"... and does not see anything (server error 500 refered to above).

Is there additional software/plugin/stuff that needs to be on this machine or is there some setup item in Eclipse that needs modification?..

happy to run/capture any debug stuff to aid in this, just be gentle.. lol

cheers

---

### Post by Mystic38 on 2013-06-30
Fixed (workaround)

I am sure there are machines that loaded Ubuntu 13.04 then loaded Eclipse from the Software Center and were able to display help. Mine didnt. 

As a rule i prefer to fix things rather than workaround but to get a solid install of Eclipse, and finding zero help, i tried something else. This is what i did.

A. uninstall Eclipse via the service center (note this does leave artifacts on the system, i didnt bother to remove them as i was going to re-install Eclipse from Eclipse.org).
B. I downloaded the current version of Eclipse from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)
C. I installed via the instructions on askubuntu given in answer to a different issue (ie install of current eclipse onto ubuntu)[INDENT]
If you've downloaded Eclipse from their official website, follow these steps for the installation.
  
[LIST=1]
[*]Extract the eclipse.XX.YY.tar.gz using
  
tar -zxvf eclipse.XX.YY.tar.gz 
[*]Become root.
  
sudo -i 
[*]Copy the extracted folder to /opt
  
cp -r eclipse.XX.YY /opt 
[*]Create a desktop file and install it:
  
gedit eclipse.desktop   and copy the following to the eclipse.desktop file.
  
[Desktop Entry] Name=Eclipse  Type=Application Exec=eclipse Terminal=false Icon=eclipse Comment=Integrated Development Environment NoDisplay=false Categories=Development;IDE; Name[en]=Eclipse   then execute the following command to automatically install it in the unity:
  
desktop-file-install eclipse.desktop 
[*]Create a symlink in /usr/local/bin using
  
cd /usr/local/bin ln -s /opt/eclipse/eclipse 
[*]For eclipse icon to be displayed in dash, eclipse icon can be added as
  
cp /opt/eclipse/icon.xpm /usr/share/pixmaps/eclipse.xpm 
[/LIST]
[/INDENT]
 
D. Start Eclipse, note that Help is available.
E. As i was interested in a C++ environment, I added the plug-ins via the Eclipse application, rather than via command line.

not elegant, but effective in my case.

---

### Post by ptpare on 2013-09-18
Some more clarity on this installation can be found at:
[http://grainier.net/how-to-install-eclipse-juno-in-ubuntu-13-04/](http://grainier.net/how-to-install-eclipse-juno-in-ubuntu-13-04/)

This spelt out the path for the eclipse.desktop file to be 

/usr/share/applications/

and also put the symlink in /usr/bin rather than in /usr/local/bin

---

### Post by rubo77 on 2013-10-06
Did you find a solution by now without reinstalling Eclipse?

---

