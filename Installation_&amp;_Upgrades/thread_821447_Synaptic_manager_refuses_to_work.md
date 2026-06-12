---
title: "Synaptic manager refuses to work"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by ultimate_aektzis on 2008-06-07
Hi guys.Some days before I 've tried to download the sun-javadoc via the terminal but it shows me the following message

```
[Press RETURN to try again, 'no' + RETURN to abort] 
```

I pressed no.The day after, synaptic update manager asked me to download some updates.then I opened the terminal window as I am used to doing it, to see the process of the updates and it showed me the above message.I pressed no the update process was continued but after some time an error appeared claiming that the update process failed.When some time has passed an attention-icon appeared as in the following picture.The question is what can I do to get rid of the ```
[Press RETURN to try again, 'no' + RETURN to abort] 
``` message.I would be very grateful if someone could help me.
Thanks in advance

---

### Post by Nikitas350 on 2008-06-07
Try running this in terminal:
sudo dpkg --configure -a
sudo apt-get update
If any "strage" output is appeared post it here....

---

### Post by ultimate_aektzis on 2008-06-07
My computer lamguage is greek but I am happy and lucky because you are from greece too:):)

```
periklis@p:~$ sudo dpkg --configure -a
[sudo] password for periklis: 
Sorry, try again.
[sudo] password for periklis: 
dpkg: &#951; &#960;&#949;&#961;&#953;&#959;&#967;&#942; &#964;&#951;&#962; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;&#962; &#949;&#943;&#957;&#945;&#953; &#954;&#955;&#949;&#953;&#948;&#969;&#956;&#941;&#957;&#951; &#945;&#960;&#972; &#940;&#955;&#955;&#951; &#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945;
periklis@p:~$ sudo apt-get update
Hit http://gr.archive.ubuntu.com hardy Release.gpg
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/main Translation-el                                                              
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/restricted Translation-el                                                        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/universe Translation-el                                                          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/multiverse Translation-el                                                        
&#934;&#941;&#961;&#949;:1 http://gr.archive.ubuntu.com hardy-updates Release.gpg [191B]                                                        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/main Translation-el                                                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/restricted Translation-el                                                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/universe Translation-el                                                  
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/multiverse Translation-el                                                
Hit http://gr.archive.ubuntu.com hardy Release                                                                              
&#934;&#941;&#961;&#949;:2 http://gr.archive.ubuntu.com hardy-updates Release [58,5kB]                                                          
Hit http://security.ubuntu.com hardy-security Release.gpg                                                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/main Translation-el                                                       
Hit http://gr.archive.ubuntu.com hardy/main Packages                                                                        
Hit http://gr.archive.ubuntu.com hardy/restricted Packages                                                                  
Hit http://gr.archive.ubuntu.com hardy/main Sources                                                                         
Hit http://gr.archive.ubuntu.com hardy/restricted Sources                                                                   
Hit http://gr.archive.ubuntu.com hardy/universe Packages                                                                    
Hit http://gr.archive.ubuntu.com hardy/universe Sources                                                                     
Hit http://gr.archive.ubuntu.com hardy/multiverse Packages                                                                  
Hit http://gr.archive.ubuntu.com hardy/multiverse Sources                                                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy Release.gpg                                                                          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Translation-el                                                                  
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/restricted Translation-el                                                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/universe Translation-el                                                   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/multiverse Translation-el                                                 
Hit http://security.ubuntu.com hardy-security Release                                                                       
&#934;&#941;&#961;&#949;:3 http://gr.archive.ubuntu.com hardy-updates/main Packages [90,7kB]                                                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Translation-el                                                              
&#934;&#941;&#961;&#949;:4 http://ppa.launchpad.net hardy Release [27,6kB]                                                                      
Hit http://security.ubuntu.com hardy-security/main Packages                                                                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Packages                                                                   
Hit http://security.ubuntu.com hardy-security/restricted Packages                                                      
Hit http://security.ubuntu.com hardy-security/main Sources                                                                  
Hit http://security.ubuntu.com hardy-security/restricted Sources                                                            
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Packages                                                                    
&#934;&#941;&#961;&#949;:5 http://gr.archive.ubuntu.com hardy-updates/restricted Packages [6156B]                                               
&#934;&#941;&#961;&#949;:6 http://gr.archive.ubuntu.com hardy-updates/main Sources [21,6kB]                                                     
Hit http://security.ubuntu.com hardy-security/universe Packages                                                             
Hit http://security.ubuntu.com hardy-security/universe Sources                                                              
Hit http://security.ubuntu.com hardy-security/multiverse Packages                                                           
Hit http://security.ubuntu.com hardy-security/multiverse Sources                                                            
Hit http://ppa.launchpad.net hardy/main Packages                                                                            
&#934;&#941;&#961;&#949;:7 http://gr.archive.ubuntu.com hardy-updates/restricted Sources [906B]                                                 
&#934;&#941;&#961;&#949;:8 http://gr.archive.ubuntu.com hardy-updates/universe Packages [36,9kB]                     
Hit http://ppa.launchpad.net hardy/universe Packages                                                                        
&#934;&#941;&#961;&#949;:9 http://gr.archive.ubuntu.com hardy-updates/universe Sources [6560B]                                                  
&#934;&#941;&#961;&#949;:10 http://gr.archive.ubuntu.com hardy-updates/multiverse Packages [7821B]                                     
&#934;&#941;&#961;&#949;:11 http://gr.archive.ubuntu.com hardy-updates/multiverse Sources [1234B]                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://hendrik.kaju.pri.ee gutsy Release.gpg                                                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://hendrik.kaju.pri.ee gutsy/screenlets Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://hendrik.kaju.pri.ee gutsy Release
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://hendrik.kaju.pri.ee gutsy/screenlets Packages
&#931;&#966;&#940;&#955;&#956;&#945; http://hendrik.kaju.pri.ee gutsy/screenlets Packages
  404 Not Found
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 231kB &#963;&#949; 3s (60,6kB/s)
W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.gz   404 Not Found

E: &#924;&#949;&#961;&#953;&#954;&#940; &#945;&#961;&#967;&#949;&#943;&#945; &#948;&#949;&#957; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957;, &#945;&#947;&#957;&#959;&#942;&#952;&#951;&#954;&#945;&#957; &#942; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#942;&#952;&#951;&#954;&#945;&#957; &#960;&#945;&#955;&#945;&#953;&#972;&#964;&#949;&#961;&#945; &#963;&#964;&#951; &#952;&#941;&#963;&#951; &#964;&#959;&#965;&#962;.
E: &#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#954;&#955;&#949;&#943;&#948;&#969;&#956;&#945; /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
periklis@p:~$ 


```

---

### Post by PmDematagoda on 2008-06-07
I'm sorry, but could you please translate the error message into English and post it again? I would help but I don't really understand Greek:).

---

### Post by ChameleonDave on 2008-06-07
> **PmDematagoda said:**
> I'm sorry, but could you please translate the error message into English and post it again? I would help but I don't really understand Greek:).

No need.  I don't speak Greek, but it's really rather obvious.  There is a problem with the lock file.

---

### Post by ultimate_aektzis on 2008-06-07
I will translate the greek words especially for my friend PmDematagoda:)

&#951; &#960;&#949;&#961;&#953;&#959;&#967;&#942; &#964;&#951;&#962; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;&#962; &#949;&#943;&#957;&#945;&#953; &#954;&#955;&#949;&#953;&#948;&#969;&#956;&#941;&#957;&#951; &#945;&#960;&#972; &#940;&#955;&#955;&#951; &#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945;
=the status database area is locked from another process

&#913;&#947;&#957;&#959;&#951;&#963;&#949;=ignore

&#966;&#949;&#961;&#949;=bring,move,but here  I think oit means download

&#931;&#966;&#940;&#955;&#956;&#945;=error

&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957;=downloaded

&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;=cant get/failed/failed to get,i dont know the exact translation

&#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#954;&#955;&#949;&#943;&#948;&#969;&#956;&#945;=unable to lock


If you have any more questions just ask me:)

---

### Post by ChameleonDave on 2008-06-07
I suspect that deleting the lock file will help.

```
sudo rm /var/cache/apt/archives/lock
```

I assume that you are making sure that you are using only one program at once to handle software packages.

---

### Post by Nikitas350 on 2008-06-07
Yes, the problem is with the lock file. Maybe because you have synaptic  opened. But the initial problem was different. Try close synaptic and re-run the command i wrote before...

---

### Post by ultimate_aektzis on 2008-06-07
> **Nikitas350 said:**
> Yes, the problem is with the lock file. Maybe because you have synaptic  opened. But the initial problem was different. Try close synaptic and re-run the command i wrote before...

I ve done what you said but results are pretty the same with previous ones.
I have also deleted the lock file with the above command.Whats next?

---

### Post by ultimate_aektzis on 2008-06-07
After deleting the lock file I ran update manager and I took the following message in a popup window 
```
The repository may no longer be available or could not be contacted because of network problems. 
If available an older version of the failed index will be used. 
Otherwise the repository will be ignored. 
Check your network connection and ensure the repository address in the preferences is correct.
```

---

### Post by ChameleonDave on 2008-06-07
> **ultimate_aektzis said:**
> After deleting the lock file I ran update manager and I took the following message in a popup window 
```
The repository may no longer be available or could not be contacted because of network problems. 
If available an older version of the failed index will be used. 
Otherwise the repository will be ignored. 
Check your network connection and ensure the repository address in the preferences is correct.
```
Well, do what it says.

1) Is your internet connection working fine?  Try updating again.

2) Do you have a dodgy repository that you've added to your */etc/apt/sources.list*?

---

### Post by zvacet on 2008-06-08
@ **ultimate_aektzis**

You have third party repos for Gutsy in your source list.Change gutsy to hardy or comment that repos (put # sign in front of them).Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ultimate_aektzis on 2008-06-08
> **ChameleonDave said:**
> Well, do what it says.

1) Is your internet connection working fine?  Try updating again.

2) Do you have a dodgy repository that you've added to your */etc/apt/sources.list*?

1.yes!!
2.How can I remove it from my list?

---

### Post by Nikitas350 on 2008-06-08
Did you have a network connection active? If you had one the post here the contents of /etc/apt/sources.list.

---

### Post by Pumalite on 2008-06-08
Backup your list first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list
Put a # in front of any line you deem inappropriate.(Gutsy or others)
Save, exit.
Run:
sudo apt-get update
sudo apt-get upgrade

---

### Post by ultimate_aektzis on 2008-06-08
I found the gutsy repos and I "commented" them.After I ran 
```

sudo apt-get update
sudo apt-get upgrade 
```
but I saw a strange message telling me to run dpkg --configure -a.
When I did it the problem appeared once more,as you can see 
It wants me to download javadoc but I dont want to.How can I instruct it to cancel the download permanently???I think that this will solve the problem

```
periklis@p:~$ sudo apt-get update
Hit http://gr.archive.ubuntu.com hardy Release.gpg
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/main Translation-el                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/restricted Translation-el           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/universe Translation-el             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/multiverse Translation-el           
Hit http://gr.archive.ubuntu.com hardy-updates Release.gpg                     
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/main Translation-el         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/restricted Translation-el   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/universe Translation-el     
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/multiverse Translation-el   
Hit http://gr.archive.ubuntu.com hardy Release                                 
Hit http://security.ubuntu.com hardy-security Release.gpg                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/main Translation-el          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Translation-el                     
Hit http://playonlinux.botux.net hardy Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Translation-el                 
Hit http://gr.archive.ubuntu.com hardy-updates Release                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Translation-el                 
Hit http://gr.archive.ubuntu.com hardy/main Packages                           
&#934;&#941;&#961;&#949;:1 http://ppa.launchpad.net hardy Release [27,6kB]                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/restricted Translation-el    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/universe Translation-el      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/multiverse Translation-el    
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://playonlinux.botux.net hardy Release                                 
Hit http://gr.archive.ubuntu.com hardy/restricted Packages                     
Hit http://gr.archive.ubuntu.com hardy/main Sources                            
Hit http://gr.archive.ubuntu.com hardy/restricted Sources                      
Hit http://gr.archive.ubuntu.com hardy/universe Packages                       
Hit http://gr.archive.ubuntu.com hardy/universe Sources                        
Hit http://gr.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://gr.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://gr.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://gr.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://gr.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://gr.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://gr.archive.ubuntu.com hardy-updates/universe Packages               
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Packages                           
Hit http://gr.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://gr.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://gr.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://security.ubuntu.com hardy-security/main Packages                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Packages                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Packages                       
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://playonlinux.botux.net hardy/main Packages                           
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://ppa.launchpad.net hardy/universe Packages                           
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 1B &#963;&#949; 0s (1B/s)               
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
periklis@p:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
periklis@p:~$ dpkg --configure -a
dpkg: &#951; &#950;&#951;&#964;&#959;&#973;&#956;&#949;&#957;&#951; &#949;&#957;&#941;&#961;&#947;&#949;&#953;&#945; &#945;&#960;&#945;&#953;&#964;&#949;&#943; &#960;&#961;&#959;&#957;&#972;&#956;&#953;&#945; &#965;&#960;&#949;&#961;&#967;&#961;&#942;&#963;&#964;&#951;
periklis@p:~$ sudo  dpkg --configure -a
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; sun-java6-doc (--configure):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 1
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 sun-java6-doc
periklis@p:~$ 

```

---

### Post by Pumalite on 2008-06-08
Run:
sudso dpkg --configure -a
Post the output

---

### Post by ultimate_aektzis on 2008-06-08
Hmm,there is no susdo command.You are probably mean sudo...

```
periklis@p:~$ sudo dpkg --configure -a
[sudo] password for periklis: 
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; sun-java6-doc (--configure):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 1
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 sun-java6-doc
periklis@p:~$ 


```

---

### Post by Pumalite on 2008-06-08
Run:
sudo apt-get -f install
Post the output.

---

### Post by zvacet on 2008-06-08
In **system>admin<software sources** change server to main and try to install  **sun-java6-doc** with synaptic.

---

### Post by ultimate_aektzis on 2008-06-08
I noticed that it prompts me to use apt-get remove:confused::confused:

```
periklis@p:~$ sudo apt-get -f install
[sudo] password for periklis: 
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#960;&#959;&#965; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#959;&#957;&#964;&#945;&#953; &#960;&#953;&#945;:
  libseda-java libcommons-cli-java circuslinux-data etw-data
  libcommons-lang-java
&#935;&#961;&#951;&#963;&#956;&#959;&#960;&#959;&#953;&#942;&#963;&#964;&#949; &#964;&#959; 'apt-get autoremove' &#947;&#953;&#945; &#957;&#945; &#964;&#945; &#945;&#960;&#959;&#956;&#945;&#954;&#961;&#973;&#957;&#949;&#964;&#949;
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
1 &#956;&#951; &#960;&#955;&#942;&#961;&#969;&#962; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945; &#942; &#945;&#966;&#945;&#953;&#961;&#941;&#952;&#951;&#954;&#945;&#957;.
After this operation, 0B of additional disk space will be used.
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; sun-java6-doc (--configure):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 1
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
periklis@p:~$ 

```

---

### Post by ultimate_aektzis on 2008-06-08
@zvacet
Do you mean to uncheck all boxes except from universe?(take a look in the image)
sorry for too many questions but I am a bit new and I dont want to make matters worse now

---

### Post by Pumalite on 2008-06-08
You are going to have to uninstall and reinstall java:
You could try:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install <packagename>

---

### Post by ultimate_aektzis on 2008-06-08
I have ran those commands the update process worked fine but when I did sudo apt-get install muine the annoyning message is appeared again.What about "kill" command.Will it help me to treminate the javadoc downloading??

```
periklis@p:~$ sudo apt-get clean
periklis@p:~$ sudo apt-get autoclean
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
periklis@p:~$ sudo apt-get update
Hit http://gr.archive.ubuntu.com hardy Release.gpg
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/main Translation-el                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/restricted Translation-el           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/universe Translation-el             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy/multiverse Translation-el           
Hit http://gr.archive.ubuntu.com hardy-updates Release.gpg                     
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/main Translation-el         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/restricted Translation-el   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/universe Translation-el     
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://gr.archive.ubuntu.com hardy-updates/multiverse Translation-el   
Hit http://gr.archive.ubuntu.com hardy Release                                 
Hit http://gr.archive.ubuntu.com hardy-updates Release                         
Hit http://gr.archive.ubuntu.com hardy/main Packages                           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Translation-el                     
Hit http://security.ubuntu.com hardy-security Release.gpg                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/main Translation-el          
Hit http://playonlinux.botux.net hardy Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Translation-el                 
Hit http://gr.archive.ubuntu.com hardy/restricted Packages                     
Hit http://gr.archive.ubuntu.com hardy/main Sources                            
Hit http://gr.archive.ubuntu.com hardy/restricted Sources                      
Hit http://gr.archive.ubuntu.com hardy/universe Packages                       
Hit http://gr.archive.ubuntu.com hardy/universe Sources                        
Hit http://gr.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://gr.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://gr.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://gr.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://gr.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://gr.archive.ubuntu.com hardy-updates/restricted Sources              
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Translation-el                 
Hit http://gr.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://gr.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://gr.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://gr.archive.ubuntu.com hardy-updates/multiverse Sources              
&#934;&#941;&#961;&#949;:1 http://ppa.launchpad.net hardy Release [27,6kB]                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/restricted Translation-el    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/universe Translation-el      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://security.ubuntu.com hardy-security/multiverse Translation-el    
Hit http://playonlinux.botux.net hardy Release                                 
Hit http://security.ubuntu.com hardy-security Release                          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Packages                           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Packages                       
Hit http://security.ubuntu.com hardy-security/main Packages                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Packages                       
Hit http://playonlinux.botux.net hardy/main Packages                           
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://ppa.launchpad.net hardy/universe Packages
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 1B &#963;&#949; 0s (1B/s)               
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
periklis@p:~$ sudo apt-get install muine
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
&#964;&#959; muine &#949;&#943;&#957;&#945;&#953; &#942;&#948;&#951; &#951; &#964;&#949;&#955;&#949;&#965;&#964;&#945;&#943;&#945; &#941;&#954;&#948;&#959;&#963;&#951;.
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#960;&#959;&#965; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#959;&#957;&#964;&#945;&#953; &#960;&#953;&#945;:
  libseda-java libcommons-cli-java circuslinux-data etw-data
  libcommons-lang-java
&#935;&#961;&#951;&#963;&#956;&#959;&#960;&#959;&#953;&#942;&#963;&#964;&#949; &#964;&#959; 'apt-get autoremove' &#947;&#953;&#945; &#957;&#945; &#964;&#945; &#945;&#960;&#959;&#956;&#945;&#954;&#961;&#973;&#957;&#949;&#964;&#949;
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
1 &#956;&#951; &#960;&#955;&#942;&#961;&#969;&#962; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945; &#942; &#945;&#966;&#945;&#953;&#961;&#941;&#952;&#951;&#954;&#945;&#957;.
After this operation, 0B of additional disk space will be used.
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

---

### Post by Pumalite on 2008-06-08
From the output:

'You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

---

### Post by ultimate_aektzis on 2008-06-08
ok but I cant understand what ```
The file should be owned by root.root and be copied
to /tmp.
```
means,what is root.root??

---

### Post by Pumalite on 2008-06-08
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zvacet on 2008-06-08
@** ultimate_aektzis**

Keep all checked but change server(you are geting updates from Greek server now) to main.I don´t know if that will be helpful.

---

### Post by ultimate_aektzis on 2008-06-09
Ok guyz I found the solution...the only necessary things were some no'z and a remove command.**I would like to thank all buddies who were willing to help me,and they did it a lot...**
C ya

---

### Post by Pumalite on 2008-06-09
Could you give us an account of how you solved your problem, so others could benefit from it?

---

### Post by ultimate_aektzis on 2008-06-10
If I remember well,when the annoyng message appeard I pressed no and closed the terminal.I opened a new terminal and I ran ```
 
 sudo apt-get remove sun-java6-doc


```
After that synaptic update manager works fine,as well as previous.
Take a look at the following example

```
periklis@p:~$ sudo apt-get update
[sudo] password for periklis: 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy Release.gpg
Hit http://archive.ubuntu.com hardy Release.gpg                                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy/main Translation-el                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Translation-el                     
Hit http://playonlinux.botux.net hardy Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Translation-el                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Translation-el                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy/restricted Translation-el              
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy/universe Translation-el                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy/multiverse Translation-el              
&#934;&#941;&#961;&#949;:1 http://archive.ubuntu.com hardy-updates Release.gpg [191B]              
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-updates/main Translation-el            
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-updates/restricted Translation-el      
Hit http://playonlinux.botux.net hardy Release                                 
&#934;&#941;&#961;&#949;:2 http://ppa.launchpad.net hardy Release [27,6kB]                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-updates/universe Translation-el        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-updates/multiverse Translation-el
Hit http://archive.ubuntu.com hardy-security Release.gpg         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-security/main Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-security/restricted Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-security/universe Translation-el       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://archive.ubuntu.com hardy-security/multiverse Translation-el     
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/main Packages                           
Hit http://archive.ubuntu.com hardy Release                                    
&#934;&#941;&#961;&#949;:3 http://archive.ubuntu.com hardy-updates Release [58,5kB]                
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://playonlinux.botux.net hardy/main Packages                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; http://ppa.launchpad.net hardy/universe Packages                       
Hit http://playonlinux.botux.net hardy/main Packages                           
Hit http://ppa.launchpad.net hardy/main Packages                          
Hit http://ppa.launchpad.net hardy/universe Packages                      
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy/main Packages                 
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
&#934;&#941;&#961;&#949;:4 http://archive.ubuntu.com hardy-updates/main Packages [205kB]
&#934;&#941;&#961;&#949;:5 http://archive.ubuntu.com hardy-updates/restricted Packages [6156B]
&#934;&#941;&#961;&#949;:6 http://archive.ubuntu.com hardy-updates/universe Packages [41,9kB]
&#934;&#941;&#961;&#949;:7 http://archive.ubuntu.com hardy-updates/multiverse Packages [7687B]
Hit http://archive.ubuntu.com hardy-security/main Packages        
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 319kB &#963;&#949; 2s (120kB/s)                
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
periklis@p:~$ 

```


Concluding, update manager refused to work due to the pending installation.

---

### Post by Pumalite on 2008-06-10
Thanks.

---

