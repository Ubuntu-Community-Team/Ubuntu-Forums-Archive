---
title: "INSTALLING WINE Trouble"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by ApacheOmega on 2011-02-05
OK I installed WINE but right now the installation is stuck at the package configuration TERMINAL. This is what the terminal says.


 TrueType core fonts for the Web EULA                                        
 &#9474;                                                                             
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                           
 &#9474;                                                                             
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement         
 &#9474; ("EULA") is a legal agreement between you (either an individual or a        
 &#9474; single entity) and Microsoft Corporation for the Microsoft software         
 &#9474; accompanying this EULA, which includes computer software and may include    
 &#9474; associated media, printed materials, and "on-line" or electronic            
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your        
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be      
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of        
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                            
 &#9474;                                                                             
 &#9474;                                                                             
 &#9474;                                  <Ok>               

I press enter and the page wont move forward - what do I do after this part?

P.S. The only reason I'm installing this is to be able to use Notepad++ so I can type some PHP code and use it in XAMPP.

Please help
Thank You!!!

---

### Post by davidmohammed on 2011-02-05
at that page - press tab until <OK> is highlighted.  Press return.

---

### Post by ApacheOmega on 2011-02-05
[solved] thank you!!!!

---

### Post by ApacheOmega on 2011-02-05
sorry I keep asking about this but I just need to know how to manually fix this problem

here it i[message]

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I need to know the steps on how to manually fix this problem
Thank You
And I hope I'm not being a Bug A BOO!!!

---

### Post by davidmohammed on 2011-02-05
what happens if you type the following

sudo apt-get --configure -a

sudo apt-get update && sudo apt-get upgrade

---

### Post by iMARUF on 2013-02-18
> **davidmohammed said:**
> at that page - press tab until <OK> is highlighted.  Press return.

Thanks a lot.:D

---

### Post by oldos2er on 2013-02-18
Closed, please don't bump old threads.

---

