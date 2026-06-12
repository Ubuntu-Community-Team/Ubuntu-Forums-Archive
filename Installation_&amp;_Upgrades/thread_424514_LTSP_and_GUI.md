---
title: "LTSP and GUI"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by drinehart on 2007-04-26
I recently followed some instructions to isntall LTSP on Feisty and everything appeared to work ok except the actual login from a client.  I was able to use <CTRL> <ALT> <F1> and login normally so I am pretty sure everything is ok.

The problem I have is that there is no graphical login, just text.  I originally installed the server ubuntu so I'm guessing the problem may lie in that I haven't installed any X Windows manager.

Can someone shed some light on this?

What can I do to fix this?  I would like to get LTSP running so I can remotely login with a graphical interface.  I'm not concerned about running X Windows on the server console since it's a headless box.

Duane

---

### Post by peckman12 on 2007-04-28
Do you get just a cursor before you press <CTRL> <ALT> <F1>?

---

### Post by peckman12 on 2007-04-29
YOU MUST CORRECT THE SETUP LTSP DOES NOT SUPPORT THE WAY OPTION 17 is in other messages.
JUST REMOVE THE IP LIKE BELOW!  I was having a video problem before this.

Identified, it was not a video problem it was looking for a none existent NFS mount.  Press <CTRL><ALT><F1> 
You will see it looking for the NFS mount.

Just add the following on your client reservations:

NOTE: You may be able to set some of these on the scope, but I know they work when you add all of them directly on the reservation.

NOTE: These must be placed at the client reservation level to work.

17 Root Path - /opt/ltsp/i386
66 Boot Server Host Name - 192.168.1.100
67 Bootfile Name- /ltsp/i386/pxelinux.0

---

### Post by drinehart on 2007-04-30
I received the graphical login screen upon boot.  I then proceeded to use the <CTRL><ALT><F1> combination to get a non-graphical login session.

I don't really understand the second post.  When I pressed the <CTRL><ALT><F1> combination I did see a mount: I/O error.  (I thought this had something to do with a USB connected HD I have connected to the server though since it was mentioned in the bootup process.)

Anyway I don't know where to add "client reservation level" information.  Can you please tell me what file that is?

Duane

---

### Post by drinehart on 2007-04-30
FOLLOWUP:

I appear to be correct in my first assumption - I need to have a windows manager installed on the server.  I recently installed Gnome on the server and upon boot my LTSP client, I was able to access the desktop.

Duane

---

### Post by tuxinator on 2007-05-02
Did you have to do anything to disable gnome on the server itself or do you just let the server boot into gnome?

I am attempting to do what you have done and would appreciate any pointers or "heads up" you have to offer.

---

### Post by drinehart on 2007-05-03
I did not do anything special to explicitly disable a GUI login upon boot.  To be honest, I have not rebooted the computer since the original install (which is what I like in a server).

There are resources on the web to explicitly stop a Linux computer from booting to a GUI.  Just search in the forums or on the web.  I think it is somewhere in the /etc/rc.d startup files (probably see something like startx).

The pointers are (from my install):

1. Do the ubuntu server install 
2. Change your apt sources to not pull form the CDROM (/etc/apt/sources.list)
3. Install and configure DHCP (to assign addresses + send kernel to workstation)
     Add following to dhcpd.conf (in /etc folder):
     filename "/ltsp/i386/pxelinux.0";
     option root-path "/opt/ltsp/i386";
4. Install LTSP with apt-get install (instructions in Ubuntu docs)
5. Build client (instructions in Ubuntu docs)
6. Install window manager if not already installed

Duane

---

### Post by smhickel on 2007-05-03
D,

I too am experiencing the same issue. In fact I posted about this about 2 hours ago...

Not sure what the issue is. 

The screen goes through the ubuntu login but then gets to a text-based screen and then starts blanking off and on. You can see a login but no gui. 

Instructions to get LTSP under FEISTY only speak to properly setting up /etc/ltsp/dhcpd.conf. Took me forever to figure out proper syntac, as the default did not work. FInally used:

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.155;
  option domain-name "one'sdomainname";
  option domain-name-servers 192.168.1.50;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.69;
  option subnet-mask 255.255.255.0;

 
  filename "ltsp/i386/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

So the issue is that it does get through most of the client boot up but does not get to the gui and starts blinking.

I saw a note somewhere that said to edit the nsf file deep down in an ltsp directory somewhere and change the timeout value, which I did. I was getting a mount error with a < 28 near it. The error went away when I did this but still did not allow a gui boot up of a thin client...

Also, (I assume this is because I converted from ubuntu to edubuntu) I had to run a script in /usr/sbin called ltsp-build-client before my edubuntu had any of the /opt/ltsp/i386 files. That took about 20 minutes to complete. 

I searched high and low for any hits on these issues and google was kind of sparce.

Steve

---

