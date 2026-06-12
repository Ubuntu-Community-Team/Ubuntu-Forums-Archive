---
title: "Install Eclipse in ubuntu 10.4?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by whitebee on 2010-05-05
Hi all:

I just reinstall my system and replace my old ubuntu 9.10 (where eclipse was installed) by 10.4. I try to install eclipse again in 10.4 by:

sudo apt-get install eclipse

But I get errors:


The following packages have unmet dependencies:
  eclipse: Depends: eclipse-jdt but it is not going to be installed
           Depends: eclipse-pde but it is not going to be installed
E: Broken packages


So I try to install eclipse-jdt, but get another two errors:


The following packages have unmet dependencies:
  eclipse-jdt: Depends: eclipse-platform (= 3.5.2-2ubuntu4) but it is not going to be installed
               Depends: eclipse-plugin-cvs (= 3.5.2-2ubuntu4) but it is not going to be installed
E: Broken packages


I try and realize that eclipse-plugin-cvs depends on eclipse-platform, thus I try to install eclispe-platform, but I get another error:


The following packages have unmet dependencies:
  eclipse-platform: Depends: ant (>= 1.7.1)
E: Broken packages


I think it wants ant with version >= 1.7.1, but my ant is 1.8!

I am stuck; please help? I also remember that in 9.10 installing eclipse is straightforward: I only needed to install eclipse, that's all. How come it gets so complicated in ubuntu 10.4?

What should I do? Please help -- any help will be highly appreciated. I really need eclipse to do homework! :((

Thanks a lot in advance :)

---

### Post by nmaster on 2010-05-05
try fixing the broken packages with ```
sudo apt-get install -f
``` then try again.

---

### Post by whitebee on 2010-05-05
Thanks so much, but it still doesn't work ... I get the same errors as before. Please help? :S

---

### Post by whitebee on 2010-05-05
I suddenly think of a question: I install ant1.8 but haven't built it yet. When I type in "ant" it says:

Buildfile: build.xml does not exist!
Build failed

Could it be a problem? Is it why eclipse-platform requires ant (>=1.7.1)?

(But what puzzles me is: why couldn't I just install eclipse anymore? :( thanks for your help!)

---

### Post by nmaster on 2010-05-05
i'm not really sure what the problem is, but perhaps you could try downloading the tar.gz from here: [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

then all you need to do is extract with 'tar xvzf THE_FILE.tar.gz' and look at the README file.

sorry, i'm not really sure about ant and i've never actually used eclipse. what happens if you try ```
sudo apt-get install ant && sudo apt-get install eclipse
```

---

### Post by bhavin137 on 2010-08-04
Hey im also having the same problem
i dont kno the soln but one thing is for sure
ant 1.8 is working properly the build file for the application to be built using ant is missing which it has to if u havent built nething using ant
pls refer to the installation guide in your system (if installed) at /usr/share/doc/ant1.8-doc/manual/index.html


cheers,
azorac   :o

---

### Post by ytsurk on 2010-08-04
i prefeer to install it manually,
see here

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

---

### Post by ubscott on 2010-12-04
hi,

i'm also having trouble installing Eclipse on Ubuntu 10.0.0.4.  first i tried to install it via Synaptic.  i kept on receiving errors about unsatisfied dependencies.  

i found this thread and this statement:
sudo apt-get install -f

...gave me a list of packages that were updated.  it seems that my Java installation is good to go.  however, this command:
sudo apt-get install openjdk-6-jdk

gives me:
Package openjdk-6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openjdk-6-jdk has no installation candidate

i have visited this page:
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

i have Ubuntu 10.04.  The page tells me i need Eclipse 3.5.2.  However, i don't see Eclipse 3.5.2 in Synaptic.  I see 3.5.1 instead.

I try to mark first 'elipse' page for installation, get this:

eclipse:
 Depends: eclipse-jdt but it is not going to be installed
 Depends: eclipse-pde but it is not going to be installed

I try elipse-pde:
eclipse-pde:
 Depends: eclipse-jdt but it is not going to be installed
 Depends: eclipse-platform but it is not going to be installed

i try eclipse-platform:
eclipse-platform:
  Depends: eclipse-platform-data (=3.5.1+repack~1-0ubuntu1) but 3.5.2-2ubuntu4.2 is to be installed

finally, i have found this thread:
[http://ubuntuforums.org/archive/index.php/t-422791.html](http://ubuntuforums.org/archive/index.php/t-422791.html)

at the bottom the solution was to access this URL:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

...which no longer resolves.

can someone help me get Eclipse going for Ubuntu 10.4?

thanks.

---

### Post by ToFue on 2010-12-04
Rule out apt as the culprit (overkill method).

Verify that all repos are correct; the default repos should provide it though. 
Purge the previous install attempts.
Clean the repo & package data:
```

$ sudo apt-get autoremove
$ sudo apt-get autoclean
$ sudo apt-get check
$ sudo apt-get update

then install:

$ sudo apt-get --fix-broken --install-recomends install eclipse 
```

Do you get the same results under Synaptic Package Manager? Consider using that instead of apt-get, just lick the checkbox for eclipse, then visually verify the package versions if you wish (shouldn't be nescessary)

In Synaptic, once you click 'eclipse' all nessesary packages should select automatically.. don't limit to Just eclipse-platform, for instance (it's just the framework with no real function for what you need to do)

It's possible that eclipse's mirrors for dependencies were down, or not linked correctly- that would be a goof by the maintainer.. but if installing source, you can retrieve and build the dependancy tree from source using apt.. see " ```
$ info apt-get
```

If all else fails, you could d/l all the source for all the dependancies & their dependancies, compiling to each's instruction, in accordance to eclipse's instructions.. (README's within the extracted source directory)... or convince your professor to let you use netbeans :p

---

### Post by ubscott on 2010-12-05
hi ToFue,

your commands worked like a charm.  i have a lot of output and no error messages.  so, i think i'm ready to use Eclipse.

thanks!

---

### Post by ToFue on 2010-12-30
Awesome! Glad to help! :guitar:

---

### Post by MattJ100 on 2011-04-09
Unfortunately ToFue's commands did not solve the problem for me.

Like a number of people at the start of the thread, I too have ant1.8 installed.

I managed to install eclipse with aptitude instead, simply:

```
sudo aptitude install eclipse
```

Which informed me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  ant1.8 
The following NEW packages will be installed:
  ant{a} ant-gcj{a} eclipse eclipse-jdt{a} eclipse-pde{a} eclipse-platform{a} eclipse-platform-data{a} 
  eclipse-plugin-cvs{a} gcj-4.4-base{a} gcj-4.4-jre-lib{a} jarwrapper{a} junit{a} junit4{a} libasm3-java{a} 
  libcommons-beanutils-java{a} libcommons-codec-java{a} libcommons-collections3-java{a} libcommons-compress-java{a} 
  libcommons-digester-java{a} libcommons-el-java{a} libcommons-httpclient-java{a} libcommons-logging-java{a} 
  libdb-je-java{a} libdb4.7-java{a} libdb4.7-java-gcj{a} libecj-java{a} libgcj-bc{a} libgcj-common{a} libgcj10{a} 
  libhamcrest-java{a} libjasper-java{a} libjetty-java{a} libjline-java{a} libjsch-java{a} libjtidy-java{a} 
  liblucene2-java{a} libregexp-java{a} libservlet2.4-java{a} libslf4j-java{a} realpath{a} sat4j{a} 
0 packages upgraded, 41 newly installed, 0 to remove and 51 not upgraded.
Need to get 147MB/169MB of archives. After unpacking 232MB will be used.
The following packages have unmet dependencies:
  ant1.8: Conflicts: ant but 1.7.1-4ubuntu1.1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
ant1.8
ant1.8-optional

Install the following packages:
ant-optional [1.7.1-4ubuntu1.1 (lucid-updates, lucid-security)]
ant-optional-gcj [1.7.1-4ubuntu1.1 (lucid-updates, lucid-security, now)]

Score is -190

Accept this solution? [Y/n/q/?] 

```

After choosing Y and letting it do its business I now have a working Eclipse.

---

### Post by mathuin on 2011-05-24
Unfortunately these solutions do not work for me.  I need to use ant 1.8 for one project and eclipse for another.  What do I need to do to convince eclipse that the ant1.8 package complies with its ant requirements?

Thank you in advance!

Jack.

---

### Post by GeorgeGW on 2011-06-04
I have exactly same problem. Android development toolkit requires ant1.8. 

But sudo apt-get command installed eclipse use ant 1.7.1, which was messed up by installation of ant1.8. 

I have not tried to run sudo apt-get eclipse again thinking that it will break the ant1.8 and ADK 

Is there any expert can weigh in on this issue?



Mathuin>  Did you figure out something?

---

### Post by mathuin on 2011-06-04
I'm currently doing this completely lame workaround of running eclipse from the command line after downloading it to my home directory. :-(

Jack.

---

### Post by GeorgeGW on 2011-06-05
mathuin>  I think that might be the only way to go before the standard synaptic package upgraded to newer versions.  Thanks for confirming such work around.

---

