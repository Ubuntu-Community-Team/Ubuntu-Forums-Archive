---
title: "Need Help With Sun Java 6 Ubuntu"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by explicit10 on 2008-04-30
Ok ive been trying to get java for DAYS!! i cant get it...
Ive went to add/remove applications found sun java 6 and when i try to install i get the error...

Cannot install 'sun-java6-bin'

This application conflicts with other installed software. To install 'sun-java6-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

What can i do!! 

some one please help if you can it would be much appreciated.

---

### Post by ibutho on 2008-04-30
Do you have openjdk or icedtea java installed? If so, uninstall it and then install sun java.

---

### Post by chewearn on 2008-04-30
> **explicit10 said:**
> This application conflicts with other installed software. To install 'sun-java6-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.


Synaptic Package Manager can be found in:
System > Administration > Synaptic Package Manager

Open the application to find out the exact problem.

---

### Post by explicit10 on 2008-04-30
Nope, i dont think i do, neither of them was in my add/remove applications..

---

### Post by explicit10 on 2008-04-30
> **AstalaVista said:**
> Synaptic Package Manager can be found in:
System > Administration > Synaptic Package Manager

Open the application to find out the exact problem.

I have been in there i cant find the problem.. mostly becuase i have no idea what i am looking for..

---

### Post by explicit10 on 2008-04-30
if anyone else has something that might work let me know! i need to fix this asap!

---

### Post by chewearn on 2008-04-30
> **explicit10 said:**
> if anyone else has something that might work let me know! i need to fix this asap!

In synaptic package manager, search for sun-java6-bin, mark it for install, click Apply button on the toolbar.  That should give you the exact error message.

Another method, use command line:
```
sudo apt-get install sun-java6-bin
```

You can copy the output of the command, and post it here.

---

### Post by explicit10 on 2008-04-30
I get this...

sun-java6-bin:
 Depends: sun-java6-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable
 Depends: libstdc++5  but it is not installable

And then i go try to install one of the ones above like Unixodbc and i get the same error with anuther list of things it depends on..

---

### Post by explicit10 on 2008-04-30
When i enter the code in the terminal i get..

bryson@bryson-desktop:~$ sudo apt-get install sun-java6-bin
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
The following information may help resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
                 Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
E: Broken packages
bryson@bryson-desktop:~$

---

### Post by explicit10 on 2008-04-30
Some one reply please..

---

### Post by DMK62 on 2008-04-30
See if the following helps 

Make sure Synaptic is not running.

From the terminal run the following commands

sudo dpkg --configure -a 

sudo apt-get update

sudo apt-get upgrade

Open Synaptic and do a search for Sun Java , select to install sun-java6-plugin ( it will also mark the bin and jre for install and that is ok )

If you are still encountering errors then do a search for java in synaptic and post back the currently installed versions.

Dale

---

### Post by explicit10 on 2008-04-30
](*,)

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> See if the following helps 

Make sure Synaptic is not running.

From the terminal run the following commands

sudo dpkg --configure -a 

sudo apt-get update

sudo apt-get upgrade

Open Synaptic and do a search for Sun Java , select to install sun-java6-plugin ( it will also mark the bin and jre for install and that is ok )

If you are still encountering errors then do a search for java in synaptic and post back the currently installed versions.

Dale

I did all that, then went into synaptic and i dont see sun-java6-plugin.

---

### Post by explicit10 on 2008-04-30
I keep Getting told that it depends on other stuff.. so i go and try to install the other stuff then the other stuff needs other stuff.. its just a never ending circle of stuff depending on other stuff and in the end i still dont have java!! this is really anoying

---

### Post by DMK62 on 2008-04-30
It is possible that some of the files may not have been fetched properly or that there are problems with the files on the repositories you are using.

Reboot the computer.

Go to System > Admin > Software Sources and change the  download from option under the first tab to another server in your country or to Main Server ( Main Server will be slow ). Make sure Main, Universe, Restricted and Multiverse are all checked. Click close and it will ask you to reload and make sure you do that. It may take a while to complete.

Go to terminal and enter

sudo apt-get update

sudo apt-get upgrade

sudo apt-get clean

Open Synaptic and hit the reload button. Repeat my previous procedure for installing java in synaptic.

Dale

---

### Post by explicit10 on 2008-04-30
Thank you dale, i will give that a try now and post how it goes when i am done!

---

### Post by explicit10 on 2008-04-30
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.bz2:](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/main/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/restricted/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/universe/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/restricted/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/main/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/main/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/universe/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/multiverse/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/multiverse/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/main/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/main/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/main/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/restricted/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/universe/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/universe/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/multiverse/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/main/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/main/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/restricted/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/restricted/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/main/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/restricted/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/universe/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/universe/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/universe/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/multiverse/binary-amd64/Packages.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/multiverse/binary-amd64/Packages.gz:) 404 Not Found
[http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/multiverse/source/Sources.gz:](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found



Then the next error: 


An error occured

The following details are provided:

W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) gutsy Release: The following signatures were invalid: NODATA 1 NODATA 2



Tryed it twice and same thing

---

### Post by explicit10 on 2008-04-30
Bump

---

### Post by DMK62 on 2008-04-30
Still mourning the Habs loss here , sorry it took a while to get back.

Since it looks like you are in Canada try change the repositories to gulus.usherbrooke.ca . It's one of the fastest mirrors in Canada. Repeat the instructions as per my last post.

I will refresh this post to check for any further posts by you.

Dale

Do you have any idea what the dfreer entry is for ? Ok I found out it is an AMD64 repo. If the above fails you may want to remove  dfreer temporarily while you install java. It can always be added after.

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> Still mourning the Habs loss here , sorry it took a while to get back.

Since it looks like you are in Canada try change the repositories to gulus.usherbrooke.ca . It's one of the fastest mirrors in Canada. Repeat the instructions as per my last post.

I will refresh this post to check for any further posts by you.

Dale

Do you have any idea what the dfreer entry is for ? Ok I found out it is an AMD64 repo. If the above fails you may want to remove  dfreer temporarily while you install java. It can always be added after.


Just trying that now ill let you know what happens

---

### Post by explicit10 on 2008-04-30
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.bz2:](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by shakabra on 2008-04-30
Just curious, what is the output of "http:sudo update-alternatives --config java

---

### Post by shakabra on 2008-04-30
sorry take out the http:

---

### Post by explicit10 on 2008-04-30
> **shakabra said:**
> Just curious, what is the output of "http:sudo update-alternatives --config java

Not sure if i did what you were asking.. but..



bryson@bryson-desktop:~$ http:sudo update-alternatives --config java
bash: http:sudo: command not found

---

### Post by explicit10 on 2008-04-30
> **shakabra said:**
> sorry take out the http:

bryson@bryson-desktop:~$ sudo update-alternatives --config java
[sudo] password for bryson:

There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.
bryson@bryson-desktop:~$

---

### Post by DMK62 on 2008-04-30
Go to System>Admin>Software Sources and under the Third Party tab remove any reference to dfreer and do the same for Authentication and repeat the procedure with gulus.usherbrooke.ca

The do the terminal commands in my prev post and then install java with synaptic. 

Dale

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> Go to System>Admin>Software Sources and under the Third Party tab remove any reference to dfreer and do the same for Authentication and repeat the procedure with gulus.usherbrooke.ca

The do the terminal commands in my prev post and then install java with synaptic. 

Dale

Ok, i did that and it started to install and then it just closed O.o

---

### Post by shakabra on 2008-04-30
I'm kinda new at this too, but you can type " locate java"  into the terminal to find out what version you have.

---

### Post by explicit10 on 2008-04-30
+ should i have source code checked.. 

and under third party i have nothing checked.. is this right?

---

### Post by explicit10 on 2008-04-30
> **shakabra said:**
> I'm kinda new at this too, but you can type " locate java"  into the terminal to find out what version you have.

I gave it a try and i got TONS of codes pop up

---

### Post by DMK62 on 2008-04-30
Source code is fine with just a dash.

---

### Post by irunwithknives on 2008-04-30
i suggest installing azureus through Add-remove.  It came with all of the java plugins I have ever needed

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> Source code is fine with just a dash.

I think somthing worked.. i got no error!! it just closed when it was done..

---

### Post by explicit10 on 2008-04-30
> **irunwithknives said:**
> i suggest installing azureus through Add-remove.  It came with all of the java plugins I have ever needed

tryed that.. i got yet anuther error..

---

### Post by DMK62 on 2008-04-30
Then follow my instructions for installing via synaptic.

If that installs ok check it in firefox using about : plugins ( there are no spaces in that I had to space it so there was no happy emote ) in the address bar.

Dale

---

### Post by jamesstansell on 2008-04-30
Hi explicit10,

Synaptic has a "Broken" packages filter that may help you.

Based on "Depends: sun-java6-jre (= 6-03-0ubuntu2)" that you reported I guess you're running Ubuntu 7.10?  You're not 64bit are you?

Just curious - do you want Java to run applets in your web browser, or is it something else?

-james.

---

### Post by explicit10 on 2008-04-30
> **jamesstansell said:**
> Hi explicit10,

Synaptic has a "Broken" packages filter that may help you.

Based on "Depends: sun-java6-jre (= 6-03-0ubuntu2)" that you reported I guess you're running Ubuntu 7.10?  You're not 64bit are you?

Just curious - do you want Java to run applets in your web browser, or is it something else?

-james.

I want it to run frostwire.. I think it might be working now.. waiting 1 more minute for the installing.. no error so far.. so i think it might work! and yes im running on 7.10 and i am pretty sure im 64bit

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> Then follow my instructions for installing via synaptic.

If that installs ok check it in firefox using about : plugins ( there are no spaces in that I had to space it so there was no happy emote ) in the address bar.

Dale

HAHA!! i think it workeddddd!!!!! Where do i find about plugins??

---

### Post by DMK62 on 2008-04-30
With the recent release of Heron all the servers are under load and it can / does affect the other versions. I have a feeling the server he had been trying was timing out on 2 of the 6 packages needed for sun java.

The dfreer repo is for AMD64

Dale

enter the about:plugins in the address bar of Firefox , if my post has a smiley its supposed to be a :

---

### Post by explicit10 on 2008-04-30
> **DMK62 said:**
> With the recent release of Heron all the servers are under load and it can / does affect the other versions. I have a feeling the server he had been trying was timing out on 2 of the 6 packages needed for sun java.

The dfreer repo is for AMD64

Dale

enter the about:plugins in the address barof Firefox , if my post has a smiley its supposed to be a :

Ok, found the page, dont see nothing that says java.. but im pretty sure something worked!

---

### Post by jamesstansell on 2008-04-30
You type about:plugins in the URL bar in Firefox.  There is no Sun Java plugin for 64bit though.  On 7.10 you might be able to install gcjwebplugin, but you shouldn't need it for frostwire.

update-java-alternatives --jre -l

should give you something like this

java-6-sun 63 /usr/lib/jvm/java-6-sun

and /usr/bin/java -version

should give you something similar to

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by DMK62 on 2008-04-30
[http://javatester.org/version.html](http://javatester.org/version.html)

I am running 32 bit so sorry about the prev reference to the plugin. Thanks for that info James.

---

### Post by explicit10 on 2008-05-01
> **jamesstansell said:**
> You type about:plugins in the URL bar in Firefox.  There is no Sun Java plugin for 64bit though.  On 7.10 you might be able to install gcjwebplugin, but you shouldn't need it for frostwire.

update-java-alternatives --jre -l

should give you something like this

java-6-sun 63 /usr/lib/jvm/java-6-sun

and /usr/bin/java -version

should give you something similar to

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)


bryson@bryson-desktop:~$ update-java-alternatives --jre -l
java-6-sun 63 /usr/lib/jvm/java-6-sun
bryson@bryson-desktop:~$ /usr/bin/java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)
bryson@bryson-desktop:~$ 


But.. Frostwire still wont come on.. i click it and nothing comes up..

---

### Post by DMK62 on 2008-05-01
Maybe James will be able to help you out on the 64-bit part. Wish I could help further on that but my knowledge in this area is limited to 32 bit.

You might want to create a post in the X86 64-bit Users category and make sure to link to this post there.

Dale

---

### Post by explicit10 on 2008-05-01
> **DMK62 said:**
> Maybe James will be able to help you out on the 64-bit part. Wish I could help further on that but my knowledge in this area is limited to 32 bit.

You might want to create a post in the X86 64-bit Users category and make sure to link to this post there.

Dale

I think i am accualy starting to get some where! thank you for all your help man! much appreciated. same with james.. both of you have been big helps. If run into any more problems iwill post them and maybe you two can help

---

### Post by shakabra on 2008-05-01
I got frostwire working by installing java 5.  Then i ran "sudo update-alternatives --config java" and chose option #2.

---

### Post by explicit10 on 2008-05-01
Well i still cant get frostwire to work.. i click it and nothing happens.. any thoughts?

---

### Post by explicit10 on 2008-05-01
> **shakabra said:**
> I got frostwire working by installing java 5.  Then i ran "sudo update-alternatives --config java" and chose option #2.

I tryed it 

bryson@bryson-desktop:~$ sudo update-alternatives --config java
[sudo] password for bryson:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/lib/jvm/java-6-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-7-icedtea/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.


do i need 5.. becuase it still isnt working.. shouldnt 6 work too

---

### Post by DMK62 on 2008-05-01
You're welcome !

Feel free to ask as many questions as you need. It can be tough going at first to get things working ( esp with some things on 64 bit ).

Congrats on hanging in there the last few days !

Dale

---

### Post by shakabra on 2008-05-01
Run "frostwire" from the terminal and post the output.

---

### Post by c4v3m4n on 2008-05-01
This link helped me out getting it installed.  Hope it helps you.  Also i think all i need to use was this code but i gave you the link just in case.

```
$ sudo apt-get install sun-java6-bin sun-java6-jre
```
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")

---

### Post by shakabra on 2008-05-01
I think you are frostwire is using icedtea for java.  That won't work.  Try 
"sudo update-alternatives --config java" again and make sure to choose the actual non-free java 6 as your alternative.

---

### Post by explicit10 on 2008-05-01
> **shakabra said:**
> Run "frostwire" from the terminal and post the output.

how do i run it from the terminal

---

### Post by shakabra on 2008-05-01
just type "frostwire" without the quotes.

---

### Post by explicit10 on 2008-05-01
> **shakabra said:**
> just type "frostwire" without the quotes.

bryson@bryson-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aecdb29ce25, pid=10570, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as hs_err_pid10570.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125: 10570 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

---

### Post by shakabra on 2008-05-01
I am using Hardy and Java 6 wouldn't work with Frostwire.  I installed Java 5 and used that as my alternative and it worked for me.

---

### Post by explicit10 on 2008-05-01
> **shakabra said:**
> I am using Hardy and Java 6 wouldn't work with Frostwire.  I installed Java 5 and used that as my alternative and it worked for me.

ill give it a try and post my problems if i get any

---

### Post by jamesstansell on 2008-05-01
> **explicit10 said:**
> bryson@bryson-desktop:~$ frostwire
...
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15


That's a problem I haven't heard of before.  Of course, I've only run 32bit Java so far, and I'm not a frostwire user either.

I was expecting the output to show what version of frostwire you have, but it didn't.  Are you using the latest?

---

### Post by explicit10 on 2008-05-01
Changed to 5 im pretty sure and it still wont work

---

### Post by explicit10 on 2008-05-01
> **jamesstansell said:**
> That's a problem I haven't heard of before.  Of course, I've only run 32bit Java so far, and I'm not a frostwire user either.

I was expecting the output to show what version of frostwire you have, but it didn't.  Are you using the latest?

I think i am james, i just installed a few days ago.. i am open to using any other program out there to download music.. this one just the first one i herd of.. any others would be just as good..

---

### Post by jamesstansell on 2008-05-01
This may be of help:

[http://ubuntuforums.org/showpost.php?p=4805210&postcount=3](http://ubuntuforums.org/showpost.php?p=4805210&postcount=3)

As for downloading music, it's not something I've done much, but I have been happy on occasion with the miro package.

sudo apt-get install miro

Oddly enough, if it doesn't run properly one thing that might help is uninstalling Java!

---

### Post by explicit10 on 2008-05-01
> **jamesstansell said:**
> This may be of help:

[http://ubuntuforums.org/showpost.php?p=4805210&postcount=3](http://ubuntuforums.org/showpost.php?p=4805210&postcount=3)

As for downloading music, it's not something I've done much, but I have been happy on occasion with the miro package.

sudo apt-get install miro

Oddly enough, if it doesn't run properly one thing that might help is uninstalling Java!

haha uninstall!!! jeez =P i just got it haha.. Well. ill give that link a try.. i need to download music i am sick of youtube`in all my music =P

---

### Post by DMK62 on 2008-05-01
I may be going way out into left field ....

If you cannot get things to work with Java or encounter other issues you may want to consider downloading the 32 bit version of Ubuntu and install that on  your 64 bit system. From what I have heard there is a bit of loss in performance but it should install ok in most cases.

Things like flash and java are a lot more easier to install / configure with 32 bit as opposed to 64 bit. Seeing that you are new to Ubuntu and linux it is a very steep learning curve with 64 bit.

Dale

---

### Post by jamesstansell on 2008-05-01
> **jamesstansell said:**
> 
sudo apt-get install miro


Oops - I forgot you are on Ubuntu 7.10 - that's a very old package in the default repository.  Here's the developer's installation instructions:

[https://www.getmiro.com/download/ubuntu.php](https://www.getmiro.com/download/ubuntu.php)

---

### Post by shakabra on 2008-05-01
I did a little research and this appears to be similar to a known bug with Java.

---

### Post by explicit10 on 2008-05-01
OHHHH also i wanted to get somthing called beryl or somthing to work.. but i couldnt if you guys herd of this or have some experience please comment

---

### Post by jamesstansell on 2008-05-01
> **DMK62 said:**
> Things like flash and java are a lot more easier to install / configure with 32 bit as opposed to 64 bit. Seeing that you are new to Ubuntu and linux it is a very steep learning curve with 64 bit.
I pretty much echo that sentiment.  I'm an old hand with Linux and Ubuntu, but I've stayed on the 32bit versions myself so far.  Even Hardy doesn't seem to help much with these things yet for 64bit users.

There are some sticky threads in the 64bit forum that are worth looking at.

-james.

---

### Post by DMK62 on 2008-05-01
What you are referring to is now know as compiz fusion. You need to have 3 d acceleration and if you have an ATI or Nvidia video card you will need to enable the restricted drivers for that by going to System > Admin > Restricted Drivers Manager. 

You can add additional features / components to it by using synaptic and do a search for compiz.

Dale

p.s. Hoping you have a nvidia card lol.

---

### Post by explicit10 on 2008-05-01
> **jamesstansell said:**
> I pretty much echo that sentiment.  I'm an old hand with Linux and Ubuntu, but I've stayed on the 32bit versions myself so far.  Even Hardy doesn't seem to help much with these things yet for 64bit users.

There are some sticky threads in the 64bit forum that are worth looking at.

-james.

Not sure i want to go down to the 32 bit though.. i seem to be getting along now with your guys help

---

### Post by explicit10 on 2008-05-01
> **DMK62 said:**
> What you are referring to is now know as compiz fusion. You need to have 3 d acceleration and if you have an ATI or Nvidia video card you will need to enable the restricted drivers for that by going to System > Admin > Restricted Drivers Manager. 

You can add additional features / components to it by using synaptic and do a search for compiz.

Dale

p.s. Hoping you have a nvidia card lol.

Yes i bough a kick *** vid card awhile ago.. so i should be good to go with that

---

### Post by explicit10 on 2008-05-01
> **jamesstansell said:**
> This may be of help:

[http://ubuntuforums.org/showpost.php?p=4805210&postcount=3](http://ubuntuforums.org/showpost.php?p=4805210&postcount=3)

As for downloading music, it's not something I've done much, but I have been happy on occasion with the miro package.

sudo apt-get install miro

Oddly enough, if it doesn't run properly one thing that might help is uninstalling Java!

James.. what is miro, what does it do?

---

### Post by jamesstansell on 2008-05-01
> **explicit10 said:**
> James.. what is miro, what does it do?

As the webpage says "Miro 1.2 - Turn your computer into an internet TV.
Download Miro to watch free internet video channels and play any video file."

I think it probably does music too, but I guess it's really geared more toward video.

I uninstalled it during the upgrade to Hardy, and I haven't even set it up again yet.  If you haven't guessed yet, I do a lot more reading than listening or watching. :)

-james.

---

### Post by explicit10 on 2008-05-01
ahh haha i am going to give it a try.. thanks for the info.. Uhm so i just got this compiz fusion thing.. does anyone know how to work the cube and stuff?

---

### Post by DMK62 on 2008-05-01
In synaptic search for compiz and install compizconfig-settings-manager.

It will show up under System>Preferences>Advanced Desktop Settings.

You can spend weeks in the settings !!!

Dale

---

### Post by shakabra on 2008-05-01
You need to install compizconfig-settings-mangager.  This will give you a GUI, located in System>Preferences, to change to compiz settings.  Make sure that you driver is enabled.

---

### Post by explicit10 on 2008-05-01
> **shakabra said:**
> You need to install compizconfig-settings-mangager.  This will give you a GUI, located in System>Preferences, to change to compiz settings.  Make sure that you driver is enabled.

i have that.. i have the cube enabled.. i just dont know how to make it work.

---

### Post by explicit10 on 2008-05-01
> **DMK62 said:**
> In synaptic search for compiz and install compizconfig-settings-manager.

It will show up under System>Preferences>Advanced Desktop Settings.

You can spend weeks in the settings !!!

Dale

i have alot turned on.. i just not sure how most of it works..

---

### Post by DMK62 on 2008-05-01
[http://wiki.compiz-fusion.org](http://wiki.compiz-fusion.org)

That site will explain most of its functions and how to use them.

There is a lot of info there so you may end up like James and I and end up doing more reading than listening or watching ( of course excluding the Habs ) lol.

Dale

---

### Post by gh423 on 2008-05-05
I also could not get firefox to use sun-java. I tried a lot of ideas from forums, etc. It finally started to work after running:

sudo update-alternatives --config xulrunner-1.9-javaplugin.so

and selecting the line for sun java. This was using sun-java6.

I found this by running “update-alternatives -all” and selecting everything that looked like sun java. The above config option was the only one that I found that had not already been set to a sun java option by previously running update-alternatives with "--config java” and “--config jre”

---

