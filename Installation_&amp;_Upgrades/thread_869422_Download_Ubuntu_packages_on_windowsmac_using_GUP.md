---
title: "Download Ubuntu packages on windows/mac using GUP"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by priomsrb on 2008-07-24
Hi!

Ubuntu is great OS, but one thing that frustrated me about it was that it was hard to install packages if you did not have an internet connection. So I've made a little tool called GUP(Get Ubuntu Packages) that will download Ubuntu/Kubuntu/Xubuntu packages with all their dependencies on any OS.

What GUP does is that, after being given a list of packages to download, it will calculate it's dependencies and then produce a file called 'download_urls.txt' containing URLs of files to download. From then the user can use his own download manager or use the wget.exe(included) to download the package files.

The package information is kept locally and so not network connection is required. This also means that GUP is very fast to calculate dependencies(few seconds for hundreds of packages).

Currently the OS is required to have python installed, but I will soon try to put up versions which doesn't require python. Also only hardy is supported at the moment though it is easy to add support for other versions.

Please try it out and let me know what you think.

---

### Post by remick182 on 2008-08-04
I was hoping to use your program so that I might download needed packages under WinXP, but I can't decompress the zip file.  It's telling me that the files are password protected..and I see no password in your post.  I've tried using Windows' extraction program, WinRAR, and ZipGenius.  No luck with any of them.  Any ideas?

---

### Post by tayundo on 2008-09-03
Hi, my name is William and I desperately need this program. I joined this forum just to get it! But when I try to extract the files with WinRar it gives me an "Unknown compression method" error message on everything. Any ideas? I have been trying to get MPlayer on my Hardy system for a couple weeks now :-(

---

### Post by tayundo on 2008-09-12
Hey, William again, still hoping to get a reply here. Not only have I tried WinRar, but also 7ZIP, and my Ubuntu archive manager. All give the same error, "Unknown compression method". PLEASE, someone respond with an answer to this. Do I need a particular decompressor, or, as I believe, is this file corrupt. Please and thank you.

---

### Post by skrjabin on 2009-02-18
You can find working windows programs here.

Good luck.

---

### Post by skrjabin on 2009-02-18
On this URL, to be exact:

[http://bapoumba.wordpress.com/2007/12/15/wubdepends-get-ubuntu-packages-for-an-off-line-machine/](http://bapoumba.wordpress.com/2007/12/15/wubdepends-get-ubuntu-packages-for-an-off-line-machine/)

---

### Post by noonenodead on 2009-03-06
extract with winzip 12

---

### Post by priomsrb on 2009-12-02
Hi,
I am extremely sorry for not being able to reply to my thread. I simply forgot about it when I didn't get any replies after a few days.

Unfortunately I have found that the zip I uploaded doesn't seem to work properly. Also I have lost the source code for GUP so I can't upload it again.

But there is some good news! There is a good program called Keryx([http://keryxproject.org/](http://keryxproject.org/)) that works like GUP but is much better and has a GUI. So I think using that will solve your problems.

Sorry again for my late reply

---

### Post by EXCiD3 on 2009-12-02
Nice work on the application. We're in need of some contributors to Keryx if anyone is interested in working with us. It's great to see people trying to tackle this obstacle, we just need to get everyone on the same project to produce something really really good that makes it onto the LiveCD! :)

---

