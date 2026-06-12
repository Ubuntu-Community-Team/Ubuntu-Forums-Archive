---
title: "Samba Question, Probably Easy For You Guys"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-01
I use a minimalist samba file that works great for file sharing on my home network.

The only (extremely minor) problem I have is that I want to change the name of the computer when it shows up in the computer list.

For example, my computer name on the network would show up as:

jeremy-desktop (samba version)

I simply want it to show up as:

jeremy-desktop

So basically I want to remove the samba version from the computer name. I couldn't find the option online so perhaps my search skills are rusty today. Is there a samba option I can set to simplify the computer name?

---

### Post by gregphil on 2008-10-01
It is in the smb.conf file in /etc/samba.

Either servername or netbious name, I forget which.

try "man smb.conf"

---

### Post by syko21 on 2008-10-01
ctrl + f works well if you already know the name you are looking for in smb.conf just read the comments around that line and edit accordingly


EDIT:
ps>
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.BACKUP
```
just in case you want some insurance if something screws up

---

### Post by jlacroix on 2008-10-01
That's the problem guys, the very first thing I do when installing Linux is to delete the smb.conf and replace it with my own. This is the smb.conf file I use now so you can see what I mean:

```
[global]
workgroup = SERVICE
security = share
include = /etc/samba/smbshared.conf

wins support = no

```

The smbshared.conf file just has my shares. This set up works VERY well and it's the easiest set up ever, it's pretty much no-nonsense file sharing, so that's why I use that file.

Anyway, as you can see I removed all the default stuff. In the man page I do see this:

>   %L
           the NetBIOS name of the server. This allows you to change your
           config based on what the client calls you. Your server can have a
           &#8220;dual personality&#8221;.

That doesn't look like a smb.conf option to me...

(Also, I don't know if that's even the option I want).

---

### Post by uBeer on 2008-10-02
Put this in your smb.conf:

server string = %h

That'll give you the wanted result.
Have fun sharing!

---

### Post by plun on 2008-10-02
> **uBeer said:**
> Put this in your smb.conf:

server string = %h

That'll give you the wanted result.
Have fun sharing!

Nope...

> ## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HEMMA

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z



I am testing this and server string is enabled....

Now testing wins support.

Impossible to connect to a Ubuntu client, OK to my Ubuntu server.

Nautilus smb sharing must be a complete mess..

---

### Post by jlacroix on 2008-10-02
> **uBeer said:**
> Put this in your smb.conf:

server string = %h

That'll give you the wanted result.
Have fun sharing!

I did that, and I didn't notice any change. I did restart the samba daemon.

---

