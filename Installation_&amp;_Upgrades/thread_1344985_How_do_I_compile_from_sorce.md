---
title: "How do I compile from sorce???"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by jitup on 2009-12-03
Hello, I tried to follow the guides it did not work. I have Ubuntu Studio 9.10 and I am trying to compile my first program from sorce. I am trying to install cinelerra 4.1. If it makes any differance, I am running in 64 bit. Thank you

---

### Post by Some Penguin on 2009-12-03
What does "did not work" mean?  Show some commands and error messages.

---

### Post by M!K3_$ on 2009-12-03
[https://wiki.ubuntu.com/CompilingSoftware]("https://wiki.ubuntu.com/CompilingSoftware")

basically just download the source. untar it.
```
tar -xvf bla.zar.gz
```

then
```
./configure
```

then
```
make
```

finally
```
sudo make install
```

---

### Post by jitup on 2009-12-03
when I try these 
[PHP]sudo apt-get install build-essentialand in order to run the configure and autogen.sh files that come with many programs: 

sudo apt-get install automakeFinally, you will need CheckInstall to safely insert your program in your system: 

sudo apt-get install checkinstall[/PHP]
it says un avalible

when I try 
```
./cinelerra
``` it says directory dose not exist
I put it in my home file

---

### Post by M!K3_$ on 2009-12-03
> **jitup said:**
> when I try these 
[PHP]sudo apt-get install build-essentialand in order to run the configure and autogen.sh files that come with many programs: 

sudo apt-get install automakeFinally, you will need CheckInstall to safely insert your program in your system: 

sudo apt-get install checkinstall[/PHP]
it says un avalible

when I try 
```
./cinelerra
``` it says directory dose not exist
I put it in my home file

can you reword post. your "code" block seems to be wrong.

---

### Post by jitup on 2009-12-04
when I try
```
sudo apt-get install build-essentialand 
sudo apt-get install 
sudo apt-get install checkinstall
```
it fails and says something about unavalible or outdated

and when I try
```
./cinelerra
```
it says directory dose not exist when I untared it in my home folder

---

### Post by oldos2er on 2009-12-04
The proper command would be ```
sudo apt-get update && sudo apt-get install build-essential automake checkinstall
```

 This will enable you to compile source code.

---

### Post by jitup on 2009-12-04
I found out that I do have a txt editor, gedit. so I ran the code above and this is what I got.
```
jim@ubuntu:~$ &#65279;sudo apt-get update && sudo apt-get install build-essential automake checkinstall
sudo: command not found
jim@ubuntu:~$ 




```

What did I do wrong??

---

### Post by M!K3_$ on 2009-12-04
> **jitup said:**
> I found out that I do have a txt editor, gedit. so I ran the code above and this is what I got.
```
jim@ubuntu:~$ &#65279;sudo apt-get update && sudo apt-get install build-essential automake checkinstall
sudo: command not found
jim@ubuntu:~$ 




```

What did I do wrong??

i think you only need 1 sudo.
or you could do each command separately

---

### Post by jitup on 2009-12-04
ok, this time I ran 
```
sudo apt-get install build-essential automake checkinstall
```

and I got this
```
jim@ubuntu:~$ sudo apt-get install build-essential automake checkinstall
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
jim@ubuntu:~$ 



```
what dose this mean???
I appreciate all the help

---

### Post by oldos2er on 2009-12-04
Check System, Administration, Software Sources, and make sure you have all repositories enabled.

---

### Post by oldos2er on 2009-12-04
> **M!K3_$ said:**
> i think you only need 1 sudo.

 No, you need both when using "&&".

---

### Post by jitup on 2009-12-04
ok I ran it again after enabling the cd and this is what I got
```
jim@ubuntu:~$ sudo apt-get update && sudo apt-get install build-essential automake checkinstall
[sudo] password for jim: 
Ign cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/main Translation-en_US
Ign cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/multiverse Translation-en_US
Ign cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/universe Translation-en_US
Err http://security.ubuntu.com karmic-security Release.gpg                     
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/main Translation-en_US          
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/restricted Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/universe Translation-en_US      
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com karmic Release.gpg                            
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates Release.gpg  
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done                                
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/main Packages (/var/lib/apt/lists/Ubuntu-Studio%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027)_dists_karmic_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/multiverse Packages (/var/lib/apt/lists/Ubuntu-Studio%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027)_dists_karmic_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/restricted Packages (/var/lib/apt/lists/Ubuntu-Studio%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027)_dists_karmic_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 9.10 _Karmic Koala_ - Release amd64 (20091027) karmic/universe Packages (/var/lib/apt/lists/Ubuntu-Studio%209.10%20%5fKarmic%20Koala%5f%20-%20Release%20amd64%20(20091027)_dists_karmic_universe_binary-amd64_Packages)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate


```

I am unable to get internet on the computer, so if possible send me a link to what ever needs downloaded and I will go to the liberary and download it.

---

### Post by oldos2er on 2009-12-05
> **jitup said:**
> I am unable to get internet on the computer, so if possible send me a link to what ever needs downloaded and I will go to the liberary and download it.


 You could try Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)).

---

