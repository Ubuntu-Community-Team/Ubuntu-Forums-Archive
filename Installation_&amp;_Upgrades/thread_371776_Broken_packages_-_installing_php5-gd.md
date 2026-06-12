---
title: "Broken packages - installing php5-gd"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by adam_pretty on 2007-02-27
I have been trying to get GD enabled in php5 - 
(so that I can use the automatic thumbnail creation in Wordpress)

but when I try and install using sudo aptitude php5-gd, I get the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  php5-gd 
The following NEW packages will be automatically installed:
  libt1-5 
The following packages have been kept back:
  lighttpd 
The following NEW packages will be installed:
  libt1-5 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 174kB of archives. After unpacking 512kB will be used.
The following packages have unmet dependencies:
  php5-gd: Depends: phpapi-20051025 which is a virtual package.
           Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.2.0-0.dotdeb.3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
php5-gd [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  lighttpd 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

```

I dont know how to resolve it - tried uninstalling and reinstalling php5 and apache2 but no joy...

---

### Post by adam_pretty on 2007-02-28
* bump *

?

---

### Post by williammanda on 2007-02-28
I would be interested to see this answer as well. I have the same issue with a different file.
Thanks

---

### Post by adam_pretty on 2007-03-02
I am now getting something similar with mysql ! Help!

Just suddenly started getting errors while working on a site... mysql is now broken and I dont know how to fix it.

```

adam@adam-desktop:~$ sudo aptitude install php5-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  php5-mysql php5-mysqli 
The following packages have been kept back:
  lighttpd 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 62.6kB of archives. After unpacking 279kB will be used.
The following packages have unmet dependencies:
  php5-mysqli: Depends: phpapi-20051025 which is a virtual package.
               Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.2.0-0.dotdeb.3 is installed.
  php5-mysql: Depends: phpapi-20051025 which is a virtual package.
              Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.2.0-0.dotdeb.3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
php5-mysql [5.2.0-0.dotdeb.3 (now)]

Keep the following packages at their current version:
php5-mysqli [Not Installed]

Score is -31

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  lighttpd 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done

```

---

### Post by adam_pretty on 2007-03-02
OK

The solution (for mysql at least) was to NOT accept the 1st solution, and go with the 2nd... downgraded everything to the ubuntu version, from dotdeb3. Works now :)

---

### Post by chrisishardcore on 2007-09-29
When I tried to install this on debian I got a similar error.  In my case, it said it was looking for:
5.2.0-8+etch7 but that some other version of php5-common was installed (5.2.0.10 or so).

To fix this, go to aptitude, go to installed packages (or wherever php5-common lives).
Click on php5-common, look at the details, scroll down.  You will see a list of version.  Find the version that you are looking for (in my case the 8+etch7 one) and then mark it to be installed.  It gave me some warning about downgrading, I just said ok and continued to tell it to install.

Once that completed, php5-gd installed with no problems.  I only wish I'd figured that out 5 months ago!

---

