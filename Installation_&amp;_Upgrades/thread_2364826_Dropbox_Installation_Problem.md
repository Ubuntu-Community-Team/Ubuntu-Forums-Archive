---
title: "Dropbox Installation Problem"
date: 2017-06-28
forum: Installation &amp; Upgrades
---

### Post by tckutlu on 2017-06-28
Greetings, 
I'm a new Ubuntu user and i prefered to install Ubuntu 17.04 Zesty Zapus on my computer.
The problem is when i try to install Dropbox due to Ubuntu Software, Dropbox can be downloaded but can't be opened.
I recieved the below message yesterday.
[ATTACH=CONFIG]275798[/ATTACH]

When i click on Restart Nautilus button, there's nothing happened also right click function of the mause is temporarily disabled.
Then i searched the problem on internet, found some topics. One of the suggestions is about restarting Nautilus on terminal.
I wrote the below commands on terminal.```
nautilus -q
```Then redo the installation step but the same problem happened.
Then i keep on searching on internet. By the way i uninstalled the Dropbox and typed the below commands on terminal.
```
rm -rvf ~/.dropbox ~/.dropbox-dist
``` Then i visited the Dropbox official website and downloaded the tar file, after finished the download, i typed the below commands on terminal.
```
sudo tar -xvzf /home/tckutlu/&#304;ndirilenler/dropbox-lnx.x86-29.4.20.tar.gz -C /opt
```On the terminal window, i saw any problem but when i looked at the opt folder, i saw that tar file didn't extracted it's files there.
Then i visit the Dropbox's official page again. They have written a command for installation. And i typed that command on terminal which is
```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -
``` But i recieved a certification problem.
After that i searched certification problem on internet and found some topics. i choosed an upvoted post's suggested command which is adding a 
--no-check-certificate defination on the below codes. The last codes looked like:
```
cd ~ && wget --no-check-certificate "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf-
``` And i saw that something happens which can be seen on the below image.
[ATTACH=CONFIG]275799[/ATTACH]
The file was downloaded but when i clicked the file i got an error message which can be seen at the below image:
[ATTACH=CONFIG]275797[/ATTACH]

The methods that i tried to choose didn't solve my problem. Perhaps you can show me what the problem is and help me to solve it.
Thanks in advance.

---

### Post by tckutlu on 2017-06-28
Problem solved.
I opened terminal after installed Dropbox on Ubuntu Software. 
Then i typed the below commands.
```
LC_ALL=C dropbox start -i
```

---

