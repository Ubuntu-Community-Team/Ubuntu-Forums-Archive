---
title: "Problems with adding printer"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by Promethe on 2005-10-30
Weird.
A few hours ago it was working. I was able to look throught printers in network. But suddenly - it stopped working. And doesn't want to run again.
At first - I wanted to add new printer. So I opened printer manager, and clicked "Add printer". Second later, a got beautiful window saying:
> The Application "gnome-cups-add" has quit unexpectedly.
Which looked exactly like this:
[[IMG]http://img415.imageshack.us/img415/9767/screenshot7ch.th.png[/IMG]](http://img415.imageshack.us/my.php?image=screenshot7ch.png)
So I fired up Terminal and typed
> gnome-cups-add
I've got "Matrix feeling" thru a few seconds looking at running down list of errors. It looked like this:
```
promethe@ubuntu:~$ sudo gnome-cups-add

** (gnome-cups-add:11797): WARNING **: IPP request failed with status 1030
** (gnome-cups-add:11946): WARNING **: model named 'HP Color LaserJet 4500 v2014.200 Postscript (recommended)' doesn't have a recognized structure

** (gnome-cups-add:11946): WARNING **: model named 'HP Color LaserJet 4500 v2014.200 Postscript (recommended)' doesn't have a recognized structure

** (gnome-cups-add:11946): WARNING **: Two ppds have driver == 'Standard (CUPS)'
        ->hplip/HP_Color_LaserJet_4500.ppd (HP Color LaserJet 4500 v2014.200 Postscript[1]) and
        ->foomatic-ppds/hplip/HP_Color_LaserJet_4500.ppd (HP Color LaserJet 4500 v2014.200 Postscript)[1]

** (gnome-cups-add:11946): WARNING **: Two ppds have driver == 'hpijs'
        ->hplip/HP-Color_LaserJet_4550-hpijs.ppd (HP Color LaserJet 4550 Foomatic/hpijs[0]) and
        ->foomatic-ppds/hplip/HP-Color_LaserJet_4550-hpijs.ppd (HP Color LaserJet 4550 Foomatic/hpijs)[0]

** (gnome-cups-add:11946): WARNING **: model named 'HP Color LaserJet 4550 v3010.107 Postscript (recommended)' doesn't have a recognized structure

** (gnome-cups-add:11946): WARNING **: model named 'HP Color LaserJet 4550 v3010.107 Postscript (recommended)' doesn't have a recognized structure

--------------- cuted out, the same error but models another ---------------

** (gnome-cups-add:11963): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs)[1]

** (gnome-cups-add:11963): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs)[1]
```

And the known window came at least. With the very same bug as posted above - that it "quited unexpectly".
Great. I've got a 75-page work in TeX to print right now... And printing it to PDF and sending to another machine isn't solution for me.
Anyone wants help me? Please...
Restarting cups, reinstalling drivers - it didn't help.
Any help apprieciated.
./promethe

---

### Post by kairu0 on 2005-10-31
Maybe it would work if you installed your printer via the CUPS web interface.

1. Edit /etc/cups/cupsd.conf for editing and change "RunAsUser Yes" to "RunAsUser No"
2. Access it through [http://localhost:631](http://localhost:631) in your web browser

---

### Post by s|k on 2006-03-07
This worked for me, I can now print, my printing manager still doesn't work though and I can't print a test page, but I can print anything else.

---

