---
title: "download softwares"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by jeyram on 2007-07-15
i am using Ubuntu(feisty). i don't have internet connection in my home.  so if i want to install any software i have to download. but if get dependency problem i have to find out every libraries manually.

are there any sort cut to download particular software with their dependency?

---

### Post by Koybe on 2007-07-15
Could you tell us what are you trying to install and which error did you get into?

---

### Post by jim_p on 2007-07-15
Just a thought, but I think it's worth a try...

Open up Synaptic, and choose the stuff you want to install as if you had an internet connection.
You will be prompted for any dependencies that will be automatically checked.

DO NOT CLICK "APPLY" YET

Go to "Create a download script" and save it as an .sh file.
This will make a "batch file" with all the needed stuff for download.
You can then take this file to any pc with a fast internet connection and run it.
(Don't do this in a Windows pc because Windows dont have wget installed by default)
It will download the files and you can take them to your pc!! And an example, just to make sure I didn't miss something:

Lets say you want to install Kopete, which has libjasper-runtime as a dependency.
You mark Kopete for installation, you are prompted for its dependency and you say yes so that libjasper-runtime is marked too. You go to "File" > "Create a download script" and save it somewhere.
**Make sure you change the rights to edit/read/execute it because it was created by the root user!**

Open it up with a text editor and you will see something like this
```

#!/bin/sh
wget ftp://ftp.ntua.gr/ubuntu/pool/universe/j/jasper/libjasper-runtime_1.701.0-2_i386.deb
wget ftp://ftp.ntua.gr/ubuntu/pool/main/k/kopete/kopete_3.5.4+kopete0.12.2-0ubuntu1~dapper1_i386.deb

```

Now you are ready to go! Kopete + all its dependencies

---

