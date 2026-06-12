---
title: "Need basic help on installing Mendeley"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Radissthor on 2009-12-28
Hello Everyone,

I need really basic help with very noob problem. I want to install Mendeley, a very good software to manage pdfs that lets you highlight and annotate freely (I mention it because it took me a while to find a good, user-friendly software that did that). The thing is that I wanted to install the update and I couldn't. I think that the reason is that I did a very poor install in the first place. So now I removed the folder with nautilus under root. I now want to install it again, but this time downloading it with the whole Ubuntu package and all that. 

Here's the instructions that are posted on the web site:

[http://www.mendeley.com/download-mendeley-desktop/ubuntu](http://www.mendeley.com/download-mendeley-desktop/ubuntu)

I followed, or at least tried, the instructions. I typed 

```
sudo apt-get install mendeleydesktop
```

but I got the error:

E: Couldn't find package mendeleydesktop

I'm on Jaunty 9.04 32 bit

How should I proceed?

Thanks in advanced.

---

### Post by Radissthor on 2009-12-28
I figured out what I had to do on my own, so I'll share with the rest in case anyone else goes through the same problem:

I went to System->Administration->Software Sources

Then click on the Third Party Software tab and click on the "Add" button

There in the APT line I wrote: 

deb [http://www.mendeley.com/repositories/xUbuntu_9.04](http://www.mendeley.com/repositories/xUbuntu_9.04) /

and that was it. I closed, went to terminal, did an update and then just typed:
```

sudo apt-get install mendeleydesktop
```

and it got installed without problems. It seems that I couldn't find the package because the packages added are only those that are developed by Ubuntu, unless you manually add other software sources. 

Well, if I made any errors in the explanation I would appreciate corrections from the "wiser ones" =P

Cheerios!
:)

---

### Post by BAB SWAIN on 2010-12-01
thnks for your instruction,i have install mendeley and its working nicely.

---

