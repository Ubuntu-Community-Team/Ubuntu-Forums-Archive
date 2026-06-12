---
title: "installing Genymotion"
date: 2016-06-10
forum: Installation &amp; Upgrades
---

### Post by dawicz on 2016-06-10
Hi there, 
 
In order to install Genymotion I'd follow all steps from this video [https://www.youtube.com/watch?v=k3MSTD9SLy4](https://www.youtube.com/watch?v=k3MSTD9SLy4), but the programm didn't even start. That's what was written in the terminal: 

root@dawid-SATELLITE-L850:/home/dawid/Downloads/genymotion# ./genymotion
./genymotion: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /home/dawid/Downloads/genymotion/libQt5Core.so.5)
./genymotion: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /home/dawid/Downloads/genymotion/libQt5WebKit.so.5)
./genymotion: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /home/dawid/Downloads/genymotion/libicui18n.so.52)
./genymotion: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `CXXABI_1.3.8' not found (required by /home/dawid/Downloads/genymotion/libicuuc.so.52)
./genymotion: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by /home/dawid/Downloads/genymotion/libQt5Qml.so.5)
root@dawid-SATELLITE-L850:/home/dawid/Downloads/genymotion# ^C

Virtual box works fine. What I found in the Web is that I need to add some libraries, but dunno how to do it :(

---

### Post by Rustan on 2016-06-10
**[COLOR="#FF0000"]root[/COLOR]**@dawid-SATELLITE-L850

it definitely joke ... am I right?

Genymotion 2.7.1 requires
Ubuntu 15.10 (Wily Werewolf) or above (64bit)

I am using Kubuntu 16.10 there is no problem with Genymotion

---

### Post by squirrel3 on 2016-06-10
Perhaps try this method. Install and reboot.

[http://techapple.net/2014/07/tutorial-installsetup-genymotion-android-emulator-linux-ubuntulinuxmintfedoraarchlinux/](http://techapple.net/2014/07/tutorial-installsetup-genymotion-android-emulator-linux-ubuntulinuxmintfedoraarchlinux/)

---

### Post by dawicz on 2016-06-22
> **Rustan said:**
> **[COLOR=#FF0000]root[/COLOR]**@dawid-SATELLITE-L850

it definitely joke ... am I right?

Genymotion 2.7.1 requires
Ubuntu 15.10 (Wily Werewolf) or above (64bit)

I am using Kubuntu 16.10 there is no problem with Genymotion

The guy in instrucion vid got even older Ubuntu distribution I think.

---

### Post by dawicz on 2016-06-23
> **squirrel3 said:**
> Perhaps try this method. Install and reboot.

[http://techapple.net/2014/07/tutorial-installsetup-genymotion-android-emulator-linux-ubuntulinuxmintfedoraarchlinux/](http://techapple.net/2014/07/tutorial-installsetup-genymotion-android-emulator-linux-ubuntulinuxmintfedoraarchlinux/)


It's not working at all, I just got a pop-up with error every time I switch on my PC. I will update my ubuntu version and try again. As was said in the first post, my distribution might be too old.

---

