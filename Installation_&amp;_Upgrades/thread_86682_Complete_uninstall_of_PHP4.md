---
title: "Complete uninstall of PHP4?"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by iluminate on 2005-11-06
Hi all,
I'm on my way to install PHP5 and Mysql5.
But how do I uninstall PHP4 and all modules the easiest way?
Yes I can uncheck every package that has something to do with PHP in Synaptic,
but is this really the right way to go?
Any help with an explanation or a link to a "how-to" would really be appricated.

Cheers!

---

### Post by heimo on 2005-11-06
It should be sufficient to
```
sudo apt-get install php5
```

This will remove libapache2-mod-php4 php4 and then
```
sudo apt-get remove php4-common
```

Or, you could first:
```
sudo apt-get --purge remove libapache2-mod-php4 php4 php4-common
``` Note that this will also purge any related configuration files and it may not be what you want to do. At least backup any self edited configuration files before doing this, or omit --purge flag.

And then explicitely install:
```
sudo apt-get install libapache2-mod-php5 php5 php5-common
```

Or... Remove the packages using Synaptic Package Manager and then install the 5-versions.

---

### Post by iluminate on 2005-11-06
Thank you very much for the promt reply and help. Very much appreciated.
I'm on my way to complete ditch Gates and go for linux.
It takes time though to learn everything, almost like learning how to ride a bike once again. :)

I have one more question though. In Synaptic you have something called "Mark for removal" and "Mark for Complete removal" <<
What is the difference?

Thanks to you I have now installed PHP5, but as always there is something that's not working. If I type in [http://localhost/phpinfo.php](http://localhost/phpinfo.php) I recieve the info about PHP but when I type in my ip [http://myip/phpinfo.php](http://myip/phpinfo.php) I get "save file as"...How is this really possible??
I have stoped and restarted the apache so I dont think that's the issue.

Once again, many thanks !
Cheers

---

### Post by heimo on 2005-11-06
[quote=iluminate]

I have one more question though. In Synaptic you have something called "Mark for removal" and "Mark for Complete removal" <<
What is the difference?
[/quote] 
I don't use Synaptic, but my guess is the difference is same as between apt-get remove and apt-get --purge remove, however I might be completely wrong. (*starts Synaptic, lets see...*) Yeah, that's it - "complete removel" will remove configuration too. Regular removal doesn't remove related config files (thus making it easier to reinstall later with same settings).
 
[quote=iluminate]
Thanks to you I have now installed PHP5, but as always there is something that's not working. If I type in [http://localhost/phpinfo.php]("http://localhost/phpinfo.php") I recieve the info about PHP but when I type in my ip [http://myip/phpinfo.php]("http://myip/phpinfo.php") I get "save file as"...How is this really possible??
[/quote] 
For starters you could enable mime-magic
```
sudo a2enmod mime_magic
sudo /etc/init.d/apache2 force-reload

``` 
If that doesn't help, you could try to telnet into 80,
```
telnet [yourserverip] 80
GET /phpinfo.php HTTP/1.0
[hit enter couple times]

``` This way you'll see the headers your server is sending. What's the content-type?

---

### Post by iluminate on 2005-11-06
Thanks for the tip about Telnet :)

From now on I will clear my Browser cache more often << That was the problem *mad*

Btw the output from telnet was just fine :

```
<tr class="h"><th colspan="2">HTTP Request Headers</th></tr>
<tr><td class="e">HTTP Request </td><td class="v">GET /phpinfo.php HTTP/1.0 </td></tr>
<tr class="h"><th colspan="2">HTTP Response Headers</th></tr>
<tr><td class="e">X-Powered-By </td><td class="v">PHP/5.0.5-2ubuntu1 </td></tr>
<tr><td class="e">Connection </td><td class="v">close </td></tr>
<tr><td class="e">Content-Type </td><td class="v">text/html; charset=UTF-8 </td></tr>
 
```

Thanx again! Now I will dig my hands dirty installing Mysql5. Does someone know if there exists a HowTo or tutorial?

Cheers!

---

