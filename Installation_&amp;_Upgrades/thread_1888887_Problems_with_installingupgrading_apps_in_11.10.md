---
title: "Problems with installing/upgrading apps in 11.10"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by cowgan on 2011-11-30
Hi everyone, 

I'm having problems installing any software through the cmd line or thru the software centre. This problem has started since I installed flashplugin. Although Adobe flashplugin seems to be installed, flash does not run in websites. I cannot even uninstall it as it says 'it has a problem in aptdaemon'. 
   While installing any software using 'sudo apt-get install ' it says 
 'E: Could not get lock /var/lib/dpkg/lock - open (....'

Installing any app thru the software centre takes too long to install. Sometimes it gets stuck at 'Applying Changes' and finally shows up some error (i don't remember the error).

Please help !!! I'm using Ubuntu Oneiric Ocelot 11.10. I'm an admin in the PC but I don't know the root pswd.

---

### Post by jerrrys on 2011-12-01
do you have two package managers open?  you can have only one open at a time.

if thats not the answer, open a terminal and enter:

sudo apt-get update

and post any errors

---

### Post by x1ph1as on 2011-12-01
I have the same problem.

I ran the sudo apt-get update in the terminal and got the following errors:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by efflandt on 2011-12-01
**x1ph1as** it looks like your keys might have gotten scrambled up and/or merged.  Under Software Sources on mine 437D05B5 is the key listed for Ubuntu Archive Automatic Signing Key, and Ubuntu Extras Archive Automatic Signing Key is 3E5C1192.  Note that second half of your keys match those.

So unless there are extra characters that do not show up in Software Sources, Authentication, your keys appear to have extra characters at the beginning (I could be wrong). And not sure how to check, edit, or fix them since I think they are encrypted in /etc/apt/trusted.gpg (just guessing).

---

### Post by x1ph1as on 2011-12-02
Okay, thnx, Anyone knows hows to fix it?

---

### Post by x1ph1as on 2011-12-03
I would love a solution to this problem, anyone?!

---

