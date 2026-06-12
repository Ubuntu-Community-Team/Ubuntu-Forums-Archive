---
title: "Problems with Installation of new softwares"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by adisarun on 2012-01-05
[FONT=Verdana]I have been using Ubuntu 11.10 for a few months.[/FONT] Recently am getting problems with installation of any new softwares. Even thought the internet connection is fine, it shows me the following message:

"Failed to download packages. Check you internet connection"

and following that error a pop up window appears repeatedly with the following message until I close the Ubuntu Software Center.

"Requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources."

It would be greatly helpful, if anyone guides me to fix this problem at the earliest.

NOTE: I get may errors while trying to update the system from Terminal like "Something wicked has happened. Failed to fetch...".

Kindly offer your suggestions.

---

### Post by Bucky Ball on 2012-01-05
What exactly are you attempting to install?

My advice would be to use a stable release but someone else may have a fix for your 11.10 probs ... 

Welcome to the forums. ;)

---

### Post by ddales on 2012-01-05
You can also get this error message when your clock is off.  I know it may sound silly but it happened to me.  I set the clock to the correct time and the error went away.

---

### Post by adisarun on 2012-01-05
To start with, I encountered problems from the time I tried to install an anti-virus. Initially I tried with Clam that comes with Ubuntu but failed to install it completely. Later I used Mark for Complete Removal option in Synaptic Package Manager and removed it. Now I have no anti-virus in my system.

I attempted to install "Sudoku" game afterwards. Later I noticed that during every attempt to install a new software through Terminal or Ubuntu Software Center, I have above mentioned problems.

---

### Post by mactonweb on 2012-01-05
Even i'm facing the same problem error with new installations.

---

### Post by drsrinivas294 on 2012-01-06
Me too facing the same problem from past 2 days

---

### Post by oldos2er on 2012-01-06
> **adisarun said:**
> I attempted to install "Sudoku" game afterwards. Later I noticed that during every attempt to install a new software through Terminal or Ubuntu Software Center, I have above mentioned problems.

Can you post the output from ```
sudo apt-get update
``` here?

---

### Post by adisarun on 2012-01-06
arun@arun:~$ sudo apt-get update
[sudo] password for arun: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                   
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                       
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                           
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                           
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources/DiffIndex                                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex                                      
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                   
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex           
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                  
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex            
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                                                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_IN                                            
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en         
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                       
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_IN             
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_IN](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en](http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IN](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IN)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_IN](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
arun@arun:~$

---

### Post by raja.genupula on 2012-01-07
Hi Arun

Open your update manager -> settings -> in the 1st tab at download from change your server to other mirror and try again.

Have you changed any internet settings of your software sources recently ? 

All the best .

---

### Post by adisarun on 2012-01-07
Guys,

Its highly disheartening that the problem persists even after I have erased the existing Ubuntu 11.10 and reinstalled Ubuntu 11.04.

Again there is no problem with Internet connection. But when I give sudo apt-get update, the same errors listed above appears. Still I could not install anything from software center, even vlc player.

I am badly in need of guidance from you all. Please help me.

---

### Post by raja.genupula on 2012-01-07
Hi Arun
Check this

1 open **terminal**
2.type **sudo gedit /etc/resolv.conf**
3. there after **nameserver** check weather you have proper DNS or not . If not then please type your DNS  Address and save then close it.


then try again with **sudo apt-get update** .

All the Best Arun and let me know what you got .

---

