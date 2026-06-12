---
title: "The update information is outdated - Ubuntu 20.04"
date: 2021-10-25
forum: Installation &amp; Upgrades
---

### Post by berg73 on 2021-10-25
Hi there,

I'm a new user of Ubuntu 20.04 and my knowledge of Ubuntu and using the terminal is very limited. In the last few days I have been receiving a notification saying "The update information is outdated...". 

I have followed the advice on this notification by clicking "Show updates", and I then get a response saying "The software on this computer is up to date". I have also gone into the terminal and entered "sudo apt update" and receive a response saying "All packages are up to date".

Screenshot attached - I tried to attach two other screenshots but they wont attach for some reason. 

Can someone please help with this?

---

### Post by grahammechanical on 2021-10-25
Try this. Click on Activities and type software and then click on Software Updater. See what that does. Ubuntu is set to notify the user of updates after a set period of time. Using the terminal to update might not satisfy the OS that the check for updates has been made. Using Software Updater might register that a check for updates has been made.

We can vary to time interval in the software & Updates utility>Updates tab.

Regards

---

### Post by berg73 on 2021-10-25
> **grahammechanical said:**
> Try this. Click on Activities and type software and then click on Software Updater. See what that does. Ubuntu is set to notify the user of updates after a set period of time. Using the terminal to update might not satisfy the OS that the check for updates has been made. Using Software Updater might register that a check for updates has been made.

We can vary to time interval in the software & Updates utility>Updates tab.

Regards

Thanks for your reply Graham. I just tried this and received the response "The software on this computer is up to date".

I don't know if this is helpful to know... But the red exclamation icon is currently not showing either, however it has disappeared and then reappeared in the past week, so i'm expecting it will probably show up again at some point

---

### Post by Impavidus on 2021-10-26
The message "The update information is outdated" means that Ubuntu was scheduled to check for updates, but the check failed. This may be caused by a network problem on your side, with the server or somewhere inbetween or by having some repository configured that was shut down or never existed. When you run the update manager or sudo apt update, you force a check for updates and if this check succeeds, the warning message is cleared. If the check doesn't succeed, you should get more details in an error message.

You can configure how often Ubuntu should check for updates. Some (like I) like to check daily, others only weekly, some set it to never, but then you should regularly run a check manually

The message "The software on this computer is up to date" means that all updates that your Ubuntu knows about have been installed successfully. But if the update information is outdated, that doesn't help.

If the red exclamation mark is gone, it's OK now. The warning may return later if another check for updates fails. Maybe your internet connection isn't very reliable, or the server you pull the updates from isn't very good. In the latter case, try switching to a different server.

---

### Post by ActionParsnip on 2021-10-26
What is the output of
```

sudo apt update

```

Is it smooth with zero warning or errors?

---

### Post by berg73 on 2021-10-26
> **Impavidus said:**
> The message "The update information is outdated" means that Ubuntu was scheduled to check for updates, but the check failed. This may be caused by a network problem on your side, with the server or somewhere inbetween or by having some repository configured that was shut down or never existed. When you run the update manager or sudo apt update, you force a check for updates and if this check succeeds, the warning message is cleared. If the check doesn't succeed, you should get more details in an error message.

You can configure how often Ubuntu should check for updates. Some (like I) like to check daily, others only weekly, some set it to never, but then you should regularly run a check manually

The message "The software on this computer is up to date" means that all updates that your Ubuntu knows about have been installed successfully. But if the update information is outdated, that doesn't help.

If the red exclamation mark is gone, it's OK now. The warning may return later if another check for updates fails. Maybe your internet connection isn't very reliable, or the server you pull the updates from isn't very good. In the latter case, try switching to a different server.

Thanks for your reply Impavidus. As expected the exclamation mark returned earlier, and after running "sudo apt update" it remained, despite the response from that command saying "All packages are up to date".

The exclamation mark currently is not showing again.

As far as i'm aware my internet connection is reliable, I haven't experienced it cutting out or any other problems with connecting. I could try and switch to a different server, is this difficult and are there any risks associated with doing that?

---

### Post by berg73 on 2021-10-26
> **ActionParsnip said:**
> What is the output of
```

sudo apt update

```

Is it smooth with zero warning or errors?

Hi ActionParsnip, yes the output after entering in "sudo apt update" is smooth. I get the following response:

***berg@Berg:~$ sudo apt update***
***[sudo] password for berg: ***
***Reading package lists... Done***
***Building dependency tree       ***
***Reading state information... Done***
***All packages are up to date.***

---

