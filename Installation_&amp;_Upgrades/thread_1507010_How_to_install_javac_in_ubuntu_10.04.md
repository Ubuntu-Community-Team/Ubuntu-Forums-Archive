---
title: "How to install javac in ubuntu 10.04"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by raac on 2010-06-11
Hi guys, I would appreciate if someone explains me from scratch and in detailed how can I install javac. I'm new with linux so please be specific in what to do. I found one post saying something about adding extra repositories but I don't know what repositories, where to add them, how to add them......Anyway, hope to hear from someone.

Thanks

---

### Post by lechien73 on 2010-06-11
I didn't have to add any new repositories, I installed it by:

[LIST=1]
[*]Go to System > Administration > Synaptic Package Manager
[*]Type *sun* in the Quick Search box
[*]Mark: sun-java6-javadb, sun-java6-jre, sun-java6-jdk for installation
[*]Click Apply
[/LIST]

If you're looking for a different version of java, then just type *javac* in the Quick Search box, and install one of the environments that Synaptic returns.

---

### Post by raac on 2010-06-11
I tried that and it doesn't show none of those three packages,sun-java6.... none of those are in the synaptic package manager....what can I do??

---

### Post by darkod on 2010-06-11
Open System-Administration-Software Sources and check which repositories are enabled (selected). The top two or three should be at least. If they are not, select them.

After that search again in Synaptic for sun-java6-jdk, that is the main package for development. javac is only the executable compiler name. The JDK, Java Development Kit is what you need for compiling applications.

The JRE is usually installed by default, that's the Runtime Environment you need for running java programs/apps, even the ones included on websites.

---

### Post by raac on 2010-06-11
Actually the top four are selected, which are..

Canonical-supported Open Source software (main)
Community-maintained Open Source software(universe)
Proprietary drivers for devices(restricted)
Software restricted by copyright or legal issues(multiverse)

The one that is not selected is Source code

should i select it?? if not what can I do??

---

### Post by darkod on 2010-06-11
Are you sure there is no sun-java6-jdk in Synaptic?

Open terminal and run:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-java6-jdk

---

### Post by raac on 2010-06-11
Yes I'm positive these are the ones related to java that are in the synaptic package manager.

java-package
javacc
jacacc-doc
sun-javadb-client
sun-javadb-common
sun-javadb-core
sun-javadb-demo
sun-javadb-doc
sun-javadb-javadoc

I did what you told me to do and I got this message

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

I hope you guys could help me out

---

### Post by darkod on 2010-06-11
You can download it from here:
[http://java.sun.com/javase/downloads/widget/jdk6.jsp](http://java.sun.com/javase/downloads/widget/jdk6.jsp)

And I just remembered, Sun got bought by Oracle so maybe it's not called sun any more. Try in Synaptic with just 'java jdk' and see which packages it offers.

Alternatively use the download link above, just select your OS and download the file. You will have to install it, depending what type of file it is.

---

### Post by raac on 2010-06-11
I downloaded the bin file from that website, then I executed it in my usr/local

I accepted the terms, and a directory named jdk1.6.0_20 was created.

But when I try
> javac programName.java

It tells me 

"javac: Command not found."

What am I missing?

---

### Post by a2l007 on 2010-08-15
Actually Lucid has ditched sun jdk in its release and has opted to go with openjdk..so if u want to install sun jdk, just do the following.


- Open up /etc/apt/sources.list in your favourite text editor. Add the following line at the bottom of the page:

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Then run:

[INDENT]```
sudo apt-get update
```


After updating the repo, just run the following command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-fonts sun-java6-jdk
```


Thats it..we're done






Cheers

[/INDENT]

---

### Post by lykeion on 2010-08-15
> **raac said:**
> Hi guys, I would appreciate if someone explains me from scratch and in detailed how can I install javac. I'm new with linux so please be specific in what to do. I found one post saying something about adding extra repositories but I don't know what repositories, where to add them, how to add them......Anyway, hope to hear from someone.


If I'd been raac, I would have been very confused by this help.
He asks how to install the java compiler (javac)
and people tell him to install sun-java6-jdk either from the partner repository or from downloaded bin file.
He tries the last method and get "javac command not found" and no one is telling him why.

Just to clear up this issue, since the thread seems to be active again (although original poster is long gone).

The java compiler in OpenJDK is fully sufficient in most cases.
Here's a link with a relevant discussion of the differences between OpenJDK and Sun JDK:
[http://stackoverflow.com/questions/1977238/why-should-i-use-the-sun-jdk-over-the-openjdk-or-vice-versa](http://stackoverflow.com/questions/1977238/why-should-i-use-the-sun-jdk-over-the-openjdk-or-vice-versa)

If that discussion is over your head, you'd probably do best to stick with OpenJDK because it's simpler.

raac should have been adviced to install openjdk-6-jdk and all of his problems would have been solved

Instead of this he was left with a not completed manual installation of Sun JDK. So somebody should have told him that you need to configure javac in a manual installation:
sudo update-alternatives --config javac

---

### Post by crossdelena on 2010-09-10
[FONT="Verdana"]Hello lykeion,

 Thanks for simplifying the problem, by installing open-jdk, javac worked for me.[/FONT]

---

