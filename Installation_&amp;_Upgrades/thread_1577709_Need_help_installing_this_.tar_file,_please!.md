---
title: "Need help installing this .tar file, please!"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by pooja on 2010-09-19
Hi everyone!
I need some help installing a third-party software. It's called *rescuetime*.
I downloaded the .tar file from their website, [rescuetime.com Linux (link)]("https://launchpad.net/rescuetime-linux-uploader"), and extracted it via Archive Manager in my folder, "*/home/pooja/*". Inside the extracted folder, rescuetime-linux-uploader-99, I found a README file with installation instructions. Following the instructions, I installed the Firefox plugin (I never use Epiphany). I then went on running **```
python setup.py build
```** then **```
sudo python setup.py install
```**
These last two commands are supposed to install a script into /usr/bin/rescuetime_linux_uploader that allows one to run the executable from the command line and it will also install the gnome panel applet. However I can't find the **rescuetime_linux_uploader** script so I'm getting the following message from the Terminal
```
pooja@pooja-laptop:~$ cd ~/rescuetime-linux-uploader-99/
pooja@pooja-laptop:~/rescuetime-linux-uploader-99$ rescutime_linux_uploader
rescutime_linux_uploader: command not found

```

Now I'm stuck, I don't know how to proceed - can somebody help me, please?
I'm attaching the README file.

---

