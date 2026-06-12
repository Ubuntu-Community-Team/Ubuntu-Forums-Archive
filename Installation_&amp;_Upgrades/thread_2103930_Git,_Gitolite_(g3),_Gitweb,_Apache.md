---
title: "Git, Gitolite (g3), Gitweb, Apache"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by wand3r3r on 2013-01-11
So I have been trying to pull together some information to set up gitolite on my servers to allow per repo based access.  One of my developer teams has some temporary folks coming on board to help them along and while they are here we don't want them having unlimited access to all the repos and our customer's proprietary products.   Gitolite managed this very well.  However my developer teams also use gitweb.  The team wanted user based permission on gitweb as well.  We would not want the new folks downloading snapshots or even copying and pasting lines of code.  After some research I found the information and explanations lacking.  So this is my attempt to pull together some of that information

My first step was getting gitolite version 3 (g3) installed and working in a basic fashion.  There was nothing special about this.  Created a user git and installed $HOME/bin.
[http://sitaramc.github.com/gitolite/qi.html]("http://sitaramc.github.com/gitolite/qi.html")

Next to reconfigure gitweb.  Again nothing special.
```
$projectroot = "/home/git/repositories";
$projects_list = "/home/git/projects.list";
```

I had to set the .gitolite.rc UMASK value
```
UMASK = 0022 
```
I found that the suggested mask of 0027 did not work properly for me.  I also changed the permission set on the existing repos at this time
```
chmod -R 755
```

Added the following code to my /etc/gitweb.conf and followed the suggested changes documented in the file.
[http://sitaramc.github.com/gitolite/gitweb.conf.html]("http://sitaramc.github.com/gitolite/gitweb.conf.html")

Added the git group to the www-data and the www-data group to git
```
sudo usermod -a -G www-data git
sudo usermod -a -G git www-data
```

At this point I had been reading a lot about htpasswd in "g2" but couldn't find euivelent documentation about "g3" So I created the htpasswd file.
```
su - git
cd ~/
touch htpasswd
```

And added the following to the .gitolite.rc
```
%RC = (
    HTPASSWD_FILE              => '/home/git/htpasswd'
<sic>
 COMMANDS                    =>
        {
            <sic>
            'htpasswd'          =>  1,
        },
<sic>
```

[http://www.marcmorgan.ca/2011/06/15/version-control-with-git-access-control-with-gitolite-and-authenticated-web-repository-viewing-with-gitweb-apache-on-ubuntu-11-04-server/]("http://www.marcmorgan.ca/2011/06/15/version-control-with-git-access-control-with-gitolite-and-authenticated-web-repository-viewing-with-gitweb-apache-on-ubuntu-11-04-server/")

Then added password authentication to the /etc/apache2/conf.d/gitweb file.  This added password based access to the site.
```
<Directory /usr/share/gitweb>
  Options FollowSymLinks +ExecCGI
  AddHandler cgi-script .cgi
  # User based authentication for gitweb
  AuthType Basic
  AuthName "Gitweb"
  AuthUserFile /home/git/htpasswd
  Require valid-user
</Directory>
```

Now all I had to do was create a password for the htpasswd file
```
ssh git@<myserver> htpasswd
```

---

