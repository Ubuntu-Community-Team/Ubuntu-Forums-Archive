---
title: "Aptitude says non-installed package is &quot;broken&quot; -- How does it make sense?"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by cacadril2 on 2013-10-16
Hello,

I wonder if I am misunderstanding what this program says, because it does not make sense to me. 

In aptitude, in the ncurses interface, it says at the top: "#Broken: 10".
At the bottom of the screen it says: "[1(1)/...] Suggest 11 keeps" .
I press "b" to see the first broken package. It highlights the following line:

pB  libgettextpo0:i386   +349 kB  <none>  0.18,1,1-5ubun

(but when I press enter to see details of the package, the version is 0.18.1.1-5ubuntu3.)

In the lower half of the terminal window the information panel says:

Some dependencies of libgettextpo0:i386 are not satisfied:
 * libgettextpo0:i386 depends on libgomp1:i386 (>= 4.2.1)
 * libgettextpo0:i386 depends on libunistring0:i386

If I type "e" to "examine" the proposed resolution, I get a list of 11 packages, including libgettextpo0:i386,
under the heading "Keep the following packages at their current version". In the right margin it says "[UNINST]".

This does not make sense to me, because the letter 'p' in the left margin (where it says "pB libgett...") means that the current state is "purged" or not installed. The column where the text "<none>" appears, I presume is the currently installed version of the package, while the version in the left column I presume is the available version that would be installed if I chose to do so.
If I do not install the package, it does not need to have any dependencies satisfied. If I chose to install it, Aptitude should automatically select the dependencies as well.There are thousands of other packages that are not currently installed and whose dependencies are not all currently installed. That would be thousands of "broken" packages.

So I think it must be me who misunderstand what the interface is trying to tell me, or else there is a bug in aptitude.
Can anyone help out?

---

### Post by varunendra on 2013-10-17
Welcome to the forums cacadril2 ! :)

> **cacadril2 said:**
> If I do not install the package, it does not need to have any dependencies satisfied. If I chose to install it, Aptitude should automatically select the dependencies as well.There are thousands of other packages that are not currently installed and whose dependencies are not all currently installed. That would be thousands of "broken" packages.

So I think it must be me who misunderstand what the interface is trying to tell me, or else there is a bug in aptitude.

It is most probably a matter of outdated, held packages which is a common reason for such problems. I am not much familiar with aptitude, but what are you trying to do with it? Install an application, or update or something else?

I feel more familiar with apt-get, so please post back the output of -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

If the first command returns similar errors, then stop there and post back the full output here.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

