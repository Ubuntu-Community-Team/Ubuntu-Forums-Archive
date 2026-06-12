---
title: "SCIM and Gmail on Jaunty beta"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mhenriday on 2009-03-30
After upgrading from (64-bit) **Intrepid** to (64-bit) **Jaunty** beta, I found that **SCIM**, while working nominally in, e g, the **Gnome** text editor and different versions of **OOo 3**, no longer works in **Gmail** ; thus, for example, to write Chinese or Japanese text in a **Gmail** text box, I first have to type it into an editor and then paste it into **Gmail**. Irritating - and surprising, as it worked perfectly well in **Intrepid**. Is this a bug to be reported, or have I missed an update to **SCIM** obvious to other users ?...

Henri

Update : I have decided to report this as a bug : [Bug #351770]("https://bugs.launchpad.net/ubuntu/+bug/351770")....

---

### Post by mhenriday on 2009-04-04
Given the major interest that this query has sparked, I feel the need to be more precise : I have now found that **SCIM** and **Gmail** work very well together when running **Firefox**/**Swifteasel 3.0.8** on **Jaunty**, but I see the problem described above when running **Firefox 3.1 b3** on this system. The odd thing is that **SCIM** and **Gmail** worked fine together when running **Firefox 3.1 b3** on **Intrepid** on my 64-bit machine but, as mentioned above, stopped doing so when I upgraded to **Jaunty**. So is this a **Jaunty** problem, or a **Firefox** problem, or a **SCIM** problem, or a **Gmail** problem ? You tell me !...

Henri

---

### Post by Zorael on 2009-04-04
3.1b3 from where? Any packages?

I'm running firefox-3.6=**3.6~a1~hg20090403r26892+nobinonly-0ubuntu1~umd1** from the Ubuntu Mozilla Daily ppa below, and scim works for me in gmail.
> **Darkshade said:**
> ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main #minefield
```
That's what I'm using


Edit: Actually here's the link, since you'll most likely need the pgp key and stuff: [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by mhenriday on 2009-04-05
**Zorael**, thanks for your tip ! Uppgrading to the **Firefox 3.6 alpha** (minefield) did indeed resolve the **SCIM** problem I was experiencing when running **3.1 b3**, now I can insert glyphs in both Chinese (&#20013;&#25991;) and Japanese (&#26085;&#26412;&#35486;). But what goes 'round comes 'round : my **Delicious** bookmarks can't be displayed in **3.6 alpha**, as the latest version of the former (2.1.034) is not compatible with the latter. You pays your money and you takes your choice....

Henri

---

### Post by Zorael on 2009-04-05
You could try disabling extension compatibility checks; perhaps that addon just might work after all.

See [http://edgecrafting.blogspot.com/2009/03/firefox-3-disable-extension.html](http://edgecrafting.blogspot.com/2009/03/firefox-3-disable-extension.html).

---

### Post by mhenriday on 2009-04-06
My experience is that those pesky extension compatibility checks are necessary ; things tend to crash if they are turned off. I now have no less than four **FF** versions on my panel - **Swiftweasel 3.0.8 pgo**, **FF 3.0.8**, **FF 3.1 b3**, and **FF 3.6 alpha**, so I can pick and choose depending what I want to do. Thanks, in any event for the tip !...

Henri

---

