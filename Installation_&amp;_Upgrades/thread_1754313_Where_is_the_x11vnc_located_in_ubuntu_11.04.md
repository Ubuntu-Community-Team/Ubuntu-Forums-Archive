---
title: "Where is the x11vnc located in ubuntu 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by HeimdalWK on 2011-05-09
I am working with Ubuntu for the first time since school and it was an intro class.  I am trying to setup a file server for part of a school project.  I installed x11vnc and am trying to set the password.  However everywhere I look says the file would be located at ~/.vnc/passwd.  However when I ls from the home directory .vnc does not exist.  When I type out vncpasswd ~/.vnc/passwd I get returned a message The program 'vncpasswd' can be found in the following packages:
 * tightvncserver
 * vnc4server


Any idea how I can get this setup?  Am I using old information that is no longer accurate or am i messing this up somewhere?

---

### Post by HeimdalWK on 2011-05-16
bump

---

### Post by MAFoElffen on 2011-05-16
> **HeimdalWK said:**
> I am working with Ubuntu for the first time since school and it was an intro class.  I am trying to setup a file server for part of a school project.  I installed x11vnc and am trying to set the password.  However everywhere I look says the file would be located at ~/.vnc/passwd.  However when I ls from the home directory .vnc does not exist.  When I type out vncpasswd ~/.vnc/passwd I get returned a message The program 'vncpasswd' can be found in the following packages:
 * tightvncserver
 * vnc4server


Any idea how I can get this setup?  Am I using old information that is no longer accurate or am i messing this up somewhere?
You know than VNC is gnome based and server is tty?  In server, you usually install ssh server, during the install in will gen public and private keys... and can use a local userid/password for client assess.  The ssh client is usually via a terminal session using:
```

ssh -x user_name@ip_address

```VNC is usually setup on a server by installing a gnome desktop on that server (ubuntu-desktop, kubuntu-desktop or xubuntu-desktop)... VNC is part of those desktops.  Then starting that desktop, going to system settings, vnc settings, configure... But would need that desktop running when trying to connect VNC... which is going to add overhead to run that desktop. (That is why ssh is preferred for servers).

But look at the files in ~/.tsclient... and the piece I think you might be  missing from the list you posted is: [FONT=monospace]
[/FONT]xtightvncviewer
 
Hope this info helps.

---

### Post by HeimdalWK on 2011-05-19
I know very little about unix, just some few basic commands.  The rest I am picking up.  The reason i chose to use everything I have chosen is because of a site I found.  If there is something I need to change please let me know I would greatly appreciate any advice.

Thank you

---

