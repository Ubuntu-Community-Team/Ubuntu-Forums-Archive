---
title: "Buzilla installation Error on Ubuntu"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by nitinds on 2007-11-28
Hi,
i am new to Ubuntu.
when i am installing Bugzilla Packege "**bugzilla_2.20-1_all.deb**" on Ubuntu 
the Error appears...
[COLOR="Red"][B]" (Reading database ... 135691 files and directories currently installed)
Preparing to rplace bugzilla 2.22.1-2 (using .../bugzilla_2.22.1-2ubuntu1_all.deb) ...
Unpacking replacement bugzilla...
Setting bugzilla (2.22.1-2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf

can't connect to the database.
Error: Can't connect to local MySQL server through socket '/var/run/mysql/mysqld.sock' (@)
	Is your database installed and up and running?
	Do you have the currect username and password selected in localconfig?"[/B][/COLOR]

Can you please suggest me what should i do for that?

Thanks,
Nitin Saxena:(

---

### Post by joshthejest on 2007-12-03
I have a similar problem... this is what I'm trying.

sudo aptitude purge bugzilla 
sudo rm -r /etc/bugzilla
sudo aptitude update
sudo aptitude install bugzilla

This gave me back the configuration setup during install...

Then I got these errors:

Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bugzilla (2.22.1-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/bugzilla/dbconfig-params
-ne granting access to database bugzilla for joshthejest@localhost: 
-e already exists.
-ne creating database bugzilla: 
-e already exists.
dbconfig-common: flushing administrative password
.: 77: Can't open /etc/bugzilla/dbconfig-params
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bugzilla

---

### Post by joshthejest on 2007-12-03
running **sudo dpkg --configure bugzilla** allowed me to do some parts of the configuration again.

---

### Post by joshthejest on 2007-12-03
I edited /etc/dbconfig-common/bugzilla.conf 
I changed the line
dbc_install='true' 
to
dbc_install='false'

then ran 
sudo dpkg --configure bugzilla

I chose Y for all of the options and to install the package maintainers version when the blue screen came up.

Now when I got to
url/bugzilla
I get redirected to the cgi-bin and it says:

Can't connect to the database.
Error: Access denied for user 'bugzilla'@'localhost' (using password: YES)
  Is your database installed and up and running?
  Do you have the correct username and password selected in localconfig?


For help, please send mail to this site's webmaster, giving this error message and the time and date of the error. 


somewhere I need to edit something... then maybe it will work.

---

### Post by joshthejest on 2007-12-03
Configuration files are in /etc/bugzilla/
edit localconfig
change the db information.

---

### Post by eneve on 2008-04-09
I would like to give a little more help here.  I had this same problem when installing Bugzilla on Ubuntu Gutsy.

```

Error: Access denied for user 'bugzilla'@'localhost' (using password: YES)
  Is your database installed and up and running?
  Do you have the correct username and password selected in localconfig?

```

Next I read this on Google Groups:

  "I decided to run checksetup.pl manually, which failed as well, and it
  turned out that /etc/bugzilla/localconfig had "secret" as password
  instead of the bugzilla user's password.  Fixed this and entered a
  couple of values in checksetup, and it worked."

So I decided to take a look at this /etc/bugzilla/localconfig and it sure enough had 'secret' in as the password so I changed that to the password I selected.

  NOTE: I also looked at /etc/bugzilla/dbconfig-params to see what the user / pass were.

Then I ran 

```
sudo dpkg-reconfigure bugzilla
```

only to get the same error as before.

Lastly I ran:

```

sudo perl /usr/share/bugzilla/lib/checksetup.pl 

```

and 

```

sudo /etc/init.d.apache2 restart

```

And then it all started working!  I hope this helps someone!

---

### Post by periphery on 2008-05-05
Thanks eneve your instructions got me back on track:

After apt died, I changed my db password manually using:

sudo pico /etc/bugzilla/pico localconfig

Then just ran the bugzilla check setup script:

sudo perl /usr/share/bugzilla/lib/checksetup.pl

It asked me details about the administrator again which after entering and then restarting apache with:

sudo /etc/init.d.apache2 restart

I was able to access bugzilla with no problem after that with the url:

[http://myserveraddress/bugzilla](http://myserveraddress/bugzilla)  :p

---

### Post by mohnkern on 2008-05-07
Well, I had the same set of problems, and the stuff here got me a lot closer.  Now I go to the login page, put in my user name and password and get:

The requested URL /cgi-bin/bugzilla/cgi-bin/bugzilla/index.cgi was not found on this server.

/usr/lib/cgi-bin/bugzilla exists, and index.cgi is there. 

If I run index.cgi as a non root account I get 

Error reading /etc/bugzilla/params: Permission denied at /usr/share/perl5/Bugzilla/Config.pm line 178.
Compilation failed in require at /usr/share/perl5/Bugzilla/DB.pm line 50.
BEGIN failed--compilation aborted at /usr/share/perl5/Bugzilla/DB.pm line 50.
Compilation failed in require at /usr/share/bugzilla/globals.pl line 35.
BEGIN failed--compilation aborted at /usr/share/bugzilla/globals.pl line 35.
Compilation failed in require at ./index.cgi line 33.


If I run as root, it works fine.

---

### Post by NTolerance on 2008-06-26
> **mohnkern said:**
> Well, I had the same set of problems, and the stuff here got me a lot closer.  Now I go to the login page, put in my user name and password and get:

The requested URL /cgi-bin/bugzilla/cgi-bin/bugzilla/index.cgi was not found on this server.

/usr/lib/cgi-bin/bugzilla exists, and index.cgi is there. 

If I run index.cgi as a non root account I get 

Error reading /etc/bugzilla/params: Permission denied at /usr/share/perl5/Bugzilla/Config.pm line 178.
Compilation failed in require at /usr/share/perl5/Bugzilla/DB.pm line 50.
BEGIN failed--compilation aborted at /usr/share/perl5/Bugzilla/DB.pm line 50.
Compilation failed in require at /usr/share/bugzilla/globals.pl line 35.
BEGIN failed--compilation aborted at /usr/share/bugzilla/globals.pl line 35.
Compilation failed in require at ./index.cgi line 33.


If I run as root, it works fine.

I encountered this problem on Debian Etch.  There appears to be an issue with the Debian/Ubuntu Bugzilla package that creates this error.  Fix:

1.  Log into the Bugzilla web page as admin with the "log in" link at the lower right hand corner of the page.  

2.  Click on the "parameters" link at the bottom left of the page.  

3.  Check the "urlbase" setting.  When my system was broken in the same way as yours the urlbase value was appended to what was already in the browser URL, so the CGI file was not found.  I simply erased the entire value in "urlbase" and saved my settings.  Now I can log in at the home page correctly.

---

### Post by david.matheson on 2008-06-29
> **NTolerance said:**
> 3.  Check the "urlbase" setting.  When my system was broken in the same way as yours the urlbase value was appended to what was already in the browser URL, so the CGI file was not found.  I simply erased the entire value in "urlbase" and saved my settings.  Now I can log in at the home page correctly.

This worked for me!  Thanks!  Have you found anything else that this has broken?

---

### Post by NTolerance on 2008-06-30
> **david.matheson said:**
> This worked for me!  Thanks!  Have you found anything else that this has broken?

Actually, while my fix does correct that problem, it creates an issue with the e-mail links that Bugzilla sends out for bug tracking.  Best thing to do is put the full Bugzilla URL in that setting like this example:

```
http://192.168.10.150/cgi-bin/bugzilla/
```

---

### Post by aravinda_sh on 2008-07-09
Hi I am installing bugzilla on Ubuntu and having problem when I ru testserver.pl.

When I run the command "sudo perl testserver.pl http://192.168.110.201/bugzilla" the following error are displayed and the installation is not complete.

TEST-OK Webserver is running under group id in $webservergroup.
TEST-OK Got front picture.
TEST-FAILED Webserver is not executing CGI files.
TEST-FAILED Webserver is permitting fetch of [http://192.168.110.201/bugzilla/localconfig](http://192.168.110.201/bugzilla/localconfig).
This is a serious security problem.
Check your webserver configuration.

How to get CGI file executing. How to get out of the failure "Webserver is not executing CGI files"

Please help me
Aravinda

---

### Post by NTolerance on 2008-07-09
edit:  nm, can't delete posts

---

