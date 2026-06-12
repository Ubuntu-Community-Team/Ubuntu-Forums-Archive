---
title: "Error while trying to update Ubuntu 20.04"
date: 2022-05-12
forum: Installation &amp; Upgrades
---

### Post by rocco.martinello on 2022-05-12
Hi to all,
when I try to update Ubuntu 20.04 focal it is impossible and the following message appears:
```
The package system is damaged Check if third party repositories are in use. If so, disable them, as these sometimes cause problems.
Also run the following command in a terminal: apt-get install -f
Transaction failed: The package system is damaged
The following packages have unmet dependencies:
libpython3.7-stdlib: Depends: libpython3.7-minimal (=3.7.13-1+focal1) but 3.7.13-1+focal3 is installed
Depends: libcrypt1 (>=1:4.1.0) but 1:4.4.10-10ubuntu4 is installed
Depends: liblzma5 (>=5.1.1alpha+20120614) but 5.2.4-1ubuntu1.1 is installed
Depends: libncursesw6 (>=6) but 6.2-0ubuntu2 is installed
Depends: libreadline8 (>=7.0~beta) but 8.0-4 is installed
Depends: libsqlite3-0 (>=3.7.15) but 3.31.1-4ubuntu0.2 is installed
Depends: libtinfo6 (>=6) but 6.2-Oubuntu2 is installed
python3.7: Depends: python3.7-minimal (=3.7.13-1+focal3) but 3.7.13-1+focal3 is installed
Depends: libpython3.7-stdlib (=3.7.13-1+focal3) but 3.7.13-1+focal1 is installed
```
I tried to write in a terminal the command
```
sudo apt-get install -f
```
but it didn't work and the following message appeared:
```
dpkg: error in processing the archive /var/cache/apt/archives/libpython3.7-stdlib_3.7.13-1+focal3_amd64.deb (--unpack):
 attempted overwrite of "/usr/lib/python3.7/distutils/__init__.py" also present in the package python3.7-distutils 3.7.13-1+focal1
dpkg-deb: error: paste subprocess was terminated by the signal (Pipe interrupted)
Processing errors occurred:
 /var/cache/apt/archives/libpython3.7-stdlib_3.7.13-1+focal3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Because of this problem I cannot update my operating system: how can I get rid of this issue?
Thank in advance to those who will answer!

---

### Post by Bashing-om on 2022-05-12
rocco.martinello; Yukkie

A quick look and appears this is a PPA issue ,*OR* from an old release - not from the current  ubuntu repo.
I have:
> 
 sysop@2004x-c:~$ apt list libpython3.7-minimal
Listing... Done
sysop@2004x-c:~$ apt list python3.7-distutils
Listing... Done
sysop@2004x-c:~$ apt list libpython3.7-stdlib
Listing... Done


As not in our repo - begs the question of the origination.
post back the outputs of terminal commands:
```

apt policy libpython3.7-minimal
apt policy python3.7-distutils
apt policy libpython3.7-stdlib

```
Be aware that focal runs libpython3.8
as shown:
> 
apt policy libpython3.8
libpython3.8:
  Installed: 3.8.10-0ubuntu1~20.04.4
  Candidate: 3.8.10-0ubuntu1~20.04.4
  Version table:
 *** 3.8.10-0ubuntu1~20.04.4 500
<snip>


[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by rocco.martinello on 2022-05-12
Hello Bashing-om and thank you very much for your answer!
I gave in the terminal the commands that you told me and the results are as follows:
```
rocco@rocco-desktop:~$ apt policy libpython3.7-minimallibpython3.7-minimal:
  Installed: 3.7.13-1+focal3
  Candidate:  3.7.13-1+focal3
  Version table:
 *** 3.7.13-1+focal3 500
        500 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
rocco@rocco-desktop:~$ apt policy python3.7-distutils
python3.7-distutils:
  Installed: 3.7.13-1+focal1
  Candidate:  3.7.13-1+focal3
  Version table:
     3.7.13-1+focal3 500
        500 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal/main amd64 Packages
        500 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal/main i386 Packages
 *** 3.7.13-1+focal1 100
        100 /var/lib/dpkg/status
rocco@rocco-desktop:~$ apt policy libpython3.7-stdlib
libpython3.7-stdlib:
  Installed: 3.7.13-1+focal1
  Candidate:  3.7.13-1+focal3
  Version table:
     3.7.13-1+focal3 500
        500 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal/main amd64 Packages
 *** 3.7.13-1+focal1 100
        100 /var/lib/dpkg/status
```
Could you tell me how to solve the problem, please?

Cheers,
Rocco

---

### Post by Bashing-om on 2022-05-13
rocco.martinello; Well ....

> 
Could you tell me how to solve the problem, please?


Not readily can I say as most depends on why you have installed python from the deadsnakes PPA.

The PPA maintainer,  Felix Krull, may be interested in why this situation has arisen. He has designated:
[https://github.com/deadsnakes/issues/issues](https://github.com/deadsnakes/issues/issues)
to report any issues with the software.
Contacting the PPA maintainer mat be your best course here if you really do need deadsnakes'  python.

Else --- one might be able to "ppa-purge" to remove the 3,7 python and install focal's 3,8 version ??

[INDENT]what you want to do
[/INDENT]

---

### Post by rocco.martinello on 2022-05-13
Hello Bashing-om and thank you very much for your answer!
I installed a version of Python (probably a version other than the one installed by default on Ubuntu) because I wanted to learn how to use Python.
Now I can uninstall Python if this can solve the problem!
So can I purge Python without causing problems to the Operating System and programs installed on it?
If this is possible how can I do?
I will consider to report this issue to Felix!
Please let me know!
Cheers,
Rocco

---

### Post by Bashing-om on 2022-05-13
rocco.martinello; Hummm ..

to revert python to the repo version ,,,, try:
```

sudo ppa-purge ppa:deadsnakes/ppa

```

I do not recall if the tool is installed by default on recent systems - might have to install "ppa-purge"
```

sudo apt install ppa-purge

```

Nor do I know if removing the entry from your sources has yet been implemented - 

If the ppa-purge runs to completion check your sources:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

If deadsnakes is still present will have to delete the entries before attempting to update again the system.
//
Is late here and my eyes are crossing - off to bed now. I will return my tomorrow afternoon and check on your progress.
//
[INDENT]maybe Yes
[INDENT][INDENT]could be - not so yes[/INDENT][/INDENT][/INDENT]

---

### Post by rocco.martinello on 2022-05-13
Hi Bashing-om,
unfortunately the solution that you proposed didn't work.
Do you know how to solve the problem?
```
rocco@rocco-desktop:~$ sudo ppa-purge ppa:deadsnakes/ppa
[sudo] password for rocco: 
sudo: ppa-purge: comand not found

```
```
sudo apt install ppa-purge
Reading package list... Done
Dependency tree generation      
Read status information... Done
It is useful to perform "apt --fix-broken install" to fix this.
The following packages have unsatisfied dependencies:
 libpython3.7-stdlib : Depends: libpython3.7-minimal (= 3.7.13-1+focal1) but the version 3.7.13-1+focal3 is about to be installed
 python3.7 : Depends: libpython3.7-stdlib (= 3.7.13-1+focal3) but the version 3.7.13-1+focal1 is about to be installed
E: Dependencies not met. Try "apt --fix-broken install" without packages (or specify a solution).
```
I tried the following
```
apt --fix-broken install
```
but it didn't work.
How can I solve this issue?
Thanks in advance to those who will answer!
Rocco

---

### Post by deadflowr on 2022-05-13
ppa-purge needs to be installed.
But that might be an issue.
Maybe you can download it and use dpkg to install it.
You can try
```
cd Downloads
apt download ppa-purge
sudo dpkg -i ppa-purge+press TAB to auto fill the rest
```
I literally mean to Press the TAB button.
It should autofill the proper name.
No need for the +sign it should be
```
ppa-purgeTAB
```
no spaces between ppa-purge and the TAB button press.

If the apt download command fails you can grab it from here: [https://packages.ubuntu.com/focal/all/ppa-purge/download]("https://packages.ubuntu.com/focal/all/ppa-purge/download")

---

