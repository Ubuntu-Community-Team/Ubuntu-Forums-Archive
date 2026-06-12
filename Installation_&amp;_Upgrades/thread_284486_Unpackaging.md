---
title: "Unpackaging"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by Zeek00 on 2006-10-25
Hey,

I've downloaded some files, for games of mine that are archived in a couple different formats. I've had .rar .7z  .zip. Is there a package I can download that will read and unpackage ALL of these file types.

I've installed Ark and Xarchive both claiming to unpack these file times and upon trying to use the program I get this error message:

`The Utility 7za is not in your PATH.

Please install it or contact your system administrator'

How can I fix that problem? or is there an easier way to just download a program that is almost out of the box ready and does it all :)

Zeek

---

### Post by studentism on 2006-10-25
"sudo apt-get install p7zip"  should do the trick.

Haven't used either of those utilities, but I'd imagine they're dependent on that package.  It might be worth noting that you already have built in unzipping functionality with "unzip foo.zip"

---

### Post by Zeek00 on 2006-10-25
```
~$ sudo apt-get install p7zip

Reading package lists... Done
Building dependency tree... Done
Package p7zip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package p7zip has no installation candidate

```

---

### Post by Zeek00 on 2006-10-25
> **studentism said:**
> It might be worth noting that you already have built in unzipping functionality with "unzip foo.zip"

wouldn't unZIP be used for a file with the extension of .zip, however I'm trying to unpackage somthing with a .7z or .7zip.

---

### Post by studentism on 2006-10-25
> **Zeek00 said:**
> I've had .rar .7z  **.zip**.

Regardless, edit your /etc/apt/sources.list to add the universe repository to the "deb http://archive.ubuntu.com/ubuntu" and "deb-src http://archive.ubuntu.com/ubuntu" (text editor, just add "universe" after "main restricted" or whatever other ones you added).  Then "sudo apt-get update; sudo apt-get install p7zip".

---

### Post by Zeek00 on 2006-10-25
I edited the source list, and added the two entries. Upon typeing

`sudo apt-get install p7zip' I got the same error message as before...

---

### Post by Zeek00 on 2006-10-25
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
[U]# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[/U]

Make sure I placed the lines where they needed to be...

---

### Post by studentism on 2006-10-25
The # symbol is a comment symbol, meaning whatever follows it is ignored by the apt-get program.  To fix the problem, remove the # from a line that you want to use.  However, just so you don't have to repeat this in the future for other packages you want to install(say, in the multiverse), you might as well put these two lines in sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

It doesn't matter an incredible amount here, but it's good practice to leave your old configuration in the file but commented, in case you need to revert back to it.

After you update and save, make sure you "sudo apt-get update" before attempting the install again; this updates the list of available packages.

Also, for an explanation of the repositories and what they contain:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Zeek00 on 2006-10-25
```
$ sudo apt-get install p7zip
E: Malformed line 20 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
```

Ditched the pound symbols before the entries and this is the error, count to line 20 and guess which one it is :) the one we added

---

### Post by Zeek00 on 2006-10-25
Never mind, I didn't read the extra part you added to the ending. I got it to update and it should install now. Thanks!

---

