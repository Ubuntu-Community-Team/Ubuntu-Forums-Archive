---
title: "Not able to see any graphical ICONS except right click in Ubuntu 13.04"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by nagaraja2 on 2013-09-08
Hi,

I have installed latest ubuntu version by down loading from net. After installation it showed option to select from Windows XP and ubuntu. After selecting ubuntu for boot, it shows only desktop but no icons on the desktop. But i am able to use right click using mouse other than that noting can be done. 

During installation i created my own login, even i don't have root password. I used Cntrl Alt F1 for command prompt login there also i am not able reboot restart or poweroff the system.

Need help urgently.

Regards,
Nagaraja S

---

### Post by grahammechanical on 2013-09-08
Can we deal with one thing at a time?

When you installed Ubuntu did you tick to install third party software? If you did, then you are running on a proprietary video driver and it may not be giving you a good experience. At the desktop right click the desktop and select Change Desktop Background. That will open System Settings in the Appearance utility. Click the button marked Settings to see other Settings utilities. Select Software and Updates and open the Additonal Drivers tab. Wait until the utility shows you some video drivers and experiment changing video drivers to find one that works. You might want to select the driver called Nouveau. It is open source and it is the driver that is used when we run the live session.

In Ubuntu we do not have a root password. The password that you set when installing will work just as well. When we need to do anything as administrator then we are asked to authenticate the action. We use the password we chose at installation time and we become administrator for as long as the action is being performed or until a certain amount of time has passed. In this way we do not run Ubuntu as root and we do not put Ubuntu at risk by someone else using the machine when the user is running as root.

When we are in a terminal we use the word sudo in front of commands that need to be run as administrator. For example, to shutdown we run

```
sudo shutdown -h now
```

We will be asked for our password. Use the one that you choose during installation. To restart we use

```
sudo shutdown -r now
```

So, for commands that can only be run by the administrator or root, as you call it, we put sudo in front of the command and then we are asked for the password. We authenticate the task and then administrator/root authority stops when the command has completed the task or 15 minutes has passed.

We do not recommend running Ubuntu as a root user. It is very risky. It is possible for the system to be damaged. This is the official explanation.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you choose to run Ubuntu as a root user and you break things, then I cannot help you put things right. It is your responsibility.

Regards.

---

### Post by nagaraja2 on 2013-09-09
HI,

No i didn't select that option during installation. And in the Additional Drivers tab i don't see any drivers listed there. Please help me how do i install these required drivers now.
And thanks for explaining about root concept in Ubuntu.

Regards,
Nagaraja S

---

