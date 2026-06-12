---
title: "Apache2, Perl, and CGI"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by sog on 2006-06-07
this is undoubtedly a fairly simple apache configuration issue, but since i'm not entirely clear on how Ubuntu manages Apache i figured it'd be safer to ask then try and figure it out. didn't turn up the answer crawling through the forums. 

so the question is this: 

i'm using Ubuntu as a LAMP server, and when installing LTS i selected the "Install LAMP Server" option. so far, so good. Apache works, PHP works, etc. 

but i'm currently trying to get Movable Type set up on the box (yes, i'd prefer to use Wordpress, but can't at the present time), and my instance of Apache is render the MT Perl CGI files as text. it's simply displaying the text of the scripts rather than executing them. 

i've tried installing libapache2-mod-perl2 and libapache-mod-perl, then reloading apache but nothing doing. 

sudo a2enmod tells me that the cgi module for Apache is installed and enabled, as is cgid, so i can't figure out what else i need to do to get Apache to execute my Perl scripts. 

any ideas?

---

### Post by sog on 2006-06-07
forgot to add that i have chmodded the .cgi files in question, so that's not it.

one more thing i forgot to mention:

apparently this problem can be a result of uploading perl scripts in binary rather than ASCII fashion, but my MT implementation was uploaded to the server as a tar file via scp. my understanding is that zipped files must be transferred as binaries anyhow, so i don't think that's the problem.

---

### Post by sog on 2006-06-07
figured it out. in /etc/apache2.conf, you need to uncomment the line below:

# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi

to 

# To use CGI scripts outside /cgi-bin/:
#
AddHandler cgi-script .cgi

if you start getting 403 errors for trying to run scripts out of other directories, you can add the following to your /etc/apache2/sites-available/default file:

        ScriptAlias /yourdir/ /your/dir/here/
        <Directory "/your/dir/here">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


hth.

---

### Post by SneakyWho_am_i on 2008-05-14
lol, and remember to restart apache!!
I was pulling my hair out because I just couldn't get cgi running, it made no sense at all!!

```
sudo /etc/init.d/apache2 force-reload
```

Whew!

Yeah I know it was an old post but I was looking for answers.. And if I am then someone else will be too....

---

### Post by jcahn2 on 2008-05-21
Thanks,

This also stumped me for a week.  That expression 
AddHandler cgi-script .cgi
was nowhere in my default apache2.conf so I just added it.

Jack

---

