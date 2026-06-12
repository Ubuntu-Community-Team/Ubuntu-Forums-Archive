---
title: "Support am/pm time format!"
date: 2008-03-08
forum: Ireland Team - Ireland
---

### Post by ebel_ on 2008-03-08
Hi guys.

Currently in ubuntu there is no definition for am/pm for irish english. You can't put the clock format in 12 hour time. You can see this from the command line with the command: "date '+%r'" it should give you something like "06:52:03 PM" but it will lack the AM/PM.

I've created a patch to fix this. It works fine for me locally. I'll put up a package for this soon.

In the mean time you can use ubuntu's new brainstorm to promote this idea. Click on the image below and click on the green arrow to show that approve of it. The people who vote for this, the more likely it is that this will make it into offical ubuntu.


[[IMG]http://brainstorm.ubuntu.com/idea/3904/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3904/)

---

### Post by ebel_ on 2008-03-08
I've created a custom package that has the patch applied. It's in my PPA (Personal Package Archive).

To fix am/pm for the irish locale, you'll need to add my PPA to your apt sources list. Download this file [http://technomancy.org/ubuntu/rorymcc-ppa.list](http://technomancy.org/ubuntu/rorymcc-ppa.list) into /etc/apt/sources.list.d/,

eg use the following command ```
sudo wget -O /etc/apt/source.list.d/rorymcc-ppa.list http://technomancy.org/ubuntu/rorymcc-ppa.list
```

Then just update your software and you should have the proper time format available. To check from the command line, enter ```
LANG=en_IE.UTF-8 date '+%r'
```, it'll give the time. If it has an AM or PM, it has worked.

This also enables the 12 hour clock on the clock applet.

---

### Post by Comhra on 2008-03-09
The IRC meeting was fun.  See you at the next one.

---

### Post by Comhra on 2008-03-09
Got the am/pm issue solved, thanks to Ebel. Working properly now. :)

---

### Post by ebel_ on 2008-03-25
Hi guys, just an update, this has been fixed for hardy!

Thanks to the awesome Martin Pitt for accepting my patch and applying it to langpack-locales 2.7.9-1. This should appear in Hardy. :)

---

### Post by spmccann on 2008-04-21
Well  done ebel getting that fixed. Top job man.

---

