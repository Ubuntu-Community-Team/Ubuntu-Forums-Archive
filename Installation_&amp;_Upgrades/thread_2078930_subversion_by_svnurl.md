---
title: "subversion by svn://url"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-11-01
hi im back, my friend wanted SVN on a ubuntu SERVER edition vm....

```

sudo apt-get install subversion

```

```

sudo mkdir /home/svn
sudo mkdir /home/svn/project
sudo groupadd svn
sudo chgrp svn /home/svn/project
sudo chmod g+w /home/svn/project
sudo chmod g+s /home/svn/project

```

as every user you want to access your svn run this....

```

sudo usermod -a -G svn $USER

```

get with the sudo voodoo

```

sudo su

```

dump moar coad!!!

```

umask 002
svnadmin create /home/svn/project
umask 022
cd /home/svn/project/conf
mv svnserve.conf svnserve.conf.backup
mv passwd passwd.backup

```

MOAR

```

cat > /home/svn/project/conf/passwd << EOF
[users]
subversion = svn
EOF

```

lock er down

```

chmod 600 passwd

```


MOAR!!!!!

```

cat > /home/svn/project/conf/svnserve.conf << EOF
[general]
anon-access = read
password-db = passwd
[sasl]
EOF

```

test run

```

sudo svnserve -d --foreground -r /home/svn

```


quit playing in root already!
```

exit

```

and since svn:// is so UGLY when your guessing how to feed it urls...

```

cd
svn co svn://127.0.0.1:3690/project project

```

```

cd /etc/init.d
sudo wget http://odyniec.net/articles/ubuntu-subversion-server/svnserve .
sudo chmod 750 svnserve

```
edit svnserve to point to

DAEMON_ARGS="-d -r /home/svn"

(if you botch it 'sudo update-rc.d -f svnserve remove')

```

sudo update-rc.d svnserve defaults

```

to commit your username is "subversion" and your password is "svn"

---

