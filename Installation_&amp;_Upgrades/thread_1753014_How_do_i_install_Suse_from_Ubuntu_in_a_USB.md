---
title: "How do i install Suse from Ubuntu in a USB?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Nichijou on 2011-05-08
Hi there! i wanna know how i can install Suse the last version from Ubuntu 11.04 into a USB to boot and intall it,so what should i do??? :confused:

---

### Post by lmarmisa on 2011-05-08
Try to use UNetbootin:

```

sudo apt-get install unetbootin

```

---

### Post by Nichijou on 2011-05-08
it tyed to do that but it appears this 
> nichijou@nichijou-EasyNote-MZ36:~$ sudo apt-get install unetbootin
[sudo] password for nichijou: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.24-1build0.10.10.1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
 unetbootin : Depends: p7zip-full but it is not going to be installed
              Depends: extlinux but it is not going to be installed
              Recommends: unetbootin-translations (>= 549-1~getdeb2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
nichijou@nichijou-EasyNote-MZ36:~$ 




---

### Post by lmarmisa on 2011-05-08
Have you tried to run the proposed command?

```

sudo apt-get -f install

```

---

### Post by Nichijou on 2011-05-08
> Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                    
 &#9474;                                                                             
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)             
 &#9474;                                                                             
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM      
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON    
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE    
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY      
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE     
 &#9474; TERMS OF THE AGREEMENT.                                                     
 &#9474;                                                                             
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary       
 &#9474;     form, any other machine readable materials including, but not           
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               



how can i i press ok ( pressing enter button does not funnction)

---

### Post by lmarmisa on 2011-05-08
> **Nichijou said:**
> how can i i press ok ( pressing enter button does not funnction)

Maybe Tab or arrows can help you.

---

### Post by Nichijou on 2011-05-09
yeah was that... im so n00b,anyway, Thanks a lot!

---

