---
title: "installing saxon and rxp"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by maverick_iceman on 2010-01-06
Hi guys,

I am new to ubuntu just my toes here after being a windows addict for long. I am not sure if this is the correct forum so please guide me if this post should be some where else. 

I am trying to install rxp [http://www.cogsci.ed.ac.uk/~richard/rxp.html]("http://www.cogsci.ed.ac.uk/%7Erichard/rxp.html") and saxon [http://saxon.sourceforge.net/](http://saxon.sourceforge.net/) on my pc which has ubuntu 9.10  (64 bit) dual boot with windows vista.

The problem is I do not know much know how about how to build from source. I tried searching in synaptic package manager for the above two packages but could not find them ( may be I am not looking at right place ). Also on the net I was unable to find a debian packages for these two that I have observed most of the times used by ubuntu.

I tried googling on how to install the above for ubuntu with few results like this one [http://home.uchicago.edu/~quinnc/cocoon_on_ubuntu.html]("http://home.uchicago.edu/%7Equinnc/cocoon_on_ubuntu.html") says me to install cocoon first. Another one [http://ubuntuforums.org/showthread.php?t=356214](http://ubuntuforums.org/showthread.php?t=356214) just tells about sudo apt-get install libsaxon-java. But when I run this command it says latest version of saxon is already present. Further when i try commands like java -jar saxon.jar something.xml some.xsl I get error of somthing like not found. 

I also tried downloading the packages and then unzipping them in my java folder ( here also I am confused which java folder are they talking about ) . I found three of them in /etc like just Java then java-6-openjdk and java-6-sun. Then again in  /usr/lib folder java, java-wrappers,jini,jvm same folders in usr/lib64/. I am confused as to where should I extract those jar files and another thing. It says you do not have permissions to do any changes in those folders.

If some body can guide on how to go about it. In windows where all the programs are kept like in C:\Program Files and there you can do anything. So such a restriction in ubuntu was puzzling for me.

Cheers

---

### Post by daniloviz on 2010-01-08
Same problem here with Saxon... 

```

# apt-get install libsaxon-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsaxon-java is already the newest version.

# java -version 
java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) Client VM (build 14.3-b01, mixed mode, sharing)

```

But Tomcat doesn't see Saxon...
and code link this is just printed out on the screen instead of showing the content of the XML file...
```

<html> 
<body>
  List of titles in this catalog:
  <br/>
  <ul>
  {
		for $x in doc("catalog.xml")/catalog/cd/title
        order by $x
        return <li>{data($x)}</li>
  }
  </ul>
</body>
</html>

```

Any help?
Thank you
DV

---

