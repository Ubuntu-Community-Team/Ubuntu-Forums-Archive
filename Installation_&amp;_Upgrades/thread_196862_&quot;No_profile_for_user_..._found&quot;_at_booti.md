---
title: "&quot;No profile for user ... found&quot; at booting."
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by laodan on 2006-06-14
Updated yesterday from Breezy 5.10 to Dapper 6.06 and got stuck in an xserver crashing at boot. Thanks to tseliot's sticky post Dealing with problems with the Xserver the problem was finally solved.

After solving this problem I had a very pleasent experience with Dapper for several hours. Restarting the computer this evening I got a mention about a home.drcm file that had to be owned by the user with 644 permissions and also the home folder.

First thing I did was to change the permissions on the drcm file and my home folder. After leaving the file manager, at each trial to do something, I got stuck with the mention: "permission denied". 

So I shut down the computer hoping that a restart would solve the problem. It did not. I got stuck in an even deeper problem.

Booting worked till I got a black screen with window saying:
[COLOR="Blue"]"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with the failsafe sessions to see if you can fix this problem.
(~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0.xservers" -h "" -l ":0" "laodan"
/etc/gdm/PreSession: Beginning session setup...
No profile for user 'laodan' found
(gnome-session: 4608 ): libgnomevfs-WARNING**: unable to create ~/.gnome directory: Permission denied
Could not create per-user gnome configuration directory '/home/laodan/.gnome2/': Permission denied.[/COLOR]

I clicked ok and got a window saying:
[COLOR="Blue"]The greeter application appears to be crashing
Attempting to use a different one.[/COLOR]
I clicked ok and got a window GNOME Desktop Manager. I Opened file and chose the failsafe terminal option. I inputed my username and then my password and got a window telling:
[COLOR="DarkRed"]To run a command as administrator (user "root", use "sudo <command>"
See "man sudo-root" for details.[/COLOR]
And then I got the command shell with:
laodan@ubuntu:/$

I tried the su command and got the same answer as in my xserver problem yesterday:
[COLOR="Blue"]CONFIGURATION ERROR - unknown item 'QUOTAS_ENAB' (notify administrator)
CONFIGURATION ERROR - unknown item 'NOLOGIN_STR' (notify administrator)
CONFIGURATION ERROR - unknown item 'ENV_HZ' (notify administrator)
CONFIGURATION ERROR - unknown item 'CHFN_AUTH' (notify administrator)
CONFIGURATION ERROR - unknown item 'CLOSE_SESSION' (notify administrator)[/COLOR]

Thinking that I was eventually having the xserver crashing problem again I repeated the instructions given by tseliot about xserver crash and after reboot landed again into the same problem described here-above: 
[COLOR="Blue"]"Your session only lasted less than 10 seconds... "[/COLOR]

Then I tried the startx command and got the following:
[COLOR="Blue"]xauth: timeout is locking authority file /home/laodan/.serverauth.5806
x: user not authorized to run the xserver, aborting.
rm: cannot remove '/home/laodan/.server auth.5806: Permission denied
Could not get a file descriptor referring to the console.[/COLOR]

It seems thus that my problem this June 14th is related to my changing the ownership of my home folder and the setting of its 644 permissions...

Does someone have an idea about what I should be doing to solve this particular problem?
Thanks in advance.

laodan

---

### Post by zxee on 2006-06-14
I have some notes to myself for the "session only lasted 10 seconds" error but the distro that I had and fixed this problem on is slack not ubuntu so try at your own risk. Seems like it should work though.
from the command line/shell cd /home  chmod 700 yourusername   
chown yourusername yourusername
chgrp yourusername yourusername
Hope that works for you.

---

### Post by laodan on 2006-06-14
Thanks zxee.
Command [COLOR="Blue"]/shell cd/home chmod 700 yourusername[/COLOR]
gives:
[COLOR="Blue"]bash: /shell: no such file or directory[/COLOR]

---

### Post by zxee on 2006-06-14
Ahhh, when I typed "yourusername" I meant that to mean replace yourusername with the name of your user. So if I was doing this and my user was zxee I would type chmod 700 zxee 
(after I had done cd /home) Personally I would do the commands one at a time.
1) cd /home
2) chmod 700 (put your user name here)
3) chown          "               "
4) chgrp           "                "
with numbers 3 and 4 the user name for the account you are trying to gain access to goes twice. I hope that's clearer.

---

### Post by laodan on 2006-06-14
Evidently, that's what I did...
command [COLOR="Blue"]/shell cd/home chmod 700 laodan[/COLOR]
gives:
[COLOR="Blue"]bash: /shell: no such file or directory[/COLOR]

Tried the [COLOR="Blue"]cd /home[/COLOR] command and got [COLOR="Blue"]sudo: cd /home: command not found[/COLOR]

---

### Post by zxee on 2006-06-14
[QUOTE=laodan]Evidently, that's what I did...
command [COLOR="Blue"]/shell cd/home chmod 700 laodan[/COLOR]
gives:
[COLOR="Blue"]bash: /shell: no such file or directory[/COLOR]

Tried the [COLOR="Blue"]cd /home[/COLOR] command and got [COLOR="Blue"]sudo: cd /home: command not found[/COLOR][/QUOTE]

Do you have a space between cd and /home?
try just cd /  (with a space after the cd)  
Can you cd  (Change Directories) on your system?
If the cd command isn't working maybe something is wrong with your path.
Or you don't have a /home/laodan directory anymore? Sorry this didn't work.
You could just create a new user and tranfer your files to the new user. 
sudo adduser laodan2

---

### Post by laodan on 2006-06-14
Yes I had a space between [COLOR="Blue"]cd[/COLOR] and [COLOR="Blue"]/home[/COLOR].

I tried the [COLOR="Blue"]echo $PATH[/COLOR] and got:
[COLOR="Blue"]/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/x11:/usr/9 ames[/COLOR]

Thanks for the follow-up.

---

### Post by zxee on 2006-06-14
I edited my previous post. BTW your path looks fine.
I don't know why you can't cd to /home
Maybe try ls -la /home that should show you the permissions and owner of /home.
Mine look like this:
zxee@juntu:~$ ls -la /home
total 12
drwxr-xr-x  3 root root 4096 2006-04-19 17:16 .
drwxr-xr-x 21 root root 4096 2006-04-19 15:54 ..
drwxr-xr-x 43 zxee zxee 4096 2006-06-14 19:26 zxee
zxee@juntu:~$
Or try creating a new user as I suggested in my edit of previous post.

---

### Post by laodan on 2006-06-14
Did the [COLOR="Blue"]sudo adduser laodan2[/COLOR]
It installed.
I rdid [COLOR="Blue"]sudo reboot[/COLOR]
and got again stuck in the initial problem as described in first post of this thread.
So I went through the same steps as indicated in that first post
...  got a window saying:
The greeter application appears to be crashing
Attempting to use a different one.
I clicked ok and got a window GNOME Desktop Manager. I Opened file and chose the failsafe terminal option. I inputed my username laodan2 and then my password and got the following:
[COLOR="Blue"]bash: /home/laodan/.bashrc: Permission denied[/COLOR]

As I understand it my problem has been that ubuntu did not accept my changing home directory owner to laodan (first post in this thread).  It seems indeed that the directory is still there but Ubuntu does not let me access it...

---

### Post by zxee on 2006-06-15
what is the output of: id

---

### Post by laodan on 2006-06-15
did [COLOR="Blue"]laodan@ubuntu:~$ ls -la /home[/COLOR]
and got:
[COLOR="Blue"]total 16
drwxrwxrwx   4 laodan laodan    4096   2006-06-14 .
drwxrwxr-x  24 laodan laodan    4096   2006-06-14 ..
drw-r--r--   59 laodan laodan    4096   2006-06-14 laodan
drwxr-xr-x    2 laodan2 laodan2 4096   2006-06-14 laodan2[/COLOR]

So it seems all the directories are still there but are the permissions set correctly?

Again thanks to follow my plight and hopefully also my recovery...

---

### Post by laodan on 2006-06-15
Did [COLOR="Blue"]laodan@ubuntu:~$ ls -la /home[/COLOR]
and got
[COLOR="Blue"]total 16
drwxrwxrwx    4  laodan laodan   4096  2006-06-14 .
drwxrwxr-x   24  laodan laodan    4096  2006-06-14 ..
drw-r--r--    59  laodan laodan    4096  2006-06-14 laodan
drwxr-xr-x     2  laodan2 laodan2 4096  2006-06-14 laodan2[/COLOR]

Seems everything is still there but what about the permissions?

Did also[COLOR="Blue"] id[/COLOR]
and go[COLOR="Blue"]t:
uid=0(root) grd=0(root) groups=0(root), 1000(laodan)[/COLOR]

Thanks again for showing me a way ahead...

---

### Post by zxee on 2006-06-15
Permissions don't look right on this: drw-r--r-- 59 laodan laodan 4096 2006-06-14 laodan
But that doesn't explain why you can't login to the new account you created. 
I think this problem may have something to do with the error: bash: /.bashrc: Permission denied but I don't know how to resolve it. Sorry let's see if anyone else can come up with something.

The output from id isn't right as far as I can tell. Mine looks like this:
zxee@juntu:~$ id
uid=1000(zxee) gid=1000(zxee) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(zxee)
There shouldn't be zeros for uid, groups and many entries are missing altogether.

---

### Post by laodan on 2006-06-15
I finally succeeded to enter the system under laodan2 but how do I now find root permission so as to go modify the permissions of [COLOR="Blue"]/home/laodan[/COLOR]?

in [COLOR="Blue"]/home/laodan[/COLOR] directory [COLOR="Red"]Owner has not the permission to execute[/COLOR] ... I don't know how I did to take away from myself the permission to execute my home forlder...

So my problem now is to go modify the permissions in the folder [COLOR="Blue"]/home/laodan[/COLOR] from within [COLOR="Blue"]/home/laodan2[/COLOR]. In other words how do I get root privilege in [COLOR="Blue"]/home/laodan2[/COLOR] ?

Does someone have an answer?
Thanks in advance

---

