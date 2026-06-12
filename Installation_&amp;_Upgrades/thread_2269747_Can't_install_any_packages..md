---
title: "Can't install any packages."
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by md-riaj197 on 2015-03-17
I am using ubuntu 14.10. I am trying to install all updates, but it's show me the following result: :(

[I][SIZE=2][FONT=arial]**The package system is broken**[/FONT][/SIZE]

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f[/I]

Details:

```

The following packages have unmet dependencies:

gcc-4.9-multilib: Depends: gcc-4.9-base (= 4.9.1-16ubuntu6) but 4.9.1-16ubuntu6 is installed
                  Depends: gcc-4.9 (= 4.9.1-16ubuntu6) but 4.9.1-16ubuntu6 is installed
                  Depends: libc6-dev-i386 (>= 2.11) but it is not installed
                  Depends: lib32gcc-4.9-dev (= 4.9.1-16ubuntu6) but 4.9.1-16ubuntu6 is installed
                  Depends: libx32gcc-4.9-dev (= 4.9.1-16ubuntu6) but 4.9.1-16ubuntu6 is installed
libc6-dev-x32: Depends: libc6-x32 (= 2.19-10ubuntu2.3) but 2.19-10ubuntu2.3 is installed
               Depends: libc6-dev-i386 (= 2.19-10ubuntu2.3) but it is not installed
               Depends: libc6-dev (= 2.19-10ubuntu2.3) but 2.19-10ubuntu2.3 is installed

```

Then I removed the third party repositories and run the command in terminal **'sudo apt-get -f install'**. But after all I got the following error: :cry:

```

dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.19-10ubuntu2.3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/fpu_control.h', which is also in package libc6-dev-amd64 2.19-10ubuntu2.3
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev-i386_2.19-10ubuntu2.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, now I need the person who can fix the problem. Great pleasure if you can help me to get out this problem. Please... :-|

---

### Post by ian-weisser on 2015-03-17
> dpkg: error processing archive /var/cache/apt/archives/[COLOR=#ff0000]libc6-dev-i386_2.19-10ubuntu2.3_amd64.deb[/COLOR] (--unpack):  trying to overwrite '[COLOR=#800080]/usr/include/fpu_control.h[/COLOR]', which is also in package [COLOR=#0000ff]libc6-dev-amd64 2.19-10ubuntu2.3[/COLOR]

You have two packages: [COLOR=#ff0000]libc6-dev-i386 2.19-10ubuntu2.3-amd64.deb[/COLOR]  [COLOR=#0000ff]libc6-dev-amd64 2.19-10ubuntu2.3
[/COLOR]Those two packages have a *file conflict* ([COLOR=#800080]/usr/include/fpu_control.h[/COLOR]).
You cannot install both packages at the same time. Ever. They *conflict*.

The conflict makes sense - they seem to be the same package for two different architectures.

The package manager does not know which one you wish to keep, and the error is it's way of telling you. Uninstall one of them.
Since it's merely a -dev package, it may be simpler to uninstall both until you get your apparent multiarch problem sorted.

---

### Post by md-riaj197 on 2015-03-18
> **ian-weisser said:**
> 
The package manager does not know which one you wish to keep, and the error is it's way of telling you. Uninstall one of them.

I am trying to remove the file but they said **'E: Unable to locate package /var/cache/apt/archives'** though I have already the *'archives'* package consists of *'libc6-dev-i386_2.19-10ubuntu2.3_amd64.deb'* file. So, kindly please tell me how can I uninstall one of them file that you suggested.

---

### Post by md-riaj197 on 2015-03-18
Ok, I have solved the issue. Thank you :)

---

### Post by dino99 on 2015-03-18
it is : /var/cache/apt/archives/

---

