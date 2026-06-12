---
title: "Issues in upgrading to 18.04"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by karthikeyan.d on 2018-08-15
I recently bought a new laptop which came with 16.04. I wanted to
upgrade it to 18.04 immediately. After using the Software Updater
to update 16.04, I started "update-manager -cd" from a terminal.
When it finished the "Installing the upgrades" step, it showed
the message "Checking for installed snaps" and just hung there. It
also changed its colour. After waiting for more than 10 mins, I
terminated update-manager (^C) and restarted it. It did some quick
checks and suggested a system restart. I did and saw that the system
came up with 18.04.

I am now using 18.04 but would like to confirm that the upgrade was
completed sucessfully, especially the cleaning up part which I did
not see in the UI. How to check this?

------------------------

Also, during the installation step, I saw some error messages related
to some packages. For example,

(frontend:27373): GdkPixbuf-^[[1;33mWARNING^[[0m **: ^[[34m10:31:08.101^[[0m: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory^M
^M
This likely means that your installation is broken.^M
Try running the command^M
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache^M
to make things work again for the time being.^M


/usr/sbin/dkms: line 2026: echo: write error: Broken pipe
/usr/sbin/dkms: line 2028: echo: write error: Broken pipe

Do these mean that something is broken in the installation?

Thanks

---

### Post by Claus7 on 2018-08-15
Hello,

what does theses commands do?
sudo apt update
sudo apt upgrade

If you have still packages that have a problem, then you will get some messages from those commands. You will be able to see if packages are up to date and if you need to upgrade any of them.
I cannot tell from the messages you got if everything in your system is ok, yet if something went wrong, you will be able to have an idea from these commands.

Regards!

---

### Post by karthikeyan.d on 2018-08-17
> **Claus7 said:**
> Hello,

what does theses commands do?
sudo apt update
sudo apt upgrade

If you have still packages that have a problem, then you will get some messages from those commands. You will be able to see if packages are up to date and if you need to upgrade any of them.
I cannot tell from the messages you got if everything in your system is ok, yet if something went wrong, you will be able to have an idea from these commands.

Regards!

"sudo apt update" mentioned that 3 packages need to be upgraded. No error messages. Saw two interesting messages during the "sudo apt upgrade" run. The first one listed a bunch of packages and said that they were automatically installed and were no longer required. The second was

/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory

Thanks

---

### Post by Claus7 on 2018-08-27
Hello,

you could try also:
sudo apt autoremove

This will remove all the unnecessary packages from your system. It might help you to get rid of the message that you are getting as well.

Regards!

---

### Post by karthikeyan.d on 2018-10-05
I downloaded the iso of 18.04.1 and installed it, replacing the 16.04. Things seem fine so far. Thanks for the help.

---

