---
title: "openoffice.org-java-common"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zika on 2009-03-14
while watching updates today (lots of openoffice stuff) I've noticed many complaints about: openoffice.org-java-common is not installed. this is clean install from yesterday. should I install that package? I would like to install some 64-bit java jdk or similar. is this openoffice 64-bit? what to do?
I have java-64-plugin operational on my machine. I will need Java probably for R but so I do not want to stuff my machine with java's I will not use ... ;)
what is a good java jdk 64-bit for jaunty?

---

### Post by rbmorse on 2009-03-14
Yes, you should install the java-common package.  It's pretty big and brings lots of dependencies, so I can understand why it's not in the distribution CDs or .iso files.

I use the java that gets installed with the Ubuntu-restricted-extras package.  Works OK.

---

### Post by zika on 2009-03-14
> **rbmorse said:**
> Yes, you should install the java-common package.  It's pretty big and brings lots of dependencies, so I can understand why it's not in the distribution CDs or .iso files.
I use the java that gets installed with the Ubuntu-restricted-extras package.  Works OK.
I've installed sun-java6-jdk and that brought (a little bit older 12 instead of 14) also a 64-bit FF plugin so I, finally, have all the stuff from the same version. I've removed symbolic link to libnpjp2.so from latest incarnation of plugin and have put link to this one instead. now I have R installed with JGR and java working both in FF and as a Java for programming. I will deal with openoffice.org-java-common once the need for it emerges ... :) I need openoffice just to open files that comes from users in order to be able to do statistical analysis they need or to check on conclusions they made.

---

### Post by Nullack on 2009-03-17
What does this package do though> Is there benchmarks?

---

### Post by calc on 2009-03-17
> **zika said:**
> while watching updates today (lots of openoffice stuff) I've noticed many complaints about: openoffice.org-java-common is not installed. this is clean install from yesterday. should I install that package? I would like to install some 64-bit java jdk or similar. is this openoffice 64-bit? what to do?
I have java-64-plugin operational on my machine. I will need Java probably for R but so I do not want to stuff my machine with java's I will not use ... ;)
what is a good java jdk 64-bit for jaunty?

What has happened is I added a comment to the 'javaldx' error message that already occurs to tell the user that they should install openoffice.org-java-common. This is because many things in OOo need Java but there is not enough room on the CD to have Java on it. The openoffice.org-java-common package pulls in the Java bits needed by OOo to properly function.

---

### Post by zika on 2009-03-17
> **calc said:**
> What has happened is I added a comment to the 'javaldx' error message that already occurs to tell the user that they should install openoffice.org-java-common. This is because many things in OOo need Java but there is not enough room on the CD to have Java on it. The openoffice.org-java-common package pulls in the Java bits needed by OOo to properly function.
Thank You. I installed it. Now that is resolved.

---

### Post by Nullack on 2009-03-18
Calc I understand the problem and I'm also manually installing the open office java package which brings in the openjdk, icedtea and so on.

Though in terms of the user experience this is kinda messy isnt is? Could there be a way, say the first time a user runs an OO app, that a dialogue is produced which recommends downloading the additional packages? Leaving it until it errors out is problematic from a user experience point of view I think.

---

