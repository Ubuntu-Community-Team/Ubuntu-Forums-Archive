---
title: "Apache short url"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-11-29
Hello.

I would like to make a "Short Url" in apache2 so I dont have to typ tls-ams-sgr-01/blablabla and just bla/ and get to the page.

I have made a CNAME in bind, but now I have to configure something in apache2 but I dont know what, where and how.

If someone could point me to the right direction.

Thanks in advance!

---

### Post by slickymaster on 2012-11-29
The recommended way to setup short URLs in Apache is by editing the Apache config files. This requires that you have access to the server configuration. If you are on a shared host, you most likely don't and will need to use a **.htaccess** file instead. Using **.htaccess** files is less efficient and doesn't give you as much control when it comes to fancy setups with multiple domains but they are powerful enough to set up most short url configurations.

Most linux distributions setup Apache with set of **sites-available/** and **sites-enabled/** folders setup. The correct config file to edit is the one in **/etc/apache2/sites-available/** where the configuration for your wiki has been setup. If you haven't set one up and are using the default **/var/www** for your wiki setup then you can edit **/etc/apache2/sites-available/default**.

---

### Post by MocroNL on 2012-11-29
Thank you for the reply.

I have checked the sites-available/default but I got no clue what to do there. And where is htaccess located? I cannot find it in de apache map. 

Do you have a simple tutorial I can follow? It would make my life easier :)

Kind regards

---

### Post by slickymaster on 2012-11-29
See if this can help you: [Manual:Short URL/Apache]("http://www.mediawiki.org/wiki/Manual:Short_URL/Apache").

---

### Post by MocroNL on 2012-11-29
Already have tried to find something useful in that wiki page. It explains some of the things but not how you get the job done..

But thank you anyway.

If there is someone with a useful guide, howto or tutorial I could really use that.

Kind regards

---

### Post by pkadeel on 2012-11-29
one question; Do you intend to use those short urls for local use or internet use?
If all you want is local use then you need virtual host setup which is very easy. Is that what you want?

---

### Post by MocroNL on 2012-11-29
Yes! sorry I did not mention that.....

It is just for local use.

Kind regards.

---

### Post by pkadeel on 2012-11-29
create a new file using a text editor like gedit and put following code in it
```

<VirtualHost *:80>
               ServerName [COLOR=Red]s1.loc[/COLOR]
               ServerAdmin admin@[COLOR=Red]s1.loc[/COLOR]
               DocumentRoot /var/www/[COLOR=Red]site1[/COLOR]
               <Directory  /var/www/[COLOR=Red]site1[/COLOR]/>
                     Options Indexes FollowSymLinks
                     AllowOverride All
                    Order Deny,Allow
                    Allow from all
               </Directory>
               DirectoryIndex index.html
               ErrorLog ${APACHE_LOG_DIR}/[COLOR=Red]site1[/COLOR]-error.log
               CustomLog ${APACHE_LOG_DIR}/[COLOR=Red]site1[/COLOR]-access.log" combined
</VirtualHost>

```Save this file in your Documents folder and name it '[COLOR=Red]site1[/COLOR]'
"/var/www/[COLOR=Red]site1[/COLOR]" folder must be present before proceeding. You can use any path on your computer where you want to keep the files related to this site. if this path is not present then then create it first.
Now in terminal do
```

cd ~/Documents
sudo cp [COLOR=Red]site1[/COLOR] /etc/apache2/sites-available/[COLOR=Red]site1[/COLOR]
sudo a2ensite [COLOR=Red]site1[/COLOR]
sudo service apache2 restart
gksu gedit /etc/hosts

```after last command gedit will open a file with few lines containing
```

127.0.0.1       localhost
127.0.1.1       tls-ams-sgr-01
and few other lines
```add to that file and save it. Do not remove any thing already present in that file.
```

127.0.0.1     [COLOR=Red]s1.loc[/COLOR]

```now in your browser type [http://[COLOR=Red]s1.loc[/COLOR]]("http://s1.loc")

---

### Post by MocroNL on 2012-11-29
Thank you for the reply! I will try this in a moment.

But is this the way to make a link like tls-ams-sgr-01/SugarCRM. Because its an already working link.

To just sugarcrm/ ??

Kind regards

---

### Post by pkadeel on 2012-11-29
> **MocroNL said:**
> Thank you for the reply! I will try this in a moment.

But is this the way to make a link like tls-ams-sgr-01/SugarCRM

To just sugarcrm/ ??

Kind regards
Yes. my post above replace all occurrences of "s1.loc" and "site1" with "sugarcrm".
I assume that you have a folder named "SugarCRM" in /var/www. Also rename that folder to "sugarcrm"

---

### Post by MocroNL on 2012-12-14
Mission completed ! 

Thanks guys.

---

