---
title: "problems with adept manager...."
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by prashant_saxena on 2008-03-12
hi,i m totally new to kubuntu(or ny linux version either :)) . i hav sum issues which desperately need sum 1 to took upon.

1)my adept manager can never download ny updates or a new software.i tried to edit "manage repositories' but no help.it jus shows "waiting for headers 17%" nd wud never move forward.may b i hav messed up sum settings for it.
i hav attached da screen shot.plz help me to solve this issue.
thanxs

---

### Post by prshah on 2008-03-12
> **prashant_saxena said:**
> hi,i m totally new to kubuntu(or ny linux version either :)) . i hav sum issues which desperately need sum 1 to took upon.

1)my adept manager can never download ny updates or a new software.i tried to edit "manage repositories' but no help.it jus shows "waiting for headers 17%" nd wud never move forward.may b i hav messed up sum settings for it.
i hav attached da screen shot.plz help me to solve this issue.
thanxs

What type of connection? Over a slow broadband or dial up connection it can take a while.

Also what is your computer's configuration?

Cheers,
PRShah

---

### Post by Seisen on 2008-03-12
Also depending on which mirror you are downloading from some are slower than others so that could be a factor too.

---

### Post by prashant_saxena on 2008-03-12
I m using lan which has good enough speed..
nd config is 
2ghz core 2 duo,2gb ram,160 sata hdd

---

### Post by prashant_saxena on 2008-03-12
but it never downloads even a byte of data...even if left for n hour :(

---

### Post by undecidable on 2008-03-12
Can I suggest, instead of using Adept (even though I love it)
open Konsole and try:

apt-get -V update
that will try to synchronize your local software database with the repositories specified in /etc/apt/sources.list.
The -V is verbose, so it should show any error messages.

Then:
apt-get -u -V upgrade		
that will check what is to be upgraded, (you would then be asked if you want to proceed)
again the -V will give verbose messages.

If both of those succeed, try:
apt-get -s -V upgrade	
that will simulate the upgrade, taking you past just checking what is available.

However ancient Chinese wisdom suggests the symptoms you are seeing are consistent with a gateway blockage:
a.  is there a firewall or a proxy server at the exit from your lan?  if so it may be blocking the incoming updates.
b.  do you have a firewall on your own machine?  
In both cases you may be able to check the logs.

---

### Post by prashant_saxena on 2008-03-12
when i typed the command "apt-get -V update" i got this:

prashant@VY-235:~$ apt-get -V update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

as far as firewall is concerned..i dont think i hav ny.ya but i hav to change proxy setting for connecting to net.do we require to provide proxy settings for adept manager seperately? if yes...then form where.
thanxs

---

### Post by prashant_saxena on 2008-03-12
it would be of great help if i any one could tell me the exact settings for "manage repositories"
my settings are as follows:

kubuntu software:
all options checked

third party software:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner (Source Code)
is checked

updates:
all options are checked

thanks

---

### Post by prashant_saxena on 2008-03-12
..

---

### Post by prshah on 2008-03-12
> **prashant_saxena said:**
> when i typed the command "apt-get -V update" i got this:

prashant@VY-235:~$ apt-get -V update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

as far as firewall is concerned..i dont think i hav ny.ya but i hav to change proxy setting for connecting to net.do we require to provide proxy settings for adept manager seperately? if yes...then form where.
thanxs

First: the command is ```
sudo apt-get...
``` (Put a sudo in front of the command that you have typed above.

Next: Open synaptic go to Settings>Network and input your proxy configuration.

Cheers,
PRShah

---

### Post by prashant_saxena on 2008-03-12
even adding sudo in front of the code didnt helped :(  :(
again showing an error

prashant@VY-235:~$ sudo apt-get -V update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by prashant_saxena on 2008-03-12
> **prshah said:**
> First: the command is ```
sudo apt-get...
``` (Put a sudo in front of the command that you have typed above.

Next: Open synaptic go to Settings>Network and input your proxy configuration.

Cheers,
PRShah
even adding sudo in front of the code didnt helped :(  :(
again showing an error

prashant@VY-235:~$ sudo apt-get -V update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by patrickaupperle on 2008-03-12
Never mind, forgot to refresh before post

---

### Post by prashant_saxena on 2008-03-12
after typing  sudo apt-get -V update
i got
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IN
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_IN
  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_IN.bz2)  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_IN.bz2)  Could not connect to archive.ubuntu.com:80 (91.189.88.46). - connect (111 Connection refused) [IP: 91.189.88.46 80]
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.



seems like thr is some big problem here...

---

### Post by undecidable on 2008-03-12
prashant

My apologies, I forgot the sudo.  all apt-get commands need to be preceded by sudo and then typing in your password (when it asks).  PRShah is as usual correct.

---

### Post by prashant_saxena on 2008-03-12
never mind @ undecidable :)
can u tell me the links which i should add to my repro list??
i jus have i link in it:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner (Source Code)

and i feel that sumthing is missing there

---

### Post by prashant_saxena on 2008-03-12
problem solved :guitar:
i just changed the download server...nd boom...it starts
a real thanks to all those who helpd to solve this issue
i love kubuntu ;)
cheers

---

### Post by undecidable on 2008-03-12
Well, the problem is clear - you cannot connect to the repositories,
but the reason is not.

Can you browse to these places?
In firefox (or whatever browser you use)
try typing in the address bar:

[http://archive.ubuntu.com](http://archive.ubuntu.com)
then if that works:
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/)

I think this is where Adept, and apt-get are trying to connect to.

----
With respect to your next post,
why dont you print out, or attach, your:
/etc/apt/sources.lst
that is the most relaible way of telling what is in it.

---

### Post by undecidable on 2008-03-12
you are solving problems faster than I can reply - good work.
It might be worth posting the download server that didn't work for others' information.

---

### Post by prshah on 2008-03-12
Why not mark this thread solved? Click on "Thread Tools" near the top of the page, then click on "Mark thread as solved."

---

