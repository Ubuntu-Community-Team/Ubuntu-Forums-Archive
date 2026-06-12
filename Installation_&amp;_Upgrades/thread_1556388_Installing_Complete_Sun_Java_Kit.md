---
title: "Installing Complete Sun Java Kit"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2010-08-19
I'm running latest Ubuntu 10.04. I have to install an Informix database, and it requires full-blown java from sun. Whatever Java is installed, it's not good enough for the install. I'm a little confused by Sun's instructions. Would someone point me to Java install instructions here or as an alternative what to download in synaptic or apt-get?

tnx
cmn

---

### Post by oldfred on 2010-08-19
My update script included Java but I now have commented it out.

# Java - Sun/Oracle non-free use std openjdk-6-jdk
#[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

#add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
#sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
#sudo apt-get install sun-java6-bin sun-java6-jdk  
#sudo update-java-alternatives -s java-6-sun

---

### Post by cmnorton on 2010-08-19
Thanks. I'll try this out.

---

### Post by cmnorton on 2010-09-01
> **oldfred said:**
> My update script included Java but I now have commented it out.

# Java - Sun/Oracle non-free use std openjdk-6-jdk
#[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

#add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
#sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
#sudo apt-get install sun-java6-bin sun-java6-jdk  
#sudo update-java-alternatives -s java-6-sun

I got this when I entered the second command.

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

Any ideas on what to do to get around it?

---

### Post by oldfred on 2010-09-01
I had to remove comment and run as sudo, but I just reran the commands and they still work for me.

---

### Post by TBABill on 2010-09-01
Just as easy to mark all the open source java in Synaptic for removal, click apply to remove then, and then install Sun Java, also within Synaptic.

---

### Post by mozkill on 2010-09-03
> **TBABill said:**
> Just as easy to mark all the open source java in Synaptic for removal, click apply to remove then, and then install Sun Java, also within Synaptic.


Sun Java is not an option in Synaptic (default install of Ubuntu 10.4 x64).   What is the Java repository URL you are using?

---

### Post by cmnorton on 2010-09-03
Offhand I don't know. I'm running 10.04, and did manage to get some Sun java installed.

---

### Post by oldfred on 2010-09-03
In system, administration, software sources
I have check off all four choices on page one -main, universe, restricted, multiverse and included one page 2 partners.

---

### Post by QIII on 2010-09-03
Activate the Lucid partner repository.   Java is there.

It's on the "Other Software" tab in Software Sources.

You need to be aware that the version in the partner repository (last I looked) is Update 20.  The current version is Update 21.  

You can either install Update 20 from the repo (much easier) and use it, or you can follow these instructions to install Update 21 if you absolutely must have Update 21:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

The "uninstall" instructions from the URL I cited are very easy, so you  can back it out easily if the partner repo is updated with Update 21.

If you do this per the URL, you will need to install the JDK directly from the Java website.  If you do it that  way, I'd install the JDK in your /home so you can get rid of it easily  if you want to remove it and use the repo to install all the sun-java6  packages.  Just be aware that any IDE you have linked to that JDK will  have to have the path updated.

---

### Post by cmnorton on 2010-09-03
Will get back to it Tuesday, and will find that out. tnx

---

