---
title: "apache removal and reinstall"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by stevens.r on 2018-03-10
could someone clarify for me apache stopped working yesterday and idk why log files are either empty or tells me nothing useful

is reinstalling as simple as this am i missing any steps after install 

im on Ubuntu 16.04 headless

sudo apt-get update
sudo apt-get remove apache2
sudo apt-get purge apache2
sudo apt-get install apache2

help would be greatly appreciated trying to study for mid-terms and fixing this is killing me

---

### Post by TheFu on 2018-03-10
What needs to happen depends on the specific webapps/websites you've setup.

"purge" removes the files AND the settings in /etc/. 
"remove" removes the files, but not the settings in /etc/
Only 1 is needed.  The manpage for apt-get explains in more detail.

But this doesn't "fix" anything. It just puts apache back to the installed state, which usually isn't helpful for 95% of the uses for apache. IMHO.  YMMV.

I'd probably use **sudo apt install --reinstall apache2**

---

### Post by stevens.r on 2018-03-11
Thanks for the help ill try that


update
reinstall didn't work im going to purge it and install fresh and see if that makes a difference

---

### Post by TheFu on 2018-03-11
> **TheFu said:**
> 
But this doesn't "fix" anything. It just puts apache back to the installed state, which usually isn't helpful for 95% of the uses for apache. IMHO.  YMMV.

Perhaps if you shared what was wrong?

---

### Post by stevens.r on 2018-03-11
I don't know whats wrong it just stopped working i have a program called muximux which is apache's root folder [https://github.com/mescon/Muximux](https://github.com/mescon/Muximux)
the last time it updated was 7 months ago but I have this in the error but I don't know I always had the error

[COLOR=#000000][Fri Mar 09 10:17:49.527795 2018] [:error] [pid 14607] [client 216.218.206.66:35732] PHP Warning: file_get_contents(): Filename cannot be empty in /var/www/Muximux/muximux.php on line 1122

and I have a bunch of reverse proxies set up in default-ssl.conf

all of just suddenly stopped working don't know why

its a very basic set up almost all of the setting are set default

to completely reinstall it I only have to edit 3 files[/COLOR]

---

