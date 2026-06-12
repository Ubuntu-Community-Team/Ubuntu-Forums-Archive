---
title: "Re: Tweaking your Ubuntu after installation"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by caiphn on 2005-02-21
I was reading through the guide that is setup and it says in order to update various components, such as getting the drivers my video card would require would be to use the sudo apt-get 'name' command, however this is what is happening.

 sudo apt-get install nvidia-glx
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate

So obviously I need to download these items from somewhere? I tried to do the Synaptic update, seemed weird that there was no upgrades as this system just got online now. What am I doing wrong?

---

### Post by kassetra on 2005-02-21
You need to add some repositories, here is a great [starter guide]("http://ubuntuguide.org/#extrarepositories").

---

### Post by caiphn on 2005-02-21
Hey, thanks a lot, I appreciate it.

---

