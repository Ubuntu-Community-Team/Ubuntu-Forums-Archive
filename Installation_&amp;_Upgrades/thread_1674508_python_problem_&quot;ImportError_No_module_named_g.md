---
title: "python problem: &quot;ImportError: No module named gtk&quot;"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by rclocher3 on 2011-01-24
Greetings all,

Recently I tried to launch gufw, otherwise known as the Firewall Configuration application.  Nothing happened when I launched it, so I launched it from a terminal:

rob@teeny:~$ gufw
    from instance   import Check
  File "/usr/share/gufw/instance.py", line 18, in <module>
    import gtk
ImportError: No module named gtk

It seems that I have a Python problem.  I ran the Update Manager, and my system is up-to-date.  (I'm running Maverick Meerkat Netbook Edition.)

Then I remembered that I tried to install Python 2.5.5 from source a couple months ago, in order to run the game FreeOrion.  (I never did get FreeOrion working, but the problem was with OpenGL and my graphics adapter.)

So I don't remember if I was successful in installing Python 2.5.5 because it was a while ago.  I'm afraid that my Python installation is broken because of my tinkering.

If someone could help me fix my Python installation, I would be very grateful!

- Rob

---

### Post by sikander3786 on 2011-01-24
Please post the complete outputs of these commands.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by Claus7 on 2011-01-24
Hello,

in case you see that you have to get rid of many packages due to the fact that the two versions conflict with each other, while you are trying to reinstall or reconfigure packages, do not hurry to remove some if proposed.

I had messed the installation of python myself and this is how I was able to solve my problem. Do not know if this might ruin the execution of the game though...
[http://ubuntuforums.org/showthread.php?t=1084491](http://ubuntuforums.org/showthread.php?t=1084491)

Regards!

---

### Post by rclocher3 on 2011-01-25
Sikander and Claus, thank you very much for your help!  I also reported this problem as a Ubuntu question for the gui-ufw package here:
[https://answers.launchpad.net/ubuntu/+source/gui-ufw/+question/142613](https://answers.launchpad.net/ubuntu/+source/gui-ufw/+question/142613)

They were able to point me in the right direction.  I had installed Python 2.5.5 from source code a while ago, and that installation was causing the problem.  The solution in my case was to manually remove the installation of Python 2.5.5.

Thanks again!  It makes me happy to be part of such a helpful community.

- Rob

---

