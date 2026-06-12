---
title: "can't talk"
date: 2021-01-18
forum: Installation &amp; Upgrades
---

### Post by josephfg on 2021-01-18
I am running ubuntu server on my laptop and had a network but with the fossa upgrade it was lost.  Now I have ubuntu studio on my file server but it is disco.  Can I ever get these two to talk? Thanks in advance.

---

### Post by TheFu on 2021-01-18
what do you mean by "talk".
ssh,scp,sftp,rsync all work perfectly here. Use sftp://<ip>/ in the file manager to connect between any systems running openssh-server.  If you have DNS or static IPs setup for each system in the dhcp settings for your router, ip addresses won't move. Most modern dhcp servers support this - called "dhcp reservations"

---

### Post by tea for one on 2021-01-18
> **josephfg said:**
> I am running ubuntu server on my laptop and had a network but with the fossa upgrade it was lost.  Now I have ubuntu studio on my file server but it is disco.  Can I ever get these two to talk? Thanks in advance.

Ubuntu Disco Dingo reached End of Life in January 2020. You should install a current version.

---

### Post by josephfg on 2021-01-18
I mean to see the files on my lenovo (file server) from my hp laptop.
I'll be accessing this forum on the HP.

I don't know networking protocols much.

---

### Post by TheFu on 2021-01-18
Well, you should be using ssh, sftp, scp, rsync, sshfs, x2go, ....  as the protocols between different Unix/Linux systems.
On all the systems, run this:
```
sudo apt install ssh fail2ban
```
After doing that, almost all Linux file managers will accept *sftp://{insert-IP-address}/* in the URL to connect to a different system. Pretty easy and fast.  Sorta ... just works.  fail2ban prevents brute force attacks.

I use caja on my 20.04 desktop (that's the default Mate desktop file manager).  Because I have a DNS server and my internal LAN uses static IPs for all systems (or DHCP reservations), I can use **sftp://istar/** to connect to my other system named istar.  I could use the IP address for it, but that's what DNS is for - so I don't have to know it.

Once you have ssh installed (that is a meta-package for both the ssh-client and the ssh-server), there are about 50 other tools that work for connecting Unix-to-Unix systems.
> ssh is enough for

[LIST]
[*]    secure remote access to files via sftp
[*]    secure remote filesystem access via sshfs
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    securely run applications on a different machine, but display the window locally
[*]    secure remote desktops via x2go/freenx
[*]    secure remote file replication with rsync (ssh is the default rsync protocol)
[*]    secure port forwarding of selected ports
[*]    secure remote editing with vim/gvim and other editors
[*]    pseudo-VPN with sshuttle
[/LIST]

[http://diogomelo.net/blog/10/ssh-tricks](http://diogomelo.net/blog/10/ssh-tricks) for people completely new to ssh wonders.
[http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) as you learn more.

ssh has been used since the mid-1990s. It is the only system-to-system connection tool that I know which is both more secure AND more convenient once keys have been setup for key-based authentication. This authentication is valid for any ssh-based connection. Imagine being asked for a password only once a day (or every 12 hours) to unlock the ssh-key, but then have full access to a different system.  The system can be on your LAN or halfway around the world.  ssh is how a single Unix/Linux admin can manage thousands of servers spread around the world. There are millions of these servers being managed by a relatively few people.

In the time you've spent already, you could have installed and been using key-based authentication between both your systems.  When you know what you are doing, it is about 60 seconds of effort to install and configure ssh-keys.  Plus, Windows supports ssh and sftp for about 2-3 yrs (Win10). Don't know why it took them so long.

I've provided steps to setup ssh-keys and transfer those keys in these forums a number of times.
[https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
[https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278)

Of course, there are thousands of different protocols. If you weren't using laptops, I'd suggest some others like NFS. But NFS needs a system that doesn't move. Isn't powered off and stays at the same location on the network. That isn't a typical laptop purpose. But NFS is the native way for Unix systems to share storage. 99.95% of the time, the NFS-client system doesn't know that the storage is actually from another system. All problems (cough .... almost all), work perfectly using NFS storage. NFS performance is excellent when the wired network connecting the clients and server are excellent.

"Talking" can mean by a number of other things like DLNA, XMPP, IRC, video streaming using webcams ... thousands of methods.  But nobody can help if you aren't clear on what you hope to see "talk" between these systems.

---

### Post by josephfg on 2021-01-19
ok, where can I get ubuntu studio for a stick drive in the latest release?

---

### Post by CelticWarrior on 2021-01-19
[https://ubuntustudio.org/download/](https://ubuntustudio.org/download/)

---

### Post by josephfg on 2021-01-19
udisks-error
quark, 11

when I try to format my cruzer stick

---

### Post by TheFu on 2021-01-19
> **josephfg said:**
> when I try to format my cruzer stick

Maybe you should start a different thread so other experts in whatever the new issue is can help? Be clear. Don't assume anyone knows what you are trying to accomplish.

Unless formatting a cruzer stick (whatever that is) is somehow related to "can't talk"?

Different people here have different knowledge. _Use a good thread title_ to get the people you want help from to look deeper.

---

### Post by josephfg on 2021-01-19
update: I disabled remote administration in the BIOS on my file server.
Seems like a half-way point.

the message you referenced was directly related to the one just above, the error message I got.

quark, 11

working on it. . .

---

### Post by yancek on 2021-01-19
What is on the usb?  If nothing on it, what was on it?  I'd start by rewriting the partition table, don't know if you know how to do that but it's fairly simple with GParted.  Obviously this will destroy all data on the usb but that would happen anyway when you write Ubuntu to the usb. 

>  Unless formatting a cruzer stick (whatever that is) 

Sandisk Cruzer.

---

### Post by josephfg on 2021-01-20
yes, thanks. I have this issue almost licked.  Will keep updating until done.

yes I know this

I am now downloading the image direct to my stick. Should work!

failed once. uh-oh!

fails with 18s left!

---

### Post by CelticWarrior on 2021-01-20
> [COLOR=#000000]I am now downloading the image direct to my stick. Should work![/COLOR]

No, it definitely shouldn't. You need some tool to extract and write the ISO (AKA "burn") onto the USB stick in order to have a bootable drive.

---

### Post by josephfg on 2021-01-20
ok, update: working on getting my lenovo internet ready then gonna d/l the new studio for it.  Should work.

> **CelticWarrior said:**
> No, it definitely shouldn't. You need some tool to extract and write the ISO (AKA "burn") onto the USB stick in order to have a bootable drive.

Thank you.  I will google the procedure.

> **tea for one said:**
> Ubuntu Disco Dingo reached End of Life in January 2020. You should install a current version.

I am attempting to do just that.

---

### Post by josephfg on 2021-01-21
ok, I installed Termius, cross-platform ssh client.

---

### Post by TheFu on 2021-01-21
> **josephfg said:**
> ok, I installed Termius, cross-platform ssh client.

Why?

---

