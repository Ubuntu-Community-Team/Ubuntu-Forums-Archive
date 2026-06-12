---
title: "Help needed on how to install Tar.Gz. files"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by aerwin on 2008-05-23
Hi I have been trying to find out how to get things installed on ubuntu version 8.04. Every time I download a piece of software all it gives me is (*.tar.gz)files. How do I install these softwares if the synaptic Package manager doesn't see them? Please help

:confused:

---

### Post by hal8000 on 2008-05-23
> **aerwin said:**
> Hi I have been trying to find out how to get things installed on ubuntu version 8.04. Every time I download a piece of software all it gives me is (*.tar.gz)files. How do I install these softwares if the synaptic Package manager doesn't see them? Please help

:confused:

First of all you extract the package. If for example you
downloaded foobar.tar.gz  then extract it with:

tar xzvf foobar.tar.gz


This will unpack the contents and create a folder in the directory you downloaded it to. You can probably use nautilus to browse the folder contents. There will be a readme.txt or install file, these give instructions on how to install, but its  generally

./configure
make

then 
sudo make install

N.B. some software may not work due to missing dependencies or require different library files.

You may be better off posting what you want to install and where you are downloading from, especially if its not on the Ubuntu repositories

---

### Post by ajgreeny on 2008-05-23
As a new user (?) you would be best advised to not install programs that way.  If you know what the program you want is called search for it in synaptic and install it from there, or use add/remove programs in the menus.  Using tarballs is something I have never needed to do in 3 years of using Ubuntu, and I doubt I ever will need to.  Everything I need is available from the repos, and I imagine it will be for you too.

Just a tip, when searching for programs in synaptic always use lower case search terms.

---

### Post by aerwin on 2008-05-23
Thanks for the help. I am going to try what you guys said and let you know how it went.

---

### Post by housam on 2008-05-23
Here is also a guide for [[COLOR="Red"]_how to install anything in Ubuntu_[/COLOR]]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Herman on 2008-05-23
Here's another nice link, [Complete Guide to Installation in Ubuntu]("http://ubuntuforums.org/showthread.php?t=500020") by starcraft.man.

I agree with ajgreeny and housam, no-one should probably need to be installing any software from a .tar.gz file they downloaded from some site on the internet unless the software they are installing cannot be found as a .deb files in a repository and they're an expert and they are sure they know what they are doing.
hal8000's advice would be correct for someone who is certain they really need to install software that way.

Synaptic Package Manager and Add/Remove software are really nice frontend 'GUI' programs for apt-get.
Our apt-get system comes from Debian and it's really interesting to try to understand how that works. Even if you don't quite understand it thoroughly, it's worth spending a little time reading about it so you'll have some idea, and because it's cool! Our apt-get system is one of the main reasons why a person would want to choose Ubuntu or any other Debian based distro over some other Linux, or any other operating system. Our apt-get system is great!

Everyone should read [about apt-get]("http://ubuntuforums.org/showthread.php?t=103462") by ubuntu_demon, 
which has a link to -->  [A Concise apt-get / dpkg primer for new Debian users]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html"). 

These links from Ubuntu Community Documentation are worth reading too: 
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")   |    [Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

Here is a link that explains why we have "Main", "Restricted"," Universe, and "multiverse", [Components]("http://www.ubuntu.com/community/ubuntustory/components"). (Community).

Yet another really interesting link is this one, [SecureApt - Debian Wiki]("http://wiki.debian.org/SecureApt")
 
Here's another, [SecureApt - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SecureApt")

We should never try to install software packages from the internet or from strange sources. (Unless we really need that particular software and there is no other way of getting it, and we are experts and understand the risks. [What is a Rootkit?]("http://www.linfo.org/rootkit.html") - The Linux Information Project - [LINFO]("http://www.bellevuelinux.org/linfo.html")

We should always get our software from the Ubuntu repositories because then we know it is authenticated, safe, and compatible with Ubuntu.

---

