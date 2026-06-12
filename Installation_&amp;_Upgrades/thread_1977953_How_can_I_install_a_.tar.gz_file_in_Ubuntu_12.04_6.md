---
title: "How can I install a *.tar.gz file in Ubuntu 12.04 64-bits?"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by ricardo072 on 2012-05-11
Hi All,

I'm not an Ubuntu guru,.. so, could you please tell me how can I install eclipse classic (eclipse-SDK-3.7.2-linux-gtk-x86_64.tar.gz) from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) ??

As you may guess, my OS is Ubuntu 12.04 64-bits.

Best regards.
Thanks a lot.

---

### Post by ricardo072 on 2012-05-11
I think, I can do the following:

- gunzip (to unzip the file)
- tar -xvf <filename>
- do I need something else?

Pls, I need confirmation from the rest of the Gurus here if this is the best way to do this..

:guitar:


Thanks a lot, 
Best regards.

---

### Post by Slim Odds on 2012-05-11
> **ricardo072 said:**
> I think, I can do the following:

- gunzip (to unzip the file)
- tar -xvf <filename>
- do I need something else?

Pls, I need confirmation from the rest of the Gurus here if this is the best way to do this..

:guitar:


Thanks a lot, 
Best regards.
A ".tar.gz" file is just like a ZIP file. It can contain anything. You have to know what's in it to know what to do with it.

---

### Post by Enigmapond on 2012-05-11
Does it need to be compiled or does it have an installer for Linux?

---

### Post by ricardo072 on 2012-05-11
For this case, it is "eclipse-SDK-3.7.2-linux-gtk-x86_64.tar.gz" and I'm not familiar with the content on linux.. I do not know what this file contains,... will Eclipse be portable (as the same is currently for Windows)?

I'm not using ubuntu right now..

---

### Post by morrie on 2012-07-11
I know from experience that you can just extract the Eclipse build into a folder and run the "Eclipse" program.  (It really is that easy).  Just make sure you have proper access to that location, as the program will need access to all the build files.

---

### Post by cecilieaux on 2012-11-05
I have the same newbie problem: a *.tar.gz stops me dead in my tracks. 

In this particular moment, I downloaded Open Office from Apache (been using the Windows version and it seems to work faster and lighter than Libre).

I opened it up in the archive manager and there doesn't seem to be an obvious install starting point, just a bunch of .deb files.

Help ... anyone!

---

### Post by snowpine on 2012-11-05
> **cecilieaux said:**
> I have the same newbie problem: a *.tar.gz stops me dead in my tracks. 

In this particular moment, I downloaded Open Office from Apache (been using the Windows version and it seems to work faster and lighter than Libre).

I opened it up in the archive manager and there doesn't seem to be an obvious install starting point, just a bunch of .deb files.

Help ... anyone!

You can install a .deb file with:

```
sudo dpkg -i whatever.deb
```

HOWEVER, in Linux we do not typically install software "the Windows way" by downloading installers from the web. Libreoffice is installed by default in Ubuntu and is really 100% the same as Openoffice (compiled from the same code).

---

### Post by cecilieaux on 2012-11-05
I was in the same quandary and just found a web page devoted to just this topic: 

[http://www.geeksite.in/how-tos/linux/ubuntu-how-tos/how-to-install-openoffice-org-3-3-on-ubuntu-12-04-11-10-11-04.html](http://www.geeksite.in/how-tos/linux/ubuntu-how-tos/how-to-install-openoffice-org-3-3-on-ubuntu-12-04-11-10-11-04.html)

Hope this helps the next person.

---

### Post by cecilieaux on 2012-11-05
Thanks, Snowpine. I didn't expect an answer so quickly.

---

### Post by LatinHacker on 2013-04-05
What if it is not a deb?

---

