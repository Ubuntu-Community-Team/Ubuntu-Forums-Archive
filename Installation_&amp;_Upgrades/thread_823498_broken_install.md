---
title: "broken install"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by dwanders on 2008-06-09
Is there a way to clear a broken install? I was downloading a package (not intending to install it on my version of Ubuntu) and somehow managed to get half way installed. Now every time I run an upgrade I am getting:

subprocess post-removal script returned error exit status 100
Errors were encountered while processing:
php-java-bridge

and the program will not remove, I have tried:

sudo dpkg --remove, apt-get remove, apt-get -fix, aptitude remove, and cannot clean that bugger outa there. And ideas would be greatly appreciated.

---

### Post by Pumalite on 2008-06-09
Have a read:
[http://ubuntuforums.org/showthread.php?t=586957](http://ubuntuforums.org/showthread.php?t=586957)
[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)
[http://ubuntuforums.org/showthread.php?t=596697](http://ubuntuforums.org/showthread.php?t=596697)
[http://ubuntuforums.org/showthread.php?t=634624](http://ubuntuforums.org/showthread.php?t=634624)

---

### Post by dwanders on 2008-06-09
Is there any way to make apt/dpkg just ignore this package? 
Based on the links, I have tried tried (and had failed):

sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get check
sudo apt-get install 
sudo apt-get -f remove
sudo dpkg -r php-java-bridge

All processes return the following error:

subprocess post-removal script returned error exit status 100
Errors were encountered while processing:
php-java-bridge

sometimes also get:
E: Sub-process /usr/bin/dpkg returned an error code (1)

(I can get the full output of each command if it will be beneficial)
I have also tried:
sudo synaptic > fix broken > get the same error message
sudo aptitude > find broken > then remove same error

Any help is appreciated.

---

### Post by dwanders on 2008-06-09
Not sure what the ramifications of this action are, but this seemed to have done the trick based on the information at: 

  [http://ubuntuforums.org/showthread.php?t=634624](http://ubuntuforums.org/showthread.php?t=634624)

I went to /var/lib/dpkg/info/ and did a php* which listed the offending package:
php-java-bridge.md5sums
php-java-bridge.postinst
php-java-bridge.conffiles
php-java-bridge.postrm
php-java-bridge.list

moved everything to my home folder sudo mv /var/lib/dpkg/info/php-java* ~
ran an update sudo apt-get update = no problems
ran an upgrade sudo apt-get upgrade = no errors
ran synaptic and it listed some residual files for the php-java package, so I had it purge the file, and everything seems to be running fine. 

Thanks for the links and your time.

---

### Post by Pumalite on 2008-06-09
You are welcome. Good luck.

---

