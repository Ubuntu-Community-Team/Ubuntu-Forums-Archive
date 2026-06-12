---
title: "Updating Wordpress site with SFTP"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by Will_Moonen on 2015-05-26
Hi Everyone,

Posting something about Wordpress might be a bit of a stretch here.
However, since it is based on Ubuntu and vsftp I'm trying my luck... :)

I&#8217;m having trouble trying to update plugins and Wordpress (sftp-option) using vsftpd.
When updating Wordpress it ends with: &#8220;Unable to locate WordPress Root directory&#8221;.
When updating plugins it ends with: &#8220;Unable to locate WordPress Content directory (wp-content)&#8221;.

I&#8217;m running Ubuntu 14.04.2 with all updates.

The different Wordpress sites are installed as a virtual host in separate folders under /var/www/html.
I have installed vsftpd as described here: [https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html).
In addition, I have created a separate user account (being wp-update) pointing to /var/www/html as being the home for all the Wordpress sites (represented as a folder for each virtual hosts). I&#8217;m able to login using FileZilla/sftp with this wp-update account and can create folders and files. 

The (self-signed!) certificates are created with this:
[http://www.server-world.info/en/note?os=Ubuntu_14.04&p=ssl](http://www.server-world.info/en/note?os=Ubuntu_14.04&p=ssl)

The vsftp log has multiple entries like the one below:
Tue May 26 18:54:22 2015 [pid 14175] [wp-update] DEBUG: Client "192.168.0.150", "No SSL session reuse on data channel."

When selecting the ssh2-option, the update was successful without entering any of the authentication keys. However, somehow, I&#8217;m not convinces that this is how it is supposed to work?!

What am I missing here?

---

### Post by SeijiSensei on 2015-05-26
Why aren't you updating from the WP Dashboard?

---

### Post by Will_Moonen on 2015-05-27
> **SeijiSensei said:**
> Why aren't you updating from the WP Dashboard?

This is the result when trying to update from the WP dashboard.

---

### Post by SeijiSensei on 2015-05-27
I don't understand the problem then.  Updating from the Dashboard just downloads objects from the WP servers and installs them.  There's no need for vsftpd or anything like that. That's the package you would install to create your own FTP server, not use theirs.

I don't see much need for encryption when installing packages so I can't be much more help here, I'm afraid.

---

### Post by Will_Moonen on 2015-05-27
> **SeijiSensei said:**
> I don't understand the problem then.  Updating from the Dashboard just downloads objects from the WP servers and installs them.  There's no need for vsftpd or anything like that. That's the package you would install to create your own FTP server, not use theirs.

I don't see much need for encryption when installing packages so I can't be much more help here, I'm afraid.

Thanks for the update. :D

This now becomes somewhat confusing. Everytime I tried updating, the following line is written in the vsftpd-log:
Tue May 26 18:54:22 2015 [pid 14175] [wp-update] DEBUG: Client "192.168.0.150", "No SSL session reuse on data channel." 

Would you know where that comes from?
Because it is this message that made me believe Wordpress is invoking vsftpd (one way or the other).

---

### Post by SeijiSensei on 2015-05-27
I really don't know. I see postings on the Internet like this: [http://www.jamison.org/2010/12/04/how-to-configure-wordpress-for-automatic-ftps-updates-using-vsftp-in-ubuntu/](http://www.jamison.org/2010/12/04/how-to-configure-wordpress-for-automatic-ftps-updates-using-vsftp-in-ubuntu/), but nowhere does it tell me why I would want to use SFTP or why it needs vsftpd for this purpose.  To me this seems to make a simple task more complex, but my understanding of Wordpress consists of getting my blogs to work on my public web server.  Perhaps it's because I'm not as a paranoid about security as some people.  In my twenty years of hosting web sites, I've only had one insignificant breach many years ago, and that resulted from not keeping Apache updated. I've written my fair share of PHP applications, too, and none of them has been breached.

Searching Google for that particular error string (always a good first step in cases like this) gives me this: [https://www.google.com/search?q=No+SSL+session+reuse+on+data+channel](https://www.google.com/search?q=No+SSL+session+reuse+on+data+channel)

---

### Post by RobGoss on 2015-05-28
If your having trouble updating your WordPress website you should call your hosing provider, I had a problem like this one time and it was because my hosting provider had placed a restriction on my account for some reason.

---

### Post by Will_Moonen on 2015-05-28
Not sure what went wrong here.
I was able to get things going with the help of:
[https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-12-04)

And more in particular:
> sudo chown www-data:www-data /var/www -R  
sudo chmod g+w /var/www -R 

Thank you for the time and patience,
Will Moonen

---

### Post by SeijiSensei on 2015-05-29
That error message about vsftpd turned out to be a red herring it appears.

The Apache web server runs as the user called "www-data" and has the same permissions as that user, which is to say hardly any.  Because WP uses Apache+PHP, it is acting as the www-data user.  When you run updates in WP, it needs to write into a number of directories in the wordpress tree like /wp-includes/ and, for things like themes, /wp-content/.  That mean those directories must have permissions that let the Apache user write into them.  This is required no matter what method you use for updates.

The commands you entered above give the server permission to write anywhere in your web directories.  That solves the problem but leaves a very big security hole in its wake.  If someone can trick the web server into writing something else into those directories, your site can be defaced by changing the content in /wp-content/.  They could also turn your site into the host for a spamming attack where emails are sent directing people to visit a "pharmacy" site hiding inside yours.  

The most secure method is to turn off write permissions and only enable write access to the wordpress tree when you plan to run an update.  However this poses a problem if you upload objects like graphics to your site.  Those are written into /wp-content/uploads/ which contains a set of subdirectories by year and month.  So you'll need to enable write permissions there even if you turn them off everywhere else.

Turn off write permissions except for uploads
```

sudo chmod a-w /var/www -R
sudo chmod u+w /var/www/wordpress/wp-content/uploads -R

```


For updates:
```

cd /var/www
sudo chmod u+w wordpress -R
[run the updates from the Dashboard]
sudo chmod u-w wordpress -R
sudo chmod u+w wordpress/wp-content/uploads -R

```

---

