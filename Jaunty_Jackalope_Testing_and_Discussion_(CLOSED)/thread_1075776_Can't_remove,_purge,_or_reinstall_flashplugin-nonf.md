---
title: "Can't remove, purge, or reinstall flashplugin-nonfree"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DPic on 2009-02-20
Everytime, this is what i get: 
```
Setting up flashplugin-nonfree (10.0.15.3ubuntu3) ...
cd: 135: can't cd to /var/cache/flashplugin-nonfree
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by DPic on 2009-02-20
I noticed the lind "cd: 135: can't cd to /var/cache/flashplugin-nonfree"
and went to find that the directory/file doesn't exist. Anyone know what i should do?

---

### Post by ugkbunb on 2009-02-20
> **DPic said:**
> I noticed the lind "cd: 135: can't cd to /var/cache/flashplugin-nonfree"
and went to find that the directory/file doesn't exist. Anyone know what i should do?

a complete longshot... but perhaps create the directory and see where it hangsup next.

isn't there a fix-broken option in aptitude? 

again just guesses... sorry i couldnt be of more help

---

### Post by DPic on 2009-02-20
Well, after creating that folder, i get a little bit further...

```
Setting up flashplugin-nonfree (10.0.15.3ubuntu3) ...
Downloading...
--2009-02-20 17:56:48--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.15.3.orig.tar.gz
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3935267 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.15.3.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1%  140K 27s
    50K .......... .......... .......... .......... ..........  2%  509K 17s
[...]
  3750K .......... .......... .......... .......... .......... 98%  476K 0s
  3800K .......... .......... .......... .......... ...       100%  465K=11s

2009-02-20 17:57:03 (362 KB/s) - `./adobe-flashplugin_10.0.15.3.orig.tar.gz' saved [3935267/3935267]

Download done.
Flash Plugin installed.
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The file "/var/lib/dpkg/alternatives/iceape-flashplugin" is empty. Any ideas on what to do now?

---

### Post by DPic on 2009-02-20
Apparently, this also affects mozilla-plugin-gnash

```
Removing flashplugin-nonfree ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for priority ()
dpkg: error processing flashplugin-nonfree (--purge):
 subprocess pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing mozilla-plugin-gnash ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for priority ()
dpkg: error processing mozilla-plugin-gnash (--purge):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by DPic on 2009-02-20
I also tried "sudo dpkg --force-uninstall-reinstreq flashplugin-nonfree" but it has the same problem

---

### Post by RIchard James13 on 2009-02-20
I bleieve the fix command is
```
sudo apt-get -f install
```

However that does not always work

You can remove a package using DPKG like this
```
sudo dpkg -r flashplugin-nonfree
```

you might want to create the file it is trying to read as well
try using touch
> sudo touch /var/lib/dpkg/alternatives/iceape-flashplugin

That will create a zero length file.

If it keeps complaining about EOF then try opening the file with an editor and put a space in it.

---

### Post by jerrylamos on 2009-02-20
I install flashplugin-nonfree in jaunty by:

sudo cp -v libflashplayer.so /usr/lib/mozilla/plugins

If you want to remove it, just delete it.

The .so I'm using lately is:

2008-11-18 18:53 libflashplayer.so

which I probably got from doing a jaunty install, selecting youtube.com which then said I should install flashplayer which I did.  I then saved the .so in a shared directory.  Since then I just do the copy of the .so to do an install.  Very quick....

Jerry

---

### Post by DPic on 2009-02-20
> **RIchard James13 said:**
> I bleieve the fix command is
```
sudo apt-get -f install
```

However that does not always work

Nope, tried that. 

> **RIchard James13 said:**
> You can remove a package using DPKG like this
```
sudo dpkg -r flashplugin-nonfree
```

Nope, tried that too. 

> **RIchard James13 said:**
> you might want to create the file it is trying to read as well
try using touch


That will create a zero length file.

If it keeps complaining about EOF then try opening the file with an editor and put a space in it.

/var/cache/flashplugin-nonfree was the folder that didn't exist, but after i created it an error talking about the file /var/lib/dpkg/alternatives/iceape-flashplugin which already existed. It was empty so i tried copying the contents of the same file from a working machine with flash but the error did not change.

---

### Post by RIchard James13 on 2009-02-20
Ok if I install the mozilla-plugin-gnash it creates the file iceape-flashplugin in the alternatives directory

The contents are
```
auto
/usr/lib/iceape/plugins/flashplugin-alternative.so

/usr/lib/gnash/libgnashplugin.so
50

```

Neither of those files are needed on my system to remove mozilla-plugin-gnash. I can delete them and it uninstalls fine.

Maybe it is not that file.

in the pre remove script for that package it says
```
#!/bin/sh

set -e

case "$1" in
        remove|upgrade|deconfigure)
                for p in iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons; do 
                       update-alternatives --remove "$p-flashplugin" /usr/lib/gnash/libgnashplugin.so;
                        [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
                                update-alternatives --remove-all "$p-flashplugin"
                done
                ;;
        failed-upgrade)
		if dpkg --compare-versions "$2" ">>"  0.8.1~trunk.070802-0ubuntu3 &&
	           dpkg --compare-versions "$2" "<<" 0.8.1~trunk.070802-0ubuntu5
		then 
		   for p in iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons; do 
                        update-alternatives --remove "$p-flashplugin" /usr/lib/gnash/libgnashplugin.so;
                        [ `update-alternatives --list "$p-flashplugin" | wc -l` = 0 ]  && \
                                update-alternatives --remove-all "$p-flashplugin"
		   done
		else 		
		  echo "prerm called with argument \`$1'" >&2
                  exit 1
		fi                
		;;
        *)
                echo "prerm called with unknown argument \`$1'" >&2
                exit 1
                ;;
esac



exit 0
```
[I]
update-alternatives creates, removes, maintains and displays information about the symbolic links comprising the Debian alternatives system.

       It  is  possible for several programs fulfilling the same or similar functions to be installed on a single system at the same time.  For example, many systems have sev&#8208;
       eral text editors installed at once.  This gives choice to the users of a system, allowing each to use a different editor, if desired, but makes it difficult for a pro&#8208;
       gram to make a good choice for an editor to invoke if the user has not specified a particular preference.

       Debian’s alternatives system aims to solve this problem.  A generic name in the filesystem is shared by all files providing interchangeable functionality.  The alterna&#8208;
       tives system and the system administrator together determine which actual file is referenced by this generic name.  For example, if the text editors  ed(1)  and  nvi(1)
       are  both installed on the system, the alternatives system will cause the generic name /usr/bin/editor to refer to /usr/bin/nvi by default. The system administrator can
       override this and cause it to refer to /usr/bin/ed instead, and the alternatives system will not alter this setting until explicitly requested to do so.
[/I]

It loops through the alternatives names for flash plugins
iceape-flashplugin 
iceweasel-flashplugin 
mozilla-flashplugin 
firefox-flashplugin 
xulrunner-flashplugin 
midbrowser-flashplugin 
xulrunner-addons-flashplugin

running them through the program update-alternatives and removing the links to /usr/lib/gnash/libgnashplugin.so

Then it checks if each of the lists of alternatives is empty (there is no flash plugin) and removes the lists

try typing at the command line
```
sudo update-alternatives --display iceape-flashplugin
```

for each one of these listed in the pre remove file. And see if it generates an error.

Check in /etc/alternatives the file may be missing.

Another alternative is to delete the pre remove file and get another copy. 

The file is in
```
/var/lib/dpkg/info/mozilla-plugin-gnash.prerm
```

---

### Post by DPic on 2009-02-20
> **RIchard James13 said:**
> try typing at the command line
```
sudo update-alternatives --display iceape-flashplugin
```

for each one of these listed in the pre remove file. And see if it generates an error.

I get this: 
```
:~$ sudo update-alternatives --display iceape-flashplugin
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for priority ()
```

---

### Post by RIchard James13 on 2009-02-20
What does the command 
```
ls -l /etc/alternatives/*flash*
```
display?

---

### Post by RIchard James13 on 2009-02-20
I can now replicate the error

If I truncate the 
```
/var/lib/dpkg/alternatives/iceape-flashplugin
```
file then I get

```
$ sudo update-alternatives --display iceape-flashplugin
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()

```

Editing the file and adding in the lines
```
auto
/usr/lib/iceape/plugins/flashplugin-alternative.so

/usr/lib/gnash/libgnashplugin.so
50
```

Does not work it still gives the error message.

Copying one of the other flashplugin files over the top gives the right result.

```
$ sudo cp iceweasel-flashplugin iceape-flashplugin
```

```
$ sudo update-alternatives --display iceape-flashplugin
iceape-flashplugin - status is auto.
 link currently points to /usr/lib/gnash/libgnashplugin.so
/usr/lib/gnash/libgnashplugin.so - priority 50
Current `best' version is /usr/lib/gnash/libgnashplugin.so.

```

---

### Post by DPic on 2009-02-20
> **RIchard James13 said:**
> What does the command 
```
ls -l /etc/alternatives/*flash*
```
display?

```
ls -l /etc/alternatives/*flash*
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/firefox-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/iceape-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/iceweasel-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/midbrowser-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/mozilla-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/xulrunner-addons-flashplugin -> /usr/lib/gnash/libgnashplugin.so
lrwxrwxrwx 1 root root 32 2009-02-17 19:12 /etc/alternatives/xulrunner-flashplugin -> /usr/lib/gnash/libgnashplugin.so
```

> **RIchard James13 said:**
> Copying one of the other flashplugin files over the top gives the right result.

```
$ sudo cp iceweasel-flashplugin iceape-flashplugin
```

```
$ sudo update-alternatives --display iceape-flashplugin
iceape-flashplugin - status is auto.
 link currently points to /usr/lib/gnash/libgnashplugin.so
/usr/lib/gnash/libgnashplugin.so - priority 50
Current `best' version is /usr/lib/gnash/libgnashplugin.so.

```

Nope, i get this: 
```
/var/lib/dpkg/alternatives$ sudo cp iceweasel-flashplugin iceape-flashplugin
danny@danny-desktop:/var/lib/dpkg/alternatives$ sudo update-alternatives --display iceape-flashplugin
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/iceape-flashplugin for update_mode ()
```

Did i do it right?

---

### Post by RIchard James13 on 2009-02-21
What does this return
```
$ ls -l /var/lib/dpkg/alternatives/*flash*
```

after root root should be a number if the number is 0 then the file may be truncated.

Try removing any file that is of size 0.

It is possible to restore the broken files by running
```
$ sudo bash
# for p in iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons; do update-alternatives --install /usr/lib/$p/plugins/flashplugin-alternative.so p$-flashplugin /usr/lib/gnash/libgnashplugin.so 50; done
```

---

### Post by DPic on 2009-02-21
> **RIchard James13 said:**
> What does this return
```
$ ls -l /var/lib/dpkg/alternatives/*flash*
```

after root root should be a number if the number is 0 then the file may be truncated.

Try removing any file that is of size 0.

It is possible to restore the broken files by running
```
$ sudo bash
# for p in iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons; do update-alternatives --install /usr/lib/$p/plugins/flashplugin-alternative.so p$-flashplugin /usr/lib/gnash/libgnashplugin.so 50; done
```

I got: 
```
ls -l /var/lib/dpkg/alternatives/*flash*
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/firefox-flashplugin
-rw-r--r-- 1 root root   0 2009-02-20 23:35 /var/lib/dpkg/alternatives/iceape-flashplugin
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/iceape-flashplugin~
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/iceweasel-flashplugin
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/midbrowser-flashplugin
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 104 2009-02-21 00:36 /var/lib/dpkg/alternatives/phimBHflashplugin
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/xulrunner-addons-flashplugin
-rw-r--r-- 1 root root   0 2009-02-17 19:12 /var/lib/dpkg/alternatives/xulrunner-flashplugin

```

Should i delete all of those except for that one?

---

### Post by RIchard James13 on 2009-02-21
Yes delete them all except for the phimBHflashplugin then try it again.

---

### Post by DPic on 2009-02-21
Thank you so much! That worked xD

i have no idea how things got so messed up

---

