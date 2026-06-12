---
title: "Problems with Java after upgrade to Gutsy"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Respen on 2007-11-26
I have recently upgraded to Gutsy from Feisty.  In Feisty, I had Java and Eclipse working just fine, however, I had to do a clean install of Feisty and was able to upgrade then.  The problem came when I installed the most recent version of Sun's Java on the repository through the Synaptic Package Manager.  Eclipse seems to be working fine for the most part.  I also removed the GCJ version of Java, to see if that would help, which it did not.  I have edited the jvm file to look for the latest version of Java as well; my displayed version shows that it is Java 6.

The problem seems to be that the Java version I now have (1.6.03 or something like that) will not recognize enums, or objects that I create on my own.  I am certain that the java files I am referring to had no compilation errors when I had things working in Feisty.

I would appreciate any help with this that anyone can give.  I have searched this forum and other places, trying various things for a while now, to no avail. :(

---

### Post by Respen on 2007-11-28
Does anyone know how I might solve this problem?

---

### Post by smyrman on 2008-02-11
[B]Other java problem in gutsy:
[/B]
A bit of topic.. I know im not helping much here, but I cant run any java apps on the web after upgrading to gutsy.
running:
$ sudo update-alternatives --config java
does not help

icedtea java doesnt work with the webapps and sun java webstart does not work

tryed uninstalling all java versions, but doesn't help.

So my question (know that I'm still not helping here)
Do you have any other java problems then the compiler related ones?

---

### Post by Respen on 2008-02-25
I think our problems might be similar, I shall explain.

I finally decided to revert back to Feisty (for multiple reasons), and I seem to be having the same problem.  I tried all the fixes that got it to work the first time to no avail.  So, I just gave up in the meantime and went on with my life without Java.  However, I visited a site using a Java application which I could not get to fully work.  It partially worked though.  It was an in-site download manager, but it hung up on the point where I actually wanted to save the file to a specific location.  The GUI seemed to be written in Java, and it was able to display and navigate a filesystem.  That was about all it could do though.

I did not work too hard on trying to get it to work, so it could have been some security settings getting in the way.  However, it follows the pattern of the problem I already have: partially working Java.  I was able to write a simple Hello World program and it worked without difficulty, but anything involving classes does not seem to work.

From what you have said, I gather that we may have the same problem, though I know not what it is.  You should try some of the more involved fixes out there to be sure though.  It has been so long since I last searched for the fixes, so I will not be much help in directing you to them.  My advice is to do a forum search for Java and possibly Eclipse (since it needs Java to work anyway).

---

