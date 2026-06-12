---
title: "need some help getting Freemind..."
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by STUMPOFWAR on 2007-05-14
I became addicted to using freemind in OS X....now that I have made the jump to Ubuntu I am having trouble installing it....

I followed the directions in the community  Freemind document and got this error message in Terminal:
[I]seliason@Teletran-1:~$ sudo apt-get install freemind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freemind: Depends: simplyhtml but it is not going to be installed
E: Broken packages
[/I]

I tried it through Synaptic and I got a similar error (IE unmet dependencies)
 I have added the required repositories so I am not sure what I am doing wrong.

So I apt-get SIMPLYHTML and i get another dependcy error about java (sun-j2re1.4 , blackdown-j2re1.4 and two others that I forget right now)

I then try to apt-get each of the four programs listed but each says that it is not available.

What options do I have?

---

### Post by STUMPOFWAR on 2007-05-14
I tooled around with this some more.

apt-get  freemind gets me a dependency error for Sun-Java5-jre

apt-get sun-java5-jre gets me a dependency error for sun-java5-bin

apt-get for sun-java5-bin gets me an error saying that the file is not available and that I 
should apt-get sun-java5-jre..... arg!

---

### Post by STUMPOFWAR on 2007-05-15
no help?.....did I post this in the wrong forum?

I  found a post talking about an IBM java file......I downloaded the correct one (ibm-java2-sdk-5.0-4.0-linux-ppc.tgz.).......the Java community doc has a note saying to rename it to (ibm-java2-sdk-50-linux-ppc.tgz )....whcih I did....


Then is says to:

       make-jpkg ibm-java2-sdk-50-linux-ppc.tgz

to make it a deb

then after making it a deb:
        sudo dpkg -i ibm-j2sdk1.5_1.5.0_powerpc.deb

but when I run Make-jpkg I get an error that "ibm-java2-sdk-50-linux-ppc.tgz" does not exist......

I have the file sitting on my desktop

---

### Post by Dixxon on 2007-05-17
Try this one ... [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux#Ubuntu_.26_Kubuntu)

---

### Post by STUMPOFWAR on 2007-05-17
I tried those directions prior to posting.

I think it comes down to a Java problem......

Could the fact that I am using a PPC laptop be the root of the problem?

---

### Post by STUMPOFWAR on 2007-06-01
still can't get it to work

---

