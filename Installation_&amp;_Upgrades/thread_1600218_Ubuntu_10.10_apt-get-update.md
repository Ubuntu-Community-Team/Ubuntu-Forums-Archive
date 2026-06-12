---
title: "Ubuntu 10.10 apt-get-update"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by dirkdekker on 2010-10-18
for nessesary  updates on ubuntu 10.10:  sudo apt-get update
Thsi is the result:

Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) maverick Release.gpg
  Temporary failure resolving 'nl.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Temporary failure resolving 'security.ubuntu.com'
..........

What is going wrong?

Pingen to any URL's is oke.

---

### Post by Rubi1200 on 2010-10-19
Server temporarily down? Your internet connection not functioning for some reason?

I would give it 24 hours and then try again. If you still have issues post back here.

---

### Post by zeckdikalajingga on 2010-10-19
hi there, i am trying to update from ubuntu 10.04 to ubuntu 10.10
after i press Alt+F2 and type in typed -
"update-manager -d"  (without the quotes) into the command box, the Update Manager does not opened up...

what should i do ?... is there any other way?

---

### Post by ratcheer on 2010-10-19
> **zeckdikalajingga said:**
> hi there, i am trying to update from ubuntu 10.04 to ubuntu 10.10
after i press Alt+F2 and type in typed -
"update-manager -d"  (without the quotes) into the command box, the Update Manager does not opened up...

what should i do ?... is there any other way?

Try running "sudo update-manager -d" in a normal terminal.

Tim

---

### Post by zeckdikalajingga on 2010-10-19
my computer is a PC computer, with 1.6 ghz pentium 4, 2gb ram, graphic card ATI saphire.

---

### Post by zeckdikalajingga on 2010-10-19
> **ratcheer said:**
> Try running "sudo update-manager -d" in a normal terminal.

Tim

thanks bro... it works!

---

### Post by ratcheer on 2010-10-19
> **zeckdikalajingga said:**
> thanks bro... it works!

You are welcome.

Tim

---

### Post by nagesh.mandlem on 2011-02-01
Hi,

I have installed 10.10 on my dell machine. When I try to do apt-get update I get the following error..Can you please let me  know where the issue is.. I see the following error.. My interconnection is fine. Is there some thing wrong in the format?

Thanks,
Nagesh

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (111: Connection refused)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (111: Connection refused)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)
Err [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) maverick/main Translation-en_IN
  Unable to connect to ppa.launchpad.net:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                             
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                  
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                               
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg                                              
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                              
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (111: Connection refused)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (111: Connection refused)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

