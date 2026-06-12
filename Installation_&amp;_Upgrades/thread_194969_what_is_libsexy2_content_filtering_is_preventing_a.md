---
title: "what is libsexy2? content filtering is preventing access"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by nmsmith on 2006-06-12
I'm trying to upgrade using **sudo apt-get dist-upgrade**. The system upgrade graphical program didn't succeed, so I found out how to get bash to use proxies and tried apt-get. Now however I get:

```
1087 upgraded, 246 newly installed, 67 to remove and 1 not upgraded.
Need to get 39.2kB/651MB of archives.
After unpacking 411MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com dapper/main libsexy2 0.1.7-0ubuntu5
  302 Moved Temporarily
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.7-0ubuntu5_i386.deb  302 Moved Temporarily
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Trying to go to the http address in Firefox I get a message that says that the obvious rude keyword has been found in the address, so it will not display. (I'm worried that I may not even be able to view this thread, so I'm not writing the text directly!). What is this library? Is it required? Is it gettable from elsewhere?

~nick

---

### Post by pellgarlic on 2006-06-12
google is your friend:

[http://www.chipx86.com/wiki/Libsexy](http://www.chipx86.com/wiki/Libsexy)

[http://packages.ubuntu.com/dapper/libs/libsexy2](http://packages.ubuntu.com/dapper/libs/libsexy2)

don't know if it's necessary/important.

perhaps the "302 Moved Temporarily" should incline you to try again in a while, or look for news on their website about it being moved.

---

### Post by nmsmith on 2006-06-12
Thanks for the research pellgarlic, but the issue comes from the 'sexy' string in the title.
I quote:
[B]Your organization's Internet use policy restricts access to this web page at this time.
Reason:
The Websense category "Block" is filtered. Keyword found: sexy.
URL: 
http:/www.chipx86.com/wiki/Libsexy[/B]

I guess this is something that simply can't be done at work.

---

### Post by pellgarlic on 2006-06-12
ah, i see! 

what you could do is this: download the [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.7-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.7-0ubuntu5_i386.deb) file at home/a friend's/an internet cafe, if you can, then put it on a usb stick/cd and take it into work. double-click on the deb file, and an "install" window will open (or do an "apt-get install libsexy2_0.1.7-0ubuntu5_i386.deb). install it, then retry the "sudo apt-get dist-upgrade". 

don't know if it'll work, but it might be worth a shot. i'm guessing you're doing it at work because you have a faster internet connection there? if that's the case, this way might allow you to have to do minimal downloading elsewhere, and do the rest of the dist-upgrade at work.

---

### Post by nmsmith on 2006-06-12
[QUOTE=pellgarlic]i'm guessing you're doing it at work because you have a faster internet connection there?[/QUOTE]

Very perceptive, but it's also because at the time I wrote I had pretty much nothing to do with myself, and also because my wife is using the car for the next few weeks and I didn't fancy cycling home with my laptop.

Thanks for the advice though. Good thinking.

---

