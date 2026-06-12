---
title: "Hello, how can I installing Pidgin and Skype in Ubuntu 16.04.1? I have try many ways."
date: 2016-08-15
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2016-08-15
Hello, how can I installing Pidgin and Skype in Ubuntu 16.04.1? I have try many ways...

---

### Post by howefield on 2016-08-15
Have you tried firstly for Pidgin..

```
sudo apt install pidgin
```

and for Skype, load up the *Software & Updates* application and go into the the *Other Software* tab, check off the *Canonical Partners* repository, reload the software sources and install with..

```
sudo apt install skype
```

---

### Post by spi2 on 2016-08-16
Hello, thanks, apology what you mean "reload the software sources"?

---

### Post by howefield on 2016-08-16
> **spi2 said:**
> Hello, thanks, apology what you mean "reload the software sources"?

Don't worry too much about that, it simply means that having added the Canonical Partners repository the list of software applications that your system knows about is out of date, so need updating to include the packages from the Partners repository, you will be prompted to reload (update) as you close out the Software & Updates application as per the attached image..

---

### Post by spi2 on 2016-08-16
thanks!

Hello, ok with pidgin, but with Skype " [COLOR=#000000][FONT=&quot]sudo apt install skype" : display an error: cannot find skype....[/FONT][/COLOR]

---

### Post by howefield on 2016-08-16
Can you post the output of..

```
cat /etc/apt/sources.list
```

---

### Post by spi2 on 2016-08-17
Hello,

```
ubuntu@ubuntu:~$ sudo apt install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted






ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$
```

---

### Post by howefield on 2016-08-17
Seems that you have failed to add the Canonical Partners repository, so back to post #2.

When you successfully add the repository, you'll have 2 new lines in your sources.list for the partners repository file that look something like..

```
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner
```

---

### Post by spi2 on 2016-08-17
hello, apology, what can I do? run [COLOR=#000000][FONT=&quot]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner?[/FONT][/COLOR]

no this only:

```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted
```

---

### Post by howefield on 2016-08-17
> **spi2 said:**
> hello, apology, what can I do? run [COLOR=#000000][FONT=&quot]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner?[/FONT][/COLOR]

Hello, you can add the repository graphically via the Software & Updates application. Open the dash and search for it.. once opened go to the Other Software tab as per the attached image. Once you click on the close button you will be prompted to update your package lists, accept this and reload. Then you should be able run

```
sudo apt install skype
```

Alternatively, you can add the repository via the command line seeing as you seem reasonable comfortable using it, if you prefer try this instead of the above..

```
echo deb http://archive.canonical.com/ubuntu xenial partner | sudo tee -a /etc/apt/sources.list
```

then

```
sudo apt update
```
```
sudo apt install skype
```

---

### Post by spi2 on 2016-08-17
now this:
```
ubuntu@ubuntu:~$ sudo apt install skype
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
```

---

### Post by howefield on 2016-08-17
OK, this is turning from quite an easy package installation to something a little more awkward :)

No worries, perhaps it has something to do with "I have try many ways..." - can you provide the output of

```
ls -al /etc/apt/sources.list.d/
```

---

### Post by spi2 on 2016-08-18
Hello,
is simple, I have install Chrome, what does it matter with Skype?

ubuntu@ubuntu:~$ ls -al /etc/apt/sources.list.d/
total 16
drwxr-xr-x 1 root root 4096 Aug 17 12:09 .
drwxr-xr-x 1 root root 4096 Aug 18  2016 ..
-rw-r--r-- 1 root root  189 Aug 17 15:33 google-chrome.list
-rw-r--r-- 1 root root  189 Aug 17 15:33 google-chrome.list.save
ubuntu@ubuntu:~$

---

