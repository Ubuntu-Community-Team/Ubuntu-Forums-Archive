---
title: "Ubuntu Update Manager Not Working"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by oyesola on 2011-02-15
Please help, the following is the message I am getting from the update manager when I try to start it:


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'

---

### Post by nidzo732 on 2011-02-15
Try running in terminal 
```
sudo update-manager
```And post the output here

---

### Post by sikander3786 on 2011-02-15
Welcome to the forums :-)

From Applications > Accessories > Terminal, please post the complete output of this commands.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by makeos on 2011-04-19
> **sikander3786 said:**
> Welcome to the forums :-)

From Applications > Accessories > Terminal, please post the complete output of this commands.

```
sudo apt-get update
```While posting, click the # icon in post menu and paste your text in between the generated ```
 tags for readability purposes.

I'm having the same problem. Now i get this:
[CODE]E: Lists directory /var/lib/apt/lists/partial is missing.
```

---

### Post by sikander3786 on 2011-04-19
> **makeos said:**
> I'm having the same problem. Now i get this:
```
E: Lists directory /var/lib/apt/lists/partial is missing.
```
Create the missing directory.

```
sudo mkdir /var/lib/apt/lists/partial
```

And try again.

```
sudo apt-get update
```

---

### Post by nits. on 2011-06-14
Followed the sudo apt-get update.

Got this:
Fetched 123 kB in 9s (12.3 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Can't run  1) synaptic package manager 2) update manager.

ubuntu software center starts but doesn't fetch lists of any software.

---

### Post by mörgæs on 2011-06-14
Hi, welcome to the fora.

Try to reboot the computer and run these:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jasmeet walia on 2012-03-30
please help me out . i m nt able to run my update manager . it shows the following error when i open the update manager

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Line 1 too long in source list /etc/apt/sources.list.d/medibuntu.list.'


will apreciate if sm1 could help me asap

---

### Post by mörgæs on 2012-03-30
You have already posted the reason: 

```
'E:Line 1 too long in source list /etc/apt/sources.list.d/medibuntu.list.'
```

---

### Post by Old_Grey_Wolf on 2012-03-30
> **jasmeet walia said:**
> please help me out . ...

'E:Line 1 too long in source list /etc/apt/sources.list.d/medibuntu.list.'
.

Remove the offending file ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

Then add the medibuntu repository back
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

---

### Post by GreenRaccoon on 2012-04-05
> **mörgæs said:**
> Hi, welcome to the fora.

Try to reboot the computer and run these:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Thanks!  This worked for me!  Before, I had tried running "sudo apt-get update", and this was the output:
```
...
Fetched 22.8 MB in 31s (736 kB/s)                                              
Reading package lists... Error!
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://mirrors.rit.edu precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://mirrors.rit.edu precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://mirrors.rit.edu precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirrors.rit.edu_ubuntu_dists_precise-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```
And the output of "sudo apt-get upgrade":
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirrors.rit.edu_ubuntu_dists_precise-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```
When I ran
```
sudo rm /var/lib/apt/lists/* -vf
```
it complained
```
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
```
but it still worked, even without removing this directory.

Thanks a ton!

---

### Post by mörgæs on 2012-04-05
You're welcome :-)

---

