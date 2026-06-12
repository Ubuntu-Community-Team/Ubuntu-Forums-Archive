---
title: "Installing Skype"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by RipperUK on 2012-10-27
I have tried Installing skype through the website both 32 bit and 64 bit only the 64 bit one installed but I could not open skype and Ubuntu software center and still no luck I have also tried software updater and get this error message check your Internet connection and this summary

W:Failed to fetch [http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

If someone could please help that would be great thank you.

---

### Post by AlexDudko on 2012-10-27
Are you connected to Internet when you try to install Skype? It installs easily in Software Center.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Are you connected to Internet when you try to install Skype? It installs easily in Software Center.

yes it doesn't install it shows the progress bar then just disappears like I never even went to install it in the first place.

---

### Post by RipperUK on 2012-10-27
> **RipperUK said:**
> yes it doesn't install it shows the progress bar then just disappears like I never even went to install it in the first place.

Also If it helps I am using a wired Internet connection and it is my primary Internet connection.

---

### Post by AlexDudko on 2012-10-27
Can you show the output of this command:
> sudo apt-get install skype

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Can you show the output of this command:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

---

### Post by AlexDudko on 2012-10-27
Paste here the output of this command, please:
> cat /etc/apt/sources.list

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Paste here the output of this command, please:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse

---

### Post by AlexDudko on 2012-10-27
> **RipperUK said:**
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse

Add this line to /etc/apt/sources.list file:
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
and run one by one these commands:
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install skype

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Add this line to /etc/apt/sources.list file:

and run one by one these commands:

Could not save the file /etc/apt/sources.list.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by AlexDudko on 2012-10-27
> **RipperUK said:**
> Could not save the file /etc/apt/sources.list.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Try this:
> sudo vi /etc/apt/sources.list
or this:
> gksudo gedit /etc/apt/sources.list

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Try this:

or this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~                                                                                                                                               
~

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Try this:

or this:

I used the other one and run the commands one by one and got this

ashleyhalo@ubuntu:~$ sudo apt-get update
[sudo] password for ashleyhalo: 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease         
Get:1 [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg [933 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease
Get:2 [http://archive.canonical.com](http://archive.canonical.com) quantal Release [7,078 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]              
Get:5 [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages [2,981 B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages                
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages                
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_GB       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [19.0 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_GB     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [4,847 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_GB               
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en         
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [45.1 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [18.4 kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [14 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en      
Err [http://archive.canonical.com](http://archive.canonical.com) quantal/main amd64 Packages          
  404  Not Found [IP: 91.189.92.150 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Fetched 199 kB in 2s (77.0 kB/s)
W: Failed to fetch [http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
ashleyhalo@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ashleyhalo@ubuntu:~$ sudo apt-get install skype 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by AlexDudko on 2012-10-27
Can you see (find) skype in Ubuntu Software Center? If yes, try to install it.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Can you see (find) skype in Ubuntu Software Center? If yes, try to install it.

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details
The following packages have unmet dependencies:

skype: Depends: skype-bin but it is not going to be installed

---

### Post by RipperUK on 2012-10-27
I tried installing it again to double check and this came up 

Failed to download repository information

Check your Internet connection.

Details
W:Failed to fetch [http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by RipperUK on 2012-10-27
Also I don't know if this helps But I am running Ubuntu 12.10 alongside windows 7 home premium with skype already installed on my windows .

---

### Post by AlexDudko on 2012-10-27
There's a problem with repositories.
Though you can download the dependent package skype-bin [here]("http://archive.canonical.com/pool/partner/s/skype/") and install it manually.
To install it manually download the package skype-bin_4.0.0.8-0oneiric1_i386.deb from the above link and execute this command in the directory were the package is:
> sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb
If there are no mistakes try to install skype again:
> sudo apt-get install skype
otherwise paste here the error output.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> There's a problem with repositories.
Though you can download the dependent package skype-bin [here]("http://archive.canonical.com/pool/partner/s/skype/") and install it manually.
To install it manually download the package skype-bin_4.0.0.8-0oneiric1_i386.deb from the above link and execute this command in the directory were the package is:

If there are no mistakes try to install skype again:

otherwise paste here the error output.

ashleyhalo@ubuntu:~$ '/home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb' sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb 
bash: /home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb: Permission denied
ashleyhalo@ubuntu:~$

---

### Post by RipperUK on 2012-10-27
If i didn't do it right I am sorry but I am new to linux.

---

### Post by RipperUK on 2012-10-27
I tried the second command and got this 

ashleyhalo@ubuntu:~$ '/home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb' sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb 
bash: /home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb: Permission denied
ashleyhalo@ubuntu:~$ sudo apt-get install skype 
[sudo] password for ashleyhalo: 
Sorry, try again.
[sudo] password for ashleyhalo: 
Sorry, try again.
[sudo] password for ashleyhalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
ashleyhalo@ubuntu:~$

---

### Post by AlexDudko on 2012-10-27
> **RipperUK said:**
> I tried the second command and got this 

ashleyhalo@ubuntu:~$ '/home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb' sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb 
bash: /home/ashleyhalo/Downloads/skype-bin_4.0.0.8-0oneiric1_i386.deb: Permission denied
ashleyhalo@ubuntu:~$ sudo apt-get install skype 
[sudo] password for ashleyhalo: 
Sorry, try again.
[sudo] password for ashleyhalo: 
Sorry, try again.
[sudo] password for ashleyhalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
ashleyhalo@ubuntu:~$

Execute these commands:
> cd Downloads
sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Execute these commands:

ashleyhalo@ubuntu:~/Downloads$ sudo dpkg -i skype-bin_4.0.0.8-0oneiric1_i386.deb 
[sudo] password for ashleyhalo: 
dpkg: error processing skype-bin_4.0.0.8-0oneiric1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 skype-bin_4.0.0.8-0oneiric1_i386.deb
ashleyhalo@ubuntu:~/Downloads$

---

### Post by AlexDudko on 2012-10-27
Well, I'm stuck here. This is the only architecture available for installation. It should be OK, but need some i386 libraries as dependencies.
Maybe someone else could help you.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Well, I'm stuck here. This is the only architecture available for installation. It should be OK, but need some i386 libraries as dependencies.
Maybe someone else could help you.

What if i purge skype from the system and try again.

---

### Post by Technicolor on 2012-10-27
Can you paste the output of
```
cat /etc/apt/sources.list
```
again, just to make sure nothing changed

---

### Post by AlexDudko on 2012-10-27
> **RipperUK said:**
> What if i purge skype from the system and try again.

You can purge a package if it is installed otherwise there's nothing to purge.

---

### Post by RipperUK on 2012-10-27
> **Technicolor said:**
> Can you paste the output of
```
cat /etc/apt/sources.list
```again, just to make sure nothing changed

ashleyhalo@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> You can purge a package if it is installed otherwise there's nothing to purge.

Also On software sources updates tab I only have the top two boxes checked the other two pre-released updates (quantal-proposed) and unsupported updates (quantal-backports)  I do not don't know if this helps.

---

### Post by AlexDudko on 2012-10-27
Check in Ubuntu Software Center -> Edit -> Software Sources -> tab Other Software if Canonical Partners is checked.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> Check in Ubuntu Software Center -> Edit -> Software Sources -> tab Other Software if Canonical Partners is checked.

its the only one there and its ticked.

---

### Post by Technicolor on 2012-10-27
> **RipperUK said:**
> ashleyhalo@ubuntu:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
Hm.
Can you open up your terminal and type in ```
sudo synaptic
```and then go to
Settings > Repositories, checkmark all 4 boxes (except source code, just leave it alone, checkmarked or not), and then go to the "Other Software", and checkmark the Canonical Partners boxes, and then click OK?
Then it should ask you to update the package databases, and if it doesn't do it atuomatically, click the reload button on the top-left corner of synaptic.
And then close out synaptic, and then try in the terminal
```
sudo apt-get purge skype && sudo apt-get install skype
```

---

### Post by RipperUK on 2012-10-27
> **Technicolor said:**
> Hm.
Can you open up your terminal and type in ```
sudo synaptic
```and then go to
Settings > Repositories, checkmark all 4 boxes (except source code, just leave it alone, checkmarked or not), and then go to the "Other Software", and checkmark the Canonical Partners boxes, and then click OK?
Then it should ask you to update the package databases, and if it doesn't do it atuomatically, click the reload button on the top-left corner of synaptic.
And then close out synaptic, and then try in the terminal
```
sudo apt-get purge skype && sudo apt-get install skype
```

ashleyhalo@ubuntu:~$ sudo synaptic
[sudo] password for ashleyhalo: 
sudo: synaptic: command not found

---

### Post by Technicolor on 2012-10-27
Okay, just did some research and found this:
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/1016294)
From what I've read, it means that until this package is fixed, I believe you can't install skype or other packages that depend on it.

---

### Post by Technicolor on 2012-10-27
> **RipperUK said:**
> ashleyhalo@ubuntu:~$ sudo synaptic
[sudo] password for ashleyhalo: 
sudo: synaptic: command not found
Okay, then how about
```
sudo apt-get install synaptic
```and THEN run those commands?
Also, see above post.

---

### Post by RipperUK on 2012-10-27
> **Technicolor said:**
> Okay, then how about
```
sudo apt-get install synaptic
```and THEN run those commands?
Also, see above post.

Failed to fetch [http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]
Some index files failed to download. They have been ignored, or old ones used instead.

And in the terminal I had this 

ashleyhalo@ubuntu:~$ sudo apt-get install synaptic
[sudo] password for ashleyhalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libept1.4.12 librarian0 libvte-common libvte9 rarian-compat
  sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide perlsgml w3-recs opensp
  libxml2-utils dwww menu deborphan
The following NEW packages will be installed:
  docbook-xml libept1.4.12 librarian0 libvte-common libvte9 rarian-compat
  sgml-data synaptic
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,749 kB of archives.
After this operation, 13.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main sgml-data all 2.0.8 [276 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main docbook-xml all 4.5-7ubuntu1 [336 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libept1.4.12 amd64 1.0.9 [135 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libvte-common all 1:0.28.2-5ubuntu1 [22.8 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libvte9 amd64 1:0.28.2-5ubuntu1 [374 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main librarian0 amd64 0.8.1-5build1 [57.9 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main rarian-compat amd64 0.8.1-5build1 [102 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe synaptic amd64 0.75.12build1 [2,446 kB]
Fetched 3,749 kB in 12s (289 kB/s)                                             
Selecting previously unselected package sgml-data.
(Reading database ... 148736 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.8_all.deb) ...
Selecting previously unselected package docbook-xml.
Unpacking docbook-xml (from .../docbook-xml_4.5-7ubuntu1_all.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.9_amd64.deb) ...
Selecting previously unselected package libvte-common.
Unpacking libvte-common (from .../libvte-common_1%3a0.28.2-5ubuntu1_all.deb) ...
Selecting previously unselected package libvte9.
Unpacking libvte9 (from .../libvte9_1%3a0.28.2-5ubuntu1_amd64.deb) ...
Selecting previously unselected package librarian0.
Unpacking librarian0 (from .../librarian0_0.8.1-5build1_amd64.deb) ...
Selecting previously unselected package rarian-compat.
Unpacking rarian-compat (from .../rarian-compat_0.8.1-5build1_amd64.deb) ...
Selecting previously unselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.12build1_amd64.deb) ...
Processing triggers for sgml-base ...
Updating the super catalog...
Processing triggers for doc-base ...
Scrollkeeper was installed, forcing re-registration of all documents.
Unregistering 34 doc-base files, re-registering 34 doc-base files...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up sgml-data (2.0.8) ...
Setting up libept1.4.12 (1.0.9) ...
Setting up libvte-common (1:0.28.2-5ubuntu1) ...
Setting up libvte9 (1:0.28.2-5ubuntu1) ...
Setting up librarian0 (0.8.1-5build1) ...
Setting up synaptic (0.75.12build1) ...
Processing triggers for sgml-base ...
Updating the super catalog...
Setting up docbook-xml (4.5-7ubuntu1) ...
update-catalog: Suppressing action on super catalog. Invoking trigger instead.
update-catalog: Please rebuild the package being set up with a version of debhelper fixing #477751.
Processing triggers for sgml-base ...
Updating the super catalog...
Setting up rarian-compat (0.8.1-5build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ashleyhalo@ubuntu:~$ sudo synaptic
gpg: /tmp/tmpb6uw1u/trustdb.gpg: trustdb created
gpg: /tmp/tmpcik_pg/trustdb.gpg: trustdb created
ashleyhalo@ubuntu:~$ sudo apt-get purge skype && sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
ashleyhalo@ubuntu:~$ 


Also what does synaptic do?

---

### Post by Technicolor on 2012-10-27
> **RipperUK said:**
> Failed to fetch [http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.canonical.com/commercial-ppa-uploaders/skype/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]
Some index files failed to download. They have been ignored, or old ones used instead.

Also what does synaptic do?
Synaptic is a package manager. IMHO, I think it's better than those software centers and etc.
I'm just used to it, and usually solved all my package problems when I tried installing/removing packages w/ Software Center or apt-get, and failed at doing so. (I'm a hardcore 10.04 (which had synaptic preinstalled) moved ArchLinux fan, I never liked that new Unity thing)

Yeah, if you didn't read the post above my how-to install Synaptic, it's basically a bug in libraries, and you'll simply have to wait until they fix it so you can install Skype normally.

Also, it looks like it did not find skype installed, so how about doing ```
sudo apt-get install skype
``` now (just in case that bug was fixed, and I was reading some outdated thing)?

---

### Post by westie457 on 2012-10-27
Hi the server for the ppa is down or the package has been removed.
Open your sources list in Software Centre, Edit > Software Sources. Go to the 'other software' tab and uncheck the box for the ppa. Close out of that and the Software Centre.
Retry the installation instructions from earlier or go to here  [http://beta.skype.com/en/download-skype/skype-for-computer/](http://beta.skype.com/en/download-skype/skype-for-computer/) and get the stable one for Ubuntu 10.04. If I remember correctly it will update to a newer version automatically

---

### Post by Technicolor on 2012-10-27
> **westie457 said:**
> Hi the server for the ppa is down or the package has been removed.
Open your sources list in Software Centre, Edit > Software Sources. Go to the 'other software' tab and uncheck the box for the ppa. Close out of that and the Software Centre.
Retry the installation instructions from earlier or go to here  [http://beta.skype.com/en/download-skype/skype-for-computer/](http://beta.skype.com/en/download-skype/skype-for-computer/) and get the stable one for Ubuntu 10.04. If I remember correctly it will update to a newer version automatically
Isn't ia32-libs a dependency of skype (I remember it being one)? I recently read a bug on it affecting x86_64 users, and how they could not install it.

---

### Post by RipperUK on 2012-10-27
> **Technicolor said:**
> Synaptic is a package manager. IMHO, I think it's better than those software centers and etc.
I'm just used to it, and usually solved all my package problems when I tried installing/removing packages w/ Software Center or apt-get, and failed at doing so. (I'm a hardcore 10.04 (which had synaptic preinstalled) moved ArchLinux fan, I never liked that new Unity thing)

Yeah, if you didn't read the post above my how-to install Synaptic, it's basically a bug in libraries, and you'll simply have to wait until they fix it so you can install Skype normally.

Also, it looks like it did not find skype installed, so how about doing ```
sudo apt-get install skype
``` now (just in case that bug was fixed, and I was reading some outdated thing)?

sudo apt-get install skype
[sudo] password for ashleyhalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

Also should I uninstall synaptic since it didn't work?

---

### Post by Technicolor on 2012-10-27
> **RipperUK said:**
> sudo apt-get install skype
[sudo] password for ashleyhalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype

Also should I uninstall synaptic since it didn't work?
From what westie (on page 4) says, the server is down, or the package is temporarily (or permanently) gone from the Canonical repo, so try to follow his instructions on getting and installing the package manually.
And if you want to, for all I know, it might be useful sometime.

---

### Post by RipperUK on 2012-10-27
> **Technicolor said:**
> From what westie (on page 4) says, the server is down, or the package is temporarily (or permanently) gone from the Canonical repo, so try to follow his instructions on getting and installing the package manually.
And if you want to, for all I know, it might be useful sometime.

So I don't need it but its good to have ok I really want to be able to fix this but I am just having no luck.

---

### Post by RipperUK on 2012-10-27
Also I tried installing skype from the site earlier the 32bit version didn't work the 64 bit version worked and went to install but didn't (don't know why some sort of error i think) So Does it look like I will just have to wait? I wish i just got Ubuntu 12.04 and not 12.10 damn me  wanting the latest version :)

---

### Post by AlexDudko on 2012-10-27
There's really a bug in Ubuntu-12.10 with i386 architecture libraries. And it means there's no easy way to skype in this version.
But, I just checked it installs just fine in Ubuntu-12.04 - a long term support release. You may want to reinstall your Ubuntu and try the LTS version.

---

### Post by RipperUK on 2012-10-27
> **AlexDudko said:**
> There's really a bug in Ubuntu-12.10 with i386 architecture libraries. And it means there's no easy way to skype in this version.
But, I just checked it installs just fine in Ubuntu-12.04 - a long term support release. You may want to reinstall your Ubuntu and try the LTS version.

how do i do that cant i just downgrade as I used the windows installer (wubi I think its called) to install Ubuntu 12.10 alongside windows 7.

---

### Post by RipperUK on 2012-10-27
If anything I will just wait a little and see if there is a fix and just use windows 7 for all my major programs and applications unless someone else can help but if not thank you anyway for all the help regardless :).

---

### Post by Technicolor on 2012-10-27
> **RipperUK said:**
> If anything I will just wait a little and see if there is a fix and just use windows 7 for all my major programs and applications unless someone else can help but if not thank you anyway for all the help regardless :).
That'd be a smart way of doing things.
And no problem.

---

