---
title: "changed permission in /usr - help!"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2005-04-26
My son was too lazy today, so he decided to change permissions for /usr to avoid typing 'sudo' while messing with 'wine'. Well, now the system works sort of funny, I cannot launch any app required admin rights, got "sudo: must be setuid root". I changed permissions back to root:root, but I guess it is not so easy now.

How to fix it?

---

### Post by alastair on 2005-04-26
alastair@muse:~$ ll /usr/bin/sudo
-rwsr-xr-x  2 root root 95512 2005-03-02 21:10 /usr/bin/sudo

i.e.

chmod u+s /usr/bin/sudo

However .... I think your system might be a bit screwed.

The only thing I can think of doing is getting a list of files under /usr and their permissions on a GOOD system, and running a script to fix yours. i.e. Boot something like Knoppix (or Ubuntu rescue?), mounting your /usr (or /, whatever) and running a script. Or reinstalling.

I can get you a "good" list if you want.

---

### Post by foxy123 on 2005-04-26
[QUOTE=alastair]alastair@muse:~$ ll /usr/bin/sudo
-rwsr-xr-x  2 root root 95512 2005-03-02 21:10 /usr/bin/sudo

i.e.

chmod u+s /usr/bin/sudo

However .... I think your system might be a bit screwed.

The only thing I can think of doing is getting a list of files under /usr and their permissions on a GOOD system, and running a script to fix yours. i.e. Boot something like Knoppix (or Ubuntu rescue?), mounting your /usr (or /, whatever) and running a script. Or reinstalling.

I can get you a "good" list if you want.[/QUOTE]
it would be very welcomed. chmod requires sudo, which does not work.

I've got SuSE here, so I can fix it from there. How should I make the script?

---

### Post by alastair on 2005-04-26
[QUOTE=foxy123]it would be very welcomed. chmod requires sudo, which does not work.

I've got SuSE here, so I can fix it from there. How should I make the script?[/QUOTE]

OK - I have uploaded "usr.txt.bz2" - created using :

find /usr/ -printf "%p %m\n" > /tmp/usr.txt
bzip2 -9 /tmp/usr.txt

Format :

<path> <perm>

where <perm> is octal permission e.g.

/usr/share/doc/yelp 755

As for the script, well .... something like :

```

while read path perm ; do
    echo "check : $path"
    if [ -e /mnt/<orig usr>/$path ]; then
         chmod $perm /mnt/<orig usr/$path
    fi
done

```

Change <orig usr> to the mount dir.

Save in "script.sh" and run via :   bash script.sh < usr.txt

Your original /usr is assumed mounted under /mnt/<orig usr> e.g.

/mnt/usr_orig/usr/share/doc/yelp

Now - this assume ONLY permissions were changed. Also, my /usr will probably NOT be the same as yours (hence my check above for "-e" - does your file exist? Your installation might still be suspect depending on what the original cause/command used was.

I HAVE NOT CHECKED THE SCRIPT!

USE AT YOUR OWN RISK!

BACKUP ANY IMPORTANT FILES!

Please be careful and use "echo" rather than "chmod" to check the script seems to do the right thing.

Let us know how you get on.

---

### Post by foxy123 on 2005-04-27
> **alastair]OK - I have uploaded "usr.txt.bz2" - created using :

find /usr/ -printf "%p %m\n" > /tmp/usr.txt
bzip2 -9 /tmp/usr.txt

Format :

<path> <perm>

where <perm> is octal permission e.g.

/usr/share/doc/yelp 755

As for the script, well .... something like :

```

while read path perm  said:**
> ; then
         chmod $perm /mnt/<orig usr/$path
    fi
done

```

Change <orig usr> to the mount dir.

Save in "script.sh" and run via :   bash script.sh < usr.txt

Your original /usr is assumed mounted under /mnt/<orig usr> e.g.

/mnt/usr_orig/usr/share/doc/yelp

Now - this assume ONLY permissions were changed. Also, my /usr will probably NOT be the same as yours (hence my check above for "-e" - does your file exist? Your installation might still be suspect depending on what the original cause/command used was.

I HAVE NOT CHECKED THE SCRIPT!

USE AT YOUR OWN RISK!

BACKUP ANY IMPORTANT FILES!

Please be careful and use "echo" rather than "chmod" to check the script seems to do the right thing.

Let us know how you get on.
 Thanks a lot. I will try it this evening when back from work. Reinstall is always an option though.

---

### Post by foxy123 on 2005-04-27
[QUOTE=foxy123]Thanks a lot. I will try it this evening when back from work. Reinstall is always an option though.[/QUOTE]
 thanks a lot. it did help, almost. For some reasons the script did not change the mode to 4755, but there are not o many such files so I did it manually. All other permissions are fine. It work ok now. I hope it is fixed.

---

### Post by foxy123 on 2005-04-28
on the second thought, it did not. I had to fix a path which I took wrong. So now it looks that all permissions have been changed. However, it works funny sometimes. amaroK got a message that gstreamers plugins are not installed but plays files anyway. But frreezes sometimes. USB camera does not mount now, though it did few days ago...

I am so reluctant to reinstall the system because I've just set up everything to my liking...

---

### Post by alastair on 2005-04-28
It was a long shot really. You could re-check against the list I sent and see if there are differences - but my system is different, so there was bound to be some missed changes.

If you have specific problems (e.g. camera) to discuss - start a new thread, mention what you did here and post some log messages. Same for other issues.

---

