---
title: "included php as part of 7.10 install, but what was php configure command?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by geekpie on 2008-03-25
I installed php during the 7.10 server version ubuntu install process a few weeks ago. phpinfo says "PHP Version 5.2.3-1ubuntu6.3": 

Server API is Apache 2.0 Handler.

I have 2 questions: why doesn't phpinfo show the Configure Command (showing the compiled in modules)? Even though I didn't compile php myself, isn't this information available? 

the other thing is, and it's probably more of a php question, I added the xmlrpc php extension using the command:

sudo apt-get install xmlrpc

all went smoothly, and the file /usr/lib/php5/20060613+lfs/xmlrpc.so appeared but then the command 

php -m

which is supposed to "Show compiled in modules" 

at the ubuntu command line shows xmlrpc as one of the modules: but I've just installed xmlrpc as a shared object extension, not a compiled in extension?

---

