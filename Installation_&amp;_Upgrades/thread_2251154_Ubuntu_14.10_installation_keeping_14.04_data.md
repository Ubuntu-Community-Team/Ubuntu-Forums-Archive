---
title: "Ubuntu 14.10 installation keeping 14.04 data?"
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by neo-xactor on 2014-11-02
I have downloaded iso of 14.04 iso and i want to install it keeping my 14.04 data like i have installed almost all kali linux tools in that . So its painful to download again in new 14.10 
Is there any way?

---

### Post by yancek on 2014-11-02
It might work but the question I would have is why update to 14.10 when support for it will end next year when you will still have nearly four years of support for 14.04.  What's not working on 14.04?

---

### Post by neo-xactor on 2014-11-02
i wanted to try new .. :)

---

### Post by neo-xactor on 2014-11-02
you know how to do it?

---

### Post by oldfred on 2014-11-02
I like to keep long term install as main working install, and then create another 20 or 25GB for another / (root) partition for testing newer versions. Then I can test and still know I can boot.

You cannot keep versions as newer install will more often than not have a newer version of software.
But you can export a list of installed applications and use that to reinstall those same applications in new install.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

My standard rsync to another drive is so I can easily reinstall.

 Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by neo-xactor on 2014-11-02
I know it but I wanted somthing like that make backup of everything i installed and in 14.10 i can restore? I heared about fake-root but dont know is it exactly do the same?

---

### Post by yancek on 2014-11-02
> I know it but I wanted somthing like that make backup of everything i installed and in 14.10 i can restore?

If you mean software applications you installed, oldfred explained what you need to do above.  If you are referring to data such as documents, video, music you should have all that on a separate data partition then it won't be affected by an update.  The suggestion above to create a separate partition on which to test new systems is good.  You could also install VirtualBox and use that to test.

---

