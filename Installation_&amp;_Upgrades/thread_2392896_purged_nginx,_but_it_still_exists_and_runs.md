---
title: "purged nginx, but it still exists and runs"
date: 2018-05-26
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-26
i have done "apt-get purge nginx" but not only is it still preset, it starts up when i reboot.  the reason i did this is because i wanted to run apache2.  **what direction do i need to go to deal with this?**

---

### Post by deadflowr on 2018-05-27
```
dpkg --list | grep nginx
```
Will show all nginx related packaged installed.

---

### Post by Skaperen on 2018-05-27
i see it now.  when i "install nginx" it adds in "nginx-common" and "nginx-core".  but when i "remove nginx" (actually i used "apt-get purge") it does not remove those.  and since they were added when "nginx" was installed, i think it is clear that these 2 packages are depended on by nginx.  so they should have no dependencies after "nginx" is removed.  yet "apt-get autoremove" does not remove them.  so what is the correct procedure to fully remove package "foo" and all its dependencies that nothing else depends on (whether installed before "foo" was installed, or installed after "foo" was installed).  i believed that to do this one would do either "apt-get remove foo" or "apt-get purge foo" followed by "apt-get autoremove".  it looks like i was wrong.

---

### Post by PaulW2U on 2018-05-27
> **Skaperen said:**
>   i believed that to do this one would do either "apt-get remove foo" or "apt-get purge foo" followed by "apt-get autoremove".  it looks like i was wrong.
From the output of
```
apt show nginx:
```
```
This is a dependency package to install either nginx-full (by default),
 nginx-light or nginx-extras.

```
Had you installed nginx-full and then removed it you would have seen the prompt to use "apt-get autoremove" to remove the remaining packages. 

From the Debian Wiki, a dependency package is:
> An empty binary package that exists only for the sake of its declared dependencies on other packages, for instance to keep the current default version of gcc installed.
I suppose it's like removing "ubuntu-desktop". You don't really remove anything but the package is best left in place to ensure proper operation of your installation when updating or upgrading.

For most package removals your thinking was correct.  :)

---

### Post by Skaperen on 2018-05-28
so what keeps "apt-get autoremove" from removing "nginx-common" and "nginx-core"?  those are the only packages i see when i do "dpkg -l | fgrep nginx".

is it the case that two packages that depend on each other will fool "apt-get autoremove"?

is there a way (a command or pipeline of commands) to get the dependency tree of either the packages that are installed and/or *all* packages in the repositor{y|ies}?

---

### Post by PaulW2U on 2018-05-28
> **Skaperen said:**
> so what keeps "apt-get autoremove" from removing "nginx-common" and "nginx-core"?  those are the only packages i see when i do "dpkg -l | fgrep nginx".
I also saw around 10 lib* packages for removal when I tested before replying to you.
> **Skaperen said:**
> is it the case that two packages that depend on each other will fool "apt-get autoremove"?
No, I think it's because nginx is a *dependency* package not a normal package. The dependencies are set in such a way that removing nginx doesn't remove anything else and there's nothing for "apt-get autoremove" to do. Like when you uninstall "ubuntu-desktop", "apt-get autoremove" won't then remove your entire desktop.
> **Skaperen said:**
> is there a way (a command or pipeline of commands) to get the dependency tree of either the packages that are installed and/or *all* packages in the repositor{y|ies}?
apt depends <package> and apt rdepends <package> will provide you will a lot of dependency information. I find using synaptic or aptitude easier to use especially when there is a lot of output to the screen.

As I don't fully understand it all myself hopefully someone else will step in and explain anything that I have left unanswered. However, you have raised an interesting point. How is anyone supposed to know from using just apt or apt-get commands that when uninstalling nginx that there are further packages to be removed? When using synaptic it would be obvious to me when searching for nginx that other packages that include nginx in their name needed to be removed so I would also tag those for removal.

---

### Post by Skaperen on 2018-05-28
i want to get rid of everything nginx related and that nginx depends on that nothing else does so it is just as if nginx was never installed, even though it was part of the image install my VPS provider provided.  i do not know if nginx is pre-installed by the official server edition.

---

