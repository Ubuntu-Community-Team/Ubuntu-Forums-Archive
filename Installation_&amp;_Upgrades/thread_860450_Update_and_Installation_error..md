---
title: "Update and Installation error."
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by murphzerz on 2008-07-15
So, recently I've been having this problem where whenever I try to update the system or install new applications, an error pops up almost immediately with the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have basically no experience in command line, and would like to figure out what is going on.

---

### Post by Pumalite on 2008-07-15
sudo dpkg --configure -a

---

### Post by David1000 on 2008-07-15
I got the same message; together with

E:_cache>open() failed.  Please report


I ran 
sudo dpkg -configure -a     in a terminal and got the message 
unknown option -o
Yes, -o even though i entered -a.
Installation of updates still fails.

Any thoughts?
Thanks

---

### Post by Pumalite on 2008-07-15
> **David1000 said:**
> I got the same message; together with

E:_cache>open() failed.  Please report


I ran 
sudo dpkg -configure -a     in a terminal and got the message 
unknown option -o
Yes, -o even though i entered -a.
Installation of updates still fails.

Any thoughts?
Thanks

sudo dpkg --configure -a

---

### Post by gba3 on 2008-07-15
At first I got the same messages but I managed somehow to identify the problem. In my case it's bzip2 package... And now I type in:

sudo dpkg --configure -a

I get no reaction. But after

sudo apt-get install -f

I get:

Preparing to replace bzip2 1.0.3-0ubuntu2 (using .../bzip2_1.0.3-0ubuntu2.1_i386.deb) ...
/usr/share/omf/bzip2/bzip2-C.omf: could not delete file: No such file or directory at /usr/sbin/install-docs line 360.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/share/omf/bzip2/bzip2-C.omf: could not delete file: No such file or directory at /usr/sbin/install-docs line 360.
dpkg: error processing /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

But if I try to lacate and fix the bzip2 package in Synaptic it returns:

E: /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb: subprocess new pre-removal script returned error exit status 2

What should I do???

---

### Post by iaculallad on 2008-07-15
Try:

```
sudo apt-get upgrade && sudo apt-get -f install
```

---

### Post by gba3 on 2008-07-15
At first I thought it helped but later it stoped with:

"Preparing to replace libsmbclient 3.0.22-1ubuntu3.3 (using .../libsmbclient_3.0.22-1ubuntu3.8_i386.deb) ...
Unpacking replacement libsmbclient ...
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I tried the same line again but then it stoped on:

"dpkg: error processing /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

So, actually I have to ask for help again...

---

### Post by Pumalite on 2008-07-15
Sudo apt-get clean
sudo apt-get -f install 
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by gba3 on 2008-07-17
After "sudo apt-get clean" it doesn't do anything. At least it just shows nothing.

Then I tried "sudo apt-get -f install"...
Response:
"Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  bzip2
The following packages will be upgraded:
  bzip2
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/265kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100114 files and directories currently installed.)
Preparing to replace bzip2 1.0.3-0ubuntu2 (using .../bzip2_1.0.3-0ubuntu2.1_i386.deb) ...
/usr/share/omf/bzip2/bzip2-C.omf: could not delete file: No such file or directory at /usr/sbin/install-docs line 360.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/share/omf/bzip2/bzip2-C.omf: could not delete file: No such file or directory at /usr/sbin/install-docs line 360.
dpkg: error processing /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bzip2_1.0.3-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I guess I'm on the exact position I were... At least I posted whole response. I don't know if it'll clear something more out. I hope it helps!

By the way, I tried "sudo apt-get install -f" too... The response:
"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

But if I do: "sudo apt-get check" the response is:
"You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
  bzip2: Depends: libbz2-1.0 (= 1.0.3-0ubuntu2) but 1.0.3-0ubuntu2.1 is installed
E: Unmet dependencies. Try using -f."

I tried to remove something like bzip2 and other packages, but no use - every time the same - exit status 2 and error code (1)...

---

### Post by Pumalite on 2008-07-17
Close Synaptic while you run -f install.

---

### Post by David1000 on 2008-07-17
My problem is fixed, I think!  I ran  
sudo dpkg --configure -a
and it worked.  The critical part is the double hyphen.  The first time I tried, I thought the double hyphen was a typo and instead used a single hyphen, and that did not work.

Many, many thanks for your help.

---

### Post by Pumalite on 2008-07-17
You are welcome. Good luck!

---

### Post by gba3 on 2008-07-27
> **Pumalite said:**
> Close Synaptic while you run -f install.

It seemed very strange to do... for me and my computer too:

"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

That's all. So I guess nobody can really help with such problem... :(
Interesting, but it seems I won't be able to update anything besause of this...

---

### Post by Pumalite on 2008-07-27
Close Synaptic or other apt-get processes while you run the command.

---

### Post by gba3 on 2008-11-24
> **Pumalite said:**
> Close Synaptic or other apt-get processes while you run the command.

Hmm... I gave up for a while - inored the problem because I really didn't see what I did wrong.

Today I tried again. There really were no other update processes running. I even quit the update notifier. No synaptic, no add/remove, no update - just the terminal was running!!!

---

