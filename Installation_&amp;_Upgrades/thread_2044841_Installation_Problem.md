---
title: "Installation Problem"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by ktseo on 2012-08-20
I am using Ubuntu 12.04, Now I want to install seospyglass software which i have downloaded from Link assistant .com

I have save this with two format which is as a folder as well as tar.gz.

After doing this when i am typing "sudo apt-get install ~/Desktop/seospyglass/install.sh
from home. it showing error of  "Unable to locate package seospyglass"

I have tried to make it executable by chmod +x ~/desktop/sepspyglass/install.sh

what now??

---

### Post by mastablasta on 2012-08-20
> **ktseo said:**
> I have tried to make it executable by chmod +x ~/desktop/sepspyglass/install.sh
 
what now??
 
double click the file to execute it if it is really made executable. otherwise you can right click it and make it executable.

---

### Post by darkod on 2012-08-20
If the software is provided and already downloaded, you don't use apt-get.

Open Terminal and change the directory to where the unpacked files are, like:
cd /Desktop/seospyglass

Then start the install with:
./install.sh (not sure if it will need sudo in front or not)

---

### Post by ktseo on 2012-08-20
> **mastablasta said:**
> double click the file to execute it if it is really made executable. otherwise you can right click it and make it executable.

How can i check it's executable or not?
How to make it executable with right click?

---

### Post by ktseo on 2012-08-20
> **darkod said:**
> If the software is provided and already downloaded, you don't use apt-get.

Open Terminal and change the directory to where the unpacked files are, like:
cd /Desktop/seospyglass

Then start the install with:
./install.sh (not sure if it will need sudo in front or not)

I have tried after changing the diretory to cd /desktop/seospyglass 
I have inserted ./install.sh and sudo ./install.sh

But it showing error "Java: Command not found.

---

### Post by darkod on 2012-08-20
Is there a readme.txt in the folder too? Usually in there are instructions how to start the installer.

I'm not sure, sometimes you might need bash without the ./, like:
```
sudo bash install.sh
```

It depends how the developer made it work. The readme.txt usually has details.

---

### Post by ktseo on 2012-08-20
> **darkod said:**
> Is there a readme.txt in the folder too? Usually in there are instructions how to start the installer.

I'm not sure, sometimes you might need bash without the ./, like:
```
sudo bash install.sh
```It depends how the developer made it work. The readme.txt usually has details.

Readme.txt is not available. 
i have tried sudo bash install.sh but it's showing same error which is "Java:command not found"

One of my friend is installed this software via this thread, I have tried same but not getting success. 

Kindly look this also. : [http://ubuntuforums.org/archive/index.php/t-1564196.html](http://ubuntuforums.org/archive/index.php/t-1564196.html)

---

### Post by darkod on 2012-08-20
Well in that thread it said it installed with the
sudo ./install.sh

And you say it doesn't work. I am not sure why that message mentions Java, maybe you need to have Java JDK installed and you don't. I have no idea what the requirements for this software are, you need to find that out on the developer website.

Once you have it downloaded and extracted, the installation seems to be started with the above command. When you are in the /Desktop/seospyglass folder make sure the install.sh is in there. You can list folder content with only:
```
ls
```

---

### Post by ktseo on 2012-08-20
> **darkod said:**
> Well in that thread it said it installed with the
sudo ./install.sh

And you say it doesn't work. I am not sure why that message mentions Java, maybe you need to have Java JDK installed and you don't. I have no idea what the requirements for this software are, you need to find that out on the developer website.

Once you have it downloaded and extracted, the installation seems to be started with the above command. When you are in the /Desktop/seospyglass folder make sure the install.sh is in there. You can list folder content with only:
```
ls
```

Have you seen the thread i have mentioned in previous post? I also searched for Java Update. But same error appearing. Anyway thanks for your time. I will wait for other's reply.

---

### Post by darkod on 2012-08-20
> **ktseo said:**
> Have you seen the thread i have mentioned in previous post? I also searched for Java Update. But same error appearing. Anyway thanks for your time. I will wait for other's reply.

I saw it and I was commenting on that thread. It said it worked with sudo ./install.sh.

> Ok, so presumably you have downloaded and unpacked the archive to the 'seospyglass' folder on your desktop?

Could you please post the output of the following command:

ls ~/Desktop/seospyglass

If the 'install.sh' file exists there, then try run it from that directory:

cd ~/Desktop/seospyglass
sudo ./install.sh

> Thanks lechien73 ([http://ubuntuforums.org/member.php?u=1031904](http://ubuntuforums.org/member.php?u=1031904)), thank you very much.
It is successfully installed.

---

### Post by mastablasta on 2012-08-20
> **ktseo said:**
> How can i check it's executable or not?
How to make it executable with right click?
 
have a look here: [http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui](http://askubuntu.com/questions/35478/how-do-i-mark-a-file-as-executable-via-a-gui)
 
oh and if sudo is really needed then i think you need to right click and then run as root.

---

