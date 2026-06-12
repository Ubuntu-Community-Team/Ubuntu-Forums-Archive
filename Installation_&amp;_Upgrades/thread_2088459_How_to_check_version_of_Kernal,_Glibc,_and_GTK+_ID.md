---
title: "How to check version of Kernal, Glibc, and GTK+? IDL troubles:old requirements(bonus)"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by CopaceticMan on 2012-11-26
__Main__

How do I check the kernal version?

I used "uname -a" and I think it is 3.5.0-18, but I am not sure.

How do I check the glibc version?

I used "ldd --version" and I think the version is 2.15, but, again, I am not sure

How do I check the GTK+ version?

I used "apt-cache policy libgtk2.0-0 libgtk-3-0" and I think I have both 2.24.13 and 3.6.0.

The versions I need to run IDL from exelisvis are Kernel 2.6.9, glibc 2.3.4, and GTK+ 2.4.13

I just want to double check the versions I got and make sure the commands I used were the right ones.

__Bonus__ 

I am having problems with IDL on Ubuntu. The run buttons at the top are not showing up, I can't use the console, and I cannot run any .pro through the IDL gui. I can through the terminal. If anyone can help me with this, and just tell me "Your dependencies are bad, and you should feel bad"  that would be greatly appreciated too.

---

### Post by ajgreeny on 2012-11-26
With that kernel you must be running 12.10, so will not have synaptic installed by default.  However, I think it is the best package manager we have and always add it to any *ubuntu family OS that doers not have it at installation.  Using that you can easily search for the package you want info about and find the version you have.

Maybe you can also use software-center in the same way.  I never use it so I don't really know if that is so.  There are ways with the command line as well, of course, but I use synaptic generally.

---

### Post by Shuudoushi on 2012-11-26
Most of that can be found in: System Monitor -> System.

---

### Post by ajgreeny on 2012-11-26
> **Shuudoushi said:**
> Most of that can be found in: System Monitor -> System.
That only tells you the kernel version; nothing else.  The OP was looking for the versions of various installed packages.

---

### Post by Shuudoushi on 2012-11-26
> **ajgreeny said:**
> That only tells you the kernel version; nothing else.  The OP was looking for the versions of various installed packages.

This is true. The OP will be able to find a better list fo ways to find the info they are after by googleing the subject. That way they arn't waiting for long periods of time hoping for a response. Forums are GREAT sources if info, but do to the speed in which you get that info may be quit slow. If they can't find the info on google by the time i get back up I'll make a detailed guide on how they would go about finding all of the info they seek.

(I kind of rambled on I think....)

---

### Post by efflandt on 2012-11-28
```
dpkg-query -l **linux*** | grep ii
```

and also **glibc*** and **gtk***

---

### Post by LuisGMarine on 2012-11-28
+1 for just using Synaptic

```
sudo apt-get install synaptic
```

Then just launch it from dash, search away and the information is right infront of you.

---

### Post by zivag on 2013-01-23
There's an app called linuxinfo (apt-get install linuxinfo - if you don't have it)
It tells glibc version as "system library" 

It's also listed in synaptic under the name libc6

Alternatively one can just run it from its location - before it was in /usr/lib, now it's in /lib/'arch'-linux-gnu (in my case it's /lib/i386-linux-gnu), and it yelds library info including version. 

And there are methods mentioned above by other ppl, that are working as well.

---

