---
title: "Cannot install Ubuntu Server 10.04"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by slorkluk on 2010-05-18
Hello, I'm a complete novice at Ubuntu. I just want to have a cheap home server set up in my house.

I am following a walkthrough guide from here:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3)

But when I get to page 3 of the guide it has me start entering commands...

Here's what it says to do:

> 7 Configure The Network
Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100):

```
vi /etc/network/interfaces
```

[QUOTE]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/QUOTE]
So after I enter all the information into the computer it asks me to do this:
> Then restart your network:

```
/etc/init.d/networking restart
```
But I cant! I have been trying to figure this out for hours but I CANNOT get this to work. How do I input this command? I tried typing sudo /etc/init.d/networking restart but every time I start typing the letter "s" this insert thing pops up at the bottom and screws everything up...

It's so frustrating, please help me :cry:

---

### Post by lisati on 2010-05-18
Are you saving the file you were editing with VI and exiting VI?

---

### Post by slorkluk on 2010-05-18
> Are you saving the file you were editing with VI and exiting VI?
Well, I guess what the guide is telling me to do is edit the network/interface using vi, but it does not tell me how to exit vi.

Thoughts on how to exit vi so I can enter the command (/etc/init.d/networking restart) to restart my network?

---

### Post by maybeway36 on 2010-05-18
To exit vi, press Esc, then :, then wq (if you want to save the file) or q! (if you don't.)
I actually use nano to edit text files. The people who are good at vi will probably laugh at me.

---

### Post by slorkluk on 2010-05-19
> **maybeway36 said:**
> To exit vi, press Esc, then :, then wq (if you want to save the file) or q! (if you don't.)
I actually use nano to edit text files. The people who are good at vi will probably laugh at me.
Awesome, that worked!

After editing the interface, I had to type ":wq!" and it saved.

The only problem now is that when I try to run this command:
```
echo server1.example.com > /etc/hostname
/etc/init.d/hostname.sh start
```
I get this message after entering it:
```
-bash: /etc/hostname: Permission denied

```
I tried using the sudo command before it but I get the same error.

Any help on this?

---

### Post by slorkluk on 2010-05-19
bump

---

