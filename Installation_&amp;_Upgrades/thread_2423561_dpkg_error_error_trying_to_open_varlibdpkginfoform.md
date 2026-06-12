---
title: "dpkg: error: error trying to open /var/lib/dpkg/info/format: Not a directory"
date: 2019-07-25
forum: Installation &amp; Upgrades
---

### Post by pranav.bhattarai on 2019-07-25
```

pranav@inspiron-5548L:~$ sudo dpkg --configure -a
dpkg: error: error trying to open /var/lib/dpkg/info/format: Not a directory

```

I can't seems to run this command for some reason which is said in error message above. 
*Any help resolving this issue will be highly appreciated.*
Distro: **Ubuntu 19.04**

---

### Post by SeijiSensei on 2019-07-25
On my system /var/lib/dpkg/info/format is an ordinary file containing simply the value "1". Perhaps you don't have a /var/lib/dpkg/info directory for some reason?

---

### Post by pranav.bhattarai on 2019-07-25
```

pranav@inspiron-5548L:/var/lib/dpkg$ ls
alternatives   diversions-old  parts             status-old
available      info            statoverride      status.original
available-old  lock            statoverride-old  triggers
diversions     lock-frontend   status            updates
pranav@inspiron-5548L:/var/lib/dpkg$ cd info
bash: cd: info: Not a directory
pranav@inspiron-5548L:/var/lib/dpkg$ sudo nano info
Use "fg" to return to nano.

[1]+  Stopped                 sudo nano info

```

this info is a file which has nothing written in it. Is it normal? Or should i write "1" in it?

---

### Post by coffeecat on 2019-07-25
> **pranav.bhattarai said:**
> 
this info is a file which has nothing written in it. Is it normal? Or should i write "1" in it?

Have another look at SeijiSensei's post.

/var/lib/dpkg/info is a **directory**

/var/lib/dpkg/info/format is a **file** with the value "1" in it.

---

### Post by pranav.bhattarai on 2019-07-25
should i create an file name "format" which has a value 1 in it. And try running: ```
 sudo dpkg --configure -a 
```
?!

---

### Post by SeijiSensei on 2019-07-25
Since you seem to have the /var/lib/dpkg/info directory, does it contain a file called format?  If not, try
```
sudo echo '1' > /var/lib/dpkg/info/format
```
then try running dpkg again.

---

### Post by coffeecat on 2019-07-25
> **SeijiSensei said:**
> Since you seem to have the /var/lib/dpkg/info directory

I wonder if the OP does have a /var/lib/dpkg/info directory. I'm concerned by this:

> **pranav.bhattarai said:**
> ```

pranav@inspiron-5548L:/var/lib/dpkg$ cd info
bash: cd: info: Not a directory

```

If the /var/lib/dpkg/info directory has disappeared and somehow been replaced by an empty /var/lib/dpkg/info file (as the OP's later text in post #3 suggests), then the OP has a serious problem. In my 18.04 system, the /var/lib/dpkg/info directory has over 9800 files.

---

### Post by VMC on 2019-07-25
The OP most likely has a '1' in that *format* file, but is missing *info* directory, where *format* belongs.

---

### Post by SeijiSensei on 2019-07-25
> **coffeecat said:**
> I wonder if the OP does have a /var/lib/dpkg/info directory. 
Yes, I missed that before. How would anyone even manage to munge things up this badly unless someone else got root privileges and engaged in a malicious act?

OP: If you really don't have an info directory, there's little you can do other than reinstalling. As coffecat says, there are over 9800 files in that directory.

I had a similar concern about [this thread](https://ubuntuforums.org/showthread.php?t=2423279) the other day. Of course, as seems par for the course these days, the OP never returned to the thread to tell us what the problem turned out to be.

---

### Post by pranav.bhattarai on 2019-07-26
```
 
pranav@inspiron-5548L:~$ sudo echo '1' > /var/lib/dpkg/info/format
bash: /var/lib/dpkg/info/format: Permission denied

```
I did tried that but it failed. What should I do?

---

### Post by pranav.bhattarai on 2019-07-26
Can i recreate those files by reinstalling all packages from bash loop script? Although this might be the last idea to try.

---

### Post by coffeecat on 2019-07-26
I fear that in focusing on the error message you started this thread with, you are missing the bigger picture. **Something** or **someone** appears to have replaced the /var/lib/dpkg/info directory with a /var/lib/dpkg/info file, and in the process you have lost in excess of 9800 important files.

My question is: what is the something, and what other damage has it done? I have no idea how to replace those 9800+ files and, in your situation, wouldn't even attempt to. Your operating system is likely severely damaged beyond reasonable repair. I would do what SeijiSensei suggests - reinstall.

Someone or something. What were you doing prior to seeing the dpkg error message?

---

### Post by pranav.bhattarai on 2019-07-26
Running this bash script solve this issue and decrease the number of reinstalling package day-by-day.
```

for package in $(apt remove --purge hello -y 2>&1 | grep "warning: files list file for package '" | grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do apt-get install --reinstall "$package" -y; done 

```

Problem is these programs/packages don't install  and try to tell me in each loop which increase the of execution by few seconds in each loop:
Errors were encountered while processing:  
php7.2-common
 libpaper1:amd64 
php7.2-opcache 
php7.2-cli libgs9:amd64 
fusionforge-common 


Now the solution for this issue is using this : ```
   $ sudo apt-mark hold package1 package 2 ... 
```

But i don't know how to put this command in above bash script. If u know or if u know someone who knows bash scripting will certainly help me crack this case.

---

### Post by coffeecat on 2019-07-26
@pranav.bhattarai, it is extremely discourteous to the forum membership to use a font colour almost the same as the background colour, thus making your post impossible to read. I can read your post using admin permissions, and I could edit your post to remove the pointless font colour, but I won't. Nor will I answer your question. I've come to the conclusion that you are not engaging with anything that anyone says, and that you are not prepared to enter into a sensible dialogue with those responding in this thread.

---

### Post by VMC on 2019-07-26
I just highlighted his post to be able to read it.

---

### Post by QIII on 2019-07-26
You shouldn't have to.  A polite poster wouldn't make you.

@pranav.bhattarai:

This thread is now closed.  If you care to be considerate of everyone else in the community by modifying your posts to use default fonts and colors to make them readable, PM me with a good reason to re-open it.

---

