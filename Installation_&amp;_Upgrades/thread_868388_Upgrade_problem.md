---
title: "Upgrade problem"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by satimis on 2008-07-23
Hi folks,


Ubuntu LAMP server 7.04 amd64


Encountered following upgrade problem after running ugdate.


$ sudo apt-get ugrade```

.....
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
critical bugs of php5 (5.2.1-0ubuntu1.5 -> 5.2.1-0ubuntu1.6) <done>
 #471104 - php5: Please rebuild against up to date timezone data (Fixed: php5/5.2.6-1)
serious bugs of linux-libc-dev (2.6.20-17.36 -> 2.6.20-17.37) <pending>
 #435700 - keepalived: FTBFS: conflicting types for 'loff_t'
   Merged with: 434040
Summary:
 php5(1 bug), linux-libc-dev(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]

```

After entering "n" and pressing [Enter]

```

****************************************************************************
****** Exit with an error by force in order to stop the installation. ******
****************************************************************************
E: Sub-process if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi returned an error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi

```


Please advise how to fix the problem.  TIA


B.R.
satimis

---

