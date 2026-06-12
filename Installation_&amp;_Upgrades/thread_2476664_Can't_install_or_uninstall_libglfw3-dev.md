---
title: "Can't install or uninstall libglfw3-dev"
date: 2022-07-02
forum: Installation &amp; Upgrades
---

### Post by sicarumba on 2022-07-02
Hello all

I am trying to install glfw3-dev version 3.3.2 on my Ubuntu 16.04 LTS. I've downloaded the source, compiled it with cmake and tried to install it. All the messages I see appear to suggest it's installed (lots of lines of "up-to-date", no error messages).  But when I do 

```
apt list libglfw3-dev
```

I get

```
Listing... Done
libglfw3-dev/xenial 3.1.2-3 amd64
```

Which is the version it was before I tried installing 3.3.2. When I try to uninstall it I am told it's not installed. 

```
sudo apt remove --purge libglfw3-dev
```

```
Package 'libglfw3-dev; is not installed, so not removed
```


```
sudo dpkg --remove libglfw3-dev
```

```
dpkg: warning: ignoring request to remove libglfw3-dev which isn't installed

```

If it isn't installed, why isn't my install of 3.3.2 working. And if it is installed, why can't I remove it? 

Thank you in advance, no doubt it's a simple solution for someone ... just not me!

---

### Post by Impavidus on 2022-07-02
> **sicarumba said:**
> Hello all

I am trying to install glfw3-dev version 3.3.2 on my Ubuntu 16.04 LTS. I've downloaded the source, compiled it with cmake and tried to install it. All the messages I see appear to suggest it's installed (lots of lines of "up-to-date", no error messages).
libglfw3-dev is a package containing some header files and a few other helper files. It doesn't require compilation. It depends on libglfw3, which contains the actual library files, which do require compilation if you install from source. Usually we don't install such libraries from source, as we get the version already compiled for our version of Ubuntu from the repositories.

If you install something from source, it's possible to first pack it into a .deb package, then install that .deb package. If you don't, and it appears you didn't, then apt is completely unaware of the software you installed.

> But when I do 

```
apt list libglfw3-dev
```

I get

```
Listing... Done
libglfw3-dev/xenial 3.1.2-3 amd64
```

Which is the version it was before I tried installing 3.3.2.apt doesn't say the package is installed. This just means that apt is aware of the package. It knows the package is available from the repositories, but isn't installed.

> When I try to uninstall it I am told it's not installed. 

```
sudo apt remove --purge libglfw3-dev
```

```
Package 'libglfw3-dev; is not installed, so not removed
```


```
sudo dpkg --remove libglfw3-dev
```

```
dpkg: warning: ignoring request to remove libglfw3-dev which isn't installed

```Because it isn't installed. At least, not as far as apt is aware of.

Installing libraries from source is tricky. It's something we avoid if we can. And even if you do install one from source, make sure it doesn't conflict with the libraries already installed. Don't put it in /usr/lib. Put it in /usr/local/lib and put the header files in /usr/local/include.

That's my explanation of the problem. Next, my recommendation. Ubuntu 16.04 is old and mostly dead. There's some extended security maintenance available, but only for some core parts. I wouldn't use it any more. Ubuntu 20.04 has glfw 3.3.2 available from the repos, Ubuntu 22.04 has glfw 3.3.6 available from the repos. So the easy solution is to move to a recent and supported release of Ubuntu, a good idea anyway, and simply install glfw3 from the repos.

---

### Post by sicarumba on 2022-07-02
Thank you, that was a very informative description of what I am doing wrong. The Ubuntu install is a virtual machine and up until now it's just sort of worked for what I need it to do, so I've not felt the need to upgrade. Maybe now is the time to try 20.04.

---

### Post by mIk3_08 on 2022-07-04
Steps on how to mark this thread as solve,
Please Click the "**[COLOR=#ff0000]Solve thread[/COLOR]**" link below. For Regards and cheers.

---

