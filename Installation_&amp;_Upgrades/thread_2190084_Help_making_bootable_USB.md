---
title: "Help making bootable USB"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by gravitate on 2013-11-25
I am trying to make a bootable USB with my mac for a windows netbook which I am going to wipe and put ubuntu on. However I am trying to convert the .iso to a .img and keep getting this:

[FONT=Menlo]pc3:~ liteaddress$ hdiutil convert -format UDRW -o ~/Users/liteaddress/Downloads/ubuntu-12.04.3-desktop-i386.img ~/Users/liteaddress/Downloads/ubuntu-12.04.3-desktop-i386.iso[/FONT]
[FONT=Menlo]hdiutil: convert failed - No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$

Any ideas please?[/FONT]

---

### Post by sanderj on 2013-11-25
Do it the easy way:

```

cd  ~/Users/liteaddress/Downloads
pwd
ls ubuntu-12.04.3-desktop-i386*
hdiutil convert -format UDRW -o ubuntu-12.04.3-desktop-i386.img ubuntu-12.04.3-desktop-i386.iso
ls ubuntu-12.04.3-desktop-i386*

```

Post the output here.

PS: I wonder if ~/Users/liteaddress does exist. Don't you mean ~/Downloads? Anyway: change to the directory containing the .iso file.

---

### Post by gravitate on 2013-11-25
[FONT=Menlo]hdiutil: convert failed - No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$ ls ubuntu-12.04.3-desktop-i386*[/FONT]

---

### Post by gravitate on 2013-11-25
sorry it should have been /Users/liteaddress/Downloads I'm a bit lost now

---

### Post by gravitate on 2013-11-25
I go to get info and it says where: /Users/liteaddress/Downloads
 

Name and extension: ubuntu-12.04.3-desktop-i386.iso

---

### Post by sanderj on 2013-11-25
I'm lost. Did you find ubuntu-12.04.3-desktop-i386.iso ?

If so, do this: go into that directory and type:

```
ls -al ubuntu-12.04.3-desktop-i386*
```

and post the output here.

---

### Post by gravitate on 2013-11-25
[FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386*[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386*: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$[/FONT]

---

### Post by sanderj on 2013-11-25
> **gravitate said:**
> [FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386*[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386*: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$[/FONT]

So ... there you have the problem: first you have to find ubuntu-12.04.3-desktop-i386.iso on your system.

Wait ... you did download it, didn't you?

EDIT: if you need to download, do this

```

cd
curl -O http://ftp.belnet.be/ubuntu.com/releases/releases/precise/ubuntu-12.04.3-desktop-i386.iso
ls -al ubuntu*

```

---

### Post by gravitate on 2013-11-25
Yes its in my Downloads folder I right clicked it to 'get info' and thats where I get this info from of the where:/Users/liteaddress/Downloads

And Name and Extension: ubuntu-12.04.3-desktop-i386.iso

---

### Post by sanderj on 2013-11-25
> **gravitate said:**
> Yes its in my Downloads folder I right clicked it to 'get info' and thats where I get this info from of the where:/Users/liteaddress/Downloads

And Name and Extension: ubuntu-12.04.3-desktop-i386.iso

Then show me with the the "ls -al ubuntu*" command. If you can't, the file is not there.

---

### Post by gravitate on 2013-11-25
I will download it again :)

---

### Post by gravitate on 2013-11-25
will you be around for 10 mins to help please?

---

### Post by ian-weisser on 2013-11-25
> **gravitate said:**
> [FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386*[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386*: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$ ls -al ubuntu-12.04.3-desktop-i386[/FONT]
[FONT=Menlo]ls: ubuntu-12.04.3-desktop-i386: No such file or directory[/FONT]
[FONT=Menlo]pc3:~ liteaddress$[/FONT]

> **gravitate said:**
> Yes its in my Downloads folder I right clicked  it to 'get info' and thats where I get this info from of the  where:/Users/liteaddress/Downloads

And Name and Extension: ubuntu-12.04.3-desktop-i386.iso

You are in the wrong directory.
Your are using the **ls** command in your ~ (home) directory.
The file isn't in that directory.
The file is in your ~/Downloads directory.

Either **cd** into your Downloads directory or **ls** the Downloads directory.
Examples.
```

# I have a file named 'hello' in my Downloads directory

# Look for it without changing directories

ian@bot:~$ ls -al hello         # Doesn't work - hello isn't in that directory
ls: cannot access hello: No such file or directory

ian@bot:~$ ls -al Downloads/hello       # Works
-rw-r--r-- 1 ian ian 0 Nov 25 15:34 Downloads/hello


# Change directories

ian@bot:~$ cd Downloads/
ian@bot:~/Downloads$           # The prompt shows where I am. I have moved.

ian@bot:~/Downloads$ ls -al hello            # Look for hello in this directory (success)
-rw-r--r-- 1 ian ian 0 Nov 25 15:34 hello

ian@bot:~/Downloads$ cd ..   # Return to home directory
ian@bot:~$ 
```

---

### Post by gravitate on 2013-11-25
I went to Downloads and did your command but the command was not found:

[FONT=Menlo]pc3:Downloads liteaddress$ ls: ubuntu-12.04.3-desktop-i386*[/FONT]
[FONT=Menlo]-bash: ls:: command not found[/FONT]
[FONT=Menlo]pc3:Downloads liteaddress$[/FONT]

---

### Post by sanderj on 2013-11-25
> **gravitate said:**
> will you be around for 10 mins to help please?

Yes. What is the result of the command I gave you:

```
cd
curl -O http://ftp.belnet.be/ubuntu.com/releases/releases/precise/ubuntu-12.04.3-desktop-i386.iso
ls -al ubuntu*

```

---

### Post by ian-weisser on 2013-11-25
The **ls** command does not have a colon. You made a syntax error...and the system told you so ("command not found")

Please use [code] tags for your output. It helps make the output readable.

---

### Post by gravitate on 2013-11-25
Thanks though I understand it now but why is ls:: command not found?

---

### Post by gravitate on 2013-11-25
OK no errors now :)

```
[FONT=Menlo]pc3:downloads liteaddress$ ls ubuntu-12.04.3-desktop-i386*[/FONT][FONT=Menlo]ubuntu-12.04.3-desktop-i386.iso[/FONT]
[FONT=Menlo]pc3:downloads liteaddress$
```


That means its there right?[/FONT]

---

### Post by gravitate on 2013-11-25
```
[COLOR=#000000][FONT=Ubuntu Mono]hdiutil convert -format UDRW -o ubuntu-12.04.3-desktop-i386.img ubuntu-12.04.3-desktop-i386.iso[/FONT][/COLOR]ls ubuntu-12.04.3-desktop-i386*
```


seamed to work?! you were right looking in the wrong place :) Where do I find the .img file now in the downloads?

---

### Post by gravitate on 2013-11-25
wooow nearly there now its in the downloads but called a .img.dmg why is that?

---

### Post by sanderj on 2013-11-25
> **gravitate said:**
> ```
[COLOR=#000000][FONT=Ubuntu Mono]hdiutil convert -format UDRW -o ubuntu-12.04.3-desktop-i386.img ubuntu-12.04.3-desktop-i386.iso[/FONT][/COLOR]ls ubuntu-12.04.3-desktop-i386*
```


seamed to work?! you were right looking in the wrong place :) Where do I find the .img file now in the downloads?

I don't think so.

In your case I would give up this route. Go for unetbootin (with GUI) instead: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), possibly from Windows.

HTH

---

### Post by sanderj on 2013-11-25
> **gravitate said:**
> wooow nearly there now

Not at all, IMHO: I still see no *iso and you still have to do the dd which is much harder.

Therefore my advice to use unetbootin.

HTH

---

