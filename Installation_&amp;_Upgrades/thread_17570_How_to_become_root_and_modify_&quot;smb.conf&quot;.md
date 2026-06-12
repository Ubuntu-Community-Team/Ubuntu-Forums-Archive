---
title: "How to become root and modify &quot;smb.conf&quot;"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by joplass on 2005-03-01
Hello to everyone,
I am not particularly new to Linux but I am not an advanced user either.  Thank you to those who developed such a nice distro.  Its look is simply amazing.
Sorry about the tirade and I know I have to get to my question.

1/ I don't know how to become root
2/ The purpose at this point is for me to modify the "smb.conf" file.  While in /etc I went to tools opened up a terminal but that did not get me anywhere.

I will appreciate some help.

Thanks to all,

---

### Post by p!=f on 2005-03-01
[QUOTE=joplass]Hello to everyone,
I am not particularly new to Linux but I am not an advanced user either.  Thank you to those who developed such a nice distro.  Its look is simply amazing.
Sorry about the tirade and I know I have to get to my question.

1/ I don't know how to become root
2/ The purpose at this point is for me to modify the "smb.conf" file.  While in /etc I went to tools opened up a terminal but that did not get me anywhere.

I will appreciate some help.

Thanks to all,[/QUOTE]
By default, Ubuntu does not use root account. Its password is disabled.
Sudo is all you might want to use. So if you want to edit smb.conf file:
```

sudo gedit /etc/samba/smb.conf

```
(replace gedit with your favorite editor)
If you want to use root anyway, just run
```

sudo passwd

```
If you want to get root prompt without enabling its password run
```

 * 16:47:18 * pef @ agonicus *
[~] > sudo -s

 * 16:47:41 * root @ agonicus *
[~] >

```

Hope it helps.

---

### Post by rmjokers on 2005-03-01
There is no root user in Ubuntu by default.  However, you can use "sudo" to get priviledged access.  For instance, in the terminal, you could run the command:

sudo vim /etc/samba/smb.conf

or

sudo gedit /etc/samb/smb.conf

To edit the file you mentioned.  The first user you created when you installed Ubuntu should be able to use sudo.  If you want to do this as another user, you may have to make them a sudoer manually.

---

### Post by joplass on 2005-03-01
Thank you for the quick reply it worked fine.  While I was changing samba I was also updating firefox and I forgot the Ubuntu disc in the cd drive as a consequence I am unable to log on to Ubuntu.

I get this message:

"Your session only lasted less than 10 minutes.  If you have not log out yourself, this could mean that there is some installation problem or that you maybe out of diskspace.  Try logging in with one the failsafe sessions to see if you can fix this problem"

I have the option to see the error as:
"View details (~/.xsession-errors file)"

I selecet to view the error and it reads:
"/etc/gdm/PreSession/Default: Registring your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/Lib/gdm/: 0 Xservers" -h "" -l ":0" "job
/etc/gdm/Xsession: beginning session setup...

** (gnome-session: 3775): WARNING **: Unable to read ICE authority file : /home/job/. ICEauthority"

Completely lost guys.
I tried going to failsafe, I got the same result.
Sorry about the headache.
I know I could re-install but I stayed up late last night to have my box running.

---

### Post by joplass on 2005-03-01
Ok re-install is due.  I learned my lesson: Don't ever leave installation cd in the box  :confused:  :confused:  :confused:

---

### Post by penvzila on 2005-05-26
[QUOTE=joplass]Ok re-install is due.  I learned my lesson: Don't ever leave installation cd in the box  :confused:  :confused:  :confused:[/QUOTE]
Not really... you can either change the permissions of .ICEauthority back so you own it, or rm it altogether.  It took me a long time to learn, but reinstalling is rarely necessary with GNU/Linux.

---

