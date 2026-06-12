---
title: "Please solve it."
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by robinpaschal on 2010-08-30
When i am trying to install my software with this command.

sudo sh Desktop/seospyglass/install.sh

the error appear       sudo sh Desktop/seospyglass/install.sh

I don't know the Version of my ubuntu system.
how can i solve my problem?

---

### Post by realzippy on 2010-08-30
Did you make the script executable?

chmod +x /path/to/your/script

---

### Post by robinpaschal on 2010-08-30
See i am totally newbie with this OS. So will you tell me how can i make it executable?

---

### Post by lechien73 on 2010-08-30
The command contained in the previous post will make it executable:

```
chmod +x ~/Desktop/seospyglass/install.sh
```

What exactly is the error you receive when trying to run the installation? If you can copy and paste the exact error text, that will help.

---

### Post by robinpaschal on 2010-08-30
Well....ok now i am defining you properly. I want to install seospyware software.
I downloaded that from link-assistant.com 

I tried too many times but it give the error as following:

Couldn't find package seospglass

even it saved on desktop with both formats. I mean it is also in folder and saved as seospyglass.tar.gz

---

### Post by lechien73 on 2010-08-30
Ok, so presumably you have downloaded and unpacked the archive to the 'seospyglass' folder on your desktop?

Could you please post the output of the following command:

```
ls ~/Desktop/seospyglass
```

If the 'install.sh' file exists there, then try run it from that directory:

```
cd ~/Desktop/seospyglass
sudo ./install.sh
```

---

### Post by robinpaschal on 2010-08-31
Thanks [lechien73]("http://ubuntuforums.org/member.php?u=1031904"), thank you very much.
It is successfully installed.

Now will you tell me from where i can use it.

I am explaining....
cd ~/Desktop/seospyglass
sudo ./install.sh 
With this command it is installed. After complete the setup process i am not able to find shortcut or icon to open it.
please help me.

---

### Post by lechien73 on 2010-08-31
Just type:

```
seospyglass
```

from within a terminal window to run the program. If this resolves your issue, please could you mark the thread as [SOLVED] by clicking on the **Thread Tools** menu at the top right.

Thanks

---

### Post by robinpaschal on 2010-09-11
Hello Mates....

I have another problem with ubuntu to install the software.
Now it shows some error of java. Please anybody tell me which java i have to install.

I don't know my Ubuntu Version.

---

