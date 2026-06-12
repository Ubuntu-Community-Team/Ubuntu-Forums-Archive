---
title: "Ubuntu 10.04 - LAMP php5 userdir"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by rusty0101 on 2010-05-10
So you migrated your primary webserver to 10.04 LTS and suddenly your users are complaining that their userdir php pages are not working. They keep being asked to download their php pages or phtml, or whatever. Their user blogs are not working. You have unhappy users, and by this time you are probably one as well.

This may have come up in an earlier upgrade, but whether it is 9.10-10.04 or 8.04lts-10.04lts only is pretty irrelevant. You're feeling the pain.

You have two choices. Tell your users to move to a dedicated hosting environment of their own, or re-enable php scripting in the apache web server.

```

sudo nano /etc/apache2/mods-available/php5.conf

```

Look for the lines that look like:
```

    <IfModule mod_userdir.c>
        <Directory /home/*/public_html>
            php_admin_value engine Off
        </Directory>
    </IfModule>

```

and change em to look like:
```

#    <IfModule mod_userdir.c>
#        <Directory /home/*/public_html>
#            php_admin_value engine Off
#        </Directory>
#    </IfModule>

```

then restart apache. 
```

sudo service apache2 restart

```
or 
```

sudo /etc/init.d/apache2 restart

```
whichever you are more comfortable with.

And tell your users that they may need to restart their browsers. (or if they can figure out how, clear their web cache.)

I'll grant that there very likely are very good reasons not to allow users to do scripting in their home directories over the web. But you were not disallowing it before, were staying up to date on security issues, and had this solution shoved down your throat without any notice that it was going to happen. It might be a good time to review the decision and perhaps tell those script running freeloaders on your server, aka customers, to take a hike. But that should be your decision.

-Rusty

---

### Post by lykwydchykyn on 2010-05-25
Thanks for posting this; same happened to me and drove me nuts.  Who in the heck thought this change was a good idea?

---

### Post by ameseisch on 2010-05-28
Hmmmm... seemed like a perfect solution, worked flawlessly on of my systems that had been upgraded from 9.10 to 10.04, but not so well on another system that was a fresh install of 10.04. It did work, but had to rename directories or clear out all history and cookies related to localhost before I could see that it worked - browser and system restart didn't cut it.

---

### Post by borgg on 2010-07-23
Thanks for posting the solution worked for me!

---

### Post by fansico on 2010-09-07
Yeah! I got the same problem! Why do they disable php on user dir after upgrading?

Anyway, thanks for you solution!

---

### Post by imilanez on 2011-01-04
I've tried to implement this solution and still get the following message:

Forbidden

You don't have permission to access /~imilanez/index.php on this server.

Any ideas?

TIA

---

### Post by ScruffyReid on 2011-01-21
I am still having problems with this.  I have confirmed that I have the correct lines commented out as listed above.  My userdir works for html files, but anytime I try to create a test php file in my userdir, the browser just tries to download it.  

This is a server that has been upgraded several times all the way back to 6.04. 

Any ideas?

---

### Post by wijit on 2012-04-13
> **ScruffyReid said:**
> I am still having problems with this.  I have confirmed that I have the correct lines commented out as listed above.  My userdir works for html files, but anytime I try to create a test php file in my userdir, the browser just tries to download it.  

This is a server that has been upgraded several times all the way back to 6.04. 

Any ideas?

I have not only the same problems but php tag is not processed even in the web root directory (/var/www/). Please help.

---

### Post by lykwydchykyn on 2012-04-13
> **wijit said:**
> I have not only the same problems but php tag is not processed even in the web root directory (/var/www/). Please help.

If it's not working in /var/www, you have a completely different problem.  I'd suggest making a new thread.

---

### Post by wijit on 2012-04-13
> **wijit said:**
> I have not only the same problems but php tag is not processed even in the web root directory (/var/www/). Please help.

Apologise for all. All systems might work since installed. It's me who was not careful enough. I wrote "<php?" instead of "<?php". Cheers!

---

