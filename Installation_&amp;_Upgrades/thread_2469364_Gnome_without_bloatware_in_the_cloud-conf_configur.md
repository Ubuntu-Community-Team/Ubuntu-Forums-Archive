---
title: "Gnome without bloatware in the cloud-conf configuration file"
date: 2021-11-26
forum: Installation &amp; Upgrades
---

### Post by taralloman on 2021-11-26
Hello everyone! 
I am carrying out a project to create a fully automated ISO during its Ubuntu 20.04 server installation, via Cloud-conf file.

 I would like to install Gnome without bloatware, I tried like this:

```

#cloud-config
autoinstall:
  version: 1

#other code

packages:
- ubuntu-gnome-desktop --no-install-recommends

```

but it doesn't work
Can anyone help me?

---

### Post by grahammechanical on 2021-11-26
Please explain what you mean by

> but it doesn't work

What is it that does not work? Does the server ISO image not install Ubuntu server? Or, is Ubuntu server installed but without Gnome Desktop? Or, is Gnome Desktop installed but with all the utilities that you did not want installed?

The Autoinstall reference document says this

> **packages**
**type:** list
**default:** no packages
**can be interactive:** no

 A list of packages to install into the target system. More precisely, a list of strings to pass to “apt-get install”,

If there is something wrong with any line in the list of packages to install then it may default to no packages installed. (I think)

Please look at this advice under the heading Minimum Gnome Installation. Your command to install a minimum Gnome Desktop seems to be the wrong way around.

```
--no-install-recommends ubuntu-gnome-desktop
```

[https://blog.desdelinux.net/en/como-instalar-una-version-minima-de-ubuntu/](https://blog.desdelinux.net/en/como-instalar-una-version-minima-de-ubuntu/)

I am not speaking with authority. You are the one doing this experiment. You have more experience than me.

Regards

---

### Post by MAFoElffen on 2021-11-26
One... It is assumed that you are pointing it to the cloud-init file, it is reading and processing it, but...

Well... That is the package for the full Gnome Desktop packaged suite (which includes a whole lot of things), with all it's full lineup desktop applications and utilities,  but is not considered (by many ) to be "without bloatware"... 

Wouldn't, when you say "without bloatware" be a minimal install of XServer, with a minimal install of gnome-sessions, with just the installation of the desktop applications that you want and require? I do either that, or me and others will run a post-install process/script, to remove what we feel is "bloatware" or unwanted extra's.

Also consider that if you use the Server ISO as a Net Install for a Desktop, and want things to be configured as such, that your post-install is also where you do that... such as chaning the network management passed from NetPlan to Network Manager...

 Just being the Devil's Advocate, because that is what comes to mind when I read or hear that reference.

---

### Post by ActionParsnip on 2021-11-28
I'd suggest something like chef or puppet for automation of configuration. Makes servers very easy to manage en mass. A great skill to have

---

### Post by taralloman on 2021-11-29
Hi, first of all thank you!
Let me explain the error, what is wrong? When the package installation gets to

 ```
[COLOR=#000000][FONT=&quot]- ubuntu-gnome-desktop --no-install-recommends[/FONT][/COLOR]
```

it crashes as if it doesn't recognize the command

---

