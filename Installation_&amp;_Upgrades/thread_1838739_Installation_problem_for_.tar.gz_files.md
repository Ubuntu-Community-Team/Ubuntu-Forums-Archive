---
title: "Installation problem for .tar.gz files"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by ashishet2 on 2011-09-04
Hi guys,
I am new to ubuntu and trying to install nam simulator tool.
I have upgraded the ubuntu package.
And then i have downloaded nam-1.11-linux-i386.tar.gz
I am trying to install it through Terminal

I am coding it as tar xzvf nam-1.11-linux-i386.tar.gz

Error shown is
[B]tar (child): nam-1.11-liux-i386.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now[/B]

I have tried it too as xvfz, -xzvf, xvzf etc etc....
But again the same thing happen repeatedly

[B]The package is downloaded in downloads in home folder.
I am using Ubuntu 11.04 Latest[/B]
Getting frustrated today.Please help and tell me the correct coding and how it is done.
Will be grateful for your replies.

---

### Post by sanderd17 on 2011-09-04
1. Did you check that there is no comparable program in the software center?

2. you should first go to the correct directory before you try to unpack the archive. Since it is in the Downloads directory, you need to do
```

cd Downloads

```
(watch out, it's case sensitive)

After that, the order of the letters xzvf doesn't matter, but you need to put a dash (-) in front of it, so it should be
```

tar -xzvf nam-1.11-linux-i386.tar.gz

```

---

### Post by haqking on 2011-09-04
> **ashishet2 said:**
> Hi guys,
I am new to ubuntu and trying to install nam simulator tool.
I have upgraded the ubuntu package.
And then i have downloaded nam-1.11-linux-i386.tar.gz
I am trying to install it through Terminal

I am coding it as tar xzvf nam-1.11-linux-i386.tar.gz

Error shown is
[B]tar (child): nam-1.11-liux-i386.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now[/B]

I have tried it too as xvfz, -xzvf, xvzf etc etc....
But again the same thing happen repeatedly

[B]The package is downloaded in downloads in home folder.
I am using Ubuntu 11.04 Latest[/B]
Getting frustrated today.Please help and tell me the correct coding and how it is done.
Will be grateful for your replies.

hi and welcome to the forums.

You dont actually install a .tar.gz file.  It is merely a packaging/compression medium for other files similar to .zip files in windows.

usually you need to extract the contents of it to where you like see here 
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

then if it is source you need to compile the contents, see here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

it is usually simple and means changing to the extracted source and running the following:

when using the terminal make sure you are in correct location by using cd to change to the location and use tab completion for filenames to make sure you dont make mistakes.

That means type the first 2 or 3 letters of filename and press tab key and it should autocomplete it for you.

However before doing any of this always check the software does not already exist in the software centre or as a .deb file for download from the software webpage.  a .deb is like a .exe in windows and self installs. If you mean the Network animator tool then it is in the software centre for easy install ;-)

Enjoy

---

### Post by blind2314 on 2011-09-04
> **sanderd17 said:**
> 1. Did you check that there is no comparable program in the software center?

2. you should first go to the correct directory before you try to unpack the archive. Since it is in the Downloads directory, you need to do
```

cd Downloads

```(watch out, it's case sensitive)

After that, the order of the letters xzvf doesn't matter, but you need to put a dash (-) in front of it, so it should be
```

tar -xzvf nam-1.11-linux-i386.tar.gz

```

Not to nitpick, but tar does not require the '-' before its switches. ```
tar xzvf <blah> 
``` and ```
 tar -xzvf <blah> 
``` are equivalent.

---

### Post by sanderd17 on 2011-09-04
> **blind2314 said:**
> Not to nitpick, but tar does not require the '-' before its switches. ```
tar xzvf <blah> 
``` and ```
 tar -xzvf <blah> 
``` are equivalent.

you're right. In the man page, all one-letter options are preceded with a '-', but in the explanation it says

> 
 A function letter need not
     be prefixed with ``-'', and may be combined with other single-letter
     options.  A long function name must be prefixed with --.


So while it's generally done with a single dash, it's not needed.

---

