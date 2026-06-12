---
title: "linux ubuntu 9.10, network config problem"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by Maria_1980 on 2010-05-31
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]Hello Everyone,[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]I am newbie in linux and networking, can anyone please help me through this problem. I was asked to config couple of computers and add them to the network. I installed linux 9.10 on the client and went through the following steps as was told to do. [/SIZE][/FONT][/FONT][/COLOR]
 
 
[FONT=Verdana][COLOR=black][FONT=Arial][SIZE=2][FONT=Symbol]· [/FONT]Set up NIS and NFS on the client system. just the following bits on the client PCs: [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Arial][SIZE=2]1. Install the appropriate packages:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier New][FONT=Arial][SIZE=2]sudo aptitude install portmap nis nfs-client ssh[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Arial][SIZE=2]Enter [COLOR=darkred]CompanyNISDomainName[/COLOR] as the NIS domain. [/SIZE][/FONT]
[FONT=Arial][SIZE=2]2. Edit /etc/hosts.allow to add a line like:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]portmap : [COLOR=darkred]Server ID Address[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]3. Edit /etc/passwd to add a line at the end saying:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]+::::::[/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]4. Edit /etc/group to add a line at the end saying:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]+:::[/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]5. Edit /etc/shadow to add a line at the end saying:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]+::::::::[/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]6. Edit /etc/yp.conf and add the line:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2]ypserver [COLOR=darkred]Server IP Address[/COLOR][/SIZE][/FONT][/FONT]
[FONT=Arial][SIZE=2]7. Edit /etc/fstab and add these two lines:[/SIZE][/FONT]
[FONT=Courier New][FONT=Arial][SIZE=2][COLOR=darkred]ServerName[/COLOR]:/home /home nfs rw 0 0[/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=darkred]ServerName[/COLOR]:/srv/shares/admin /shares/admin nfs rw 0 0[/FONT][/SIZE][/FONT]
[FONT=Arial][SIZE=2]8. Restart NIS:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]sudo /etc/init.d/nis restart[/SIZE][/FONT]
[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]I have done all the steps, at the end I tried to look at share folder. [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]1. one of the computers hanged, I restart it. But then system is not boot completely. the screen shows that there are some problems with the server configuration and ICEauthority, and also shows following message:[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]/usr/lib/libgconf2-4/gconf- sanity- check one or more of the mounts listed in ect/fstab cannt yet be mounted: [/SIZE][/FONT][/FONT][/COLOR]
[FONT=Verdana][SIZE=2][FONT=Verdana][COLOR=black]/home: waiting for thunderpants:/home[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]/shares/admin: waiting for [COLOR=darkred]ServerName[/COLOR]: /srv/share:/admin[/COLOR][/FONT][/SIZE][/FONT]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]2. Second computer said does not recognise the client password and won't connect to the share folders. !!??? I can see the server on the network place area but ...!!!!??? [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]Do I need to made a change on the server? or what? help pls (I already asked this question of server administrator but didnt get clear answer, just I have told that I should not need to change any setting on the server)!!!![/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=2]I would appreciated if anyone can give me an idea pleaseee. [/SIZE][/FONT][/FONT][/COLOR]

---

