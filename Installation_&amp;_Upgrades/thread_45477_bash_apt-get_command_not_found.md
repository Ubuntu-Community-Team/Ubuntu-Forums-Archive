---
title: "bash: apt-get: command not found"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by podrik0 on 2005-06-30
I required my internet to work, which I have to install drivers for seperetly... 
 
 I go to ./configure and then: 
 
 checking how to run the C preprocessor... /lib/cpp 
 configure: error: C preprocessor "/lib/cpp" fails sanity check 
 
 So assume I need to build essential then get: 
 lib/cpp" fails sanity check 
 bash: apt-get: command not found 
 
 What is going on? I urgently need to resolve this for internet access!!! 
 THANK YOU!

---

### Post by Devi0s on 2005-06-30
I think that you need to be root to run apt-get.  Have you tried:

sudo apt-get install build-essential ?

---

### Post by podrik0 on 2005-06-30
'So assume I need to build essential then get: 
 lib/cpp" fails sanity check '

That's exactly what I am trying to do lol, but get this error:

sudo: apt-get: command not found

---

### Post by Drain on 2005-06-30
Wow - how did you install Ubuntu without apt-get? ... perhaps you can manually download apt from the Ubuntu repositories, and then use "sudo dpkg -i apt(some version number).deb" ... if that doesn't work, I have no idea what to tell you...

---

