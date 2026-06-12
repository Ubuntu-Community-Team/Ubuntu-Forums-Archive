---
title: "apache 2 not working after installng webmin"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by vinu76jsr on 2007-10-17
I installed apache php and mysql on my feisty following the instruction on how to forge
but it required me to install apache module for php but it gives following error

and after webmin another problem occur my apache2 server stop working

<code>
root@vrindavan:/home/vaibhav# apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed or
                                apache2-mpm-itk but it is not going to be installed
</code>

help me and thanx in advance

---

