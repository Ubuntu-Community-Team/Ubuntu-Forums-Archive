---
title: "How to reinstall canonical supported default firefox 3.6.x in ubuntu 10.04?"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by sri4985 on 2011-04-25
hi, i have a problem.
i installed Ubuntu 10.04 LTS - the Lucid Lynx in my system.
a default firefox 3.6.16 had came with this ubuntu.
its works fine.
after few days i have upgrade it into firefox 4.0 stable version from firefox supported site using terminal.

but the new verision of firfox is not supporting to my web based project. so, i want to reinstall my previous version of firefox.
but in Ubuntu Software Center -> internet -> web browser
there is no application for "safe and easy webbrowser from mozilla" option.

please please tell me the solution. i need my old firfox which is updates provided by the canonical and ubuntu resources.

please help me...:(:(:(

---

### Post by ajgreeny on 2011-04-25
How exactly did you install the new FF4; what command did you use and on what installation package?

If you used ```
sudo dpkg -i <package>
``` you can probably do it with ```
sudo dpkg -P <package>
```but for this latter one you do not need all the version numbers, just the name.

After the purge, just install the version from the repos again  with software-centre or synaptic.

You may be able to simply use the synaptic option to reinstall FF from the repos over version 4, but I have never been in that situation so I don't know if that works or not.

---

### Post by lovinglinux on 2011-04-25
You need to provide more information on how you installed Firefox 4. Looks like you have installed using a ppa. If this is the case, then you can disable or remove the ppa from Software Sources, then update, then reinstall Firefox. Another option would be using ppa-purge package.

I am not providing any commands until I can confirm how you installed Firefox 4.

Meanwhile, take a look at the [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by sri4985 on 2011-05-05
thanku boss,
ya, i have installed firefox 4 from ppa repositry.
and my problem also solved.

i had fallow below procedure.

"HOW TO INSTALL FIREFOX 4 IN UBUNTU :
---------------------------------------------

1) open terminal, run fallowing commands.

sudo add-apt-repository ppa:mozillateam/firefox-stable

sudo apt-get update

sudo apt-get upgrade



HOW TO UN-INSTALL FIREFOX 4 and INSTALL FIREFOX 3.6 :
-----------------------------------------------------------

1) goto SYSTEM -> ADMINISTRATION -> SOFTWARE RESOURCES -> OTHER RESOURCES -> 

2) uncheck the MOZILLA software resource.

3) now open the terminal run the below commands

su

<enter the password>

apt-get update

apt-get remove firefox

apt-get install firefox-3.6


---------------- FINISH ---------------------------"

---

