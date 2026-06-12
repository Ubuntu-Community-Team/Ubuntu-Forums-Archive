---
title: "Unable to Install Xubuntu 13.10, SiS 650 Graphic Card"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by d4rios on 2014-04-07
Hello, I start saying I'm a newbie in the Ubuntu/Linux world. 

I'd like to get rid of Windows XP and install Xubuntu to be able to use my 2004 desktop again (Intel Celeron 2.6GHz, 991MB RAM, SiS 650 Graphic Card).
I downloaded, burned the Xubuntu 13.10 iso on a DVD (I cannot boot from USB) and verified its integrity. Every time I boot it, it loads the screen where i can set some options (language etc.), but whenever i launch the live or the installation process, after some loading showing the Xubuntu logo, the screen goes black, then i can see and move a mouse cursor, then black screen, then cursor again and so on, the process gets stuck on this loop.
I searched the forum, tried the nomodeset option, acpi, i can access the terminal typing ctrl-alt-F4, but the problem is still there.
I guess this is due to my video card and my monitor trying to set the resolution (I have an LG LCD HDTV connected on VGA).

Any help on solving this problem would be really appreciated! :)

---

### Post by mörgæs on 2014-04-07
Hi, welcome to the fora.
You have SIS graphics, which gives some problems for 13.10. 14.04 (beta) installs without modifications.

The commads 
```
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get dist-upgrade
```
should do the trick for 13.10.

More info in the link in my signature.

---

### Post by d4rios on 2014-04-07
Ok, thanks! I'll try the 14.04. Is Xubuntu a good choice for my hardware?

---

### Post by mörgæs on 2014-04-07
Since you have a semi-working 13.10 I recommend that you just try the three commands in a terminal. Easier than a fresh install.

Xubuntu is a little heavier than Lubuntu. Try both of them and see which you like more.

---

### Post by d4rios on 2014-04-07
I tried the commands while installing Xubuntu 13.10, it downloaded and upgraded about 250MB of packages, but afterwards the problem was still there.
I tried booting a DVD with 14.04, but nothing has changed... what else should I do?

---

### Post by mörgæs on 2014-04-07
Please post the results from
```
lspci | grep -i vga
```

---

### Post by d4rios on 2014-04-07
> **mörgæs said:**
> Please post the results from
```
lspci | grep -i vga
```

This is what i get:

01:00.0 [COLOR=#ff0000]**VGA **[/COLOR]compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP [COLOR=#ff0000]**VGA **[/COLOR]Display Adapter

---

### Post by mörgæs on 2014-04-07
Strange... did everything look fine when you gave the three commands?
Did you reboot afterwards?
What happens in a live boot of Lubuntu 14.04 from CD (not DVD)? The ISO file must be the latest, and old one does not work.

---

### Post by d4rios on 2014-04-07
I gave the 3 commands after selecting "Install Xubuntu" from the 13.10 DVD. First 2 are ok. 
When upgrading the distro, I get several errors in the end, related to a "no space left on device".
Last 2 lines shown on terminal are:
[I]O: No space left on device
E: Subprocess /usr/bin/dpkg returned an error code (2)[/I]

Should I get 13.10 or 14.04 (Daily Build) Lubuntu?

---

### Post by Bashing-om on 2014-04-07
d4rios; Hello.

This:
> 
Last 2 lines shown on terminal are:
O: No space left on device

Says there are other problems.
Post back the output of terminal commands:
```

df -h
df -i

``` to give an idea of where the space is being taken up, and point us in a direction for corrective action.
Get that taken care of and at that time one can look at the SIS graphic's issue.

[INDENT][INDENT]where there are solutions 
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by d4rios on 2014-04-07
hello bashing-om! 
On morgaes' advice (many thanks man!) I installed Lubuntu 14.04 without particular problems, so I guess I'm not going to try Xubuntu on this machine for the moment :( . [[COLOR=#C61919]****[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")

---

### Post by Bashing-om on 2014-04-07
d4rios; Hey outstanding !

Our developers are working wonders !

Please keep us informed .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by mörgæs on 2014-04-07
You're welcome. 
Please mark the thread 'solved'.

---

