---
title: "Install Compendium in Ubuntu"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by jr13 on 2013-04-22
I am relatively new to Ubuntu but have been doing all I can to learn using the available documentation, but have run up against a problem. 
I am trying to install Compendium, and it seems straigtforward:
[http://compendium.open.ac.uk/institute/download/software/ReadMe.html](http://compendium.open.ac.uk/institute/download/software/ReadMe.html)

"Once you have downloaded the relevant .tar file from the compendiuminstitute.org website, simply unpack it.You can run Compendium by navigating to the Compendium directory and typing: ./compendium.sh"

Reality is rather different.

I've been trying to follow the steps set out here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)


But can't get step 2 to work.

Any advice would be gratefully appreciated.

Thanks

---

### Post by slickymaster on 2013-04-22
> **jr13 said:**
> I am relatively new to Ubuntu but have been doing all I can to learn using the available documentation, but have run up against a problem. 
I am trying to install Compendium, and it seems straigtforward:
[http://compendium.open.ac.uk/institute/download/software/ReadMe.html](http://compendium.open.ac.uk/institute/download/software/ReadMe.html)

"Once you have downloaded the relevant .tar file from the compendiuminstitute.org website, simply unpack it.You can run Compendium by navigating to the Compendium directory and typing: ./compendium.sh"

Reality is rather different.

I've been trying to follow the steps set out here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)


But can't get step 2 to work.

Any advice would be gratefully appreciated.

Thanks

As far as I noticed Compendium cames as downloadable jar file not a tar.gaz, so the instructions in [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) don't apply.

In the link you provid us it's stated:
> Compendium is a Java application, so it requires a Java Runtime Environment (v1.5) 32 bit to be installed before you can run it.
Linux user's have found issues with running Compendium on the OpenJDK so we recommend using Sun's JDK.

So, do you have java installed? And if yes, is it OpenJDK or Sun's JDK?
You can find out running the following command in a terminal window:
```
java -version
```

---

