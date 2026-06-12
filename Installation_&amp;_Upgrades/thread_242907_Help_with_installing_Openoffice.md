---
title: "Help with installing Openoffice"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by HEN*K on 2006-08-24
HI!

I've just recently started to use Ubuntu, and I am having problems with an installation.

The program I am trying to install is Openoffice and I've followed a six-step guide. However, the last step is not working so I'm wondering if there might be some typo or another error in the command I'm supposed to use.

The guide looks like this:
   1.  Unpack the downloaded image into a directory. For example, currently, the following command would unpack into the current directory:
   2. tar xvzf OOo_2.0.3_LinuxIntel_install.tar.gz
   3. su to root, if necessary.
   4. cd into the directory with the unpacked image. This could be RPMS.
   5. Delete any rpm files that do not apply to your system. For example, on a Fedora Core 3 system, delete any rpms specific to another distribution such as openofficeorg-suse-menus-1.9.79-1.noarch.rpm.
   6. Then execute rpm -Uvih *rpm.

The last step (Then execute rpm -Uvih *rpm.) is not working and I don't know enough about Linux to know what to do.

I get this message when I try:
sudo: illegal option `-U'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

I have followed the guide exactly as it says up to that step.

I would be happy if anyone could help me.

Thank's!
/Henke

---

### Post by tseliot on 2006-08-24
Ubuntu uses deb packages instead of rpm .

Why don't you use openoffice in the repos?

You could try converting the rpm packages into deb but, as many users reported, openoffice won't work.

---

### Post by Selbstmord on 2006-08-24
Me and HEN*K have the same problem; Openoffice is nowhere to be found in the repos...

However, I don't think we have all the universe and multiverse repos... I can't bother looking, so if someone could guide us to a repo/repos that DOES supply OO, we would be very very grateful...

---

### Post by HanZo on 2006-08-24
ehm... Openoffice is installed by default when installing the OS... what kind of install did you make? a server install?
and anyway Openoffice is in the main repositories that are enabled by default in synaptic.

---

### Post by HEN*K on 2006-08-24
All I can find is something called "OpenOffice.org From Template". If I open it, I come to some sort of start up window in wich I'm supposed to be able to open an empty document but I can't.

Are there any other programs similar to Open Office that I can use? It doesn't have to be very exclusive, I just have to be able to write essays and  stuff for school.

---

### Post by Scythe!? on 2006-08-24
I think Abiword can do it for you, but I've never used it.

---

### Post by Selbstmord on 2006-08-24
> **HanZo said:**
> ehm... Openoffice is installed by default when installing the OS... what kind of install did you make? a server install?
and anyway Openoffice is in the main repositories that are enabled by default in synaptic.

No and no.
Can't find any Openoffice from the main repos, and I did a regular install, and no Openoffice... We both used the cds supplied through ShipIt.

---

### Post by HanZo on 2006-08-25
that's very strange... by default you should have these entries in the menu (I use USP instead of the standard panle menu but it's just a different representation)
[[IMG]http://img208.imageshack.us/img208/918/screenshotyt4.th.png[/IMG]](http://img208.imageshack.us/my.php?image=screenshotyt4.png)
when searching synaptic you should get a lot of entries like this:
[[IMG]http://img219.imageshack.us/img219/6376/screenshot1zr5.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshot1zr5.png)
openoffice, as I sayd is in the official repos that are enabled by default so I really don't know what could have happened... maybe you should try to download a new cd from the net and install that... or, as somebody sayd try Abiword...

---

### Post by HEN*K on 2006-08-25
Thanks for all your help poeple. I've managed to get it working now and I am very happy. Now I can use Open Office and I will be able to write my essays and home work for school...

So, thanks again! I hope I havn't been bothering you too much...

Have a nice weekend
/Henke

---

### Post by HanZo on 2006-08-25
hehe don't worry... that's the purose of the forum to help one another... nice weekend to you to!

---

