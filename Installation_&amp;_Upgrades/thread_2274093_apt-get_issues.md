---
title: "apt-get issues"
date: 2015-04-17
forum: Installation &amp; Upgrades
---

### Post by Mike_Hughes on 2015-04-17
I issued the command sudo apt-get install proftpd. I get the following error message E: unable to locate package proftpd. Apparently it is looking on my CD for the package. How do I get apt-get to go out to the internet and get the packages?

---

### Post by Rex Bouwense on 2015-04-17
Make sure that you have checked Community-maintained free and open-source software (universe) under your Software & Updates.  Can you install it via the Synaptic Package Manager?

---

### Post by kc1di on 2015-04-17
try issuing the this command:```
sudo apt-get install proftpd-basic
```

---

### Post by Mike_Hughes on 2015-04-17
Here is what I get when I do that. 
Reading package lists . . . Done
Building dependency tree
Reading state information . . . Done
E: Unable to locate package prompted-basic

Dave looks like you are a Ham Operator. I am as well. N9GI Oh, I have no GUI on this install. It is all command line, Ugh! I also need to get Apache to start on each start up. I am also needing to configure Mailman as well. But first things first have to figure out this Bloody Apt-get issue.

[COLOR=#000000]Can you install it via the Synaptic Package Manager?

How do I do that? I don't have a GUI on this one.[/COLOR]

---

### Post by Bashing-om on 2015-04-17
Mike_Hughes; Hello:

As advised, make sure the universe repository is enabled - edit the file /etc/apt/sources.list .
That package does exost - release 14.04 is my reference:
```

apt-cache show proftpd-basic >>
Section: universe/net >>
Version: 1.3.5~rc3-2.1ubuntu2 >>
Filename: pool/universe/p/proftpd-dfsg/proftpd-basic_1.3.5~rc3-2.1ubuntu2_amd64.deb

```
If you need help adjusting your source.list file , let us know.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Mike_Hughes on 2015-04-17
I had my 32 bit system set up for 5 years until it crashed. So I haven't had to do much to it directly. When I edit the file using VI how do I get out of it and save my changes?

Here is what I got when I ran apt-cache show profited-basic

no talloc stack frame at ../source3/param/loadparm.c:4864, leaking memory
N:Unable to locate package prompted-basic
E: No package found

---

### Post by steeldriver on 2015-04-17
For vi, hit ESC to get out of insert mode, then

```

:wq

```

to **w**rite and **q**uit. You may find the nano editor easier to use.

What version of Ubuntu are you using?

---

### Post by Mike_Hughes on 2015-04-17
14.04

---

### Post by Keith_Helms on 2015-04-17
> **Mike_Hughes said:**
> Here is what I got when I ran apt-cache show profited-basic

no talloc stack frame at ../source3/param/loadparm.c:4864, leaking memory
N:Unable to locate package prompted-basic
E: No package found

Are you sure you're spelling the package name right?   The error you posted says "prompted-basic" not "proftpd-basic".

---

### Post by kc1di on 2015-04-18
> E: Unable to locate package prompted-basic
Yes I'm a ham and glad to meet another ham on here :) 
The command is **proftpd-basic** not prompted-basic give it a try again :) 
73

---

### Post by Mike_Hughes on 2015-04-18
After dinking around with this bloody install for 4 hours + with this issue.i wonder if something misfired on the install? So I think what I will do, hold your ears for a moment, is to take theology trust HD clone by Mira Software and restore a Windoze 8 install on it to blow away the current install and reinstall. Now question, I know I am full of them but here goes. I am setting this up as a Web Hosting server and a mailman box, with that said do I need to install Samba or just install the LAMP service? As always all help highly appreciated. Cheerio!

Ok I came home. I restored a Windows install on to the machine to clear out the previous Server Install. I then ran Windows to make sure it was running no issues. I then put in my Ubuntu Server 14.04 64 bit CD and did another install. Wasn't sure on all the questions but tried my best. The only issue I had crop up and don't understand why was when it came to installing the network interface. It said it couldn't use DHCP so I installed manually. I went into my DHCP reservation table and the Computer shows up in the table with the correct Mac address. When the install finished and booted I ran Sudo apt-get install Webmin to see what I would get. Well the same issue comes up Reading package lists ... Done. Building Dependency tree, Reading state information . . . Done then I get the line E: Unable to locate package webmin.  It is like it isn't going out to the internet to the repositories to get the program. Is there a way I can specify it go out to webmin to get the download. I am still puzzled on how to fix this issue. I thought reinstalling it would solve the problem. Another question. I have my router set on Static IP because I have a static IP coming in for the Web Server That shouldn't affect my router handing out addresses?

---

### Post by kc1di on 2015-04-18
does it do a```
sudo apt-get update
``` OK? if not what error message do you get?

---

### Post by steeldriver on 2015-04-18
It sounds like you have basic network connectivity issues - if you want help with those, I suggest starting by posting the following information:


[LIST=1]
[*]the contents of your /etc/network/interfaces file ([FONT=courier new]cat /etc/network/interfaces[/FONT]) 
[*]the contents of your /etc/resolv.conf file ([FONT=courier new]cat /etc/resolv.conf[/FONT]) 
[*]the outputs of the following commands 
[/LIST]
 ```

lspci -vnn | grep '\[02.0\]'

ifconfig

ip route list

ping -c4 8.8.4.4

ping -c4 google.com

```

---

### Post by Mike_Hughes on 2015-04-18
I did some google search and found out I had to modify my sources.list and do apt-get updates. Once I did that I was able to get Web-min installed. I have not been able to get it to work through another router though. On install I didn't have any name servers to put in. I am thinking that refers to DNS but wasn't sure. So need to figure out how to get a couple more DNS in the box.
I know the fun part now is setting up the Apache Server and the Mailman Server. I haven't set one of those up in 5 years. Had it going on the 32 bit machine but it crashed so have to configure all of this from scratch. I know VmHost, Sites-Available and Sites-Enabled come into play some how. Now Where is that Apache Cookbook when I need it.

---

