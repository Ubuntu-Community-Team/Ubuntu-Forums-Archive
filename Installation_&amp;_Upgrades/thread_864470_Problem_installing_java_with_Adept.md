---
title: "Problem installing java with Adept"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by Nightmist on 2008-07-19
Hello,

While Adept was installing java on my KDE4, I ran into a problem. The installer stopped at 9% and I clicked 'Show details'. There I see a window with some information about java and Sun yadayada and a confirmation box...

                                 <Ok>

...but I am unable to manipulate anything in the window. Not click <Ok> or scroll down or anything, just highlight the text. So what do I do to continue the installation?

Thanks.

---

### Post by Pumalite on 2008-07-19
Copy and paste the complete error here.

---

### Post by Nightmist on 2008-07-19
QUOTE=Pumalite;5419124]Copy and paste the complete error here.[/QUOTE]

It's not an error, just java that need me to confirm some legal stuff and whatnot... but I can't click the <Ok> "button" in the Adept window...

> Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;
                  &#9474;                                                                           &#9646;
                  &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;
                  &#9474;                                                                           &#9618;
                  &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;
                  &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;
                  &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;
                  &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;
                  &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;
                  &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;
                  &#9474;                                                                           &#9618;
                  &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;
                  &#9474;     form, any other machine readable materials including, but not         &#9618;
                  &#9474;     limited to, libraries, source files, header files, and data files),   &#9618;
                  &#9474;     any updates or error corrections provided by Sun, and any user        &#8595;
                  &#9474;
                  &#9474;                                  <Ok>
                  &#9474;                                                                           &#9474;
                  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

Can I maybe do it from a console instead?

---

### Post by Nightmist on 2008-07-19
When I could finally get Adept closed (it kept saying it was still running) I fixed it with apt-get instead.

But is there a way to "enter" the console messages that sometimes pop up with Adept so you can read them and click <Ok> and whatever?

Thanks.

---

### Post by Pumalite on 2008-07-19
Use the arrows and at the end you can accept the license.

---

### Post by aysiu on 2008-07-19
If the arrows don't work, try the Tab key. Your mouse won't work in this dialogue.

---

### Post by Nightmist on 2008-07-19
> **aysiu said:**
> If the arrows don't work, try the Tab key. Your mouse won't work in this dialogue.

I tried the arrows I think, but didn't try tab.

I'll keep that in mind for next time. But my Linux "skills" are slowly coming back to me now (it's been a while) so I can always use the console when I have to.

---

### Post by aysiu on 2008-07-19
**Tab** to switch between fields. **Enter** to select the field highlighted.

---

