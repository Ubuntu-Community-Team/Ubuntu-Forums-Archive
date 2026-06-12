---
title: "Need a little help please"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Tagati on 2008-03-23
Hi all ... iam still kinda new to linux and ubuntu, but here is my problem .. ive installed ubuntu server 6.06 and then installed the lamp setup which went fine :-) but now when i load the index page ( home page ) all i get is Index of / page and not my home page which i uploaded to /var/www. What do i need to do to change this so that when people use my Url [www.revisitedimage.com](www.revisitedimage.com) they see the right page ?? any help with this would be great as i think its some thing to do with the configuration on apache.

---

### Post by buntu_Geek on 2008-03-23
open the following document in your favorite editor....

/etc/apache2/sites-available/default

change the place where you have

DocumentRoot <some other path..>
to 
DocumentRoot /var/www

if not present add it... inside the <VirtualHost *> tag

and please note that i am giving the procedure for apache2
So if you are using earlier versions... change the path for that default document....

Hope that helps..

---

### Post by Tagati on 2008-03-23
Thanks for the reply, but when i went into the file it was allrdy done :-( at the bottom of the file was this  Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

should i change the ip address to my server address ?

---

### Post by buntu_Geek on 2008-03-23
Those are the ips that your server has to listen to....
u have to change it to all .. i mean change it to "allow from all"

and does that directory tag starts like this...
<directory /var/www >

??

---

### Post by buntu_Geek on 2008-03-23
Here i suggest you install apache2 on your server...

It has all the configs done....

And many how tos for apache 2 on [WWW..](WWW..)..

i ll catch you later... see yaa.. reply here if solved... :)

---

### Post by Tagati on 2008-03-23
I tryed to change it and now apache wont start :-( maybe i need to start again, is there a good howto out there for 6.06 server ? iam not to sure about useing bind9 but would like to do it all one step at a time.

---

### Post by buntu_Geek on 2008-03-23
Use force restart option...

And about the how to.... 

I have no experience of working with a Ubuntu server.....
so will post here when i find a good how to....

---

### Post by Tagati on 2008-03-23
Thanks guys for the help :-) ive found this [http://ubuntuforums.org/showthread.php?t=650464](http://ubuntuforums.org/showthread.php?t=650464) and iam going to try it out :-) Is there any thing else i need to install aprt from the mail server side ? as in firewall or virus software ?

---

### Post by Pumalite on 2008-03-23
I found these 2:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by Tagati on 2008-03-24
Ok i used this to set the server up [http://www.howtoforge.org/perfect_setup_ubuntu_6.06](http://www.howtoforge.org/perfect_setup_ubuntu_6.06) and every thing went to plan, but i still get the index of/ page instead of the index.html page ive put in /var/www. When i type [http://192.168.1.50/Index.html](http://192.168.1.50/Index.html) i get the page up no problems. Ive been throw the points you made before and all seems ok, not to sure where ive gone wrong here ??

---

### Post by Tagati on 2008-03-24
Ive tryed a couple of other bits and now when i force restart apache i get httpd (pid 5543?) not running and it fails ?

---

### Post by Tagati on 2008-03-24
and now when i force restart apache i get httpd (pid 4196?) not running and it fails ?

---

### Post by Tagati on 2008-03-24
Ok .... i think the problem iam haveing is that the ports on my routers firewall  where closed when i installed ubuntu server OS, would this set up the config files wrong or will this make no difference ? as this seems the only thing ive done differant from before ??

---

### Post by buntu_Geek on 2008-03-24
you have to be sure that nothing else is running at the port number... at which you are listening....

---

