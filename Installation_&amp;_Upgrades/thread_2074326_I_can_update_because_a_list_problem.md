---
title: "I can update because a list problem"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Salvagluque on 2012-10-21
Hi guys,

I have this problem from 12.04 and now, in 12.10 I still have it.
Basically this is what I get from either the terminal or the update manager.

E:Encountered a section with no Package: header,
E: Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en,
E:The package lists or status file could not be parsed or opened.

I thought the problem would leave since I just upgraded to 12.10, but it reappeared here. And I can't finish installing stuff because of this.

-Salvador

---

### Post by jerrrys on 2012-10-21
sudo rm /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i1  8n_Translation-en

sudo apt-get update

---

### Post by dino99 on 2012-10-21
you need to purge that borked file:

sudo rm /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i1 8n_Translation-en

be sure that your /etc/apt/sources.list is clean
i mean no outdated entries, only pointing to the actual distro, and take care of non genuine archive(s) like ppa.
then update and run:

sudo apt-get install -f
sudo dpkg-reconfigure debconf-i18n

and logout/in

also dont forget to use, times to times, deborphan, autoremove, autoclean, clean, bleachbit

---

### Post by Salvagluque on 2012-10-21
Thanks but didn't work. Says it just can't do it and the same message keeps coming up.

---

### Post by Salvagluque on 2012-10-21
Also tried to open the synaptic manager and couldn't even open it because of this. I just formatted the entire  disk and installed ubuntu 12.04 and upgraded to 12.10.

---

### Post by jerrrys on 2012-10-21
Which command are you talking about and cant do it?  Please be more specific.

---

### Post by jerrrys on 2012-10-21
Package lists or status file could not be parsed or opened.  If your getting more than one error of this:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

---

### Post by Salvagluque on 2012-10-21
well, all of them.

I try:
sudo rm /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en

and just go on, like normal.

checked the list and seems to be ok.
/etc/apt/sources.list

but when I run
sudo apt-get install -f

or

sudo apt-get update

the message shows up.

---

### Post by jerrrys on 2012-10-21
Please post all errors from apt-get update

---

### Post by Salvagluque on 2012-10-21
here is the entire thing I found threre are other errors. Here they are.

Reading package lists... Error!
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) quantal-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release](http://extras.ubuntu.com/ubuntu/dists/quantal/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

---

### Post by Salvagluque on 2012-10-21
By the way, when I search for the file mx.archive.ubuntu.com_ubuntu_dists_quantal_main_i1 8n_Translation-en%5fUS

it turns out I can't find it because it's not 1 espace 8 es 18, like that. and also the %5fUS is not part of the file's name.

---

### Post by jerrrys on 2012-10-21
GPG error BADSIG can be repaired by ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+BADSIG+&as_qdr=all&sa=Google+Search&lang=en)

Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/quantal/Release](http://extras.ubuntu.com/ubuntu/dists/quantal/Release) 

This does not appear to be a valid link.  For the moment I would just uncheck it in your software sources list.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

And then do another apt-get update and post the errors.

---

### Post by Salvagluque on 2012-10-21
I can't open the synaptic nor the update manager or the software sources app. 

Also tried these, but didn't work.

```
$ sudo -i

# apt-get clean

# cd /var/lib/apt

# mv lists lists.old

# mkdir -p lists/partial

# apt-get clean

# apt-get update
```

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update

sudo apt-get update
```

---

### Post by jerrrys on 2012-10-21
Did you enter those commands (one at a time) as posted below?

sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt-get clean

apt-get update

---

### Post by Salvagluque on 2012-10-21
This was what finally worked for me.

With sudo nautilus went to /var/lib/apt/lists/. Deleted everything. And then, in the terminal wrote down sudo apt-get update.The corrupted file was replaced with the update. 

Thanks Eddie Almirez

-Salvador

---

### Post by jerrrys on 2012-10-21
Glad to hear that  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

