---
title: "gpg error trying to install public key for repos"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by ryan on 2006-11-15
I am trying to install a public key in order to be able to install packages from a repo and after downloading the key I get an error message:

gpg: /home/ryan/.gnupg/gpg.conf:210: invalid option
gpg: /home/ryan/.gnupg/gpg.conf:211: invalid option

**Here is the sequence:**

ryan@ubuntu:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--09:05:16--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc.5'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s             

09:05:18 (164.99 MB/s) - `key.gpg.asc.5' saved [1730/1730]

**I try to import**

ryan@ubuntu:~$ gpg --import key.gpg.asc
gpg: /home/ryan/.gnupg/gpg.conf:210: invalid option
gpg: /home/ryan/.gnupg/gpg.conf:211: invalid option
ryan@ubuntu:~$ 

**Then I sudo and get this..**


ryan@ubuntu:~$ sudo gpg --import key.gpg.asc
Password:
gpg: WARNING: unsafe ownership on configuration file `/home/ryan/.gnupg/gpg.conf'
gpg: /home/ryan/.gnupg/gpg.conf:210: invalid option
gpg: /home/ryan/.gnupg/gpg.conf:211: invalid option



Any thoughts ? tks

---

### Post by mtn on 2006-11-15
hey, not sure if this will help, but I had to get this sorted for Automatix earlier.

i did it using synaptic, though i'm running edgy so the instructions would be different for dapper a as the repo options in synaptic have changed a bit (in layout more than anything else, I think!)

anyway, I got the key as a file by going here: [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
(edit: you can just right click this link and do "save link as")
then doing &#8220;save as&#8221;, it should be saved as a key file .asc.

then I open synaptic, system>administration>synaptic package manager
then,  settings>repositories
click the &#8220;authentication&#8221; tab and then click import key file. browse to the file etc.
once you have closed the repo tabs window you will have to click &#8220;reload&#8221; on the synaptic window.

hope this helps, and is clear enough.

---

### Post by ryan on 2006-11-15
> **mtn said:**
> hey, not sure if this will help, but I had to get this sorted for Automatix earlier.

i did it using synaptic, though i'm running edgy so the instructions would be different for dapper a as the repo options in synaptic have changed a bit (in layout more than anything else, I think!)

anyway, I got the key as a file by going here: [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
(edit: you can just right click this link and do "save link as")
then doing &#8220;save as&#8221;, it should be saved as a key file .asc.

then I open synaptic, system>administration>synaptic package manager
then,  settings>repositories
click the &#8220;authentication&#8221; tab and then click import key file. browse to the file etc.
once you have closed the repo tabs window you will have to click &#8220;reload&#8221; on the synaptic window.

hope this helps, and is clear enough.
Tks for the input I have since found out that by editing lines 210 and 211 ( there was a bunch of garbage in there seemed to take care of the problem. Once I did that everything worked fine at least for importing that key. Seahorse has now picked up my key ring but I am still having some problems with enigmail not sure if it is all related. Many tks for getting back to me.

---

### Post by wesley_of_course on 2006-12-12
Hello again.
  I tried what was suggested and got this reply;

        W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C

          What now ?

 Thanks in advance.                      ](*,)

---

### Post by stevemazdaspeed on 2006-12-12
1

---

