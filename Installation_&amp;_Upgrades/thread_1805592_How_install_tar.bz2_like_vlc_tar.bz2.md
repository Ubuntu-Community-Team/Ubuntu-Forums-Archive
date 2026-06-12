---
title: "How install tar.bz2 like vlc tar.bz2"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by AMIT000 on 2011-07-16
For beanear needed stap to stap details

---

### Post by snowpine on 2011-07-16
VLC is in the Ubuntu Software Center and you can install it with a couple clicks of your mouse.

Or if you're a terminal nerd like me:

```
sudo apt-get install vlc
```

---

### Post by raja.genupula on 2011-07-16
tar xvf pkg_name
cd to that pkg_name
./configure
make 
sudo make install


follow the above steps one by one .... you will be get it . but you can install vlc directly from terminal . google it , you can found .

---

### Post by lovinglinux on 2011-07-16
> **raja.genupula said:**
> tar xvf pkg_name
cd to that pkg_name
./configure
make 
sudo make install

follow the above steps one by one .... you will be get it . but you can install vlc directly from terminal . google it , you can found .

@raja.genupula

Keep in mind not all *tar* files are source code. I don't know about VLC, but many applications binaries are distributed as *tar* files as well and don't require compiling. Besides, the commands you are suggesting may not work for some source code. For instance, that is not the way to compile Firefox, however you posted the [same reply on a Firefox thread]("http://ubuntuforums.org/showthread.php?t=1804691"). Besides, the OP on that thread was just trying to install binaries, since Mozilla also distribute Firefox builds in *tar.bz* files.

Most of the time, when a new user is asking how to install from tar, they are referring to binaries or they don't know that you can install via repository. So, giving compiling instructions to new users will just make them more confuse. 

When I see such post I ask the user first, to make sure he indeed wants to compile software, since some applications can take a lot of time to compile, may require different steps and probably can be installed via repository.

Finally, when recommending compiling commands, please give preference to checkinstall, which is a lot easier to revert if something goes wrong.

---

### Post by oldos2er on 2011-07-16
Assuming you're doing this just for the "fun" of it: [http://www.jbkempf.com/blog/post/2009/03/03/Howto-build-VLC-1.0.0-git-in-Ubuntu-in-less-than-5-commands](http://www.jbkempf.com/blog/post/2009/03/03/Howto-build-VLC-1.0.0-git-in-Ubuntu-in-less-than-5-commands)

---

### Post by lovinglinux on 2011-07-16
> **oldos2er said:**
> Assuming you're doing this just for the "fun" of it: [http://www.jbkempf.com/blog/post/2009/03/03/Howto-build-VLC-1.0.0-git-in-Ubuntu-in-less-than-5-commands](http://www.jbkempf.com/blog/post/2009/03/03/Howto-build-VLC-1.0.0-git-in-Ubuntu-in-less-than-5-commands)

I doubt the OP is looking for compiling instructions, because it's his first post in the forums and he is trying to just install VLC. Most likely he is unaware that software can be installed via Software Center.

---

### Post by oldos2er on 2011-07-16
Quite possible. I try not to assume too much though.

---

