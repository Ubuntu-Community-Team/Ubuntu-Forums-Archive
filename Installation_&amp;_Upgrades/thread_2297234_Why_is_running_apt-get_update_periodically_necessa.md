---
title: "Why is running apt-get update periodically necessary?"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by imrazor on 2015-10-01
Stupid question time...fairly often the automatic updater fails, and I find myself having to run "sudo apt-get update" to fix the problem. What does this command do, why is it necessary periodically, and why do I have to do it manually (i.e., why isn't it automated)?

---

### Post by grahammechanical on 2015-10-01
Update Manager/Software Updater is the automated method. It usually checks for updates at least once soon after starting Ubuntu and most likely checks again hours later. There are settings that we can adjust. In fact Update Manager and Synaptic Package Manager are just GUI front ends to several apt-get commands.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

If we open System Settings>Details we may notice that a check for updates then starts to take place. Semi-automatic.

In what way does Update Manager fail? Update Manager will say there is a connection problem if it fails to access just one repository in our list of software sources. I find that clicking OK over comes this error and then Update Manager gets on with what it is supposed to do. We can add a PPA (Personal Package Archive) as a repository and that is fine for downloading and installing the software that is in the PPA but afterwards we start getting update errors. Disabling the PPA on software & Updates is the way to fix that problem.

Regards.

---

### Post by imrazor on 2015-10-01
I see the notification from Update Manager in the taskbar/dock, click on it, then press the button to install all updates, authenticate, download begins, then I get an error. Sorry, but I didn't grab a screenshot or write it down. Could this be because I have unofficial repos/ppas?

PS, I'm having trouble posting too. It's not just you.

---

### Post by tgalati4 on 2015-10-01
If your wireless network is slow to connect, sometimes the software update system will fail.  If you reboot or logout and log back in, I believe the updater will check the repositories for updates.  You can check the log files in /var/log/apt for such occurrences and any software that was installed via any method using the apt system

```
sudo apt-get update
```

This command simply downloads the package lists from the repositories listed in /etc/apt/sources.list.

```
sudo apt-get upgrade
```

This command compares the versions of packages installed on your system versus the list downloaded from the repositories in the previous command.  Any software updates are then offered to be installed.

```
man apt-get
```

Describes the functions of the *apt-get* command in detail.

---

### Post by imrazor on 2015-10-01
Took a look at the logs, which were already rotated to compressed files. The closest thing I can find to an error is the following two lines in term.log:

       [FONT=monospace][COLOR=#000000]Unknown media type in type 'all/all' [/COLOR]
Unknown media type in type 'all/allfiles'


[/FONT]

---

### Post by ian-weisser on 2015-10-01
> **imrazor said:**
> then I get an error. Sorry, but I didn't grab a screenshot or write it down. Could this be because I have unofficial repos/ppas?

There are many possible causes for the package manager to fail.
Recording the error would indeed be a useful first step toward understanding the cause and possible solutions.

---

### Post by tgalati4 on 2015-10-02
Go through all of your repositories and comment out the ones that may be causing an issue.  Repositories can be found in /etc/apt/sources.list.d

---

