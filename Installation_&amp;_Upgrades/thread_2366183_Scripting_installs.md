---
title: "Scripting installs"
date: 2017-07-14
forum: Installation &amp; Upgrades
---

### Post by rednecknerd2 on 2017-07-14
I am trying to install and configure a package using a script. (specifically slapd). The problem I am running into is that slapd requires me to enter information during the installation process. The information is more complicated than just accepting so I cant just use 

sudo apt -y install slapd

I have previously used the non interactive installer, and then just copied the config files to the new server, but this is a clunky situation and with slapd, there is a password involved in the configuration that has been causing problems. 

What I would like is the ability to enter the info I need into the script, and have it insert the correct answer as the installation progresses. 

Any ideas?

---

### Post by TheFu on 2017-07-14
There is an option for non-interactive installation. This is part of APT.  

Did you try **export DEBIAN_FRONTEND=noninteractive**?  Did that not work?

Then you can use whatever method you like to make the config files have whatever they need to have - ansible is how I do it. Ansible's APT module also has the setting for non-interactive package installation, but there is certainly a way to do that with apt-get.  It worked the last time I used it - last server build was about 3 months ago.

Google found this: [https://askubuntu.com/questions/556385/how-can-i-install-apt-packages-non-interactively](https://askubuntu.com/questions/556385/how-can-i-install-apt-packages-non-interactively)

---

