---
title: "Problem with installing fftw3 in Ubuntu 11.10"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by RMathis on 2012-01-04
I recently upgraded to Ubuntu 11.10. Now fftw3 no longer works.  I get "undefined reference to ...."  where ... are the calls to the fftw3 functions.

I originally installed fftw3 using the synaptic package manager. Neither the Ubuntu software center nor the Synaptic package manager list the fftw3 so I downloaded from the web site and followed the ./configure, make, and make install procedures. The installation seemed to work but nothing changed.

The program is located in /usr/include/fftw3.h

Where do I go from here?

Thanks

Ron

---

### Post by RMathis on 2012-01-04
I seem to have found a solution. Initially I used
g++ -lfftw3 -lm cepstrum.cc -o cepout 
it didn't compile

When I changed it to 
g++ cepstrum.cc -o cepout -lfftw3 -lm

It compiled and ran. I an not sure why this worked.

Ron

---

### Post by Mario Centeno on 2012-03-16
I had a similar problem. Thanks for posting your solution.

---

