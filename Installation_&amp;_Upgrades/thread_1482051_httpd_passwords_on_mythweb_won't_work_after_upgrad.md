---
title: "httpd passwords on mythweb won't work after upgraded to Lucid Lynx"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by vipasane on 2010-05-13
My Mythweb is asking for authentication but none username/password will work. It just prompts for authentication over and over again.

I've found few configurations regarding authentication:

in /etc/apache2/httpd.conf I have following lines:

<Directory "/var/www/mythweb">
    Options Indexes FollowSymLinks
    AuthType Basic
    AuthName "MythTV"
    AuthUserFile /etc/apache2/httpd-passwords
    require user user1 user2
    Order allow,deny
    Allow from all
</Directory>

and in /etc/apache2/sites-available/mythweb.conf I have another config:

    AuthType           Digest
    AuthName           "MythTV"
    AuthUserFile       /etc/mythtv/mythweb-digest
    Require            valid-user
    BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
    Order              allow,deny
    Satisfy            any

none of the username/paswd pairs in Authuserfile are working?
Can there be yet another file / configuraton somewhere? 
How do I know which one apache is using right now?


Any help would be appreciated 
Thanks in advance

---

### Post by vipasane on 2010-05-16
Tried these with no luck, though first two were not enabled
[http://ubuntuforums.org/showthread.php?t=1470695](http://ubuntuforums.org/showthread.php?t=1470695)

I Have Joomla installed in another directory so changed httpd.conf authentication to point on upper directory --> to see if authentication works there as expected with success --> figured out that it's using httpd.conf, commented out authentication related lines from mythweb.config 

Now everything works as expected under Joomla, but under mythweb it keeps on asking for authentication over and over again.

which log I should be digging?

Have no idea how to fix this, I'm an apache newbie 
Plz help me.

---

