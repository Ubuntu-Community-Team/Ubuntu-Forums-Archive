---
title: "DPKG wont start"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by redserpent7 on 2008-05-16
I have done some updates last night as was suggested by the updates manager. Everything went well and then I decided to shut down my computer. 

As I started Ubuntu today... it starts normally, then I tried to install an application using the Synaptic Package Manager. Synaptic shows an error message [HTML]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/HTML]

So I tried to run that in terminal and it showed the following error:
 [HTML]dpkg: parse error, in file `/var/lib/dpkg/updates/0004' near line 1:
 newline in field name `#padding'
[/HTML]

I have located that file and opened it in a text editor and it shows a list of "#padding" just that no other codes are there. I'm guessing that this happened as I updated my OS, maybe a broken package or something. I really don't remember the updated apps.... please tell me how to fix this as I'm clueless..

---

### Post by Pumalite on 2008-05-16
Post the output of:
sudo apt-get -f install

---

### Post by Oldsoldier2003 on 2008-05-16
> **redserpent7 said:**
> I have done some updates last night as was suggested by the updates manager. Everything went well and then I decided to shut down my computer. 

As I started Ubuntu today... it starts normally, then I tried to install an application using the Synaptic Package Manager. Synaptic shows an error message [HTML]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/HTML]

So I tried to run that in terminal and it showed the following error:
 [HTML]dpkg: parse error, in file `/var/lib/dpkg/updates/0004' near line 1:
 newline in field name `#padding'
[/HTML]

I have located that file and opened it in a text editor and it shows a list of "#padding" just that no other codes are there. I'm guessing that this happened as I updated my OS, maybe a broken package or something. I really don't remember the updated apps.... please tell me how to fix this as I'm clueless..

the correct command is ```
sudo dpkg --configure -a
``` the error message assumes you are running as root so it doesn't tell you to sudo. if you did sudo then ```
sudo apt-get install -f
sudo apt-get-update
``` then run ```
sudo apt-get upgrade
``` and see it it errors.

---

### Post by redserpent7 on 2008-05-16
Actually I kinda fixed that error just now:

> sudo rm /var/lib/dpkg/updates/0004 

I don't know if this is the right fix but as I can see it, that file was useless so I decided to remove it and it worked. Don't really know why I haven't thought of that earlier but it hit my head... 

Anyways thanks for the replies, I really appreciate it.

---

