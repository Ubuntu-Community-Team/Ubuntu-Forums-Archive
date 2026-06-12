---
title: "Java installation fails"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2009-11-15
I went to install the Sun Java plugin for the web browser, but I got a return error: 

```
patrick@patrick-laptop:~/Desktop$ sudo apt-get install sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
```

I currently have sun-java6-bin installed, but I am running Ubuntu *9.10* - this tells me this is a bug, (though I could be wrong if I goofed something up mortally?). Or should I report this at Launchpad, and under what?

---

### Post by Pjotr123 on 2009-11-15
Try it like this:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

