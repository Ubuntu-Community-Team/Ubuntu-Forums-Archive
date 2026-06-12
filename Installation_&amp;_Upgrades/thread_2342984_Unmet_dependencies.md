---
title: "Unmet dependencies"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by rajeshwar2 on 2016-11-11
After installing ubuntu 16.04 lts I ```
sudo apt-get update & sudo apt-get upgrade
``` Both commands are run by at first time I didn't get any error but after restart again I ran these commands but I got an error so please give the solution.

```
rajeshwar@rajeshwar-VPCEH16EN:~$ sudo apt-get update
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]                                                                      
Fetched 187 kB in 48s (3,858 B/s)                                                                                                               
Reading package lists... Done

rajeshwar@rajeshwar-VPCEH16EN:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                        Depends: libappindicator1 but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by ian-weisser on 2016-11-11
Please show us the exact instructions you followed to add Google Chrome to your system. A link to those instructions would be very helpful.

---

### Post by rajeshwar2 on 2016-11-11
```
if [[ $(getconf LONG_BIT) = "64" ]]
then
    echo "64bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb &&
    sudo dpkg -i google-chrome-stable_current_amd64.deb &&
    rm -f google-chrome-stable_current_amd64.deb
else
    echo "32bit Detected" &&
    echo "Installing Google Chrome" &&
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb &&
    sudo dpkg -i google-chrome-stable_current_i386.deb &&
    rm -f google-chrome-stable_current_i386.deb
fi

```

---

### Post by rajeshwar2 on 2016-11-11
I am getting this message when I am going to System Updator..

---

### Post by ian-weisser on 2016-11-12
Of course. Same problem.
You didn't install the dependencies that google-chrome-stable needs.
It doesn't matter which frontend to apt that you choose to use. Apt will tell all of them that the package system is broken, and why.

Read the error message again, and try following it's advice:
> **You might want to run 'apt-get -f install' to correct these**.The following packages have unmet dependencies:
 google-chrome-stable : Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                            Depends: libappindicator1 but it is not installed
E: Unmet dependencies. Try using -f.

In 14.04 and later, you can use the preferred '**sudo apt install --fix missing**' instead of the older '**sudo apt-get install --fix-missing**', but both commands do exactly the same thing using apt.

---

