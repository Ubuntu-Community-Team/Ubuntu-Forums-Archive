---
title: "Script install slapd with admin ldap password"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by paco699 on 2012-09-06
Hello all,

In my script bash, i search to install the package 'slapd' (openldap) [FONT=Arial][COLOR=#0]automatically on ubuntu12.04.

The thing is that slapd ask, [/COLOR][/FONT][FONT=Arial][COLOR=#0][FONT=Arial][COLOR=#0]in ncurses mode,[/COLOR][/FONT] to define an admin password for my openldap directory.

How can i put/insert this password in my script [FONT=Arial][COLOR=#0]to automate the installation?


Thanks very much


paco
[/COLOR][/FONT][/COLOR][/FONT]

---

### Post by paco699 on 2012-09-07
Hello all,

I looked for and I found many solutions.. For use of 'preseeding' with 'debconf-get-selections':
[http://www.debian-administration.org/articles/394](http://www.debian-administration.org/articles/394)
```
sudo debconf-set-selections <<< 'slapd/root_password password your_password'
sudo debconf-set-selections <<< 'slapd/root_password_again password your_password'
sudo aptitude -y install slapd
```And i fell also on this thread:
[http://stackoverflow.com/questions/1202347/how-can-i-pass-a-password-from-a-bash-script-to-aptitude-for-installing-mysql](http://stackoverflow.com/questions/1202347/how-can-i-pass-a-password-from-a-bash-script-to-aptitude-for-installing-mysql)

```
sudo DEBIAN_FRONTEND=noninteractive aptitude install -q -y
```or
```
#!/bin/bash

installnoninteractive(){
  sudo bash -c "DEBIAN_FRONTEND=noninteractive aptitude install -q -y $*"
}

installnoninteractive slapd
```Also I found 'expect'. For the use of 'expect':
```
#!/bin/bash
aptitude update
aptitude install expect

VAR=$(expect -c '
spawn aptitude -y install slapd
expect "New password for the slapd \"root\" user:"
send "PasswordHere\r"
expect "Repeat password for the slapd \"root\" user:"
send "PasswordHere\r"
expect eof
')

echo "$VAR"

aptitude -y install slapd
```but for 'expect' the need to install the package.

After testing all these solutions, i prefer:
```
DEBIAN_FRONTEND=noninteractive aptitude install -q -y
```It's perfect for me.

---

