---
title: "WUSB54GV4 RT73 Make error"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by justintmk on 2010-02-05
Hey guys i'm new to Linux, so bear with me if i'm making any senseless mistakes.

I recently downloaded the rt2x00 legacy drivers from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).
The rt73 one.
Everything went smoothly at first.
At first I copied the downloaded file to /usr/src
Then I extracted the file.
I then typed:
cd /usr/src/rt73-cvs-2009041204/Module

And then I typed:
sudo make

This is the part where everything went wrong.
After typing sudo make, the terminal returned the following messages:

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
rt73.ko failed to build!
make: *** [module] Error 1

I've been searching the internet continuously for two days and i've found no answer to this problem.
Everyone seems to be experiencing instances where the terminal met with errors before it even leaves the directory.
But no one seems to be experiencing the problem where rt73.ko just stubbornly does not want to build.

Anyone knows the solution to this?
I'll be extremely grateful if you do...

P.S. I also typed this into the terminal before attempting to install:

sudo apt-get install build-essential

I'm really at my wits end...
Can anyone help me?

---

### Post by konin525 on 2010-02-11
Exactly same problem her (same ubuntu version), same driver.
Anyone knows where I can find why I get Error 1....

---

### Post by arturo_ol on 2010-04-11
Hello. Having exactly the same error here, same driver.

Ubuntu 9.10.

Also downloaded Kernel Headers but I still get the error.

Do you guys found the solution for this?

Thanks in advance

---

### Post by firewalker22 on 2010-11-19
same here

---

### Post by AustinTX on 2011-01-12
I have this problem too.

---

