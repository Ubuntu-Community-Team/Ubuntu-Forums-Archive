---
title: "installing from source in lucid"
date: 2010-01-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2010-01-24
hey guys I am on lucid and am somewhat a newbie at installation fom source.
I need the latest version of a program called tucan so I did 
 svn co [https://forja.rediris.es/svn/cusl3-tucan/trunk](https://forja.rediris.es/svn/cusl3-tucan/trunk)
 in terminal after installing svn
 now what is the next step I got the long list of output alongwith
Checked out revision 1396.
 now what to do?
 where are the files downloaded to? how to compile? please soemone help

---

### Post by VMC on 2010-01-24
You need to install **build-essential** tools, to start.

---

### Post by tgpraveen on 2010-01-24
ok some one told me to do 

cd trunk && sudo make install

and then i got 

mkdir -p /usr/local/bin/ /usr/local/share/tucan/ /usr/local/share/pixmaps/ /usr/local/share/man/man1/ /usr/local/share/applications/
install -p -m 0644 *.py /usr/local/share/tucan/
chmod 0755 /usr/local/share/tucan/tucan.py
cp -pR core/ /usr/local/share/tucan/
cp -pR default_plugins/ /usr/local/share/tucan/
cp -pR i18n/ /usr/local/share/tucan/
cp -pR media/ /usr/local/share/tucan/
cp -pR ui/ /usr/local/share/tucan/
install -p -m 0644 media/tucan.svg /usr/local/share/pixmaps/
install -p -m 0644 tucan.1.gz /usr/local/share/man/man1/
install -p -m 0644 tucan.desktop /usr/local/share/applications/
ln -sf /usr/local/share/tucan/tucan.py /usr/local/bin/tucan
praveen@praveen-desktop:~/trunk$ 

Now my questions are

next what do I do I mean how do I run it. I had earlier installed tucan from the repos so now is that version itself updated?
 can I run this latest version (from source) by using the applications menu icon of tucan

---

### Post by tgpraveen on 2010-01-24
ok some one told me to do 

cd trunk && sudo make install

and then i got 

mkdir -p /usr/local/bin/ /usr/local/share/tucan/ /usr/local/share/pixmaps/ /usr/local/share/man/man1/ /usr/local/share/applications/
install -p -m 0644 *.py /usr/local/share/tucan/
chmod 0755 /usr/local/share/tucan/tucan.py
cp -pR core/ /usr/local/share/tucan/
cp -pR default_plugins/ /usr/local/share/tucan/
cp -pR i18n/ /usr/local/share/tucan/
cp -pR media/ /usr/local/share/tucan/
cp -pR ui/ /usr/local/share/tucan/
install -p -m 0644 media/tucan.svg /usr/local/share/pixmaps/
install -p -m 0644 tucan.1.gz /usr/local/share/man/man1/
install -p -m 0644 tucan.desktop /usr/local/share/applications/
ln -sf /usr/local/share/tucan/tucan.py /usr/local/bin/tucan
praveen@praveen-desktop:~/trunk$ 

Now my questions are

next what do I do I mean how do I run it. I had earlier installed tucan from the repos so now is that version itself updated?
 can I run this latest version (from source) by using the applications menu icon of tucan

---

### Post by Starks on 2010-01-24
No, because you installed locally, you need to use "/usr/local/bin/tucan" or "~/trunk/tucan" in the terminal.

At least that's how I do things when I have a repo and self-compiled version on a single machine.

---

### Post by mc4man on 2010-01-24
> can I run this latest version (from source) by using the applications menu icon of tucan

There's no reason you can't - /usr/local/bin is in your path by default - from the looks of the svn filelist it installs a .desktop so the menu item should be good.

---

### Post by tgpraveen on 2010-01-25
@mc4man:

True it worked

Thanks for all the help people!

---

