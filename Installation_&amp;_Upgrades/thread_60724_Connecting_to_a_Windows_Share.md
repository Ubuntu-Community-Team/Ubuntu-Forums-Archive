---
title: "Connecting to a Windows Share"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by duminas on 2005-08-29
Please do not tell me to use Search, I have been doing that for the past two hours. ;)
My issue is this:

I have my machine, on Ubuntu Hoary, and a machine downstairs on Windows 2000. The Windows 2000 machine has a user called *support* which I use to perform cleanup on it with (it's the family PC, but I needed a seperate account). And the main problem is below.

It has an IP of **192.168.1.100**.
Workgroup is the default that you'd see on any Windows box.
The share name I am trying to access is either **C$** or **seed**.

If I try to connect to it via Places > Connect To Server... (with the IP and sharename as appropriate), I get a Nautilus window up showing "seed" as the location all right, but the mouse pointer just sits at the spinning "I'm thinking" one Ubuntu has, and it never does anything.

If I actually provide a username, the same thing happens--no request for authentication or anything. I do have *samba* installed, but I've no idea how to use it properly.

```
smbclient -L 192.168.1.100 -U support
```spews this at me:```
timeout connecting to 192.168.1.100:445
session request to 192.168.1.100 failed (Called name not present)
timeout connecting to 192.168.1.100:445
session request to 192 failed (Called name not present)
timeout connecting to 192.168.1.100:445
Password:
Domain=[MYDOMAIN] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

***** Shares list edited out to conserve space *****

session request to 192.168.1.100 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[MYDOMAIN] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
```And at this point, I am completely lost. If anyone could offer aid, I would be appreciative. :)

---

### Post by grim42 on 2005-08-29
What happens if you type the following into a Nautilus address bar:

```
smb://192.168.1.100/seed
```

What is the IP address & subnet mask of the Ubuntu machine?

Is there a firewall running on the Windows machine? Or the Ubuntu one?

BTW: Samba is not needed for connecting to shares, only for serving shares. Ie. only is you want to share stuff from Ubuntu.

EDIT: Also try the following from a terminal window:

```
sudo apt-get install smbfs
sudo mkdir /media/smb
sudo mount -t smbfs //192.168.1.100/seed /media/smb -o username=xxx,password=xxx
```

You can also try that without the *-o username=xxx,password=xxx* part.

---

### Post by duminas on 2005-08-29
```
smb://192.168.1.100/seed
```
The left pane changes to show "seed on 192.168.1.100", but none of my files show up.

> What is the IP address & subnet mask of the Ubuntu machine?
IP: 192.168.1.102
Subnet: 255.255.255.0

> Is there a firewall running on the Windows machine? Or the Ubuntu one?Firestarter on mine, BlackICE on his. Sharing worked when I connected from Windows, though. o.O

```
sudo apt-get install smbfs
sudo mkdir /media/smb
sudo mount -t smbfs //192.168.1.100/seed /media/smb -o username=xxx,password=xxx
```This mount string times out on me, with the following:
```
timeout connecting to 192.168.1.100:445
18633: session request to 192.168.1.100 failed (Called name not present)
timeout connecting to 192.168.1.100:445
18633: session request to 192 failed (Called name not present)
timeout connecting to 192.168.1.100:445
```
And yet there my files are when I access /media/smb, wha...?

OK, it works now, but I'd still like to figure out this timeout stuff.

---

### Post by grim42 on 2005-08-29
I don't know -- it looks like it could be a firewall problem ... but the timeouts?

If you're able, what happens when trying to connect if the firewalls are temporarily disabled?

---

### Post by duminas on 2005-08-29
[QUOTE=grim42]I don't know -- it looks like it could be a firewall problem ... but the timeouts?

If you're able, what happens when trying to connect if the firewalls are temporarily disabled?[/QUOTE]
 I can't disable BlackICE right now, since the family is on the PC.
I will try it tomorrow, though.

A question before then, though:
Do you have any idea why copying files takes so absurdly long? This may just be because I've never done this with huge files before, but a 1.1 GB ISO is taking (according to Nautilus' dialogue) about 35 minutes. Even for 802.11b, this seems quite bad, when I could copy 225 MB files in about 5 minutes (again) from Windows. ^_^

Sorry for asking that, if it's a glaringly obvious reason.

---

### Post by grim42 on 2005-08-30
I have found that when copying from SMB shares via Nautilus, it can be quite slow. Unfortunately I haven't found a solution for this yet.

---

