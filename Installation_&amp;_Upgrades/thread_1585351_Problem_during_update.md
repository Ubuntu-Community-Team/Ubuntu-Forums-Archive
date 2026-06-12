---
title: "Problem during update"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by shaquille on 2010-09-30
Hi there, I am facing a disgusting problem. While I am trying to update my system using update manager It downloaded the files and then while it starts installation it shows the following message

> (Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
files list file for package 'linux-libc-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover

And then nothing occurs. I cannot install any new package either. Every time I tried the above message was showed.

**[SIZE="2"]I had to add that[/SIZE]** i had been faced a bit different problem earilier. And using the following code I solved that:

```
sudo mv /var/lib/dpkg/updates/0103 /home/shaquille/dpkg_update_0103
```

```
sudo mv /var/lib/dpkg/updates/0104 /home/shaquille/dpkg_update_0104
```

```
sudo mv /var/lib/dpkg/updates/0105 /home/shaquille/dpkg_update_0105
```

```
sudo mv /var/lib/dpkg/updates/0106 /home/shaquille/dpkg_update_0106
```

```
sudo mv /var/lib/dpkg/updates/0107 /home/shaquille/dpkg_update_0107
```

```
sudo mv /var/lib/dpkg/updates/0108 /home/shaquille/dpkg_update_0108
```

and then:

```
sudo dpkg --configure -a
```

The problem was solved then.

But now with this problem what can i do?

---

### Post by plucky on 2010-09-30
> Hi there, I am facing a disgusting problem. While I am trying to update my system using update manager It downloaded the files and then while it starts installation it shows the following message

Quote:
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
files list file for package 'linux-libc-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover
And then nothing occurs. I cannot install any new package either. Every time I tried the above message was showed.

From a terminal ```
sudo apt-get clean
sudo apt-get install -f
```

The first command will clear out the /var/cache/apt/archives of all the .deb files that have previously been downloaded so that the next command will download a new file before trying to fix the problem.

If you want to keep the .deb files,you will have to copy them to a different location.

Good Luck

---

### Post by shaquille on 2010-09-30
> **plucky said:**
> From a terminal ```
sudo apt-get clean
sudo apt-get install -f
```

The first command will clear out the /var/cache/apt/archives of all the .deb files that have previously been downloaded so that the next command will download a new file before trying to fix the problem.

If you want to keep the .deb files,you will have to copy them to a different location.

Good Luck

That doesn't work. The problem still exits.

---

### Post by plucky on 2010-09-30
> **shaquille said:**
> That doesn't work. The problem still exits.

Was there any error message?

It would help if you post the results of running the commands so that we can see the results for ourselves as there might be something that gives us a clue what the problem is.

Use [noparse]```

```[/noparse] blocks around the result as it is easier to read.

Try ```
sudo dpkg --configure -a
```

---

### Post by shaquille on 2010-10-01
> **plucky said:**
> Was there any error message?

It would help if you post the results of running the commands so that we can see the results for ourselves as there might be something that gives us a clue what the problem is.


It shows the same thing:

```
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'linux-libc-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

what should I do then?

plz.....

---

### Post by zepita on 2010-10-01
If you have independant partitions for / and /home you could try reinstalling... sometimes is better to format rather than finding a fix, but you miss the experience of the process..

good luck with that

---

### Post by shaquille on 2010-10-01
> **zepita said:**
> If you have independant partitions for / and /home you could try reinstalling... sometimes is better to format rather than finding a fix, but you miss the experience of the process..

good luck with that

I don't think it doesn't have any solution. Re-installation is the last process. I don't wanna re-install.

Aren't there any more suggestion?

---

### Post by plucky on 2010-10-01
> **shaquille said:**
> I don't think it doesn't have any solution. Re-installation is the last process. I don't wanna re-install.

Aren't there any more suggestion?

Try removing the package ```
sudo apt-get remove linux-libc-dev
```

---

### Post by shaquille on 2010-10-02
> **plucky said:**
> Try removing the package ```
sudo apt-get remove linux-libc-dev
```

I tried it. It doesn't work. The following result showed.


```
shaquille@shaquille:~$ sudo apt-get remove linux-libc-dev
[sudo] password for shaquille: 
Sorry, try again.
[sudo] password for shaquille: 
Sorry, try again.
[sudo] password for shaquille: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  backintime-common libsexy2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-dev linux-libc-dev
0 upgraded, 0 newly installed, 2 to remove and 19 not upgraded.
1 not fully installed or removed.
After this operation, 23.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 60%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'linux-libc-dev' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
shaquille@shaquille:~$ 
```

Aren't there any other way than re-installing my Ubuntu?

---

### Post by shaquille on 2010-10-05
after many research i found that my **[SIZE="2"]usr/bin/dpkg[/SIZE]** is corrupted.
How could I replace it with a fresh one?

---

