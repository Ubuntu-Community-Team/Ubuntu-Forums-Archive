---
title: "Problem installing Java applications, GCJ forced."
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by Trixsey on 2007-06-17
Hey, I'm a pretty fresh Ubuntu Feisty user, recently migrated from Windows. I've been installing a majority of my applications using apt (sudo apt-get install *package*), and it worked just fine until I started installing Java-based applications. Azureus and Eclipse are two Java applications I used frequently on my old platform, and I installed them the first day, just after installing Java 6/1.6. I didn't really pay attention to the recommended/suggested/depending packages, basically I just installed whatever apt-get told me to. I ended up with GCJ, a semi-stable Eclipse and a broken Azureus. I tried to remove GCJ, but it turned out that Eclipse and Azureus depended on it, and were removed in the process. 

Numerous people I've ran in to on #Ubuntu@FreeNode also tell me they have problems with crashing Azureus, and some of my applications I develop in Java 6/1.6 won't run with GCJ. It's not an Azureus problem though, their pre-compiled binaries work well for me, as do Eclipse. It seems Azureus is depending on "lib-gcj-compat" for no reason (I asked the Azureus developers, and they said Suns Java was preferred, and that no gcj-related package was required to run Azureus). Lots of GCJ stuff is included in both installs, even though the additional GCJ packages are recommended and not depended on). Personally I don't see the point in modularization if you link the packages together with lots of useless **** once they are done. We might as well link all packages together into one big lump and call it Lindows if we are on that track.

FAQ:
- Why not run GCJ? It causes major instability in some of the applications I develop, as well as in other software (Eclipse/Azureus).

- But GCJ is open source, isn't it worth instability and non-working programs!? Not really, seeing how the alternative (Suns Java) is open source too. Not to mention I'd rather pick free (as in no-cost-to-use software) that isn't open source given it is more stable.

- Did I install and properly configure Suns Java before installing Azureus/Eclipse? Yes.

- Did I have the package "java-gcj-compat" installed when I experienced compaibility issues with various Java applications? Yes, Azureus depends on it (for no reason).

- Did I use apt-get and not aptitude (aptitude includes recommended packages)? Yes.

- Did I actually check to see if GCJ was recommended, or if it was a depended package? Yes, both Eclipse ([http://packages.ubuntu.com/feisty/devel/eclipse](http://packages.ubuntu.com/feisty/devel/eclipse)) and Azureus ([http://packages.ubuntu.com/feisty/net/azureus](http://packages.ubuntu.com/feisty/net/azureus)) didn't depend on GCJ. Azureus depended on a package called "lib-gcj-compat" though, for no reason. I'd suggest making it recommended.

---

### Post by Trixsey on 2007-06-17
Parts of a discussion in #Java@FreeNode:

<wlfshmn> Trixsey: "Depends: java-gcj-compat | java-virtual-machine, java-gcj-compat | java2-runtime, libcommons-cli-java, liblog4j1.2-java, libseda-java, libswt-gtk-3.2-java"
<wlfshmn> Trixsey: ie. either gcj, or another JVM, and either gcj or another java runtime.
<wlfshmn> Trixsey: sun-java6-jre fullfills those dependencies, and if installed, there will be no need to install gcj for the dependency resolver
<Trixsey> "sun-java6-jre is already the newest version."

<mc__> Trixsey: just install the sun-jdk and you're done
<Trixsey> I have sun-java6-jdk already

<pr3d4t0r> Trixsey: java -version
<pr3d4t0r> Trixsey: What does that say?
<Trixsey> trixsey@Trixsey:~/Desktop$ java -version
<Trixsey> java version "1.6.0"
<Trixsey> Java(TM) SE Runtime Environment (build 1.6.0-b105)
<Trixsey> Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
<pr3d4t0r> Trixsey: OKi, you're done.
<pr3d4t0r> Trixsey: Java is set up on your system.

<pr3d4t0r> Trixsey: javac -version
<Trixsey> trixsey@Trixsey:~/Desktop$ javac -version
<Trixsey> javac 1.6.0

<mc__> Trixsey:  java --version
<Trixsey> javaJava(TM) SE Runtime Environment (build 1.6.0-b105)
<Trixsey> Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
<pr3d4t0r> Trixsey: OKi, you're set.

<Trixsey> now I do "sudo apt-get install eclipse"
<Trixsey> The following NEW packages will be installed: gcj-4.1-base gij-4.1 java-gcj-compat <--- See, it wants GCJ even though I have Java (referring to Suns java)

---

