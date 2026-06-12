---
title: "New to Ubuntu, theme installion question?"
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by alex553 on 2016-06-26
Okay so I'm new to ubuntu... and I'm sure theres things I should learn like what ppa means and what sudo means and stuff but its almost 3am and this theme is priority... >.<

I've installed Unity, and Gnome (although when I installed gnome there was a file error and it said some file didn't install...?) anyways. I've opened Unity and messed around. But I'm trying to use this command.

```
 sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"
```

It then ask for my sudo password, which I enter.

Next step,

```
 sudo apt-get update
```

When I enter this command, I get 2 lines.

"E: Malformed entry 1 in list file /etc/apt/sources.list.d/arc-theme.list (Suite)
 E: The list of sources could not be read."

From what I understand, it's saying the first command was not entered correctly? Idk... any help is appreciated.

---

### Post by alex553 on 2016-06-26
And now I'm trying to install Gufw...

```
sudo apt-get install gufw
```

And I get this...

[img]http://i.imgur.com/Vn3raCg.png[/img]

---

### Post by alex553 on 2016-06-26
Also tried using this command to clear terminal history...?

```
history -c && history -w
```

But it did nothing, just made a new line in the terminal?

---

### Post by alex553 on 2016-06-26
Okay well I used the sudo rm command to remove the offending sources.list, and now I can install gufw.

Still having trouble installing the theme though...

---

### Post by Impavidus on 2016-06-26
A PPA is an additional repository (so not one of the official Ubuntu repositories) of software that can be installed through the various interfaces of the package manager, like apt-get, synaptic or ubuntu software. PPAs allow you to install extra software or more recent versions. At the same time, they are a common source of trouble. At the moment, I don't use any PPA.
[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

**sudo** is a command that can execute another command, given as an argument, with the effective ID of a different user. It's usually used to execute commands as the root user and is the most common way to do things on Ubuntu that can only be done by the root user. This includes everything that might break your entire system.
[URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo
[/URL]
Most commands, when executed successfully, don't give any output in the terminal. The history commands just worked.

---

### Post by ajgreeny on 2016-06-26
In your first post I see reference to 15.04.

If you are still using 15.04 you will see a lot of error messages when trying to install or update packages as 15.04 has now lost support.  You should certainly upgrade your OS to 16.04 but you can not do that in one jump from 15.04->16.04 so a clean install is probably the best way forward for you.

---

### Post by grahammechanical on 2016-06-26
> "E: Malformed entry 1 in list file /etc/apt/sources.list.d/arc-theme.list (Suite)
 E: The list of sources could not be read."

From what I understand, it's saying the first command was not entered correctly? Idk... any help is appreciated.

I do not think it is saying that at all. I think that it means that the file "arc-theme.list" has an incorrectly written first line. Sometimes a "list" file will have a blank first line and that will prevent the OS from reading the "list" file. I think in your case there is something non-standard about the first line from the Ubuntu point of view.

Regards

---

### Post by Impavidus on 2016-06-26
> **alex553 said:**
> 
```
 sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/Horst3180/xUbuntu_15.04/ /' >> /etc/apt/sources.list.d/arc-theme.list"
```


That command adds the stuff between single quotes to the file /etc/apt/sources.list.d/arc-theme.list. That file doesn't exist by default, so this command must have created the file. I don't know the exact syntax of .list files, but this one strikes me as a little odd. It may be wrong. And even if it's right, it may not work on your Ubuntu.

---

