---
title: "Is it possible to add .tar.gz links to the source.list file to install them?"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by colobix on 2008-08-29
Now I have to use nautilus and place the downloaded files in the right folders. That takes forever. So is it possible to use source list to .tar.gz archives as well as deb?

---

### Post by bmwman on 2008-08-29
I don't think so :)

Those require you to compile first to get the DEBs.

---

### Post by colobix on 2008-08-29
OK so how do I install the tar.gz files then?

---

### Post by bmwman on 2008-08-29
Well it all depends on what are you trying to install. tar.gz is an archive, same as zip, rar, etc. Normally you can extract it by right click on it choose excract here. That will create a folder with the source files. Then you open the Terminal and move to that folder, i.e. "cd /home/yourusername/Desktop/theextractedfolder" . Make sure Linux is case sensitive so you need to type everything correctly.

After you're in that folder, you run "./configure", when that's done you run "make" and at the end "make install". That should be all. If the program you're trying to insall needs root privilleges you run everything with sudo. "sudo ./configure, sudo make, sudo make install". If you get any errors you probably are missinf some library or needed file.

---

### Post by colobix on 2008-08-29
It doesnt work. it says Cant find file or directory. DO i have to type it all on the same line?
Now I did this: cd /home/chris/Desktop/Songbird on the same line but nothing happend. is that right?

---

### Post by aysiu on 2008-08-29
If you're trying to install Songbird, just download [this .deb file](http://darkstar.ist.utl.pt/getdeb/ubuntu/hardy/so/songbird_0.7.0-0~getdeb1_i386.deb) and double-click it.

---

### Post by colobix on 2008-08-29
Thank you so much but for the future, I have to know how to install archive packed programs.
So what did I do wrong the last time?

---

### Post by aysiu on 2008-08-29
> **colobix said:**
> Thank you so much but for the future, I have to know how to install archive packed programs.
So what did I do wrong the last time? For the future, you *might* have to know how to install .tar.gz programs, but I wouldn't say you *have* to.

I've been using Linux since April 2005, and I've never *had* to install a .tar.gz program. That's over three years now.

Did I *choose* to install some .tar.gz programs? Sure. I mainly did it to help others (Songbird, non-repositories Firefox, FirstClass) than I did for myself.

.tar.gz just means it's a compressed file (sort of like .zip or .rar). A .tar.gz extension tells you nothing about its contents, so there is no standard procedure. Some .tar.gz files have source code that needs to be compiled. Other .tar.gz files have precompiled binaries that just need to be launched. Still others have themes or icons (and not programs at all).

I'd say just stick with the repositories.

If the program you want is not in the repositories, check getdeb.net.

If it's not there either, look for an .rpm to be *alien*ed to .deb and installed.

The last resort is a .tar.gz, and then you can get help for that here.

---

### Post by dfreer on 2008-08-29
> **colobix said:**
> Thank you so much but for the future, I have to know how to install archive packed programs.
So what did I do wrong the last time?

Well, .tar.gz can sometimes be just the source code (meaning you would have to extract the files then compile them), or sometimes it's a pre-compiled binary (which would mean you would extract the files, make sure the binary has permission to execute, and then run it).

In the case of songbird, it's already pre-compiled (if you downloaded it from the main link that is), so extract the archive, and then check your permissions, and then run the "songbird" file.

In the future, you might want to mention what program it is you are trying to install first, it helps us help you :D

---

### Post by colobix on 2008-08-29
OK thanks. because it takes me forever to find out by my self all the right folders to sort the files to. 

But I wish u guys could put songbird, skype and limewire in the add/remove list coz these are programs everyone needs. 

But thanks alot:)

---

### Post by aysiu on 2008-08-29
> **colobix said:**
> 
But I wish u guys could put songbird, skype and limewire in the add/remove list coz these are programs everyone needs. It's not really "you guys," since I am in no way involved in putting stuff in the repositories.

I don't know why Songbird isn't in a repository, but Skype already is:
[http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

You have to add the Medibuntu repositories to get it.

I'm not sure what the deal is with Limewire. Most people here who use such a program seem to recommend Frostwire instead, which is, like Songbird, at GetDeb.net:
[http://www.getdeb.net/app/Frostwire](http://www.getdeb.net/app/Frostwire)

By the way, not everyone uses those programs. As a matter of fact, I don't use Songbird or Limewire or Frostwire. And I only occasionally have used Skype (I can count the number of times on one hand).

---

### Post by colobix on 2008-08-29
OK thanks alot:)

---

